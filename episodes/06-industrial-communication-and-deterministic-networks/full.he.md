---
episode: 6
language: he
title: "תקשורת תעשייתית ורשתות דטרמיניסטיות"
target_duration: "40-45 minutes"
status: completed
extracted_from: docx
---

> CONTROL EDGE \| פרק 6<br>תקשורת תעשייתית ורשתות דטרמיניסטיות<br>מ-Fieldbus ו-Industrial Ethernet עד בקרה מסונכרנת ו-TSN<br>Latency \| Jitter \| PROFINET \| EtherNet/IP \| EtherCAT \| PTP \| Redundancy \| TSN

| קהל יעד | מהנדסי מכונות, תהליך, ייצור, מכשור, חשמל ואוטומציה |
| --- | --- |
| משך יעד | 42-45 דקות |
| פורמט | יעל - מהנדסת מכונות צעירה; אמיר - מהנדס תהליך ובקרה ותיק |
| דוגמת ליבה | תא אריזה סובל מ-Remote I/O Timeout ומחוסר סנכרון Servo בזמן Camera Burst |
| תוצר | תסריט מלא + הנחיית NotebookLM + מפות ארכיטקטורה + Checklist + מקורות |

חומר לימודי. אינו מחליף תכן רשת, הערכת Functional Safety, הנדסת Cybersecurity, הוראות יצרן, דרישות Conformance או מהדורות תקן מחייבות.

# 1. בדיקת התאמה לפני הפקה

- הפרק ממשיך ישירות מפרק 5: Coordinated Motion ו-Distributed I/O תלויים ב-Timing של התקשורת ולא רק בביצועי המנוע והבקר.

- המבנה מפריד בין Physical Media, מיתוג Ethernet, ‏IP Transport, ‏Industrial Application Profiles, סנכרון זמן והתנהגות המכונה.

- שמות פרוטוקולים מוצגים כארכיטקטורות וכ-Ecosystems שונים ולא כדירוג מהירות אוניברסלי.

- Functional-Safety Communication ו-Cybersecurity מוצגים כגבולות תכן; פרקים ייעודיים בהמשך יעמיקו בהם.

- הסיום יוצר גשר לפרק 7 בנושא שפות IEC 61131-3 ו-Software Architecture לאוטומציה.

> בדיקת עדכניות \| מפת המקורות נבדקה מול חומר רשמי ועדכני של IEC, ‏IEEE, ‏PI, ‏ODVA, ‏ETG, ‏Modbus Organization, ‏OPC Foundation ו-Ethernet-APL. היא משקפת IEC 61158-1:2023, את המבנה החדש של סדרת IEC 61784-2:2023, את IEC 61918:2018 עם תיקונים עד 2024, את IEC/IEEE 60802:2026, מהדורות IEC 62541 שפורסמו ב-2025-2026 והנחיות עדכניות של ארגוני הפרוטוקולים. בכל פרויקט יש לבדוק מהדורה ו-Profile שאומצו בחוזה ובדין.

# 2. מטרות הפרק

- לשרטט שרשרת תקשורת End-to-End מהאירוע הפיזיקלי דרך חיישן, רשת, בקר, Output ו-Actuator.

- להבחין בין Bandwidth, ‏Update Time, ‏Latency, ‏Jitter, דיוק Synchronization, ‏Data Age, ‏Packet Loss ו-Recovery Time.

- להסביר את התפקיד המעשי של Ethernet, ‏Switching, ‏IP, ‏TCP, ‏UDP ו-Industrial Application Profiles.

- להשוות Fieldbus, ‏Modbus TCP, ‏PROFINET, ‏EtherNet/IP, ‏EtherCAT ו-OPC UA ברמת הארכיטקטורה.

- לתכנן Topology, ‏Media, ‏Multicast, ‏Priority, ‏Redundancy ו-Diagnostics מתוך דרישות האפליקציה.

- להסביר Precision Time Protocol, ‏Distributed Clocks ו-Timestamped Execution.

- להבין TSN כארגז כלים תקני ואת חשיבות IEC/IEEE 60802:2026 בלי להפריז במידת ה-Interoperability הקיימת.

# 3. חלוקת זמן ומקטעים

| זמן | מקטע | מטרה |
| --- | --- | --- |
| 00:00-03:00 | פתיחה | Ping עובר בזמן ש-Control Deadlines נכשלים. |
| 03:00-06:30 | ארכיטקטורה | סיווג Traffic ומיפוי חוג End-to-End. |
| 06:30-10:30 | שכבות רשת | הפרדת Media, ‏Ethernet, ‏IP, ‏Transport ו-Automation Services. |
| 10:30-14:30 | Real-Time Metrics | Latency, ‏Jitter, ‏Data Age, עומס והתנהגות דטרמיניסטית. |
| 14:30-18:30 | Fieldbus | למה Serial ו-CAN Based Systems עדיין שימושיים. |
| 18:30-24:00 | Industrial Ethernet | השוואת ארכיטקטורות ו-Ecosystems מרכזיים. |
| 24:00-28:00 | Interaction Models | Cyclic, ‏Acyclic, ‏Client-Server, ‏Producer-Consumer ו-PubSub. |
| 28:00-32:30 | Topology ו-Switching | Managed Infrastructure, ‏VLAN, ‏Priority, ‏Multicast ו-Media. |
| 32:30-36:30 | Time Synchronization | PTP, ‏Distributed Clocks, ‏Timestamping ו-Clock Health. |
| 36:30-40:00 | Redundancy | דרישות Recovery, ‏Rings, ‏PRP ו-HSR. |
| 40:00-43:00 | TSN ו-Convergence | ארגז כלי IEEE, ‏IEC/IEEE 60802 וכיוון UAFX. |
| 43:00-45:00 | פתרון תקלה | פתרון Congestion ו-Clock Configuration וגשר לתוכנה. |

# 4. מפת ארכיטקטורת תקשורת תעשייתית

| שכבה / שלב | החלטה הנדסית | כשל אופייני |
| --- | --- | --- |
| 1. דרישת האפליקציה | להגדיר Traffic Class, ‏Deadline, ‏Update Period, ‏Data Age, תגובה לאובדן וזמינות. | בחירת Protocol לפני הגדרת התוצאה הפיזיקלית של עיכוב. |
| 2. Physical Medium | בחירת Copper, ‏Fiber, ‏Serial Bus, ‏SPE/APL, מחבר, מרחק, סביבה והארקה. | שגיאות לסירוגין, רגישות EMC, ‏Stubs ארוכים או מחברים לא מתאימים. |
| 3. Data Link ו-Switching | הגדרת Topology, ‏Duplex, ‏VLAN, ‏Queues, ‏Multicast, ‏Forwarding ו-Redundancy. | Bursts ממלאים Queues; ‏Multicast מציף Devices; תלות Line סמויה. |
| 4. Network ו-Transport | החלטה על Layer 2 מקומי, Routing, ‏TCP, ‏UDP וגבולות Addressing. | Retransmission משתנה, כתובות כפולות או Routed Path לא מתוכנן. |
| 5. Application Profile | בחירת Services, ‏Device Profiles, ‏Diagnostics, ‏Conformance וכלי Engineering. | ה-Bits עוברים אך State, יחידות, Timing או Fail Behavior אינם Interoperable. |
| 6. זמן ו-Scheduling | הגדרת Clock Profile, ‏Timestamping, ‏Execution Model, גבולות Offset ו-Alarms. | הודעות מגיעות אך התקנים מתואמים פועלים מול Time Bases שונים. |
| 7. Availability | הגדרת Faults נסבלים, Maximum Recovery, התנהגות Output ואסטרטגיית תיקון. | יש Ring, אך Recovery חורג מ-Watchdog או שני הנתיבים חולקים Cause. |
| 8. Lifecycle וראיות | שליטה ב-Configuration, ‏Firmware, ‏Backups, ‏Monitoring, ‏Captures ו-Acceptance. | הרשת עובדת בתחילה אך אי אפשר לשחזר, לאבחן או לאבטח אותה. |

# 5. מפת החלטה טכנולוגית

| טכנולוגיה / דפוס | התאמה אופיינית | שאלות בחירה |
| --- | --- | --- |
| Serial Fieldbus / Modbus RTU | מכשירים פשוטים, מרחקים, נפח מידע נמוך ו-Brownfield. | Poll Cycle, ‏Termination, ‏Stubs, כתובות, Scaling, ‏Diagnostics ו-Lifecycle? |
| Modbus TCP | Register Exchange פשוט, Meters, ‏Skids ואינטגרציה רב-יצרנית. | האם Request-Response Timing מספיק? כיצד מוגדרים Units, ‏Quality ו-Security? |
| PROFINET RT / IRT | Distributed I/O, ‏Drives ו-Machine Automation ב-Ecosystem של PI. | Conformance Class, ‏Cycle, ‏Synchronization, טופולוגיה ו-Certification? |
| EtherNet/IP עם CIP Services | General Control, Process, Safety, Time Sync ו-Motion ב-Ecosystem של ODVA. | Requested Packet Interval, ‏Multicast, ‏CIP Sync/Motion, ‏DLR ותשתית? |
| EtherCAT | I/O צפוף וביצועים גבוהים עם Synchronized Motion ו-On-the-Fly Processing. | Cycle, ‏Distributed Clocks, טופולוגיה, MainDevice ו-Diagnostics? |
| משפחות Real-Time Ethernet נוספות | POWERLINK, ‏Sercos, ‏CC-Link IE ו-Ecosystems ייעודיים. | זמינות Devices, ידע מותקן, Profiles, ‏Certification ו-Lifecycle? |
| OPC UA / UAFX | Semantic Interoperability, ‏Controller-to-Controller והעברת מידע כלפי מעלה. | איזה Profile שוחרר, Information Model, ‏PubSub Mapping, ‏Security וביצועים? |
| TSN-Profiled Converged Ethernet | תעבורה רגישה לזמן ותעבורה רגילה על תשתית משותפת מתוכננת. | אילו 802.1 Features, ‏IEC/IEEE 60802, מודל קונפיגורציה ו-Conformance? |

> עיקרון מרכזי \| רשת בקרה מתקבלת לפי ההתנהגות הפיזיקלית שהיא משמרת תחת עומס ותקלות מוגדרים - לא לפי Link Speed, לוגו Protocol, ‏Ping מוצלח או Benchmark על רשת ריקה.

# 6. הנחיית הפקה ל-NotebookLM

> הנחיה מוכנה להדבקה \| צור פרק פודקאסט הנדסי בעברית בלבד, באורך 42-45 דקות, תוך שימוש במסמך זה בלבד. השתמש בשני מגישים: יעל, מהנדסת מכונות צעירה וסקרנית ששואלת שאלות תכן ואבחון ישירות; ואמיר, מהנדס תהליך ובקרה ותיק עם ניסיון מעשי במכונות. שמור על שיחה טבעית אך מדויקת. אל תקרא טבלאות או כתובות מקורות בקול. פתח בתקלה בתא האריזה והסתר את האבחון המלא עד המקטע האחרון. הבדל שוב ושוב בין Bandwidth, Latency, Jitter, Synchronization, Data Age ו-Recovery Time. הצג PROFINET, EtherNet/IP, EtherCAT, Modbus ו-OPC UA כארכיטקטורות שונות ולא כדירוג. הסבר TSN כארגז כלים ואת IEC/IEEE 60802 כ-Profile. השתמש בדוגמאות תעשייתיות קצרות, אתגר מיתוסים נפוצים וסיים בחמש מסקנות ובגשר לשפות PLC ול-Software Architecture. בפעם הראשונה אמור את משמעות ראשי התיבות ולאחר מכן השתמש בהם באופן טבעי.

# 7. תסריט מלא לפרק

## 00:00-03:00 | פתיחה - הרשת שעוברת כל בדיקת Ping

יעל: תא האריזה עובד בצורה מושלמת במשך כמה דקות. ואז מערכת ה-Vision מעלה מקבץ תמונות, תחנת Remote I/O מדווחת Timeout, ושני צירי Servo מגיעים בהפרש של כמה מילי-שניות. האחזקה עושה Ping לכל רכיב ומקבלת תשובה נקייה. המסקנה שלהם: הרשת תקינה.

אמיר: Ping מוצלח מוכיח רק שקיים נתיב IP שהחזיר תשובה לבקשת אבחון קטנה. הוא אינו מוכיח ש-Cyclic Control Data הגיע בתוך חלון הזמן הנדרש, עם Jitter מותר, בסדר הנכון או כשההתקנים מסונכרנים לאותו שעון.

יעל: כלומר הרשת יכולה להיות מחוברת ובכל זאת לא מתאימה לבקרה.

אמיר: בדיוק. ברשת משרדית קובץ שהתעכב הוא מטרד. במכונה Output שהתעכב יכול לשנות אירוע פיזיקלי. הרשת אינה רק מעבירה מידע; היא עשויה לשאת חלק מחוג הבקרה.

יעל: העברת התמונות מרמזת על עומס רוחב פס, אבל ההפרש בין הצירים נשמע כמו בעיית Timing.

אמיר: ייתכן קשר, אבל אסור לקפוץ ישר ל'נקנה Switch מהיר יותר'. צריך לזהות את מחלקות התעבורה, חוזה הזמן של כל מחלקה, הטופולוגיה, התנהגות התורים, שיטת הסנכרון ומה כל התקן עושה כאשר Deadline מוחמץ.

יעל: היום נפריד בין Bandwidth, ‏Latency, ‏Jitter, סנכרון וזמינות, ונשווה Fieldbus, ‏Industrial Ethernet ו-TSN בלי להפוך שמות פרוטוקולים לטבלת ליגה.

אמיר: ובסיום נחזור לתא האריזה עם ראיות ולא עם אמונות מהשטח.

## 03:00-06:30 | הרשת היא חלק מארכיטקטורת המכונה

יעל: איפה מהנדס מכונות או תהליך צריך לצייר את הרשת בתרשים המערכת?

אמיר: בין כל Producer ו-Consumer של מידע בקרה. חיישן מפרסם מדידה, Controller מחשב Command, ‏Drive מקבל Setpoint ו-HMI מבקש Diagnostics. הרשת מחברת בין הפונקציות, אבל לכל Exchange יש תוצאה אחרת אם הוא מאחר או אובד.

יעל: לכן מתחילים ממחלקות מידע ולא ממותג פרוטוקול.

אמיר: כן. מסווגים Cyclic I/O, ‏Motion Setpoints, הודעות Safety, ‏Alarms, ‏Recipes, הורדות Engineering, תעבורת Historian, וידאו וגישת תחזוקה. לכל מחלקה מגדירים Update Period, גיל מידע מרבי, Jitter מותר, תגובה לאובדן, זמן התאוששות וזמינות נדרשת.

יעל: Update Period הוא אותו דבר כמו Latency?

אמיר: לא. Controller יכול לייצר ערך כל 1 ms, בעוד End-to-End Latency מהדגימה עד הפעולה יהיה כמה מילי-שניות. Jitter הוא השינוי סביב ה-Latency. Data Age כולל גם המתנה לפני שידור והמתנה עד שה-Task בצד המקבל משתמש בערך.

יעל: זה מתחבר ישירות לפרק 2. רשת מהירה אינה מפצה על PLC Task איטי.

אמיר: נכון. תגובת הקצה כוללת Sensor Conversion, עדכון Input, העברה ברשת, Task Scheduling, הרצת Logic, עדכון Output ותגובת Actuator. אופטימיזציה של חוליה אחת בלי למדוד את השרשרת יכולה לתת מפרט מרשים והתנהגות גרועה.

יעל: מה שאלת הארכיטקטורה הראשונה?

אמיר: מי בעל הבית על הזמן. האם הבקר עושה Poll, האם ההתקנים מייצרים מידע מחזורית, האם כולם חולקים Clock, או שהמקבל פועל לפי Timestamp? התשובה קובעת כיצד מנתחים Determinism.

## 06:30-10:30 | שכבות: כבל, Ethernet, ‏IP ופרוטוקול האוטומציה

יעל: מהנדסים אומרים לעיתים 'זה Ethernet' כאילו זה מתאר את כל המערכת.

אמיר: Ethernet מגדיר בעיקר Framing והתנהגות Media בשכבות התחתונות. מעליו יכולים להיות IP, ‏UDP או TCP, ומעליהם Industrial Application Protocol. חלק מהפרוטוקולים משתמשים ב-Ethernet Frames רגילים אך עוקפים TCP/IP עבור Cyclic Traffic. אחרים משתמשים ב-UDP עם End Devices מסונכרנים. EtherCAT מעבד Frame ייעודי תוך כדי מעבר דרך התחנות.

יעל: כלומר מחבר RJ45 לא אומר כיצד נתוני הבקרה יתנהגו.

אמיר: וגם קישור של 1 Gbit/s לא. צריך לדעת Physical Medium, ‏Duplex, ארכיטקטורת Switch, הגדרות VLAN ו-Priority, התנהגות Multicast, מנגנון Transport, ‏Application Profile ומימוש ההתקן.

יעל: תסביר MAC Address ו-IP Address בצורה שימושית.

אמיר: Switch מעביר Ethernet Frames בעיקר לפי MAC בתוך Layer 2 Domain. כתובת IP מאפשרת Routing בין רשתות Layer 3. Routing חשוב לסגמנטציה ול-Scale, אבל Exchange מחזורי רבים תוכננו לדומיין מקומי ממותג או דורשים תכן מפורש כאשר הם עוברים Router.

יעל: איפה TCP ו-UDP נכנסים?

אמיר: TCP מספק Ordered Reliable Byte Stream עם Acknowledgement ו-Retransmission. זה שימושי לקונפיגורציה, קבצים ושירותי Client-Server רבים, אבל Retransmission מייצר השהיה משתנה. UDP הוא Connectionless; האפליקציה צריכה לטפל באובדן, סדר ו-Freshness.

יעל: ו-Fieldbus Profile מתקן יותר מפורמט Packet.

אמיר: רצוי שהוא יגדיר Services, התנהגות Device, ‏State Machines, ‏Timing וציפיות Conformance. סדרת IEC 61158 כוללת מפרטי Fieldbus, ו-IEC 61784 מארגנת Communication Profiles. המשפחות גדולות כי Interoperability תעשייתי דורש יותר מהסכמה על Bits.

יעל: לכן Gateway יכול לתרגם Registers ובכל זאת לאבד Diagnostics או Timing Semantics.

אמיר: בדיוק. Protocol Conversion אינו מבטיח שימור התנהגות.

## 10:30-14:30 | Real Time הוא תוצאה חסומה בזמן, לא ממוצע קטן

יעל: אנשים מכנים כל רשת מהירה Real Time. באיזו הגדרה נשתמש?

אמיר: הגדרה הנדסית שימושית היא שהפעולה התקשורתית הנדרשת מסתיימת בתוך חלון זמן מוגדר וברמת ודאות מוגדרת. ה-Deadline מגיע מהאפליקציה. חוג טמפרטורה יכול לסבול מאות מילי-שניות; Coordinated Motion עשוי לדרוש Updates מסונכרנים והסכמת Clock ברמת מיקרו-שנייה.

יעל: אילו מספרים צריכים להופיע בדרישה?

אמיר: Cycle או Update Time, ‏End-to-End Latency, ‏Jitter, דיוק סנכרון, Packet Loss, ‏Startup Time, זמן התאוששות לאחר תקלה ומגבלת Data Age. בנוסף עומס רשת במצב רגיל, בשיא ובזמן כשל.

יעל: למה Average Latency מסוכן?

אמיר: כי המכונה נכשלת בזנב ההתפלגות. ממוצע של 0.5 ms יכול להסתיר אירועים של 10 ms. צריך Maximum שנמדד תחת עומס מוגדר, או Bound מוצדק, יחד עם Counters שמגלים Frames שנזרקו או איחרו.

יעל: Determinism הוא אותו דבר כמו אפס Packet Loss?

אמיר: לא. Determinism עוסק ב-Timing ובהתנהגות צפויים. מערכת יכולה לזהות Timeout באופן דטרמיניסטי ולעבור למצב בטוח. לעומת זאת רשת יכולה לא לאבד Packet בבדיקה קצרה ועדיין לסבול Queue Delay בלתי חסום בזמן Burst.

יעל: ומה לגבי אחוז ניצול Bandwidth?

אמיר: הוא חשוב, אך אינו מספיק. Average Load נמוך יכול להכיל Bursts שממלאים Queues. Frame ארוך שאינו ניתן ל-Preemption יכול לחסום Frame דחוף. Multicast יכול להיות משוכפל לפורטים רבים. צריך להבין Traffic Shape ו-Queue Behavior, לא רק Mbit/s.

יעל: כלומר Acceptance Test צריך לייצר עומס גרוע סביר, לא רשת ריקה.

אמיר: כן, כולל Engineering Download, ‏Camera Burst, שאילתות Historian, החלפת Device, Link Failure ו-Controller Switchover כאשר רלוונטי.

## 14:30-18:30 | למה Fieldbus עדיין קיים

יעל: אם Industrial Ethernet כל כך חזק, למה מפעלים עדיין משתמשים ב-Serial וב-Fieldbus מבוסס CAN?

אמיר: כי Fieldbus בשל יכול להיות פשוט, אמין ומתאים לתהליך. רשת דו-גידית Multi-drop יכולה להתאים למספר מתון של מכשירים לאורך גדול. מערכות מבוססות CAN נותנות Arbitration ו-Frames קומפקטיים. במפעל קיים יש הכשרה, חלפים ותכן שכבר עבר Validation.

יעל: Modbus RTU מכונה לעיתים פרימיטיבי.

אמיר: הוא פשוט ואינו Self-Describing. Master מבקש Coils או Registers, והמהנדס חייב לדעת מה משמעות כל Address, איך מבוצע Scaling, מה Byte Order ומה התגובה ל-Timeout ול-Exception. הפשטות יכולה להיות יתרון ב-Exchange קטן ואיטי, אך היא מעבירה אחריות סמנטית לשרטוטים ולתוכנה.

יעל: מה הטעויות ההנדסיות הנפוצות?

אמיר: Termination שגוי, Star Wiring ברשת שמצפה ל-Line, ‏Stubs ארוכים, Biasing חסר, כתובות כפולות, Baud או Parity שונים, Shielding לקוי ו-Timeout שנבחר בלי לחשב Poll Cycle מלא.

יעל: Poll Cycle מתארך ככל שמוסיפים Devices ו-Retries.

אמיר: בדיוק. ערך יכול להתעדכן פיזיקלית מהר אך להיקרא רק פעם בשנייה משום שה-Master משרת התקנים רבים. ה-HMI יכול להציג אותו כאילו הוא Current אם האפליקציה אינה נושאת Timestamp או Quality Flag.

יעל: לכן Migration לא צריך להיות מוצדק רק באמצעות מהירות.

אמיר: נכון. עוברים בגלל Lifecycle, ‏Diagnostics, נפח מידע, Maintainability, ‏Integration או Availability. לא מחליפים Fieldbus עובד בקלות, אך גם לא נותנים להרגל Brownfield למנוע ארכיטקטורה שמכונה חדשה באמת דורשת.

יעל: והתקנה נשארת מקצוע פיזיקלי.

אמיר: IEC 61918 ו-Installation Profiles בסדרת IEC 61784-5 מזכירים שטופולוגיה, כבלים, מחברים, הפרדה, הארקה ואימות הם חלק מהנדסת התקשורת.

## 18:30-24:00 | משפחות Industrial Ethernet הן ארכיטקטורות שונות

יעל: בוא נשווה את המשפחות המרכזיות בלי להכריז על מנצח אוניברסלי.

אמיר: נתחיל ב-Modbus TCP. הוא ממפה את מודל Modbus המוכר ל-TCP/IP. הוא נפוץ ושימושי ל-Request-Response פשוט, אבל הפרוטוקול לבדו אינו ארכיטקטורת Timing ל-Coordinated Motion.

יעל: PROFINET משתמש בכמה ערוצי תקשורת.

אמיר: TCP/IP רגיל מטפל בשירותים שאינם Time-Critical. ‏PROFINET RT שולח Cyclic Real-Time Frames ללא מסלול TCP/IP עבור אוטומציה טיפוסית. PROFINET IRT מוסיף מנגנוני Scheduling מסונכרנים ל-Isochronous Applications. צריך להגדיר Conformance Class וביצועים, לא להניח אותם מהמילה PROFINET.

יעל: EtherNet/IP משתמש ב-CIP בשכבת האפליקציה.

אמיר: כן. הוא תומך ב-Explicit Messaging וב-Cyclic I/O, בדרך כלל עם UDP ל-Produced/Consumed Data. ‏CIP Sync מספק Precision Time, ו-CIP Motion משתמש בהתנהגות מסונכרנת ו-Timestamps כך שה-End Devices יכולים לבצע Motion מתואם בלי לדרוש מכל Frame להגיע בדיוק באותו רגע.

יעל: EtherCAT בוחר גישה אחרת.

אמיר: ה-MainDevice שולח Frame דרך הסגמנט, וה-SubDevices קוראים ומכניסים Process Data תוך כדי מעבר. Hardware Processing ו-Distributed Clocks נותנים Timing צפוי ויעיל, ולכן הגישה אטרקטיבית ל-I/O צפוף ול-Motion. הוא מבוסס Ethernet, אבל התנהגות הסגמנט אינה זהה לרשת TCP/IP ממותגת רגילה.

יעל: ומה לגבי POWERLINK, ‏Sercos ו-CC-Link IE TSN?

אמיר: אלה Ecosystems מבוססים נוספים עם Scheduling, ‏Profiles ו-Conformance משלהם. הלקח אינו לזכור דירוג, אלא להתאים Timing, טופולוגיה, זמינות Devices, כלי Engineering, ‏Safety Profile, ‏Diagnostics, ‏Lifecycle ויכולת הצוות.

יעל: האם מכונה אחת צריכה פרוטוקול אחד?

אמיר: לא בהכרח. Motion Bus יכול לשרת Axes ו-I/O, בעוד OPC UA חושף מידע מובנה כלפי מעלה. Gateway יכול לחבר Instrument Bus ישן. אבל בכל Boundary צריך להגדיר Ownership, ‏Data Quality, זמן ותגובה לכשל.

יעל: כיצד מתייחסים להעדפת Vendor?

אמיר: כאילוץ Lifecycle לגיטימי, לא כהוכחה לעליונות טכנית. Installed Base, תמיכה מקומית, אסטרטגיית חלפים ויכולת Engineering יכולים לשלוט בעלות הכוללת יותר מפרוטוקול מהיר תיאורטית.

יעל: וגם Conformance Testing חשוב.

אמיר: מאוד. Specification מייצר אפשרות; Product שנבדק ל-Conformance ו-System Commissioning מייצרים ביטחון.

## 24:00-28:00 | Cyclic, ‏Acyclic, ‏Client-Server ו-Publish-Subscribe

יעל: השתמשנו בהרבה דפוסי תקשורת. אפשר לסדר אותם?

אמיר: Cyclic Data מוחלף במחזור מוגדר, בדרך כלל עבור Process I/O. ‏Acyclic Services נושאים Parameters, ‏Alarms, זיהוי ו-Diagnostics לפי צורך. Client-Server אומר שצד אחד מבקש Service ומקבל Response. ‏Producer-Consumer או Publish-Subscribe מאפשרים ל-Producer אחד להפיץ מידע ל-Consumer אחד או יותר.

יעל: Publish-Subscribe הוא אוטומטית Real Time?

אמיר: לא. הוא מתאר Interaction Pattern ולא Timing Guarantee. התנהגות Real-Time תלויה ב-Transport, ‏Scheduling, קונפיגורציית הרשת, Endpoints וה-Profile.

יעל: OPC UA מוצג לעיתים כתשובה אוניברסלית.

אמיר: OPC UA מספק Information Model עשיר, Services, ‏Security Model וכמה Transport Mappings. הוא מצוין ל-Semantic Interoperability. ‏OPC UA PubSub ועבודת UAFX מרחיבים אותו לכיוון Field-Level Exchange, אבל צריך להגדיר Profile, ‏Interaction וביצועים מדויקים ולא להשתמש ב-'OPC UA' כטענת Timing.

יעל: למה Semantics חשובה למהנדסי מכונות ותהליך?

אמיר: מספר ללא יחידה, Status, ‏Timestamp, טווח וזהות הוא שברירי. Model סמנטי יכול לומר שהערך הוא Discharge Pressure ב-kPa עם Quality ו-Device Context, ולא Register 40127 כפול 0.1.

יעל: אבל Model עשיר מייצר יותר קונפיגורציה.

אמיר: כן. Interoperability דורש Companion Specifications, ‏Device Profiles ומשמעת Naming. Model גמיש שמשתמשים בו בצורה לא עקבית יכול להיות קשה יותר לאינטגרציה ממפה פשוטה שנוהלה היטב.

יעל: Safety Communication משתמשת בשכבת משמעת נוספת.

אמיר: IEC 61784-3 מתאר Functional-Safety Communication Profiles בגישת Black Channel. ה-Safety Layer וה-End Points המאומתים מספקים את אמצעי ה-Safety Integrity; לא מניחים שהרשת הרגילה חפה מתקלות. זה אינו מבטל תכן Availability ו-Cybersecurity של הרשת התחתונה.

## 28:00-32:30 | טופולוגיה, Switches והנדסת תעבורה

יעל: תא האריזה משתמש ב-Line Topology דרך פורטי ההתקנים, ואז Unmanaged Switch מחבר את המצלמה וה-HMI. מה בודקים?

אמיר: קודם מציירים את הטופולוגיה הפיזית והלוגית בפועל. פורטים של Device יכולים להכיל Switch פנימי. קו של עשרים התקנים מייצר Propagation ו-Forwarding בכל תחנה. אובדן מתח של תחנה אחת יכול לפתוח את הקו אם אין Ring או Alternate Path.

יעל: מתי Managed Switch מוצדק?

אמיר: כאשר צריך ראיות ושליטה: Port Statistics, ‏Topology Discovery, ‏VLAN, ‏Priority Queues, ‏Multicast Management, ‏Port Mirroring, ‏Redundancy Protocols, תמיכת Time Sync, ‏Access Control או Alarms. ‏Unmanaged Switch יכול להתאים לתא פשוט ומבודד, אך קשה יותר לאמת ולאבחן את התנהגותו.

יעל: תסביר VLAN ו-Priority בלי להפוך את זה לקורס IT.

אמיר: VLAN מפריד Layer-2 Broadcast Domains באופן לוגי. Priority Marking מכניס Frames למחלקות Traffic, אבל Priority עובד רק אם כל Bridge מוגדר בעקביות והתורים תוכננו. Priority אינו Reserved Bandwidth, וגם Low-Priority Traffic חשוב אם Buffers או Links מגיעים לרוויה.

יעל: ומה לגבי Multicast?

אמיר: פרוטוקולי Producer-Consumer יכולים להשתמש ב-Multicast. בלי IGMP Snooping או בקרה ייעודית, Switch עלול להציף Multicast לפורטים שאינם צריכים אותו. זה מבזבז Bandwidth ויכול להעמיס ממשקי Device קטנים. Filtering שגוי יכול גם לחסום תעבורה נדרשת.

יעל: האם Camera Burst יכול למלא Queue גם כשיש Gigabit Uplink?

אמיר: כן, במיוחד במקום שבו התעבורה מתכנסת ל-Link של 100 Mbit/s או להתקן עם Buffers קטנים. Speed Transition, תעבורה א-סימטרית ו-Microbursts קובעים. Packet Capture בנקודה אחת עלול לא לראות את ה-Queue העמוס במקום אחר.

יעל: Copper מול Fiber?

אמיר: בוחרים לפי מרחק, סביבת EMC, אסטרטגיית הארקה, עמידות מחברים, Bend Radius, תחזוקה ו-Hazardous Area. Fiber מנתק נתיב גלווני ותומך במרחק, אך דורש משמעת ניקוי וחיבור. Ethernet-APL הוא Physical Layer נוסף לתעשיית התהליך: 10BASE-T1L דו-גידי עם Loop Power והרחבות למרחק ולאזורים מסוכנים.

יעל: כלומר Media Selection הוא תכן הנדסי ולא מחשבה מאוחרת של רכש.

אמיר: בדיוק.

## 32:30-36:30 | סנכרון זמן משנה את מודל הבקרה

יעל: למה לסנכרן Clocks אם הרשת כבר שולחת מידע מהר?

אמיר: כי התקנים מסונכרנים יכולים למדוד ולפעול מול Time Base משותף. Sample יכול לשאת את זמן הרכישה, ו-Axes יכולים לבצע Commands ברגע מתוזמן. כך מפרידים בין Execution Accuracy לבין Arrival Time משתנה בתוך חלון מותר.

יעל: זה מה ש-PTP מספק?

אמיר: IEEE 1588, שאומץ בינלאומית כ-IEC 61588, מגדיר Precision Time Protocol. ‏Profiles בוחרים אפשרויות לענפים שונים. IEEE 802.1AS מגדיר Timing ו-Synchronization לרשתות Bridged הרגישות לזמן. פרוטוקולים תעשייתיים יכולים להשתמש בעקרונות האלה או ב-Distributed Clocks משלהם.

יעל: איזו חומרה נדרשת?

אמיר: הדיוק תלוי במיקום Timestamp, איכות Oscillator, תמיכת Bridge, מדידת Path Delay, טופולוגיה ו-Profile. ‏Hardware Timestamping סמוך ל-Physical Interface יכול להסיר השהיית Software משתנה. סנכרון Clock רגיל בתוכנה אינו בהכרח מתאים ל-Motion.

יעל: כיצד מאמתים Synchronization?

אמיר: בודקים Grand Clock Selection, ‏Domain ו-Profile, ‏Offset, ‏Path Delay, שינויי Role, ‏Holdover ו-Alarms. אחר כך מאמתים את התוצאה הפיזיקלית באמצעות Trends מסונכרנים או ציוד מדידה. מסך שמראה Locked אינו Acceptance Criterion.

יעל: מה קורה אם הזמן שגוי אבל התקשורת עדיין פעילה?

אמיר: זה עלול להיות מסוכן יותר מניתוק נקי. התכן צריך גבול ל-Time Error, זיהוי ירידת Time Quality ותגובה מוגדרת. זמן הוא Controlled Resource ולא תשתית רקע.

יעל: בתא שלנו ייתכן שה-Axes מקבלים את כל ה-Setpoints אך מבצעים אותם מול Clocks שאינם מיושרים.

אמיר: בדיוק. צריך לבדוק גם Message Delivery וגם Clock Health.

## 36:30-40:00 | Redundancy היא דרישת זמן התאוששות

יעל: מפעלים מבקשים לעיתים Redundant Ring. האם זה מפרט מספיק?

אמיר: לא. צריך להגדיר אילו Single Faults נסבלים, האם מותרת הפסקת תקשורת, Maximum Recovery Time, מה קורה ל-Outputs בזמן התאוששות וכיצד התקלה מתריעה ומתוקנת.

יעל: השווה בין גישות נפוצות.

אמיר: גרסאות Spanning Tree מונעות Loops אך יכולות להתאושש לאט או בצורה משתנה עבור בקרה. Industrial Ring Protocols כגון MRP או DLR תוכננו לטופולוגיות מוגדרות ולהתאוששות מהירה יותר. PRP ו-HSR שולחים Frames כפולים במסלולים יתירים ויכולים לתת Seamless Switchover עם Zero Recovery Time לתקלת רשת בודדת, במחיר תשתית כפולה והתקנים תואמים.

יעל: Redundancy יכולה ליצור Common-Cause Failure חדש.

אמיר: כן. שני כבלים באותה תעלה, שני Switches על אותו ספק כוח או שני מסלולים לוגיים דרך Choke Point פיזי אחד אינם עצמאיים. טעות קונפיגורציה יכולה להשבית את שני הנתיבים יחד.

יעל: כיצד Controller Redundancy ו-Network Redundancy משתלבים?

אמיר: הם צריכים Sequence מערכת אחד. Controller Switchover, חידוש Connections, בעלות על Outputs, ‏Time Synchronization ו-Device Watchdogs נבדקים יחד. אם Recovery מהיר מה-Timeout הוא יכול להיות שקוף; אם הוא איטי יותר, ה-Device יכול לעבור למצב Safe או Stopped.

יעל: Availability אינה Safety.

אמיר: נכון. Redundancy יכולה להפחית Nuisance Stops, אבל Command מסוכן ששוכפל בצורה מושלמת עדיין מסוכן. Functional Safety, ‏Cybersecurity ו-Availability הן תכונות שונות שצריך לתאם.

יעל: וההוכחה היא Fault-Injection Test.

אמיר: מנתקים את ה-Link המוגדר, מכבים את ה-Switch המוגדר, מפריעים ל-Clock Source, מחליפים Device ומודדים את התגובה בפועל תחת עומס.

## 40:00-43:00 | TSN - ארגז כלים ועתה גם Profile תעשייתי

יעל: Time-Sensitive Networking מוצג כרשת שתאחד הכול. מה הוא למעשה?

אמיר: TSN הוא משפחת מנגנוני IEEE 802.1 עבור Time Synchronization, ‏Scheduled Traffic, ‏Traffic Shaping, ‏Frame Preemption, ‏Per-Stream Filtering and Policing, יתירות וקונפיגורציה מרכזית. הוא אינו Protocol אחד ואינו Automation Information Model.

יעל: כלומר Switch עם לוגו TSN אינו יוצר לבדו מערכת בקרה Interoperable.

אמיר: נכון. Devices צריכים לממש Features, ‏Profiles, ‏Configuration Models והנחות Timing תואמות. לכן IEC/IEEE 60802 חשוב: Profile לאוטומציה תעשייתית שפורסם ב-2026 ובוחר Features, אפשרויות ו-Procedures עבור Bridges, ‏End Stations ו-LANs.

יעל: תן דוגמאות מארגז הכלים.

אמיר: IEEE 802.1AS מספק Time Base משותף. Scheduled Traffic פותח וסוגר Transmission Gates לפי זמן. Frame Preemption מצמצם חסימה של Frame דחוף על ידי Frame ארוך בעדיפות נמוכה. Per-Stream Filtering and Policing מכיל תעבורה חריגה. Frame Replication and Elimination משפר אמינות.

יעל: האם TSN מחליף PROFINET, ‏EtherNet/IP או OPC UA FX?

אמיר: לא בפני עצמו. הוא יכול לספק תשתית Ethernet מתכנסת שעליה פרוטוקולים ומודלים תעשייתיים פועלים. ארגוני הפרוטוקולים מגדירים כיצד Services, ‏Engineering Workflow ו-Conformance שלהם משתמשים בתשתית.

יעל: מה המצב המעשי למהנדס כיום?

אמיר: להתייחס ל-TSN כיכולת מבוססת תקנים שנמצאת בהבשלה. מגדירים Products ו-Profiles שנתמכים ונבדקו בפועל, לא הבטחות Roadmap. פרסום IEC/IEEE 60802 הוא אבן דרך גדולה, אך System Interoperability עדיין תלוי במימוש וב-Conformance.

יעל: ו-UAFX מזיז את OPC UA לכיוון Field Exchange.

אמיר: כן, כאשר ה-Releases הנוכחיים מתמקדים במידה רבה ב-Controller-to-Controller וחזון רחב יותר מתפתח. שוב, בוחרים Profile משוחרר מדויק ובודקים את ה-Use Case.

## 43:00-45:00 | פתרון תקלה וסיום

יעל: חוזרים לתא האריזה. Packet Capture מראה שאין Link Loss. בכל Camera Burst ה-Unmanaged Switch מעביר תעבורת תמונות לאותו Device Line של 100 Mbit/s. ‏Egress Queue מתמלא, Cyclic Frames מאחרים ו-Watchdog של תחנת Remote I/O אחת פג.

אמיר: לבעיית ה-Motion יש סיבה נוספת. Drive חלופי אחד הוכנס לשירות ללא Time-Synchronization Profile הנדרש. הוא מקבל Commands, אבל Clock Offset גדל עד ש-Coordinated Execution חורג מהטולרנס.

יעל: לכן הפעולה המתקנת אינה רק Switch מהיר יותר.

אמיר: מפרידים Camera ו-Control Traffic לוגית ופיזית לפי צורך, משתמשים בתשתית Industrial Managed, מגדירים Real-Time Profile ו-Multicast Behavior, משחזרים קונפיגורציית סנכרון ב-Drive ומגדירים Alarms ל-Queue Drops, ‏Late Packets ו-Clock Offset.

יעל: ואז חוזרים על הבדיקה עם Worst-Case Image Transfer, ‏Engineering Traffic ו-Ring Fault.

אמיר: ומנטרים End-to-End Evidence: ‏Controller Task Timing, ‏Protocol Diagnostics, ‏Switch Counters, ‏Watchdog Events, ‏Clock Quality ו-Physical Axis Error. הרשת מתקבלת רק כאשר התנהגות המכונה נשארת בתוך הדרישה.

יעל: מה צריך לזכור?

אמיר: ראשית, Connected אינו Deterministic. שנית, Bandwidth, ‏Latency, ‏Jitter, סנכרון ו-Recovery הן דרישות שונות. שלישית, בחירת Protocol מתחילה באפליקציה וב-Lifecycle. רביעית, Topology ו-Installation הם חלק מתכן הבקרה. חמישית, כל Fault Response חייב להיות מוגדר ונבדק.

יעל: בפרק הבא נעלה מעל הרשת אל שפות תכנות PLC ו-Software Architecture: כיצד Ladder, ‏Structured Text, ‏Function Blocks, ‏State Machines ו-Modules לשימוש חוזר הופכים דרישות לקוד שניתן לתחזק.

אמיר: כי רשת דטרמיניסטית מושלמת עדיין יכולה להעביר Command שתוכנן רע - בדיוק בזמן.

# 8. הערות למפיק ולמגישים

- לשמור לאורך כל השיחה על התוצאה הפיזיקלית של Late או Stale Data.

- לא להשתמש ב-Bandwidth, ‏Latency, ‏Jitter, ‏Synchronization ו-Determinism כמילים נרדפות.

- לא לטעון שמשפחת Industrial Ethernet אחת טובה או מהירה תמיד.

- כאשר מוזכרים ביצועים מספריים, להדגיש שהם תלויי Profile, תכן ומימוש ולא System Guarantee אוניברסלי.

- להסביר ש-Gateway יכול לשמור Values אך לאבד State, ‏Diagnostics, ‏Timestamps או Failure Semantics.

- לא לרמוז ש-VLAN או Priority לבדם שומרים Bandwidth או יוצרים Determinism.

- להבהיר את הגבול בין Availability, ‏Functional Safety ו-Cybersecurity.

- לא לקרוא מספרי תקנים בדיאלוג, למעט IEC/IEEE 60802 במקטע TSN.

- להסתיר עד הסיום את הסיבה השנייה לתקלה - Clock Profile שגוי ב-Drive.

# 9. Checklist הנדסי לרשת תעשייתית

1. איזו פעולה פיזיקלית תלויה בכל Communication Flow, ומה קורה אם המידע מאחר, ישן, מוכפל או אובד?

1. מהם Update Period, ‏Maximum End-to-End Latency, ‏Jitter, דיוק Synchronization ומגבלת Data Age?

1. אילו Flows הם Cyclic I/O, ‏Motion, ‏Safety, ‏Alarms, ‏Engineering, ‏Historian, וידאו או תחזוקה?

1. איזה Protocol Profile, ‏Device Class ו-Conformance Evidence נדרשים - ולא רק איזה שם Protocol?

1. איזה Physical Medium, מחבר, מרחק, טופולוגיה, Environmental Rating והארקה מתאימים?

1. איפה נמצאים Speed Transitions, נקודות התכנסות, Queues וממשקי Device בעלי קיבולת נמוכה?

1. כיצד VLAN, ‏Priority, ‏Multicast, ‏IGMP ו-Routing מתוכננים ומתועדים?

1. מי בעל הבית על הזמן, איזה Clock Profile משמש ואיזה Offset או Time Quality מפעילים תגובה?

1. אילו Single Faults צריכים להיות נסבלים, מה Maximum Recovery ומה קורה ל-Outputs בזמן התאוששות?

1. האם נתיבים יתירים עצמאיים במסלול כבלים, מתח, Switching, ‏Configuration ו-Clock Source?

1. אילו Switch, ‏Controller ו-Protocol Counters נאספים, מתריעים ונשמרים?

1. כיצד Configuration, ‏Firmware, ‏Certificates, ‏Device Descriptions ו-Backups מנוהלים בגרסאות?

1. אילו Worst-Case Traffic ו-Fault-Injection Tests מוכיחים ביצועים לפני Release?

1. אילו שינויים מחייבים Revalidation: ‏Device, ‏Switch, טופולוגיה, מצלמה, Firmware, ‏Task Time, ‏Profile או עומס?

# 10. מילון מונחים

| מונח | משמעות בפרק |
| --- | --- |
| Bandwidth | קיבולת העברת המידע של Link; אינו Timing Guarantee. |
| Latency | זמן מאירוע מקור מוגדר עד אירוע יעד מוגדר. |
| Jitter | שינוי ב-Latency, ב-Cycle Timing או ב-Execution Timing. |
| Data Age | הזמן מרכישת או יצירת ערך ועד השימוש בו. |
| Determinism | Timing חסום וצפוי והתנהגות מוגדרת בתנאים נתונים. |
| Cyclic I/O | Process Data שמוחלף שוב ושוב במחזור מוגדר. |
| Acyclic Service | Configuration, ‏Alarm, זיהוי או Diagnostics לפי דרישה. |
| PTP - Precision Time Protocol | פרוטוקול סנכרון שעונים לפי IEEE 1588 ו-IEC 61588. |
| Distributed Clocks | ארכיטקטורה שמיישרת Clocks מקומיים לדגימה או ביצוע מסונכרנים. |
| VLAN | מנגנון Tagging וסגמנטציה לוגית ב-Layer 2. |
| QoS / Priority | סיווג תעבורה וטיפול בתורים; אינו Reserved Bandwidth אוטומטי. |
| Multicast | Sender אחד מפיץ Frames לקבוצת Receivers. |
| MRP / DLR | מנגנוני Recovery ל-Ring הקשורים לטופולוגיות ו-Ecosystems מסוימים. |
| PRP / HSR | פרוטוקולי Seamless Redundancy עם נתיבים כפולים וסילוק Frames כפולים. |
| TSN | משפחת מנגנוני IEEE 802.1 לרשת Bridged רגישה לזמן. |
| OPC UA FX / UAFX | מפרטי Field eXchange שמרחיבים OPC UA לכיוון Field-Level Interactions. |
| Ethernet-APL | Physical Layer דו-גידי, Loop-Powered ומבוסס 10BASE-T1L לתעשיית התהליך. |
| Black Channel | עיקרון Safety Communication שבו אמצעי הבטיחות עצמאיים מהנחות על ערוץ ההעברה הרגיל. |

# 11. מפת תקנים ומקורות

מקורות רשמיים ראשוניים שעליהם מבוססת המפה הטכנית. שמות התקנים והקישורים מוצגים משמאל לימין לשמירת קריאות:

1. IEC 61158-1:2023 - Fieldbus specifications: overview and guidance. Official: https://webstore.iec.ch/en/publication/66931

2. IEC 61784-2-0:2023 - Real-time Ethernet profiles: general concepts and terminology. Official: https://webstore.iec.ch/en/publication/83463

3. IEC 61918:2018+A1:2022+A2:2024 - Installation of communication networks in industrial premises. Official: https://webstore.iec.ch/en/publication/93274

4. IEC 61784-5 series - Installation profiles for communication profile families; example CPF 3. Official: https://webstore.iec.ch/en/publication/31702

5. IEC 62439-2:2021 - Media Redundancy Protocol (MRP). Official: https://webstore.iec.ch/en/publication/62849

6. IEC 62439-3:2021 - Parallel Redundancy Protocol and High-availability Seamless Redundancy. Official: https://webstore.iec.ch/en/publication/64423

7. IEC 61588:2021 / IEEE 1588-2019 - Precision Time Protocol. Official: https://webstore.iec.ch/en/publication/68542

8. IEEE 802.1AS-2025 - Timing and synchronization for time-sensitive applications. Official: https://standards.ieee.org/ieee/802.1AS/11968/

9. ISO/IEC/IEEE 8802-1Q:2024 / IEEE 802.1Q family - Bridges, VLANs and TSN mechanisms. Official: https://standards.ieee.org/ieee/8802-1Q/11825/

10. IEEE/IEC 60802-2026 - TSN profile for industrial automation. Official: https://standards.ieee.org/ieee/60802/11358/

11. IEC 62541-1:2025 - OPC UA concepts and overview. Official: https://webstore.iec.ch/en/publication/81513

12. IEC 62541-14:2026 - OPC UA PubSub. Official: https://webstore.iec.ch/en/publication/82257

13. IEC 61784-3:2021+A1:2024 - Functional-safety fieldbuses and black-channel principles. Official: https://webstore.iec.ch/en/publication/62095

14. PI - PROFINET technology description and RT/IRT channels. Official: https://www.profinet.com/profinet-explained/technology-description

15. ODVA - EtherNet/IP, CIP Sync and CIP Motion. Official: https://www.odva.org/technology-standards/key-technologies/ethernet-ip/

16. EtherCAT Technology Group - Functional principle and distributed clocks. Official: https://www.ethercat.org/en/technology.html

17. Modbus Organization - Modbus application, TCP/IP and security specifications. Official: https://www.modbus.org/modbus-specifications

18. OPC Foundation - OPC UA Field eXchange specification series. Official: https://profiles.opcfoundation.org/document/25

19. Ethernet-APL - two-wire, loop-powered 10BASE-T1L physical layer for process automation. Official: https://www.ethernet-apl.org/

> הערת שימוש \| בכל פרויקט יש לבדוק את מהדורת התקן המדויקת, האימוץ הלאומי, גרסת מפרט הפרוטוקול, Conformance Class, ‏Device Certification, גרסת היצרן והדרישה החוזית. תקנים ודפי ארגונים מגדירים מסגרת; עדיין נדרש לתכנן, להגדיר, לאמת ולתחזק את המערכת הממומשת.

# 12. שער איכות לפרק

- המאזין יכול לשרטט ארכיטקטורת תקשורת Layered ו-End-to-End.

- Bandwidth, ‏Latency, ‏Jitter, ‏Synchronization, ‏Data Age ו-Recovery Time מובחנים בבירור.

- Fieldbus ו-Industrial Ethernet מושווים לפי דרישות וארכיטקטורה ולא לפי פופולריות.

- Topology, ‏Switching, ‏Multicast, ‏Media ו-Installation מוצגים כהחלטות תכן בקרה.

- Time Synchronization מוצג כ-Controlled Resource עם Health ו-Failure Limits.

- Redundancy מוגדרת באמצעות Faults נסבלים ו-Recovery Behavior ולא רק ציור Ring.

- TSN מוצג כארגז כלי IEEE ו-IEC/IEEE 60802 כ-Industrial Profile.

- האבחון בסיום פותר גם את תסמין ה-Congestion וגם את Clock Offset.

- הסיום יוצר גשר נקי לשפות PLC ול-Software Architecture שניתן לתחזוקה.
