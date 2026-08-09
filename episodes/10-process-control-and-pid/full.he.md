---
episode: 10
language: he
title: "בקרת תהליך ו-PID - דינמיקה, כוונון והתנהגות אמיתית של חוג בקרה"
target_duration: "42-45 minutes"
status: completed
generated: "2026-08-10"
---

# CONTROL EDGE - פרק 10
## בקרת תהליך ו-PID
### דינמיקה, משוב, כוונון, רוויה, Anti-Windup, Cascade ו-Feedforward

**קהל יעד:** מהנדסי מכונות, תהליך, ייצור, מכשור ואוטומציה  
**משך יעד:** 42-45 דקות  
**פורמט:** דו-שיח בין יעל, מהנדסת מכונות צעירה, לבין אמיר, מהנדס תהליך ובקרה ותיק  
**מקרה מרכזי:** חוג בקרת טמפרטורה במחליף חום שעושה Overshoot לאחר ששסתום הקיטור הגיע לרוויה, ולאחר מכן מתנהג לא נכון במעבר מ-Manual ל-Auto  
**גרסה:** 1.0 - אוגוסט 2026

חומר לימודי. אינו מחליף תכן תהליך, תכן מערכת בקרה, הערכת סיכונים, הוראות יצרן, נהלי Commissioning או מהדורת תקן החלה על הפרויקט.

# 1. בדיקת התאמה למסמך האב

פרק 9 עסק ב-SCADA, DCS, Historian ובאמינות המידע המפעלי. פרק 10 יורד בחזרה אל חוג הבקרה החי ושואל: אחרי שהשגנו מדידה שאפשר לסמוך עליה - מה הבקר צריך לעשות איתה?

הפרק נשאר בעולם ה-Regulatory Control הבסיסי והבינוני. הוא אינו הופך לקורס אקדמי בתורת הבקרה ואינו מנסה ללמד לעומק Model Predictive Control, State Estimation או Advanced Process Control. נושאים כאלה מוזכרים רק כדי להגדיר את גבולות ה-PID.

הפרק חייב:

- להסביר את דינמיקת התהליך לפני כוונון PID;
- להבחין בין תגובה לשינוי Setpoint לבין דחיית Disturbance;
- להבחין בין פעולות P, I ו-D לבין צורות האלגוריתם התעשייתיות השונות;
- להראות מדוע Saturation, מצב Manual, גבולות יציאה והתנהגות המפעיל הם חלק מהתכן;
- להסביר Anti-Windup ו-Bumpless Transfer כתכונות יישום חיוניות;
- להציג Cascade ו-Feedforward כהרחבות מעשיות לבקרת Feedback;
- להבהיר שאין סט יחיד של ערכי PID שהוא "נכון" לכל מערכת;
- לשמור על הפרדה ברורה בין בקרה רגולטורית לבין פונקציית בטיחות.

# 2. מטרות הפרק

בסיום הפרק המאזין אמור להיות מסוגל:

1. לזהות PV, SP, CV/MV ו-Disturbances בחוג תהליך.
2. להסביר Process Gain, Time Constant ו-Dead Time במונחים הנדסיים מעשיים.
3. להבחין בין תהליך Self-Regulating, תהליך Integrating והתנהגות לא-ליניארית.
4. להסביר מה תורמים P, I ו-D, ומדוע Derivative לעיתים מופעל על PV ולא על שגיאת ה-Setpoint.
5. להבין ש-Parallel, Standard ו-Series PID עשויים להשתמש בהגדרות פרמטרים שונות.
6. להסביר Saturation, Integral Windup, Anti-Windup ו-Bumpless Transfer.
7. להבין מתי Cascade ו-Feedforward משפרים ביצועים.
8. להשוות בין Ziegler-Nichols ההיסטורי לבין IMC/SIMC מבוסס מודל ו-Autotuning.
9. להגדיר ביצועי חוג מעבר ל"נראה יציב".
10. לבנות Checklist ל-Commissioning של חוג PID אמיתי.

# 3. חלוקת זמן

| זמן | נושא | מטרה |
|---|---|---|
| 00:00-03:00 | פתיחה - מחליף החום שלא הפסיק להתחמם | להמחיש Saturation ו-Windup לפני שמגדירים אותם |
| 03:00-07:00 | מה חוג תהליך באמת שולט עליו | PV, SP, CV/MV ו-Disturbance |
| 07:00-13:00 | דינמיקת תהליך לפני כוונון | Gain, Time Constant, Dead Time, Self-Regulating מול Integrating |
| 13:00-21:00 | P, I ו-D בלי מיתולוגיה | תרומת כל רכיב והאינטראקציה ביניהם |
| 21:00-26:00 | צורות PID תעשייתיות והבדלי יישום | Parallel, Standard, Series, Direction, Derivative |
| 26:00-32:00 | Saturation, Windup ומעברי Mode | Limits, Anti-Windup, Tracking, Bumpless Transfer |
| 32:00-37:00 | איך מכוונים חוג | Step Test, Ziegler-Nichols, IMC/SIMC, Autotune, Robustness |
| 37:00-41:00 | Cascade ו-Feedforward | הרחבות מעשיות עם מחליף החום |
| 41:00-45:00 | ביצועים, Commissioning וסיכום | מדדים, Checklist ומעבר לפרק 11 |

# 4. מפות הנדסיות

## 4.1 חוג בקרה רגולטורי

Process -> Sensor -> PV -> Controller -> CV/MV -> Final Control Element -> Process

Disturbances יכולים לכלול Feed Flow, Feed Temperature, תנאי סביבה, Utility Pressure, תכונות מוצר, Fouling ופעולות מפעיל.

## 4.2 מודל תהליך מעשי

להרבה חוגים תעשייתיים אפשר להשתמש בקירוב First-Order Plus Dead Time:

- **Process Gain (K):** שינוי ה-PV במצב יציב עבור שינוי קבוע ב-Manipulated Input באזור עבודה מסוים.
- **Time Constant (tau):** קצב התגובה האופייני לאחר שהתהליך מתחיל להגיב.
- **Dead Time (theta):** הזמן שעובר עד שהשפעת הפעולה מופיעה במדידה.

זהו מודל הנדסי מקורב ולא טענה שהתהליך האמיתי הוא מסדר ראשון.

## 4.3 הבקר הוא יותר ממשוואת P + I + D

יישום תעשייתי כולל גם Direction of Action, Sample/Update Time, Scaling, Setpoint ו-Output Limits, Derivative Filtering, Anti-Windup, Manual/Auto ו-Cascade Tracking, התנהגות מול Bad PV, Initialization ו-Restart.

## 4.4 לביצועים יש כמה מטרות

חוג יכול להיות Stable ועדיין להיות גרוע. יש לבחון Disturbance Rejection, Setpoint Tracking, Overshoot, Settling, Integrated Error, תנועת Actuator, Noise Amplification, Robustness, Constraints ואינטראקציה עם חוגים אחרים.

# 5. קובצי ההפקה

- **התסריט הקנוני להקראה:** [`script.he.txt`](script.he.txt)
- **הנחיית NotebookLM:** [`notebooklm_prompt.he.txt`](notebooklm_prompt.he.txt)
- **מפת תקנים ומקורות:** [`standards_and_sources.he.md`](standards_and_sources.he.md)

התסריט הוא חלק ממקור האמת של הפרק ויש לבצע Review שלו יחד עם מסמך זה.

# 6. הערות למפיק ולמגישים

- לשמור את הפתיחה קונקרטית ולא להשתמש במונח Windup לפני שהמאזין מדמיין שסתום ב-100% ותגובה תרמית מאוחרת.
- לא להפוך את K, tau ו-theta להרצאה מתמטית; הם כלים לחשיבה הנדסית.
- בהסבר על PID Forms להדגיש סיכון במיגרציה: שדות שנראים זהים יכולים להשתמש ביחידות או במשוואות שונות.
- להציג Ziegler-Nichols בכבוד כשיטה היסטורית חשובה, אך לא כמתכון אוניברסלי.
- לא לטעון ש-Cascade חייב יחס מהירויות קבוע של 3:1 או 5:1; יש לאמת Dynamics בפועל.
- לשמור הפרדה מפורשת בין Regulatory Control לבין פונקציית Safety עצמאית.

# 7. מילון מונחים

| מונח | משמעות בפרק |
|---|---|
| PV | Process Variable - המשתנה התהליכי הנמדד שאותו רוצים לבקר |
| SP | Setpoint - הערך הרצוי של ה-PV |
| CV / MV | Control Variable / Manipulated Variable - פלט הבקר או המשתנה הפיזיקלי שמניעים |
| Disturbance | השפעה על התהליך שאינה פקודה ישירה של החוג |
| Process Gain | יחס שינוי PV במצב יציב לשינוי קבוע בקלט באזור עבודה |
| Time Constant | מהירות התגובה האופיינית לאחר שהתהליך מתחיל להגיב |
| Dead Time | השהיה עד שהשפעת הפעולה נראית במדידה |
| Self-Regulating Process | תהליך שמתקרב למצב יציב חדש עבור קלט קבוע |
| Integrating Process | תהליך שה-PV שלו ממשיך להשתנות כל עוד קיים חוסר איזון קבוע |
| Saturation | מצב שבו דרישת ה-Output מגיעה לגבול פיזי או מוגדר |
| Integral Windup | צבירת מצב Integral בזמן שהמפעיל אינו מסוגל לממש את הדרישה |
| Anti-Windup | לוגיקה שמונעת או מתקנת צבירה לא ריאלית בזמן מגבלה |
| Bumpless Transfer | מעבר Mode שנועד למנוע Step לא רצוי ב-Output |
| Cascade Control | Outer Controller מספק Setpoint ל-Inner Controller מהיר יותר |
| Feedforward | פעולה על סמך Disturbance מדוד לפני שנוצרת שגיאת Feedback |
| IAE | Integral of Absolute Error - מדד אפשרי לביצועי חוג |
| IMC/SIMC | גישות Tuning מבוססות מודל ועקרונות Internal Model Control / כללי Skogestad |

# 8. תקנים ומקורות

יש להשתמש ב-[`standards_and_sources.he.md`](standards_and_sources.he.md). המקורות המרכזיים כוללים ISA-TR5.9-2023 לצורות PID ולמינוח יישומי, IEC 61131-3:2025 לשפות בקרים, תיעוד יצרן כדוגמאות יישום, עבודת Ziegler-Nichols ההיסטורית, כללי SIMC של Skogestad וספרות עדכנית על יישום PID בעולם האמיתי.

# 9. Quality Gate לפרק

- המאזין יכול לזהות PV, SP, CV/MV ו-Disturbances בחוג אמיתי.
- דינמיקת התהליך מוסברת לפני ערכי PID.
- קיימת הפרדה בין Tuning לבין Anti-Windup, Tracking ושאר תכונות היישום.
- צורות PID מוצגות כתלויות Implementation; אין הצגה של ערכים מספריים כניידים בין יצרנים.
- Ziegler-Nichols, Model-Based Tuning ו-Autotuning מוצגים כגישות עם Trade-Offs ולא כמתכונים אוניברסליים.
- Cascade ו-Feedforward מוסברים באמצעות סיבה פיזיקלית ברורה.
- Regulatory Control אינו מוצג כתחליף לפונקציית Safety עצמאית.
- הסיום מוביל ישירות לפרק 11 על איכות תוכנה, Simulation ו-Validation.
