המקורות הבאים נבדקו לצורך הפרק. תקנים ו-Technical Reports מתעדכנים ומאומצים בצורה שונה לפי מדינה, ענף וחוזה. יש לאמת את המהדורה שחלה על הפרויקט לפני תכן או Commissioning.

1. **ISA-TR5.9-2023, Proportional-Integral-Derivative (PID) Algorithms and Performance.** מתעד צורות PID תעשייתיות נפוצות, אפשרויות מימוש ומדדי ביצועים. ISA מציינת שהמסמך נועד להניח בסיס לתקן עתידי משום שלא היה תקן יחיד שמגדיר Fundamentals ו-Special Functions של PID. מקורות רשמיים: https://www.isa.org/standards-and-publications/isa-standards/isa-5-standard וגם https://www.isa.org/standards-and-publications/isa-standards/isa-standards-committees/isa5-9

2. **ANSI/ISA-5.1-2024, Instrumentation and Control - Symbols and Identification.** רלוונטי לזיהוי עקבי של Instruments ו-Loops במסמכי הנדסה. https://www.isa.org/standards-and-publications/isa-standards/isa-standards-committees/isa5

3. **IEC 61131-3:2025, Programmable controllers - Part 3: Programming languages.** מגדיר Syntax ו-Semantics של שפות PLC; אינו קובע שיטת Tuning אוניברסלית ל-PID. https://webstore.iec.ch/en/publication/68533

4. **Rockwell Automation Studio 5000 PID/PIDE documentation.** דוגמה ספציפית של יצרן ל-Dependent/Independent Gains, Output Limits, Derivative Smoothing, Anti-Reset Windup, Tracking ו-Bumpless Transfer. אינו דרישה אוניברסלית. https://www.rockwellautomation.com/en-us/docs/studio-5000-logix-designer/37-00/contents-ditamap/studio-5000-logix-designer/pid-configuration-dialog-box---configuration-tab-o.html וגם https://www.rockwellautomation.com/en-pr/docs/studio-5000-logix-designer/38-02/contents-ditamap/instruction-set/special-instructions/proportional-integral-derivative--pid-/anti-reset-windup-bumpless-transfer-manual-auto--p.html

5. **J. G. Ziegler and N. B. Nichols, "Optimum Settings for Automatic Controllers," 1942.** המקור ההיסטורי לכללי Process Reaction ו-Ultimate Gain. DOI: https://doi.org/10.1115/1.4019264

6. **Sigurd Skogestad, "Simple analytic rules for model reduction and PID controller tuning," Journal of Process Control 13 (2003) 291-309; גרסה מתוקנת/פתוחה ב-Modeling, Identification and Control 25(2), 2004.** מקור מרכזי ל-IMC/SIMC Tuning ול-Model Reduction. https://skoge.folk.ntnu.no/publications/2003/tuningPID/README.html

7. **E. Sundström, M. Bauer, J. L. Guzmán, T. Hägglund and K. Soltesz, "A Practical Guide to PID Controller Implementation," 2026 preprint.** דיון עדכני ב-Actuator Constraints, Measurement Noise, Bumpless Transfer ו-Sampling Time. https://arxiv.org/abs/2604.15918

8. **IEC 61511 series, Functional safety - Safety instrumented systems for the process industry sector.** משמשת כאן רק כדי לשמור את הגבול בין Regulatory Control לבין Safety Instrumented Functions. יש לקבוע Applicability לפרויקט בנפרד.
