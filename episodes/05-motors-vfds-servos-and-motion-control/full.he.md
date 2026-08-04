---
episode: 5
language: he
title: "מנועים, VFD, סרוו ובקרת תנועה"
target_duration: "42-45 minutes"
status: completed
extracted_from: docx
---

> CONTROL EDGE \| פרק 5<br>מנועים, VFD, סרוו ו-Motion Control<br>משליטה במהירות ועד תנועה מדויקת ומתואמת של המכונה<br>מנועי השראה \| Vector Control \| חוגי Servo \| פרופילי תנועה \| Safe Motion \| Regeneration

| קהל יעד | מהנדסי מכונות, תהליך, ייצור, מכשור, חשמל ואוטומציה |
| --- | --- |
| משך יעד | 42-45 דקות |
| פורמט | יעל - מהנדסת מכונות צעירה; אמיר - מהנדס תהליך ובקרה ותיק שהגיע מעולם המכונות |
| דוגמת ליבה | מסוע אינדוקס חורג מהמיקום ונכשל ב-DC Bus Overvoltage בזמן האטה |
| תוצר | תסריט מלא + הנחיית NotebookLM + מפות החלטה + Checklist הפעלה + מקורות |

חומר לימודי. אינו מחליף Sizing למנוע ול-Drive, תכן חשמלי, הערכת סיכונים, Validation בטיחותי, הוראות יצרן או מהדורות תקן מחייבות.

# 1. בדיקת התאמה לפני הפקה

- הפרק ממשיך ישירות מפרק 4: ממפעילים כלליים אל מערכת ההפעלה החשמלית הדומיננטית בתעשייה - המנוע וה-Drive.

- המבנה מפריד בין פיזיקת המנוע, Power Electronics, מצב הבקרה, Feedback, מכניקה ותוכנת Motion ברמת המכונה.

- מונחי יצרנים מוצגים כדוגמאות מימוש ולא כקטגוריות הנדסיות אוניברסליות.

- Functional Safety מוסברת באמצעות Safe Motion Functions, בלי ליצור רושם ש-Drive מאושר הופך לבדו את המכונה לבטוחה.

- הסיום מוביל לפרק הבא על תקשורת תעשייתית ורשתות דטרמיניסטיות.

> בדיקת עדכניות<br>מפת המקורות נבדקה מול דפי IEC, ISO ו-PLCopen הרשמיים. היא משקפת בין היתר IEC 60034-1:2026, IEC 60034-30-1:2025, IEC 61800-9-2:2023+A1:2025 ו-Amendment 2:2026 של IEC 62061. בכל פרויקט יש לבדוק את המהדורה שאומצה בחוזה ובדין.

# 2. מטרות הפרק

- לשרטט את השרשרת המלאה מדרישת התנועה ועד מנוע, Drive, Feedback, מכניקה ו-Process Effect.

- להבחין בין Speed Control, Torque Control, Position Control ו-Coordinated Motion.

- להשוות ברמה הנדסית מנוע השראה, מנוע מגנט קבוע, Synchronous Reluctance, Stepper ו-Servo.

- לבצע Sizing לפי Torque-Speed, אינרציה, Duty Cycle, מגבלות תרמיות, Overload ואנרגיה רגנרטיבית.

- להסביר V/f, Sensorless Vector ו-Closed-Loop Vector בלי להפוך את הפרק לקורס ב-Power Electronics.

- לזהות סיכוני אינטגרציה בין Drive, מנוע וכבל: PWM, בידוד, קירור, EMC, Reflected Waves ו-Bearing Currents.

- להשתמש באופן מכוון בפרופילי תנועה, Feedback, Diagnostics ו-Safe Motion Functions.

# 3. חלוקת זמן ומקטעים

| זמן | מקטע | מטרה |
| --- | --- | --- |
| 00:00-03:00 | פתיחה | תקלה במיקום ו-Overvoltage Trip חושפות שתנועה היא בעיית מערכת. |
| 03:00-06:30 | שרשרת ההנעה | מיפוי דרישה, מכניקה, מנוע, ממיר, Feedback ובקר. |
| 06:30-10:30 | משפחות מנועים | Induction, PM, Synchronous Reluctance, Stepper ו-Servo. |
| 10:30-14:30 | Torque, Speed ו-Sizing | מומנט רציף ושיא, אינרציה, Duty ומרווח תרמי. |
| 14:30-19:00 | מצבי בקרה ב-VFD | V/f, Sensorless Vector, Closed-Loop Vector ו-Torque Control. |
| 19:00-23:00 | אינטגרציה ו-EMC | PWM, כבל, בידוד, קירור, Bearing Currents והארקה. |
| 23:00-28:00 | ארכיטקטורת Servo | חוגים מקוננים, Encoder, Following Error ו-Tuning. |
| 28:00-32:00 | פרופילי תנועה | Trapezoidal, S-Curve, Jerk, Homing ומכניקה. |
| 32:00-36:00 | תנועה מתואמת | Electronic Gearing, Camming, Interpolation ועדכון דטרמיניסטי. |
| 36:00-39:30 | Safe Motion | STO, SS1, SOS, SLS, בלימה והתנעה מחדש. |
| 39:30-42:00 | אנרגיה ודיאגנוסטיקה | יעילות מערכתית, Regeneration, Trends וראיות Commissioning. |
| 42:00-45:00 | פתרון התקלה | פתרון תקלה במסוע ומעבר לרשתות תעשייתיות. |

# 4. מפת ארכיטקטורת Drive ו-Motion

| שלב | החלטה הנדסית | כשל אופייני |
| --- | --- | --- |
| 1. דרישת התנועה | להגדיר טווח מהירות, דיוק, חזרתיות, זמן מחזור, כוח/מומנט, עצירה ואחזקת עומס. | בחירת מנוע רק לפי kW. |
| 2. עומס ומכניקה | לכמת אינרציה, חיכוך, כבידה, גיר, בורג, רצועה, גמישות ו-Backlash. | התעלמות מ-Reflected Inertia או Resonance. |
| 3. מנוע | להמיר אנרגיה חשמלית למומנט לאורך תחום המהירות וה-Duty. | Overload תרמי, קירור לקוי, Demagnetization או Brake שגוי. |
| 4. Drive / ממיר הספק | לספק מתח, זרם ותדר מבוקרים ולנהל מגבלות ו-Regeneration. | זרם חסר, Overvoltage בהאטה, Harmonics או התחממות. |
| 5. Feedback | למדוד מיקום רוטור, מהירות, זרם, מיקום עומס או תגובת תהליך. | בלבול בין Encoder Resolution לדיוק מכונה. |
| 6. Motion Controller | לייצר פרופילים, לסנכרן צירים ולתאם Machine States. | Jitter, בעלות לא ברורה או שינויי Mode סמויים. |
| 7. בטיחות ומחזור חיים | לעצור, להחזיק, לאתחל, לבדוק, לתחזק ולשמור Configuration. | STO נתפס כבידוד חשמלי או Tuning ללא תיעוד. |

# 5. מפת החלטה טכנולוגית

| טכנולוגיה | שימוש אופייני | שאלות בחירה |
| --- | --- | --- |
| מנוע Direct-On-Line | עומס במהירות קבועה כאשר Inrush ו-Process Shock מתקבלים. | Starting Current, הגנות, Starting Torque וצריכת אנרגיה. |
| VFD עם V/f | משאבות, מפוחים ומסועים פשוטים עם דרישות מתונות לדיוק ולמומנט במהירות נמוכה. | טווח מהירות, Boost, Slip, קירור ו-Minimum Frequency. |
| Sensorless Vector | טווח מהירות רחב ומומנט משופר ללא Encoder. | Motor Identification, דרישת Zero Speed ומגבלות Estimation. |
| Closed-Loop Vector | Speed/Torque מדויקים, עבודה איטית, Hoists, Winders ומכונות תובעניות. | Encoder, Overspeed, Brake Coordination ו-Tuning. |
| Servo System | Positioning דינמי, Indexing, Registration, Robot ו-Multi-Axis. | Peak/Continuous Torque, אינרציה, Resonance, מכניקה ו-Bus Cycle. |
| Stepper System | תנועה אינקרמנטלית זולה עם עומס צפוי ודינמיקה מתונה. | Missed Steps, Resonance, חימום בעמידה וירידת מומנט במהירות. |
| Regenerative Drive / Shared DC Bus | בלימות תכופות, Overhauling Load או החלפת אנרגיה בין צירים. | Grid Interface, הגנת DC Bus, Fault Propagation ואסטרטגיית בלימה. |

> עיקרון מרכזי<br>בוחרים ארכיטקטורת בקרה לפי ההתנהגות הפיזיקלית הנדרשת והתגובה לכשל. לא בוחרים Motor, Drive או Servo רק לפי kW או מונח שיווקי.

# 6. הנחיית הפקה ל-NotebookLM

> הנחיה מוכנה להדבקה<br>צור פרק פודקאסט הנדסי בעברית בלבד, באורך 42-45 דקות, תוך שימוש במסמך זה בלבד.<br><br>המגישים:<br>- יעל: מהנדסת מכונות צעירה, סקרנית ובעלת בסיס טכני חזק. היא מאתגרת מונחי אוטומציה עמומים ושואלת מנקודת מבט של עומסים, צירים, גירים, רצועות והתנהגות המכונה.<br>- אמיר: מהנדס תהליך ובקרה ותיק שהתחיל בעולם המכונות וההינע. רגוע, מבוסס ראיות ומעשי. הוא מסביר Trade-offs, Failure Modes ו-Commissioning בלי להישמע כמו הרצאה.<br><br>כללי השיחה:<br>1. שמור על שיחה טבעית: בערך 45% יעל ו-55% אמיר.<br>2. השתמש בתקלה במסוע האינדוקס כחוט מקשר; אל תגלה את האבחנה הסופית לפני הסיום.<br>3. בכל מקום רלוונטי הפרד בין Command, תגובת המנוע, תגובת העומס ו-Process Result.<br>4. הסבר משוואות באופן מילולי ואינטואיטיבי. אל תקרא טבלאות או רשימות מקורות בקול.<br>5. הימנע מקידום יצרנים. מונחים מסחריים יכולים להופיע רק כדוגמאות מימוש.<br>6. הדגש גבולות בטיחות: STO אינו בידוד חשמלי; Drive מאושר אינו מאשר את המכונה כולה.<br>7. כלול סיכום קצר אחד באמצע ו-Checklist הנדסי בסיום.<br>8. שמור על סדר המקטעים והזמנים. אל תמציא טענות שאינן במסמך.<br>9. בפעם הראשונה אמור את השם המלא של קיצורים מרכזיים: Variable-Frequency Drive, Safe Torque Off, Electromagnetic Compatibility וכדומה.<br>10. סיים במעבר ברור לתקשורת תעשייתית ולתזמון דטרמיניסטי.

# 7. תסריט מלא לפרק

## 00:00-03:00 | פתיחה - הציר מגיע, אבל לא בדיוק למקום

יעל: למסוע האינדוקס יש משימה פשוטה: להזיז מגש בדיוק ארבע מאות מילימטר, לעצור ולאפשר לרובוט לאסוף. אבל אחת לעשרים מחזורים הוא חורג בשני מילימטר. אתמול ה-Drive גם נפל על DC Bus Overvoltage בזמן האטה. התחזוקה רוצה להגדיל Position Gain, הייצור רוצה מנוע גדול יותר, והמתכנת אומר שה-Command Position מושלם. מאיפה מתחילים?

אמיר: מתחילים בכך שלא מאשרים אף אחד משלושת הפתרונות לפני שיודעים איזה גודל פיזיקלי שגוי. Command Position מושלם מוכיח רק שה-Motion Planner יצר את המספר המתוכנן. הוא לא מוכיח שה-Drive עקב אחריו, שהמנוע יצר את המומנט, שהגיר העביר אותו או שהמגש הגיע למקום.

יעל: זו הגרסה של Motion לעיקרון מהפרק הקודם: Command אינו מצב, ומצב אינו Effect.

אמיר: נכון, וב-Motion יש שכבה נוספת. ציר המנוע יכול לעקוב באופן מושלם והעומס עדיין יהיה שגוי בגלל Backlash, מתיחת רצועה, Compliance, החלקה או חיישן שמותקן בצד הלא נכון של המנגנון.

יעל: וה-Overvoltage בזמן עצירה רומז שהעומס מחזיר אנרגיה ל-Drive.

אמיר: ייתכן. מסה מסתובבת שמאטים אותה הופכת לגנרטור. האנרגיה חייבת להגיע למקום כלשהו: ל-DC Bus, ל-Braking Resistor, לציר אחר על Shared Bus, ל-Regenerative Front End, להפסדים מכניים או בחזרה לרשת. אם הנתיב אינו מספיק, מתח ה-DC עולה וה-Drive מגן על עצמו.

יעל: כלומר סימפטום אחד מצביע על מכניקה ובקרה, והשני על זרימת אנרגיה.

אמיר: כן. עד סוף הפרק נדע מתי VFD מספיק, מתי Servo מוצדק, איך לחשוב על מומנט ואינרציה, ולמה Tuning אינו מפצה על מכונה שלא הובנה.

## 03:00-06:30 | שרשרת ההנעה החשמלית

יעל: בוא נגדיר את האובייקט. האם VFD הוא Controller, Actuator או ספק כוח?

אמיר: בהתאם לארכיטקטורה הוא מכיל חלקים משלושתם. Power Drive System כולל את ממיר ההספק, הבקרה וההגנות שלו, המנוע והממשקים. ברמת המכונה צריך לשרטט שרשרת ארוכה יותר: דרישת תנועה, מכניקת העומס, מנוע, Drive, Feedback, Motion Controller, פונקציות בטיחות ו-Process Effect.

יעל: למה מתחילים בדרישה ולא במנוע?

אמיר: כי “מנוע חמישה קילוואט” כמעט לא מתאר את התנועה. משאבה עשויה לדרוש מומנט רציף סביב נקודת עבודה אחת. Indexer עשוי לדרוש Peak Torque גבוה לחלקיק שנייה ומעט מאוד הספק ממוצע. Hoist דורש מומנט מבוקר באפס או במהירות נמוכה ואסטרטגיית Brake. Winder דורש Torque Control כדי לווסת מתיחות כאשר הקוטר משתנה.

יעל: המודל המכני הוא כוח, מומנט, אינרציה ומהירות.

אמיר: וגם זמן. מומנט מאיץ אינרציה. הספק הוא מומנט כפול מהירות זוויתית. אותו מומנט במהירות גבוהה יותר דורש יותר הספק. מהלך שקל לבצע בשתי שניות יכול להיות בלתי אפשרי בשתי עשיריות שנייה, כי Acceleration Torque ואנרגיית הבלימה גדלים במהירות.

יעל: איפה נמצא ה-PLC?

אמיר: ב-VFD פשוט ה-PLC יכול לשלוח Run ו-Speed Setpoint, וה-Drive סוגר חוגי זרם ומהירות. במערכת Servo ה-Motion Controller מייצר Position Trajectory וסט-פוינטים מסונכרנים, וה-Servo Drive סוגר חוגי זרם, מהירות ולעיתים מיקום. בפלטפורמות משולבות PLC, Motion ו-Safety נמצאים באותו Controller, אבל האחריות ההנדסית עדיין צריכה להיות ברורה.

יעל: בתרשים הארכיטקטורה צריך להראות מי בעל הבית על Enable, Speed, Torque, Position, Limits, Homing, Brake ו-Safe Stop.

אמיר: בדיוק. בעלות עמומה מייצרת הפתעות מסוכנות בזמן Mode Change, אובדן תקשורת והתנעה מחדש.

## 06:30-10:30 | משפחות מנועים - השם אינו שיטת הבקרה

יעל: רוב המפעלים עדיין משתמשים במנועי השראה. למה הם כל כך דומיננטיים?

אמיר: הם חזקים, בשלים, זמינים ומתאימים גם ל-Direct-On-Line וגם ל-Converter. ברוטור Squirrel Cage אין מגנטים קבועים ואין חיבור חשמלי. עם VFD מתאים מנוע השראה יכול לתת ביצועי Speed ו-Torque מצוינים למגוון רחב של עומסים.

יעל: מה משתנה במנוע Permanent Magnet Synchronous?

אמיר: שדה הרוטור מגיע ממגנטים, ולכן הפסדי הרוטור יכולים להיות נמוכים, ו-Torque Density ותגובה דינמית יכולים להיות טובים. אבל ה-Drive חייב לדעת את מיקום הרוטור מספיק טוב כדי לכוון את הזרם ביחס לשדה. במהירות גבוהה נכנסים Voltage Limits ו-Field Weakening, ובמצבי חריגה יש להתחשב ב-Demagnetization בגלל זרם או טמפרטורה.

יעל: ומהו Synchronous Reluctance?

אמיר: המומנט נוצר משום שהרוטור שואף להתיישר במסלול בעל Reluctance נמוך. אין מגנטים ברוטור, ועם Drive מתאים ניתן להגיע ליעילות מערכתית גבוהה. זו דוגמה לכך שלא מפרידים “Motor Efficiency” מ-“Drive Compatibility”.

יעל: איפה Stepper נכנס?

אמיר: Stepper מתקדם בין מצבים אלקטרומגנטיים בדידים. ב-Open Loop הבקר מניח שכל Step שביקש אכן בוצע. זה זול ויעיל כאשר העומס וההאצה צפויים, אבל Missed Step יכול להישאר סמוי עד Homing או בדיקת איכות. Closed-Loop Stepper מוסיף Feedback, אך Torque-Speed ו-Resonance עדיין שונים מ-Servo.

יעל: אנשים קוראים למנוע עצמו Servo.

אמיר: ההגדרה ההנדסית השימושית רחבה יותר: Servo System היא מערכת Closed Loop שנועדה לגרום למיקום, מהירות או מומנט לעקוב אחרי Command עם דינמיקה ודיוק מוגדרים. היא כוללת Motor, Drive, Feedback, Control Loops ומכניקה. מנוע יקר על מנגנון גמיש אינו ציר מדויק.

יעל: ומה לגבי Brake?

אמיר: Holding Brake מיועד בדרך כלל להחזיק עומס שכבר נעצר, לא לבלום שוב ושוב את כל האנרגיה הקינטית, אלא אם תוכנן לכך. שחרור וסגירת Brake חייבים להיות מתואמים עם יצירת Torque ועם Feedback, במיוחד בציר אנכי.

## 10:30-14:30 | דרישת Torque-Speed ו-Sizing

יעל: איך עושים Sizing נכון בלי לטבוע במשוואות?

אמיר: מתחילים בפרופיל העומס לאורך זמן. בכל שלב - Acceleration, Run, Deceleration, Dwell ו-Hold - מעריכים Speed, Load Torque ו-Acceleration Torque. המומנט להאצה תלוי באינרציה הכוללת כפי שהיא משתקפת לציר המנוע. Gearbox משנה מומנט וגם Reflected Inertia, בקירוב בריבוע יחס התמסורת, ומוסיף הפסדי יעילות ו-Backlash.

יעל: ואז משווים Peak לערך רציף?

אמיר: כן. Peak Torque חייב לכסות את האירוע הקצר הגרוע ביותר עם Margin, ו-RMS Torque לאורך ה-Duty Cycle חייב להישאר בתחום התרמי של המנוע. ה-Drive צריך לספק Current ו-Overload למשך הנדרש. מהירות המנוע חייבת להישאר בתחום המכני והחשמלי, כולל Field Weakening.

יעל: למה Nameplate Power מטעה ב-Positioning?

אמיר: כי ההספק יכול להיות נמוך למרות Peak Torque גבוה במהירות נמוכה. לעומת זאת Spindle יכול לדרוש הספק גבוה במהירות גבוהה ומומנט מתון. Sizing לפי Average Power מפספס Acceleration Current; Sizing רק לפי Peak Torque יכול להביא מנוע גדול עם Rotor Inertia גבוהה שמקשה על הבקרה.

יעל: כלומר מנוע גדול יותר יכול להחמיר את התנועה.

אמיר: בהחלט. Rotor Inertia גדולה מגדילה את האנרגיה להאצה ולבלימה, יכולה לפגוע ב-Inertia Ratio, ומחייבת Drive ו-Braking גדולים יותר. הבחירה הטובה מאזנת Torque Margin, יכולת תרמית, אינרציה, טווח מהירות, התאמה מכנית וזמינות לאורך החיים.

יעל: אילו תנאי סביבה שייכים לבחירה?

אמיר: Ambient Temperature, Altitude, Enclosure, זיהום, Washdown, Hazardous Area, רטט, צורת התקנה, Bearing Load, אורך כבל וקירור. במהירות נמוכה Shaft-Mounted Fan מזיז פחות אוויר, ולכן עבודה רציפה במומנט גבוה יכולה לדרוש Forced Ventilation או Derating.

יעל: למסוע שלנו צריך את מסת המגש, האינרציה של הרצועה והגלילים, יחס הגיר, חיכוך, Move Time ו-Dwell, לא רק את תווית המנוע.

אמיר: נכון, וגם את פרופיל התנועה בפועל ואת האפשרות שהעומס יניע את המנוע בזמן האטה.

## 14:30-19:00 | מצבי בקרה ב-VFD

יעל: מה VFD בסיסי באמת שולט?

אמיר: הוא ממיר את ההספק הנכנס ל-DC Link ומייצר מתח למנוע באמצעות מיתוג Semiconductor. באמצעות שליטה בתדר ובמתח - ובמצבים מתקדמים ברכיבי הזרם - הוא שולט ב-Flux וב-Torque.

יעל: נתחיל ב-Scalar V/f.

אמיר: הוא שומר בקירוב על יחס Voltage-to-Frequency כדי לשמור Flux. זה פשוט וחזק להרבה Pumps, Fans ו-Conveyors. אבל הוא לא מפריד במפורש בין Torque ו-Flux, ומהירות משתנה עם Slip ו-Load. מומנט במהירות נמוכה ודינמיקה מהירה מוגבלים, אלא אם מוסיפים Compensation.

יעל: Sensorless Vector נשמע כמו Servo בלי Encoder.

אמיר: זו הגדרה נדיבה מדי. Sensorless Vector משתמש במודל מנוע ובגדלים חשמליים נמדדים כדי לאמוד Flux, Speed או Rotor Position במידה שמאפשרת Torque Control משופר. הוא יכול לעבוד מצוין, אבל Estimation קשה יותר ליד Zero Speed ובמצבים משתנים או כאשר Motor Identification לא טוב.

יעל: Closed-Loop Vector מוסיף Encoder.

אמיר: כן. Feedback משפר ידיעה של Actual Speed ו-Rotor Position, מאפשר מומנט מדויק במהירות נמוכה ותגובה מהירה. אבל Encoder, כבל, התקנה, Scaling ו-Plausibility הופכים לחלק מהאמינות ומהבטיחות.

יעל: ומהו Torque Mode?

אמיר: ב-Torque Mode ה-Drive מווסת את הזרם שמייצר מומנט לפי Torque Command, בתוך Speed ו-Current Limits. זה מתאים ל-Tension, Winding, Load Sharing ולעיתים Force Control. ה-Machine Controller עדיין חייב למנוע האצה לא מכוונת, כי עומס חופשי תחת Torque Command יכול להמשיך להאיץ.

יעל: מה Auto-Tune עושה?

אמיר: הוא מזהה פרמטרים חשמליים של המנוע ולעיתים מאפיינים מכניים כדי לשפר את המודל והחוגים. זו לא קסם. Motor Data נכון, תנאי בדיקה בטוחים, מצב העומס ושיטת ה-Tune חשובים. החלפת מנוע ללא עדכון Parameters יכולה לפגוע בביצועים ובהגנות.

יעל: לכן בחירת Control Mode צריכה להיכתב כדרישה: Speed Accuracy, Zero-Speed Torque, Dynamic Response, סבילות לכשל Encoder והתנהגות בכשל.

אמיר: בדיוק. לא בוחרים Vector כי הוא נשמע מתקדם, אלא כי העומס צריך את היכולת שלו.

## 19:00-23:00 | Drive, מנוע וכבל הם מערכת אלקטרומגנטית אחת

יעל: למה מנוע שעובד מצוין ישירות מהרשת עלול להיכשל עם Drive?

אמיר: כי PWM Drive אינו מציג למנוע גל סינוס טהור. קצוות מתח מהירים מתקשרים עם Impedance של הכבל ובידוד המנוע. כבלים ארוכים יכולים ליצור Reflected-Wave Peaks. Common-Mode Voltage יכול להזרים זרם דרך מיסבים ונתיבי הארקה. המיתוג יוצר Conducted ו-Radiated EMI.

יעל: מה עושים בפועל?

אמיר: משתמשים במנוע שמתאים ל-Converter Duty ולמתח ולאורך הכבל. פועלים לפי מגבלות היצרן ל-Cable Length ול-Switching Frequency. משתמשים בכבל מנוע מסוכך וב-Termination נכון. לפי הצורך מוסיפים Output Reactor, dv/dt Filter או Sine Filter. ב-Bearing Currents מטפלים באמצעות Insulated Bearings, Shaft Grounding או Common-Mode Mitigation בהתאם לתכן.

יעל: אפשר לפתור EMC על ידי חיבור Shield רק בצד אחד?

אמיר: הכלל הזה מיושם לעיתים בצורה שגויה. בזרמים בתדר גבוה של Drive חשובה לרוב Bonding בעלת Impedance נמוכה ו-Termination היקפי של Shield. הסידור הנכון תלוי בתכן EMC, ב-Equipotential Bonding ובהוראות היצרן. כללי Signal Cable אינם אוטומטית כללי Motor Cable.

יעל: ומה בצד הכניסה?

אמיר: Rectifier ו-DC Link מושכים זרם שאינו סינוסי, יוצרים Harmonics ומשפיעים על Power Quality. Line Reactor, DC Choke, Multi-Pulse או Active Front End נבחרים לפי המתקן. הגנות, Short-Circuit Rating, Leakage Current, RCD ו-Disconnecting Means צריכים להיות מתואמים עם מסמכי ה-Drive והתקינה.

יעל: ומה לגבי תרמיקה?

אמיר: הפסדי ה-Drive תלויים ב-Load, Switching, Ambient וקירור הארון. הפסדי המנוע משתנים תחת Converter Supply. במהירות נמוכה Self-Cooling יכול להיות חלש. Motor Temperature Sensor ו-Thermal Model שימושיים, אבל צריך להבין את ההנחות ואת Reset Behavior.

יעל: כלומר שינוי כבל משני מטר לארבעים מטר הוא Engineering Change.

אמיר: כן. גם העלאת Switching Frequency כדי שהמנוע יהיה שקט יותר. שיפור אקוסטי עלול להגדיל Drive Loss, Motor Stress ו-EMC Burden.

## 23:00-28:00 | ארכיטקטורת Servo וחוגים מקוננים

יעל: בוא נפתח את הבלוק דיאגרם של Servo.

אמיר: בפנים נמצא Current או Torque Loop, בדרך כלל המהיר ביותר. מחוץ לו Speed Loop. ומחוץ לו יכול להיות Position Loop. ה-Motion Controller מספק Trajectory שמגדיר היכן הציר צריך להיות בכל רגע, לא רק את היעד הסופי.

יעל: למה חוגים מקוננים?

אמיר: Inner Loop צריך להגיב מהר יותר מה-Outer Loop שהוא משרת. Torque Loop גורם לזרם לעקוב מהר. Speed Loop משתמש במומנט לתקן Velocity Error. Position Loop משתמש במהירות לתקן Position Error. אם Bandwidths אינם מופרדים או שהמכניקה רזוננטית, Gains אגרסיביים מגבירים Noise ורטט במקום דיוק.

יעל: מהו Following Error?

אמיר: ההפרש בין Commanded Position ל-Actual Position. זה Diagnostic חשוב, אבל צריך לפרש אותו יחד עם Trajectory. מעט שגיאה בזמן האצה היא צפויה. שגיאה גדולה, אסימטרית או גדלה יכולה להצביע על Torque Saturation, חיכוך, Feed-Forward שגוי, Feedback, Compliance או חסימה.

יעל: Feed-Forward נשמע כמו רמאות.

אמיר: זו תחזית, לא רמאות. Velocity Feed-Forward מספק את הפקודה הצפויה למהירות; Acceleration Feed-Forward מספק את המומנט הצפוי לאינרציה. Feedback מתקן שגיאות מודל והפרעות. כך מפחיתים Error בלי Gain מסוכן.

יעל: Encoder ברזולוציה גבוהה תמיד משפר Positioning?

אמיר: הוא משפר גרנולריות של מדידה, אבל Machine Accuracy תלוי במיקום ה-Encoder, Transmission, Thermal Growth, Backlash, Compliance, Calibration והפרעות בצד העומס. Motor Encoder לא רואה Belt Slip או Lost Motion בגיר. Load-Side Encoder יכול לסגור את הפער, אך Dual-Loop Control דורש Tuning זהיר.

יעל: Absolute לעומת Incremental?

אמיר: Incremental מודד שינוי ודורש בדרך כלל Reference לאחר אובדן מתח. Absolute שומר או מתקשר מיקום בתחום שהוגדר. אף אחד מהם לא פוטר מהגדרת Machine Zero, Travel Limits ו-Plausibility Checks.

יעל: מה מהנדס Commissioning צריך להקליט?

אמיר: Commanded ו-Actual Position, Velocity ו-Torque; Following Error; Current Limit; DC-Bus Voltage; Brake State; Encoder Status; וציר זמן של אירועי המכונה. בלי נתונים מסונכרנים מכוונים לפי רעש וזיכרון.

## 28:00-32:00 | Motion Profile, Jerk ומכניקה

יעל: המסוע יכול לנוע בפרופיל Trapezoidal: תאוצה קבועה, מהירות קבועה והאטה קבועה.

אמיר: כן, אבל שינוי מיידי בתאוצה יוצר Jerk מתמטי אינסופי ובמכונה - Shock. S-Curve מגביל Jerk על ידי Ramp של התאוצה. זה יכול להפחית רטט, עירור רצועה, תזוזת מוצר ו-Peak Torque, אך עשוי להאריך Move או לשנות Peak Velocity.

יעל: כלומר אותו מרחק ואותו זמן לא מבטיחים אותו עומס.

אמיר: נכון. Shape של הפרופיל משנה Peak Acceleration, Torque, Settling ו-Regenerative Power. גם Natural Frequencies של המכניקה חשובות. אם Command מעורר Resonance, הציר יכול להתנדנד אחרי שהמנוע הגיע.

יעל: איפה Backlash נכנס?

אמיר: Backlash הוא תחום שבו המנוע נע והעומס לא נע כאשר כיוון המומנט מתהפך. Compensation יכול לשפר Commanded Position בתנאים חוזרים, אבל הוא לא מחזיר Stiffness ולא מונע Impact. לעיתים תיקון מכני הוא Control Strategy טוב יותר.

יעל: ומהי Compliance?

אמיר: רצועות, צירים ארוכים, Couplings ושלדה מתנהגים כמו קפיצים. המנוע והעומס יכולים ליצור Two-Mass Resonance. Notch Filters וכלי Tuning עוזרים, אבל קודם בודקים Integrity, Preload, Alignment ו-Mounting Stiffness.

יעל: Homing הוא יותר מתנועה עד ש-Switch משתנה.

אמיר: כן. Homing Procedure מגדיר Approach Direction, מהירויות, Edge, Encoder Index אם קיים, Offset, Timeout ו-Failure Response. חזרתיות תלויה במכניקת החיישן ובכיוון הגישה. Safety Limits ו-Home Sensors רגילים אינם בעלי אותה אחריות.

יעל: בציר אנכי הפרופיל מתקשר גם עם Gravity ו-Brake Timing.

אמיר: בדיוק. מומנט בעלייה ובירידה שונה. בעצירה ה-Drive צריך לייצר Holding Torque לפני שחרור Brake, ולאמת תנאים לפני Torque Off. Brake Output Bit אינו הוכחה שהעומס מאובטח.

## 32:00-36:00 | תנועה מתואמת ובעלות תוכנה

יעל: מתי עוברים מ-Single Axis ל-Motion Control כדיסציפלינת תוכנה?

אמיר: כאשר צירים צריכים Time Base או יחס גאומטרי משותף. Electronic Gearing גורם לציר לעקוב אחרי Master ביחס. Electronic Camming ממפה Master Position ל-Follower Position באמצעות Curve. Interpolation מתאם צירים לאורך Path. Registration מתאים תנועה ל-Mark או לאירוע נמדד.

יעל: למה הרשת חשובה?

אמיר: Distributed Drives צריכים Cyclic Setpoints ו-Feedback עם Timing חסום. Clock Synchronization, Update Period, Jitter ו-Loss Behavior משפיעים על Coordination. רשת מהירה בממוצע אינה מספיקה אם זמן המסירה משתנה.

יעל: PLCopen Motion Control נותן Function Blocks משותפים.

אמיר: כן: Axis State Machine ובלוקים ל-Power, Move, Stop, Home, Gearing ופונקציות מתואמות. זה משפר Portability רעיונית, אבל פרטי מימוש, Error Codes ו-Real-Time Behavior שונים בין פלטפורמות. צריך להבין את ה-State Machine ולא להעתיק Blocks.

יעל: איך Machine Logic צריך לעבוד עם Motion?

אמיר: באמצעות States ובעלות מפורשת. Sequence מבקש Move; שכבת Motion בודקת Prerequisites, מבצעת ומחזירה Done, Busy, Aborted או Error. Safety יכולה להסיר Torque או לכפות Limits. Manual Mode דורש Speed, Direction ו-Hold-to-Run מוגדרים. Recovery לא צריך להמשיך מהלך בשקט לאחר הפסקה.

יעל: ומה לגבי Recipe Data?

אמיר: Units, Limits, Version ו-Validation. מרחק במילימטר לא יכול להפוך ל-Revolutions בגלל שינוי Gear Parameter. Motion Configuration חייבת Change Control, Backup ו-Restore Test.

יעל: לכן החלפת Drive יכולה להיות Software Change.

אמיר: לעיתים קרובות. Parameter Set, Motor Identification, Encoder Scaling, Safety Signature ו-Network Mapping דורשים ראיות Commissioning מבוקרות.

## 36:00-39:30 | Safe Motion הוא יותר מהפסקת כוח

יעל: בוא נדייק Safe Torque Off.

אמיר: STO מונע מה-Drive לייצר Torque במנוע במסגרת ארכיטקטורת הבטיחות שלו. הוא לא בהכרח עוצר עומס נע, מחזיק עומס אנכי, מנתק חשמל או פורק DC Bus. Risk Assessment של המכונה קובע אילו פונקציות ואמצעים מכניים נוספים נדרשים.

יעל: מהו Safe Stop 1?

אמיר: SS1 יוזם ומנטר האטה מבוקרת ולאחריה STO לפי הווריאנט. Safe Stop 2 מבצע Controlled Stop ולאחריו Safe Operating Stop, לרוב SOS, שבו מיקום מנוטר באופן בטיחותי בעוד Torque נשאר זמין.

יעל: ו-Safely Limited Speed?

אמיר: SLS מנטר שהמהירות נשארת מתחת למגבלה בטוחה. הוא שימושי ב-Setup כאשר משולב עם Guards, Enabling Device ותפיסת Risk Reduction מאומתת. קיימות גם Safe Direction, Safe Maximum Speed, Safe Brake Control ופונקציות מיקום, בהתאם ל-Drive.

יעל: Integrated Safety מקטין Wiring?

אמיר: הוא יכול לצמצם רכיבים חיצוניים ולאפשר Modes יצרניים יותר, אבל האחריות ל-Validation נשארת. Feedback Architecture, Fault Exclusions, Stopping Time, Brake Performance, Safety Communication ו-Restart Behavior נבדקים במכונה השלמה.

יעל: איך Stop Categories קשורות?

אמיר: תקינת ציוד חשמלי למכונות מגדירה קטגוריות כמו הסרת כוח מיידית, Controlled Stop ולאחריו הסרת כוח, או Controlled Stop עם כוח נשמר. Safe Motion Functions הן כלים למימוש אסטרטגיה מבוססת סיכון; השמות אינם תחליף ל-Stop Strategy ברמת המכונה.

יעל: ולתחזוקה?

אמיר: STO אינו Lockout. בידוד חשמלי, Verification of Absence of Voltage, פריקת Stored Energy ושליטה בכבידה או לחץ נעשים לפי נוהל התחזוקה והחוק.

## 39:30-42:00 | אנרגיה, Diagnostics וראיות Commissioning

יעל: Drives נמכרים כחוסכי אנרגיה. מתי זה נכון?

אמיר: בעומסי Variable Torque כמו משאבות ומפוחים צנטריפוגליים רבים, הפחתת Speed יכולה להפחית מאוד Power, אך יש לבדוק System Curve, Static Head, Efficiency ומגבלות תהליך. בעומס Constant Torque אין אותו חיסכון קובי. Drive שנבחר רע יכול להוסיף הפסדים או להזיז את התהליך מנקודה יעילה.

יעל: IEC 60034-30-1:2025 כבר כוללת IE5 למנועים Line Operated.

אמיר: נכון, אבל החלטת פרויקט צריכה לבחון את כל Motor System ואת Operating Profile. IEC 61800-9-2 נותנת שיטה מערכתית ליעילות Drive ומנוע. גם אנרגיית בלימה היא החלטה: לפזר ב-Resistor, לשתף ב-DC Bus או להחזיר לרשת.

יעל: מה כולל Commissioning Baseline טוב?

אמיר: Motor ו-Drive Identification, Nameplate Data, Parameter Backup, תוצאות Autotune, כבל ו-Filter, Current/Thermal Limits, כיוון ו-Feedback Polarity, בדיקות Low Speed ו-No Load, Trends תחת עומס, Stopping Time, Braking Temperature, Safety Validation ו-Fault Log תקין.

יעל: אילו ערכי Drive שימושיים בתפעול?

אמיר: Actual Speed, Torque-Producing Current, Total Current, DC-Bus Voltage, Thermal Estimate, Overload Utilization, Encoder Quality, Following Error, Current Limiting, Braking Status והיסטוריית תקלות עם Timestamp. מחברים אותם ל-Process Variables ולאירועים מכניים.

יעל: Predictive Maintenance לא מתחיל מ-AI.

אמיר: הוא מתחיל מסיגנלים אמינים ומהיפותזת כשל. Torque עולה באותה מהירות יכול להצביע על חיכוך. Following Error גדל בכיוון אחד יכול להצביע על Backlash או Alignment. יותר Overvoltage Events יכולים להצביע על שינוי Deceleration או Braking Path. הנתונים שימושיים כאשר הם מחוברים לפיזיקה.

## 42:00-45:00 | פתרון תקלה וסיום

יעל: חזרה למסוע. מה סדר האבחון?

אמיר: ראשית עוצרים שינויי Tuning לא מבוקרים ומגבים Drive ו-Motion Configuration. שנית מקליטים על אותו Clock את Commanded ו-Actual Motor Position, Load Position אם יש, Speed, Torque, Current, Following Error ו-DC-Bus Voltage. שלישית בודקים Belt Tension, Pulley Key, Gearbox Backlash, Coupling, Frame Stiffness והחלקת המגש.

יעל: נניח Following Error של המנוע קטן, אבל Load Encoder מראה Overshoot של שני מילימטר.

אמיר: אז Position Gain במנוע יכול להחמיר Impact. העומס נע ביחס למנוע - Belt Compliance, Slip או Backlash. מתקנים מכניקה או משתמשים ב-Load Feedback Architecture מוצדקת.

יעל: ומה לגבי DC-Bus Trip?

אמיר: משווים את התקלה ל-Deceleration ול-Regenerated Power. מאמתים Inertia ו-Motion Profile, ערך Braking Resistor, Wiring, Duty ו-Thermal Switch; בודקים שה-Braking Chopper מופעל ומתאים. אם המערכת מייצרת Regeneration לעיתים קרובות, בוחנים פתרון בלימה גדול יותר, Shared Bus או Regenerative Drive. לא מאריכים Deceleration בלי לבדוק Cycle Time ובטיחות.

יעל: אצלנו ה-Trend מראה האטה Trapezoidal חדה, Parameter של ה-Braking Resistor נשאר Default למרות שהותקן Resistor אחר, ול-Belt Tensioner יש Compliance גבוהה.

אמיר: לכן התיקון מערכתי: לתקן ולאמת את הגדרת ה-Resistor, לעבור להאטה Jerk-Limited בתוך אילוצי התהליך והעצירה, לתקן Tensioner, לבצע Retune לאחר ייצוב המכניקה ולשמור Baseline חדש. מנוע גדול היה מגדיל אינרציה; Gain גבוה לא היה פותר דבר.

יעל: ה-Checklist הסופי: Requirement, Load Model, Torque-Speed Duty, Motor Technology, Drive Current ו-Regeneration, מיקום Feedback, Mechanics, Motion Profile, EMC, Cooling, Safety, Diagnostics ו-Commissioning מבוקר.

אמיר: בדיוק. Motion Control הוא המקום שבו מודלים חשמליים, מכניים ותוכנתיים נפגשים. המערכת מבצעת לפי המודל החלש ביותר.

יעל: בפרק הבא נעקוב אחרי Setpoint ו-Feedback דרך הרשת: Industrial Ethernet, Fieldbus, Deterministic Timing, Topology ומה קורה כשהתקשורת מאחרת ולא נעלמת לחלוטין.

אמיר: ועד אז, אל תכוון Control Loop כדי לפצות על מכונה רופפת.

# 8. הערות למפיק ולמגישים

- לשמור לאורך כל הפרק על הפרדה בין Torque, Speed, Position ו-Process Effect.

- לא ליצור רושם ש-Servo תמיד מדויק יותר; המכניקה ומיקום ה-Feedback קובעים את התוצאה.

- להסביר Regenerative Energy בלי להציע פתרון בלימה אוניברסלי.

- להציג V/f, Vector ו-Servo כבחירה לפי דרישה, לא כסולם בגרות.

- להדגיש בכל אזכור של STO את גבול האחריות שלו.

- לא להקריא מספרי תקנים בדיאלוג, למעט שתי דוגמאות היעילות בסוף.

- לשמור את האבחנה הסופית למקטע האחרון.

# 9. Checklist הנדסי למנוע ול-Motion

1. איזו תנועה או השפעת תהליך נדרשת, ובאיזה דיוק, חזרתיות וזמן מחזור?

1. מהם פרופילי Load Torque, Speed, Inertia, Friction, Gravity והפרעות?

1. מהם Continuous ו-Peak Torque/Current, למשך כמה זמן ובאילו תנאי סביבה?

1. איזה Motor Technology, Cooling, Enclosure, Brake ו-Bearing Arrangement מתאימים?

1. איזה Control Mode נדרש: Scalar Speed, Vector Speed/Torque, Position Servo או Coordinated Motion?

1. היכן Feedback נמדד ואילו שגיאות מכניות נשארות מחוץ לחוג?

1. איזה Motion Profile, Jerk, Settling Time ו-Resonance מתקבלים?

1. לאן עוברת Regenerated Energy בכל עצירה ובכל Overhauling Condition?

1. האם Motor, Drive, Cable, Filter, Grounding ו-EMC תואמים כמערכת אחת?

1. מה קורה באובדן Command, Network, Encoder, Power, Brake Feedback או Cooling?

1. אילו Safe Motion Functions נדרשות וכיצד מאמתים Stopping Time ו-Holding?

1. כיצד נשלטים Parameters, Autotune Results, Safety Signatures ו-Backups?

1. אילו Trends מסונכרנים ו-Acceptance Tests מוכיחים ביצועים לפני Release?

1. אילו שינויים מחייבים Revalidation: Motor, Cable, Gearbox, Profile, Firmware, Resistor, Encoder או Load?

# 10. מילון מונחים

| מונח | משמעות בפרק |
| --- | --- |
| VFD - Variable-Frequency Drive | Drive אלקטרוני ששולט במנוע באמצעות שינוי מתח, תדר וזרם. |
| Power Drive System - PDS | Drive Module, בקרה/הגנה, מנוע והממשקים המוגדרים כמערכת. |
| Scalar V/f Control | בקרה המבוססת בעיקר על יחס Voltage-to-Frequency ולא על הפרדה מפורשת של Torque ו-Flux. |
| Vector Control | בקרה של רכיבי זרם הקשורים ל-Flux ול-Torque באמצעות מודל מנוע ו-Feedback לפי הצורך. |
| Servo System | מערכת Closed Loop של Motor, Drive, Feedback ומכניקה לעקיבה דינמית אחרי Position, Speed או Torque. |
| Continuous Torque | מומנט שניתן לקיים תרמית בתנאים המוגדרים. |
| Peak Torque | מומנט גבוה לזמן מוגבל בתוך מגבלות המנוע וה-Drive. |
| Reflected Inertia | אינרציית העומס כפי שהיא משתקפת לציר המנוע דרך התמסורת. |
| Following Error | ההפרש בין מיקום מצווה למיקום נמדד. |
| Jerk | קצב השינוי של התאוצה. |
| Regeneration | זרימת אנרגיה מהעומס המכני חזרה ל-DC Bus או לאספקה. |
| STO | פונקציית בטיחות שמונעת יצירת Torque; אינה בידוד חשמלי. |
| SS1 | פונקציית בטיחות להאטה מבוקרת ולאחריה Torque Off. |
| SLS | פונקציית בטיחות שמנטרת מהירות מול גבול בטוח. |
| PWM | Pulse-Width Modulation ליצירת מתח וזרם מבוקרים למנוע. |

# 11. מפת תקנים ומקורות

> הערת שימוש<br>בכל פרויקט יש לבדוק מהדורה שאומצה בחוזה, בדין ובענף, כולל Amendments, National Deviations והוראות יצרן.

1. IEC 60034-1:2026 - Rating and performance של מכונות חשמליות מסתובבות. מקור רשמי: https://webstore.iec.ch/en/publication/89961

2. IEC 60034-30-1:2025 - Efficiency Classes למנועי AC בהזנת רשת; המהדורה מוסיפה IE5. מקור רשמי: https://webstore.iec.ch/en/publication/91195

3. IEC 60034-2-3:2024 - שיטות בדיקה להפסדים ויעילות של מנועים בהזנת Converter. מקור רשמי: https://webstore.iec.ch/en/publication/67758

4. IEC TS 60034-25:2022 - Motor-Drive Interface, Converter Duty, Shaft Currents ו-Derating. מקור רשמי: https://webstore.iec.ch/en/publication/66456

5. IEC 61800-2:2021 - Rating Specifications ל-Adjustable-Speed AC Power Drive Systems. מקור רשמי: https://webstore.iec.ch/en/publication/62105

6. IEC 61800-3:2022/COR1:2025 - דרישות EMC ושיטות בדיקה ל-PDS ול-Machine Tools. מקור רשמי: https://webstore.iec.ch/en/publication/65056

7. IEC 61800-5-1:2022 עם Corrigenda - בטיחות חשמלית, תרמית, אש, מכנית ואנרגיה ב-PDS. מקור רשמי: https://webstore.iec.ch/en/publication/62103

8. IEC 61800-5-2:2016 - Functional Safety של Safety-Related Power Drive Systems. מקור רשמי: https://webstore.iec.ch/en/publication/24556

9. IEC 61800-5-3:2021 - דרישות Safety, Electrical ו-Environmental ל-Safety-Related Encoders. מקור רשמי: https://webstore.iec.ch/en/publication/28614

10. IEC 61800-7-1:2015 וחלקים נלווים - Generic Interface, Drive Profiles ומיפוי לרשתות. מקור רשמי: https://webstore.iec.ch/en/publication/23757

11. IEC 61800-9-2:2023+A1:2025 - קביעת יעילות וסיווג Motor Systems. מקור רשמי: https://webstore.iec.ch/en/publication/111276

12. IEC 60204-1:2016+A1:2021 - ציוד חשמלי למכונות ודרישות Stop/Control. מקור רשמי: https://webstore.iec.ch/en/publication/71256

13. ISO 13849-1:2023 - תכן ואינטגרציה של Safety-Related Parts במערכות בקרת מכונות. מקור רשמי: https://www.iso.org/standard/73481.html

14. IEC 62061:2021+A1:2024+A2:2026 - Functional Safety של מערכות בקרה בטיחותיות למכונות. מקור רשמי לתיקון 2026: https://webstore.iec.ch/en/publication/92835

15. PLCopen Motion Control - Axis State Model ו-Function Blocks לתנועה יחידה ומתואמת. מקור רשמי: https://www.plcopen.org/standards/motion-control/

# 12. שער איכות לפרק

- המאזין יכול לשרטט את השרשרת המלאה מדרישה ועד תנועה.

- Speed, Torque, Position ו-Process Effect אינם מוצגים כמילים נרדפות.

- Sizing כולל Inertia, Duty, Thermal Limits ו-Regenerative Energy.

- PWM, Cable, Motor ו-Grounding מוצגים כמערכת אלקטרומגנטית אחת.

- דיוק Servo מוגבל על ידי מכניקה ומיקום Feedback.

- Safe Motion מוצג בתוך Risk Assessment ו-Validation של המכונה.

- האבחנה הסופית פותרת גם את חריגת המיקום וגם את DC-Bus Overvoltage.

- הסיום מוביל באופן ברור לתקשורת תעשייתית דטרמיניסטית.
