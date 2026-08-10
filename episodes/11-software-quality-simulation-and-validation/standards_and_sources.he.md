# מפת תקנים ומקורות - פרק 11

> תקנים מתעדכנים ומאומצים באופן שונה לפי מדינה, ענף וחוזה. לפני שמציגים ניסוח כדרישה מחייבת יש לאמת את המהדורה, Amendments והמעמד המשפטי החלים על הפרויקט. הפרק מסביר ומסכם מושגים ואינו משכפל טקסט נורמטיבי.

1. **IEC 62381:2024 - Automation systems in the process industry - Factory acceptance test (FAT), site acceptance test (SAT), and site integration test (SIT).** המהדורה השלישית הנוכחית. מגדירה Requirements ו-Checklists ל-FAT, ל-Factory Integration Test (FIT) אופציונלי, ל-SAT ול-SIT. מקור מרכזי לדיון בבדיקות קבלה בפרק.
2. **IEC 61131-3:2025 - Programmable controllers - Part 3: Programming languages.** המהדורה הרביעית הנוכחית. מגדירה Syntax ו-Semantics ל-ST, LD, FBD ואלמנטים של SFC. היא בסיס שפות התכנות, אך אינה לבדה תקן מחזור-חיים מלא לאיכות תוכנה.
3. **PLCopen Software Construction Guidelines** ו-**PLCopen Guideline on Software Quality Metrics (2023).** הנחיות לתכנון מובנה, Rules, Coding Patterns, Libraries ומדדי איכות בסביבות IEC 61131-3 / PLCopen.
4. **ISO/IEC/IEEE 29119-1:2022** ו-**ISO/IEC/IEEE 29119-2:2021 - Software testing.** מושגים ותהליכי Test כלליים החלים על מודלים שונים של מחזור חיי תוכנה. אינם תקני אוטומציה ייעודיים, אך שימושיים למינוח ולמבנה תהליך הבדיקות.
5. **IEC 61508-3:2010 - Functional safety - Software requirements.** עוסק בתוכנה של מערכות Safety-Related E/E/PE וכולל Lifecycle Activities, Validation Information, Modification Control ודרישות לכלי פיתוח תומכים.
6. **ISO 13849-1:2023 - Safety of machinery - Safety-related parts of control systems - Part 1.** כולל Software במתודולוגיית התכן והאינטגרציה של מערכות בקרה בטיחותיות למכונות.
7. **ISO 13849-2:2012 - Part 2: Validation.** עדיין המהדורה המפורסמת הנוכחית באוגוסט 2026; מהדורה מחליפה נמצאת בפיתוח. עוסק ב-Validation באמצעות Analysis ו-Testing של פונקציות בטיחות וה-PL/Category שהושגו.
8. **IEC 62061:2021 + AMD1:2024 + AMD2:2026.** המסגרת המאוחדת הנוכחית לבטיחות פונקציונלית של Safety-Related Control Systems במכונות, כולל Design, Integration, Verification, Validation ו-Configuration Management.
9. **IEC 62832-1/-2/-3:2020 - Digital Factory framework.** עקרונות, Model Elements וכללים לניהול מידע לאורך מחזור החיים של מערכות ייצור בתהליכים רציפים, Batch ו-Discrete.
10. **ISO 23247 series - Digital twin framework for manufacturing.** Parts 1, 2 ו-4 משנת 2021 עוסקים בעקרונות, Reference Architecture ו-Information Exchange; Parts 5 ו-6 משנת 2026 מוסיפים Digital Thread ו-Digital-Twin Composition. רלוונטי להבחנה בין Simulation Model לבין Digital Twin רחב יותר.

## עוגנים הנדסיים לפרק

- ה-V-Model מוצג כ-Pattern שימושי לחיבור בין רמות דרישה ורמות בדיקה, לא כמחזור חיים מחייב לכל פרויקט אוטומציה.
- Unit Test, Software-in-the-Loop, Hardware-in-the-Loop ו-Virtual Commissioning מוצגים כשכבות Evidence עם Fidelity עולה.
- Fidelity של Model צריך להתאים לשאלה ההנדסית. Model לבדיקת Sequence לוגי לא חייב דיוק דינמי של Model לכוונון Loop.
- Requirements Coverage, State-Transition Coverage ו-Regression Scope מבוסס סיכון חשובים יותר מאחוז Code Coverage אוניברסלי אחד.

## Official source links
- IEC 62381:2024: https://webstore.iec.ch/en/publication/67572
- IEC 61131-3:2025: https://webstore.iec.ch/en/publication/68533
- PLCopen Software Construction Guidelines: https://www.plcopen.org/guidelines/software-construction-guidelines/
- PLCopen Guideline on Software Quality Metrics: https://www.plcopen.org/news/plcopen-guideline-on-software-quality-metrics/
- ISO/IEC/IEEE 29119-1:2022: https://www.iso.org/standard/81291.html
- ISO/IEC/IEEE 29119-2:2021: https://www.iso.org/standard/79428.html
- IEC 61508-3:2010: https://webstore.iec.ch/en/publication/5517
- ISO 13849-1:2023: https://www.iso.org/standard/73481.html
- ISO 13849-2:2012: https://www.iso.org/standard/53640.html
- IEC 62061:2021 + AMD1:2024 + AMD2:2026: https://webstore.iec.ch/en/publication/112847
- IEC 62832-1/-2/-3:2020: https://webstore.iec.ch/en/publication/65858
- ISO 23247 series: https://www.iso.org/standard/75066.html
