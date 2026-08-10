---
episode: 11
language: he
title: "איכות תוכנה, סימולציה ו-Validation - איך מוכיחים שתוכנת בקרה באמת מוכנה למפעל"
target_duration: "42-46 minutes"
status: completed
---

# CONTROL EDGE - פרק 11
## איכות תוכנה, Simulation ו-Validation
### איך מוכיחים שתוכנת בקרה באמת מוכנה לפגוש את המכונה והמפעל

**קהל יעד:** מהנדסי מכונות, תהליך, ייצור, מכשור ובקרה ואינטגרטורים  
**משך יעד:** 42-46 דקות  
**פורמט:** שיחה בין יעל - מהנדסת מכונות צעירה - לבין אמיר - מהנדס תהליך ובקרה ותיק  
**מקרה מרכזי:** סקיד העברה שעובר FAT רגיל, אך לאחר תקלה רגעית ב-Remote I/O חוזר מ-Retained State ומפעיל משאבה לפני ששסתום היציאה פתוח לגמרי  
**גרסה:** 1.0 | אוגוסט 2026

חומר לימודי. אינו מחליף תכן פרויקטלי, הערכת סיכונים, Test Specification חוזי, הוראות יצרן או מהדורת התקן החלה על הפרויקט.

# 1. בדיקת התאמה למסמך האב

הפרק ממשיך ישירות את פרק 10. פרק 10 הסתיים בשאלה: אחרי שבנינו Control Logic ו-PID Tuning, איך מוכיחים שהמערכת מתנהגת נכון ב-Startup, Shutdown, Fault, Restart ואחרי שינוי עתידי? פרק 11 עונה על השאלה באמצעות מחזור חיים מסודר של Software Quality, Testing ו-Acceptance.

גבולות הפרק:
- מתמקד באיכות ובדיקות של Basic Control.
- Functional Safety מוזכר רק כדי להגדיר גבול אחריות; העומק שייך לפרק 13.
- Secure Development מוזכר רק כגשר; Industrial Cybersecurity שייך לפרק 12.
- Simulation ו-Digital Twin מוצגים ככלים הנדסיים שדורשים הגדרת Fidelity ולא כמונחי שיווק.
- התוכן Vendor-Neutral ורלוונטי ל-PLC, PAC, DCS ו-Industrial PC.

# 2. מטרות למידה

בסיום הפרק המאזין יוכל:
1. להבחין באופן מעשי בין Verification, Validation ו-Acceptance.
2. להפוך דרישה עמומה לדרישה שניתן לבדוק.
3. לבנות Traceability מדרישה דרך קוד ועד Test Evidence.
4. להפריד בין Unit, Integration, System ו-Acceptance Tests.
5. לתכנן בדיקות ל-Boundaries, State Transitions, Faults, Recovery, Persistence, Timing ו-Concurrency.
6. להסביר את ההבדל בין Forcing, Software-in-the-Loop, Hardware-in-the-Loop ו-Virtual Commissioning.
7. להסביר למה גם Simulation Model צריך Scope ו-Fidelity מוגדרים.
8. להבחין בין FAT, FIT, SAT ו-SIT ומה כל אחד אמור להוכיח.
9. לבנות Regression ו-Release Process מבוססי סיכון לשינויים עתידיים.
10. לזהות איפה מסתיימת בדיקת Basic Control ומתחיל Safety Validation.

# 3. מבנה זמן

| זמן | מקטע | מטרה |
|---|---|---|
| 00:00-03:00 | פתיחה - ה-Reset שאף אחד לא בדק | להראות למה Happy Path לא מספיק. |
| 03:00-07:00 | מהי איכות תוכנה | להגדיר איכות כ-Evidence לאורך מחזור החיים. |
| 07:00-12:00 | דרישות שניתנות לבדיקה | לחבר Requirements, States ו-Traceability. |
| 12:00-17:00 | Review ו-Static Checks | לתפוס תקלות לפני הרצה דינמית. |
| 17:00-23:00 | Test Architecture | Unit, Integration, System, Acceptance, Boundaries ו-Faults. |
| 23:00-26:00 | Timing ו-Data Quality | להוסיף Temporal Behavior, Timestamps, Forces ו-Stale Data. |
| 26:00-31:00 | Simulation ו-Virtual Commissioning | לבנות מדרג Fidelity מ-Signal Injection עד HIL. |
| 31:00-36:00 | FAT, FIT, SAT ו-SIT | להפריד מטרות וקבלת מערכת. |
| 36:00-38:00 | Defect Control | להפוך Test שנכשל ל-Evidence הנדסי נשלט. |
| 38:00-41:00 | Regression ו-Release Control | להפוך שינוי עתידי לשחזור ו-Reversible. |
| 41:00-44:00 | גבול Safety Software | להסביר למה Safety דורש Lifecycle מחמיר יותר. |
| 44:00-46:00 | Checklist וסגירה | לסכם ולעבור לפרק הסייבר. |

# 4. שרשרת הראיות של איכות תוכנה

| שכבה הנדסית | Artifact מרכזי | השאלה | Evidence טיפוסי |
|---|---|---|---|
| צורך | User / Operational Requirement | מה התוצאה שנדרשת? | URS, תרחישי תפעול |
| התנהגות מערכת | Functional Requirements | מה המערכת צריכה לעשות? | FDS, Sequence, Cause & Effect |
| ארכיטקטורה | Modules ו-Interfaces | מי אחראי על מה? | Software Architecture, Interface Map |
| מימוש | PLC/DCS/HMI Code | האם מומש לפי התכן? | Code Review, Static Analysis, Unit Test |
| Integration | תתי-מערכות | האם ה-Interfaces עובדים יחד? | Integration Test, SIL/HIL |
| System | אפליקציה מלאה | האם Modes ו-Faults עובדים נכון? | System Simulation, Regression Suite |
| Acceptance | Demonstration חוזי | האם קריטריוני הקבלה הוכחו? | FAT/FIT/SAT/SIT |
| Operation/Change | Released Baseline | האם אפשר לשנות בלי לאבד Behavior ידוע? | Version Control, Impact Analysis, Regression, Rollback |

# 5. נכסי ההפקה הקנוניים

הדיאלוג המלא נמצא ב-[`script.he.txt`](script.he.txt). הנחיית NotebookLM נמצאת ב-[`notebooklm_prompt.he.txt`](notebooklm_prompt.he.txt), ומפת התקנים והמקורות עם קישורים רשמיים נמצאת ב-[`standards_and_sources.he.md`](standards_and_sources.he.md).

התסריט הקנוני כולל:
- תקלת Reset/Recovery כחוט מקשר;
- Verification מול Validation מול Acceptance;
- Requirements שניתנים לבדיקה ו-Requirement IDs;
- V-Model כ-Pattern הנדסי ולא כ-Lifecycle מחייב;
- Design Review, Code Review ו-Static Analysis;
- Unit, Integration, System ו-Acceptance Tests;
- Boundary Values, State Transitions, Fault Injection, Persistence ו-Concurrency;
- Test Oracle, Requirements Coverage ושימוש זהיר ב-Code Coverage;
- Timing, Determinism, Data Quality, Forces ו-Overrides;
- Software-in-the-Loop, Hardware-in-the-Loop ו-Virtual Commissioning;
- Model Fidelity והסיבה שגם Model צריך Validation;
- FAT, FIT אופציונלי, SAT ו-SIT;
- Defect Records, Deviations ו-Retest;
- Impact Analysis, Regression Suite, Baselines, Release IDs ו-Rollback;
- הגבול בין Testing של Basic Control לבין Functional-Safety Validation;
- צ'קליסט 12 שאלות לפני Release וגשר לפרק 12.

# 6. מטריצת Test Design מעשית

| משפחת בדיקות | דוגמה בסקיד | למה זה חשוב |
|---|---|---|
| Nominal | התחלת Transfer עם כל Permissives תקינים | מאמת Behavior ייצור רגיל |
| Boundary | Level בדיוק בגבול Start מינימלי | חושף שגיאות השוואה |
| State Transition | Stop בזמן תנועת שסתום ואז Reset | חושף Transition Logic חסר |
| Fault Injection | אובדן I/O Quality לשסתום ל-3 שניות | בודק Detection ו-Recovery |
| Persistence | Power Cycle באמצע Transfer | מאמת Retained מול Reinitialized State |
| Concurrency | שני Sequences מבקשים משאבה משותפת | חושף Ownership ו-Arbitration |
| Timing | Feedback מגיע ליד Timeout | חושף Race Conditions והנחות זמן |
| Communication | ניתוק Controller-Remote I/O | בודק Stale/Bad Data Handling |
| Operator Action | פקודה Manual בזמן Auto Fault | בודק Mode Ownership |
| Regression | הרצת הכל אחרי שינוי Valve Block | מגלה Side Effects של שינוי |

# 7. צ'קליסט 12 שאלות לפני Release

1. האם הדרישות Observable ו-Testable?
2. האם כל דרישה חשובה Traceable לקוד ול-Test Evidence?
3. האם Restart, Retained Data ו-Mode Transitions נבדקו?
4. האם Negative Paths ו-Recovery נבדקו?
5. האם מהנדס נוסף ביצע Review לארכיטקטורה ולקוד?
6. האם Test Environment ו-Software Versions מתועדים?
7. האם Fidelity של ה-Simulation Model מתועד ומאומת היכן שנדרש?
8. האם Unit, Integration, System ו-Acceptance Tests מופרדים לפי מטרה?
9. האם FAT כולל Faults ו-Recovery ולא רק Normal Operation?
10. האם SAT/SIT אימתו מחדש Wiring, Actuators, Networks ו-Interfaces באתר?
11. האם לכל שינוי יש Impact Analysis, Regression Evidence ו-Rollback?
12. האם פונקציות Safety-Related מטופלות במסגרת Safety Lifecycle המתאים?

# 8. מילון מונחים

| מונח | משמעות בפרק |
|---|---|
| Verification | ראיה שהדרישות שהוגדרו לתכן או למימוש מולאו נכון. |
| Validation | ראיה שהמערכת המשולבת עונה לצורך ולשימוש המיועד בהקשר האמיתי. |
| Acceptance | הסכמה חוזית/פרויקטלית שהקריטריונים שהוגדרו הוכחו. |
| Test Oracle | התוצאה הצפויה המתועדת שמאפשרת לקבוע Pass/Fail. |
| Regression Test | הרצה מחדש של בדיקות שעברו בעבר כדי לזהות Side Effects אחרי שינוי. |
| SIL | בהקשר הסימולציה בפרק: Software-in-the-Loop; לא להתבלבל עם Safety Integrity Level. |
| HIL | Hardware-in-the-Loop - בקר פיזי מול Plant Simulated. |
| Virtual Commissioning | בדיקת מערכת האוטומציה מול Model וירטואלי לפני אתר. |
| Model Fidelity | מידת הדיוק של ה-Model ביחס למאפיינים החשובים למטרת הבדיקה. |
| FAT / FIT / SAT / SIT | שכבות Factory Acceptance / Factory Integration / Site Acceptance / Site Integration. |
| Traceability | היכולת לקשר צורך, דרישה, מימוש ו-Test Evidence. |
| Baseline | גרסה מזוהה ומבוקרת שמשמשת Reference. |
| Impact Analysis | הערכת ההשפעה האפשרית של שינוי מוצע. |

# 9. תקנים ומקורות

ראה [`standards_and_sources.he.md`](standards_and_sources.he.md). העוגנים המרכזיים כוללים IEC 62381:2024, IEC 61131-3:2025, PLCopen Software Construction Guidelines ו-Software Quality Metrics, ISO/IEC/IEEE 29119-1/-2, IEC 61508-3, ISO 13849-1/-2, IEC 62061, IEC 62832 ו-ISO 23247.

# 10. שער איכות לפרק

- הפרק מסביר למה Happy-Path FAT לבדו אינו מספיק.
- Requirements, Implementation ו-Test Evidence מחוברים ב-Traceability.
- Static Review ו-Dynamic Testing מופרדים בבירור.
- רמות Simulation מובחנות בלי שימוש יתר במונח Digital Twin.
- FAT/FIT/SAT/SIT מקבלים מטרות שונות.
- Regression מחובר ל-Version Control, Impact Analysis ו-Rollback.
- תקני Functional Safety מוצגים כגבול Lifecycle מחמיר יותר ולא ככללי Test כלליים ל-PLC.
- הסיום יוצר מעבר ישיר לפרק 12 על Industrial Cybersecurity.
