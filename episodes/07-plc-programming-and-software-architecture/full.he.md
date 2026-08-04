---
episode: 7
language: he
title: "שפות תכנות PLC וארכיטקטורת תוכנה"
target_duration: "42-46 minutes"
status: completed
extracted_from: pdf-text-extraction
---

שפות תכנותPLC וארכיטקטורת תוכנה
-מLadder
- וStructured Text ועד מכונות מצבים, מודולים לשימוש חוזר וקוד בקרה שניתן לבדיקה
IEC 61131-3 | LD | ST | FBD | SFC
| | בעלותState | Libraries | Testing | Git
קהל יעד
מהנדסי מכונות, תהליך, ייצור, מכשור ואוטומציה
משך יעד42-46 דקות
פורמט מהנדס תהליך- מהנדסת מכונות צעירה; אמיר- יעל
ובקרה ותיק
דוגמת ליבה מערכתCIP
מפעילה משאבה מול נתיב סגור לאחר
חזרת מתח עקבState ובעלות פקודה עמומים
תוצר הנחיית+ תסריט מלאNotebookLM
מטריצת שפות+
+ מפת ארכיטקטורה+
Checklist מקורות+
חומר לימודי. אינו מחליף מפרט פונקציונלי, הערכת סיכונים, מחזור חיי תוכנה מאומת, תיעוד יצרן, בקרות
Cybersecurity
. או מהדורות תקן מחייבות
# 1. בדיקת התאמה לפני הפקה
- הפרק ממשיך ישירות מפרק6
.: רשת דטרמיניסטית יכולה להעביר פקודה שתוכננה גרוע בדיוק בזמן
- שפות- הפרק מאחד את נושאי תוכנית האבPLC
; לכדי יסוד ארכיטקטוני אחד- , ניהול קוד ואיכות תוכנה
-פרקים מאוחרים יישמו אותו בHMI
,, נתוניםSafety
- וCybersecurity
.
- ,קהל היעד נשאר מהנדסי מכונות ותהליך. תחביר מוסבר רק כאשר הוא חושף התנהגות פיזיקליתTiming
,
.בעלות או יכולת תחזוקה
- אין דירוג של שפה אחת כטובה תמיד. הקריטריון הוא עד כמה הייצוג מבטא ומאפשר אימות של הכוונה
.ההנדסית
- הסיום יוצר גשר ישיר לפרק8
על היררכייתHMI
, פקודות מפעיל והצגתAlarms
.
| בדיקת עדכניות מפת התקינה נבדקה מול חומר רשמי ועדכני שלIEC
,
PLCopen
,
ISA/OMAC
,
CODESYS
,
Siemens
- וRockwell Automation
. היא משקפתIEC 61131-3:2025
מהדורה4
,
IEC TR 61131-8:2017
,
IEC
61131-10:2019
והנחיותSoftware Construction
שלPLCopen
, כוללGuideline
- למדדי איכות מ2023
. תכונות
.כלים ופורמטים תלויות יצרן וגרסה; יש לבדוק את פלטפורמת הפרויקט ואת המהדורות שאומצו
# 2. מטרות הפרק
- -להפוך דרישות פונקציונליות לModes
,
States
,
Commands
,
Permissives
,
Interlocks
,
Trips
,
Invariants וכללי
Restart
. מפורשים
- להסביר את חבילת השפות הנוכחית שלIEC 61131-3
ואת תפקידיProgram
,
Function Block
- וFunction
.
- לבחורLadder Diagram
,
Structured Text
,
Function Block Diagram
- וSFC
אוState Machine
לפי המטרה
.ההנדסית
- לתכנן אפליקציית בקרה שכבתית עם בעלים אחד לכלOutput
- פיזי וModule Interfaces
בעליTypes
.
- להפרידConfiguration
,
Recipe Data
,
Live State
, ראיותRetentive
והחלטותRestart
.
- -להשתמש בספריות ובOOP
- בלי להסתיר התנהגות או לפגוע בOnline Diagnostics
.

- לבנותLifecycle
מעשי עםVersion Control
,
Reviews
,
Static Analysis
,
Simulation
,
Tests
, ראיותRelease
-וRestore
. שנבדק
# 3. חלוקת זמן ומקטעים
זמן
מקטע
מטרה
00:00-03:30פתיחה
State
שמור מפעיל משאבה לפני
.שהוכח נתיב השסתומים
03:30-07:30דרישות לפני קוד ,הגדרת התנהגותInvariants
,
Restart
.ומילון הגנות
07:30-12:30
מפתIEC 61131-3
,שפותPOUs
, פורמטיExchange
ומגבלותPortability
.
12:30-17:30
Ladder Diagram
החלטותBoolean
שקופות ומלכודות
.בעלות נפוצות
17:30-22:30
Structured Text
Algorithms
,, נתוניםBounded Execution
-וState
. מפורש
22:30-26:30
Function Block Diagram
,זרימת אותBasic Control
ומשמעת
.סדר ביצוע
26:30-31:30
SFC ומכונות מצבים
Steps
,
Transitions
,
Abnormal Exits
ומושגיPackML
.
31:30-36:30ארכיטקטורה שכבתית גבולותI/O
,
Device
,
Equipment
,
Sequence
- וSupervisory
.
36:30-40:30נתונים ושימוש חוזר
Typed Models
, גרסאותLibrary
,
Interfaces
- וOOP
. מרוסנת
40:30-44:00
Quality Workflow
Version Control
,
Static Analysis
,
Simulation
. והיררכיית בדיקות
44:00-46:00פתרון וסיום-בניית בעלות וRecovery
מחדש וגשר
-לHMI
.
# 4. ארכיטקטורת תוכנת בקרה שניתן לתחזק
שכבה
אחריותContract / ראיות
.
I/O Abstraction
מיפויChannels
,
Scaling
,
Inversion
,
Signal Quality
,
Forcing
וגבולSimulation
.
,יחידות הנדסיותQuality Status
,
Channel Diagnostics
. והחלפה מבוקרת
.
Device Module
,משאבה, שסתוםHeater
,
Drive או
Instrument
אחד; בעלת הפקודה
.הפיזית
Command/Status
עםTypes
,
Permissives
,
Interlocks
,
Feedback
,
Fault
Reason
- וTiming
.

שכבה
אחריותContract / ראיות
.
Equipment Module
תיאוםDevices
ליכולת כמוCirculation
,
Dosing
,
Heating
,
Positioning
אוTransfer
.
Capability Request
,
Readiness
,
Completion
,
Hold
,
Abort
- וFault Behavior
.
.
Sequence / Phase
ביצועRecipe
אוMachine Cycle
באמצעותStates
- וTransitions
.מפורשים
Entry Criteria
,
Invariants
,
Completion
Criteria
,
Timeout
- וAbnormal Exits
.
.
Supervisory Boundary
Modes
,
Production Orders
,
Handshakes
,
אישורRecipe
וסיכומיHMI
.
Authority
,
Audit Trail
, אישור פקודה
-וSituational Status
. קומפקטי
Lifecycle רוחבי ,דרישותNaming
,, ספריותVersion
Control
,, בדיקותRelease
- וRestore
.
Traceability
- מChange Request אל
Source
,
Binary
,
Target
,
Test Report
-וBackup
.
# 5. מטריצת החלטה לשפה ולמבנה
שפה / מבנה
התאמה חזקה שאלותReview
Ladder Diagram - LD
Boolean Decisions
,
Permissives
,
Interlocks
,
Mode Selection ובקרת
Device
. פשוטה
האם ישWriter
אחד? האםLatches
,
Priority
,
Reset
ותלויותScan
?מפורשים
Structured Text - ST
,חישוביםArrays
,
Recipe Validation
,
Algorithms
-, לולאות תחומות וState
Machines
.
האםTypes
,, יחידותExecution Bounds
,
Array Limits
- וSide Effects
? נשלטים
Function Block Diagram - FBD
Signal Flow
,
PID
,
Filtering
,
Scaling
,
Voting
- וAnalog Basic Control
.
האם כל עמוד מספר סיפור אות
-אחד? האם סדר הביצוע וBlock
Contract
? ברורים
SFC / State Machine מפורשת
Sequential Behavior
,
Phases
, מעברים
,חוקייםHold
,
Abort
- וRecovery
.
האםStates
, משמעותייםTransitions
-דטרמיניסטיים וAbnormal Exits
?שלמים
Function
חישוב ללאState
עםInputs
ותוצאה
.מוגדרים
האם היא דטרמיניסטית וחופשית
-מPersistent State
אוOutput Side Effects
?סמויים
Function Block
התנהגות חוזרת עםInstance Memory
,
כמוValve
,
Motor
אוController
.
,האם הבעלות ברורהInternal State
-עטוף והInterface
? קטן וניתן לבדיקה
Program / Orchestration
תיאוםModules של האפליקציה תחת
Task
. מתוזמן
האם הוא מתאםRequests
במקום
לעקוףDevice Ownership
?
| עיקרון מרכזי-בוחרים את הייצוג שהופך את ההתנהגות הפיזיקלית, הState
-, הבעלות, הTiming והתגובה לכשל
.לקלים ביותר לסקירה ולבדיקה. תחביר מוכר אינו מציל ארכיטקטורה עמומה

-. הנחיית הפקה לNotebookLM
| הנחיה מוכנה להדבקה צור פרק פודקאסט הנדסי בעברית בלבד באורך42-46
דקות, תוך שימוש אך ורק
בחבילת המקורות ובמסמך זה. השתמש בשני מגישים: יעל, מהנדסת מכונות צעירה ששואלת שאלות ישירות על
,תכןCommissioning
ותחזוקה; ואמיר, מהנדס תהליך ובקרה ותיק שמסבירSoftware Architecture
באמצעות
-ההשלכות הפיזיקליות. תן ליעל כ45%
- מזמן הדיבור ולאמיר כ55%
. השיחה צריכה להישמע כמוDesign
Review
. לאחר אירוע, לא כמו הרצאה או הקראת טבלאות
השתמש באירוע התאוששות המתח במערכתCIP
כסיפור רציף. אל תחשוף את כל הארכיטקטורה המתוקנת
עד הסיום. הסבר ראשי תיבות בפעם הראשונה. הבדל בין דרישותIEC
, הנחיותPLCopen
, מושגיState Model
שלISA/OMAC
- ודוגמאות לכלי יצרן. אמור במפורש שIEC 61131-3
אינו מבטיחPortability
שלSource Code
בין יצרנים. אל תקרא בקול קטעי קוד ארוכים, כתובותURL
. או מספרי סעיפים
,כסה דרישות פונקציונליותInvariants
,
Restart Behavior
,
Programs
,
Functions
,
Function Blocks
,
LD
,
ST
,
FBD
,
SFC
- וState Machines
מפורשות. הסברSingle-Writer Ownership
, ארכיטקטורתI/O
,
Device
,
Equipment
,
Sequence
- וSupervisory
,
Typed Command-Status Interfaces
,
Recipe Validation
,
Retained
Data
-, ספריות לשימוש חוזר וOOP
מרוסנת. כלולVersion Control
,
Code Review
,
Static Analysis
,
Simulation
,
Unit
,
Module
,
Sequence
- וIntegration Tests
, ראיותRelease
ובדיקתRestore
" . אתגר מיתוסים כגוןLadder
" ,"תמיד בטוחה יותרStructured Text
" ," היא תוכנת מחשב רגילהRetentive
פירושוResume
"-" וBackup הוא
Version Control
". סיים בארכיטקטורת המערכת המתוקנת, שישה כללים זכירים וגשר לפרק8
עלHMI
- וAlarm
Design
.
# 7. תסריט מלא לפרק
00:00-03:30 המשאבה שזכרה את הדבר הלא נכון- | פתיחה
:אמיר מערכתCIP
, ניקוי במקום, שודרגה ממוצר אחד לשלושה מתכונים. שינוי התוכנה נראה קטן: זמני פעולה
חדשים, בחירת שסתומים שונה ורצף שטיפה נוסף. בבדיקת ההתאוששות הראשונה לאחר נפילת מתח, משאבת
-הסחרור מתחילה לפעול לפחות משנייה בזמן ששסתום היציאה עדיין סגור. הDrive
נופל על לחץ, האטם המכני
שורד, והצוות מכנה את האירוע תקלה רגעית שלCommissioning
.
:יעל? פחות משנייה היא עדיין אירוע פיזיקלי אמיתי. מה התוכנית עשתה
:אמיר שלוש שגרות שונות יכלו לכתוב את פקודת המשאבה. מספר שלב הרצף היהRetentive
. רשתLadder
אחת
פירשה את השלב השמור כפקודת סחרור, שגרה אחרת עדיין בנתה מחדש את מצב השסתומים, ומנהל המתכונים
.טרם אישר שהמידע שנטען תקף. כל רשת נראתה הגיונית כשבדקו אותה לבדה
:יעל. כלומר זו לא הייתה שגיאת תחביר. זו הייתה שגיאת ארכיטקטורה
:אמיר בדיוק. הבקר ביצע הוראות חוקיות בתוך מודל בעלות גרוע. הרשת מפרק6
העבירה כלBit בזמן. לתוכנה לא
-הייתה תשובה אחת ומפורשת לארבע שאלות: מי בעל הבית של הOutput
, באיזה מצב נמצא הציוד, אילו נתונים
תקפים לאחרRestart
., ואילו תנאים חייבים להישאר נכונים לפני שמשחררים אנרגיה
:יעל היום לא נשאל איזו שפה היא הטובה ביותר באופן כללי. נשאל כיצדLadder
,
Structured Text
,
Function Block
Diagram
- וSequential Function Chart
משתלבים לקוד שמהנדס אחר יוכל להבין, לבדוק ולשנות בבטחה בעוד
.חמש שנים
:אמיר. ובסיום נחזור למערכת עם תכן שבו קשה לבטא את הפקודה הלא נכונה, ולא רק קל להסביר אותה בתגובה
03:30-07:30
| דרישות לפניRungs
:יעל- פרויקטי אוטומציה מתחילים לעיתים מI/O List
ומתכנת שפותח את סביבת הפיתוח. מה חייב להתקיים לפני
?כתיבת קוד

:אמיר , מודל התנהגות. צריך להגדיר מצבי הפעלה, מצבי ציוד, פקודותPermissives
,
Interlocks
,
Trips, כללי
Reset
, התנהגות לאחרRestart
, פונקציותManual
והגבול מול מערכותSafety. ביחידת תהליך מוסיפים את הרצף
הרצוי, נקודותHold
, מעברים חריגים ובעלות עלRecipe
. במכונה מוסיפיםCycle States
, מסלוליRecovery
ומה
מותר למפעיל לבקש בכלMode
.
:יעל זה נשמע כמוFunctional Design
, לאSoftware Design
.
:אמיר אי אפשר להפריד ביניהם. תוכנה אינה יכולה לפצות על תגובת תהליך שלא הוגדרה. קחי את המשפט
'הפעל את המשאבה כאשר היא מוכנה'. המילהReady
, חייבת להפוך לביטוי מפורש: נתיב שסתומים נכון מוכח
מפלס מינימלי, איןTrip
- פעיל, הDrive
- זמין, הMode
מאפשר התנעה אוטומטית, המתכון עברValidation, אין
Maintenance Lockout
וכל פונקצייתSafety
, נדרשת תקינה. לכל תנאי צריכים להיות מקורQuality
. ותגובה לכשל
:יעל כדאי להבדיל ביןPermissive
,
Interlock
- וTrip
?
:אמיר . כן, גם אם לכל חברה מילון מעט שונהPermissive
. מאפשר התחלהInterlock
מונע או מסיר פקודה כאשר
.תנאי נדרש חסרTrip
הוא בדרך כלל תגובת הגנה נעולה עם תנאיReset
מוגדרים. המילון חייב להיות מתועד, כי
הודעותHMI
, טבלאותCause and Effect
. ונהלי תחזוקה תלויים בו
:יעל מהוInvariant
? בהקשר הזה
:אמיר , תנאי שחייב להישאר נכון כל עוד מצב או פעולה פעילים. עבור סחרורInvariant
יכול להיות: אם פקודת
.המשאבה פעילה, נתיב זרימה פתוח חייב להיות מוכח, או שטיימר מעבר תחום בזמן עדיין פעילInvariants
מכווניםCode Review
. ובדיקות, מפני שהם הופכים כוונה מעורפלת למשפט שאפשר לאתגר
:יעל וגםRestart
הוא דרישה, לא ברירת מחדל שלMemory
.
:אמיר- בדיוק. מחליטים אם המכונה חוזרת לStopped, שומרת מצב, ממשיכה שלב שעבר אימות, או דורשת
Recovery
. של מפעילRetentive Memory
. אינה אסטרטגיית המשך. היא רק מנגנון אחסון
07:30-12:30
|
IEC 61131-3
בשנת2025 שפה משותפת, לא כלים זהים-
:יעל נבסס קודם את מפת התקינה. מה מגדירה בפועל המהדורה הנוכחית שלIEC 61131-3
?
:אמיר- המהדורה הרביעית, שפורסמה ב2025, מגדירה תחביר וסמנטיקה של חבילת שפות אחידה הכוללת
Structured Text
,
Ladder Diagram
- וFunction Block Diagram
. היא מגדירה גם רכיביSequential Function Chart
לארגון פנימי שלPrograms
- וFunction Blocks
, וכן רכיביConfiguration
.
Instruction List
, שמוכרת למהנדסים
.ממערכות ותיקות, אינה חלק מחבילת השפות הנוכחית
:יעל תאימות לתקן אומרת שאפשר להעביר כל פרויקט מיצרן אחד לאחר ולבצעCompile
?
:אמיר,הקבוצות הנתמכות, ספריות- לא. התקן משפר שפה משותפת ומושגים משותפים, אך הכלים נבדלים בתתי
Data Types
, מודלTasks
,
Hardware Configuration
,
Motion
,
Safety
,
Visualization
,
Diagnostics
. והרחבות יצרן
גם כאשר התחביר מיובא בהצלחה, ההתנהגות והראיות לאורך מחזור החיים עדיין דורשותVerification
.
:יעל? מהם אבני הבניין המשותפות מעבר לשפה הגרפית או הטקסטואלית
:אמיר
Data Types
,
Variables
,
Configurations
,
Resources
,
Tasks
- וProgram Organization Units
-. הPOUs
כולליםPrograms
,
Function Blocks
- וFunctions. Function
אמורה להתנהג כחישוב ללאState מתמשך של
Instance
.
Function Block
מחזיק זיכרוןInstance
. ומתאים לשסתום, מנוע, בקר או התנהגות חוזרת עם מצב
Program
- מתאם את התנהגות האפליקציה ומתוזמן על ידי הRuntime
.
:יעל ומה תפקידIEC TR 61131-8
?
:אמיר . הוא נותן הנחיות יישום ומימוש לשפותIEC 61131-10
מגדיר פורמטXML
לחילופי פרויקטים לפיIEC
61131-3
-. זה מסייע להעברה בין כלים ולVersion Control, אך אינו מוחק סמנטיקה ייחודית ליצרן ואינו מבטיח
Migration
. בלחיצה אחת
:יעל המהדורה של2025
גם מזכירה מחרוזותUTF-8
.

:אמיר נכון, וזה מזכיר לנו שתוכנת בקרה מטפלת כיום במידע עשיר יותר. אבל תכונות שפה עשירות אינן סיבה
להכניס כל פונקצייתIT
לתוךTask בזמן אמת. הארכיטקטורה עדיין מפרידה בין בקרה דטרמיניסטית לבין
Reporting
,
Analytics
. ושירותים שאינם קריטיים
:יעל. כלומר לתקנן את המודל המחשבתי, ולאמת את המימוש
:אמיר. בדיוק. התקן הוא דקדוק הנדסי משותף, לא תחליף לתיעוד הפלטפורמה ולבדיקות מערכת
12:30-17:30
|
Ladder Diagram זרימת כוח גלויה ומלכודות נסתרות-
:יעל
Ladder
? עדיין מועדפת אצל חשמלאים ואנשי אחזקה רבים. במה היא באמת טובה
:אמיר : בלוגיקה בוליאנית הדומה למעגלי ממסריםStart-Stop
, שרשראותPermissive
,
Interlocks
, בחירתMode
,
Alarms
ובקרתDevice
פשוטה. המסלול החזותי יכול להראות במהירות איזה תנאי פתוח בזמןOnline Monitoring
.
.זה עובד כאשר הארכיטקטורה ממושמעת
:יעל. המשפט 'כאשר הארכיטקטורה ממושמעת' נשמע חשוב
:אמיר . מאודLadder
נעשית קשה כאשר אותוCoil
נכתב בכמה מקומות, כאשרLatches משמשים בלי בעלות
Reset
מפורשת, כאשרBranches
ארוכים מסתיריםPriority
, או כאשרState
שלSequence
מיוצג בעשרותBits
.שאינם קשורים. המסך נראה מוכר, אבל לתוכנית אין מודל התנהגות ברור
:יעל- תסביר את בעיית הMultiple Writers
. באמצעות המשאבה שלנו
:אמיר- נניח שManual
,
Automatic Sequence
- וRecovery
מכילים כל אחדRung
שכותבPumpCmd
. הערך הסופי
עלול להיות תלוי בסדרScan
או בכללי הפלטפורמה. שינוי בשגרה אחת יכול לדרוס אחרת בלי התרעה. תכן טוב
יותר מאפשר לכל שכבה לשלוחRequest למודול משאבה אחד. רק המודול הזה כותב את הפקודה הפיזית ומכריע
Mode
,
Permissive
,
Interlock
- וFeedback
.
:יעל ומה לגביSet
- וReset Coils
?
:אמיר הם אינם אסורים, אבל לכלState
נעול חייבים להיות בעלים מוגדרים, מסלולReset
, כללInitialization
ומשמעותDiagnostic
.
Bit
שנשאר נעול מעבר לדרישה שלו הופך לזיכרון נסתר. התוכנה צריכה לחשוףState
או
-מקור פקודה, לא לכפות חיפוש אחר הRung
האחרון שהדליקCoil
.
:יעל גםOnline Monitoring
. עלול לתת ביטחון מזויף
:אמיר . כןRung
מודגש מציג את ההערכה הנוכחית, לא את ההיסטוריה שיצרהBit
- שמור או את הTiming בין
Tasks
-. הוא גם יכול להסתיר תקלה פיזית בOutput
. צריך להבדיל ביןRequested Command
,
Controller Output
,
Field Power
, מצבActuator
. וההשפעה על התהליך
:יעל
Ladder
חזקה בהחלטות שקופות, לא בשמירת כל ההיסטוריה של המתקן בתוךContacts
.
:אמיר ניסוח מצוין. שומריםRungs
קצרים מספיק להסבר, קוראים לתנאים לפי משמעות הנדסית, והופכים בעלות
עלOutputs
. לברורה
17:30-22:30
|
Structured Text כוח ביטוי עם אחריות בזמן אמת-
:יעל
Structured Text
נראית מוכרת למהנדסים שיודעיםPascal
,
C
אוPython
?. איפה היא מרוויחה את מקומה
:אמיר , חישוביםArrays
,
Loops
,, המרות נתוניםValidation
שלRecipes
,, טיפול במחרוזותAlgorithms
,
State
Machines
. וספריות לשימוש חוזר. היא מבטאת טרנספורמציות מורכבות באופן קומפקטי יותר מרשת גרפית
חישוב פיצוי לחץ עם עשרה ערכי ביניים עשוי להיות ברור יותר כביטויים עםTypes
מאשר כקיר שלBlocks
.
:יעל? מהן הטעויות השכיחות
:אמיר קוד צפוף שרק המחבר מבין, המרותType
משתמעות, שינוייState
סמויים בתוךFunctions
, לולאות על
מידע שגודלו משתנה בלי לחשבWorst-Case Execution Time
-, גישה לArray
בליRange Protection
, ערבוב
-יחידות הנדסיות והנחות מעולם הDesktop
לגביExceptions
.
:יעל- תן דוגמה לBounded Execution
.

:אמיר- אם לPeriodic Task
יש תקציב של עשר מילישניות, לולאה שמעבדת את כל פריטי המתכון חייבת להיות
בעלתMaximum
- ידוע. חיפוש תמים בעשרים רשומות עלול לחרוג כאשר הקונפיגורציה גדלה לאלפיים. בReal-
Time Review
לא שואלים רק אם התוצאה נכונה, אלא מהו מסלול הביצוע הארוך ביותר ומה קורה כאשר הקלט
.פגום
:יעל? כיצד יחידות צריכות להופיע בקוד
:אמיר מעדיפיםStructures
עםTypes
. חזקים, שמות בעלי משמעות והמרות מפורשותTemperature_C
,
Pressure_bar_g
- וDuration_ms
- אומרים יותר מValue1
-, גם אם הפלטפורמה אינה תומכת בUnit Types
אמיתיים. מרכזיםScaling
- בגבול הI/O
כדי שהלוגיקה הפנימית תפעל ביחידות הנדסיות. לא מפזריםRaw Counts
-וMagic Constants
.
:יעל האםCASE
הוא דרך טובה לבנותState Machine
?
:אמיר הוא יכול להיות מצוין כאשרStates
הםEnumeration
,, המעברים מפורשיםEntry Actions
, נשלטותStates
-לא חוקיים מטופלים והOutputs
נגזרים בעקביות. הוא נעשה גרוע כאשר כלState
כותב ישירות לעשרותDevices
-ותנאי מעבר משוכפלים. הState Machine
צריכה לתאםModules
., לא לעקוף אותם
:יעל ומה עםComments
?
:אמיר
תגובות צריכות להסביר למה, אילוצים והנחות. הקוד צריך לחשוף מה. תגובה שאומרת 'הפעל משאבה מעל
M120
' אינה מוסיפה דבר. תגובה שמסבירה שהשהיית הוכחת השסתום של שלוש שניות מבוססת על מעטפת
תנועה מכנית שעברהValidation
. היא שימושית וצריכה להפנות לדרישה המבוקרת
22:30-26:30
|
Function Block Diagram זרימת אות וסדר ביצוע-
:יעל
Function Block Diagram
? נפוצה בבקרת תהליך. מה הופך אותה למתאימה
:אמיר . היא מייצגת זרימת אות וקשרים בין פונקציותPID
,
Filtering
,
Scaling
,
Voting
, עיבודAnalog ולוגיקת
Control Valve
- יכולים להיות קלים לסקירה כBlocks
- מחוברים. מהנדסת מכונות יכולה לעקוב מהProcess
Variable
, דרךValidation
- והבקר, עד הFinal Element
.
:יעל? האם השרטוט מבטיח סדר ביצוע משמאל לימין
:אמיר לא מניחים זאת לפי המראה בלבד. הפלטפורמות מגדירותNetwork Order
,
Block Execution
וטיפול
-בFeedback
.
Cyclic Dependencies
דורשות זהירות. המהנדס חייב להבין אתExecution Model של הכלי ולהפוך
Dependencies
. למפורשים כאשר הסדר חשוב
:יעל מה הופךFBD
? ללא קריאה
:אמיר
Sheets
, עצומים, קווים מצטלביםGlobal Variables
סמויים, ערבוב רמותAbstraction
- וBlocks
בעליSide
Effects
לא ברורים. עמוד שמכילScaling
, של חיישןMode Logic
, כוונוןPID
,
Alarm Latching
ובעלות עלValve
Output
אינוControl Diagram
.; זו קריסת ארכיטקטורה
:יעל כלומר כלNetwork
. צריכה לספר סיפור אחד
:אמיר כן. משאירים את מסלול האות גלוי, עוטפים התנהגות חוזרת בתוךFunction Blocks
, חושפיםStatus
-וQuality
ומפרידיםBasic Control
מתיאוםSequence
.
FBD
חזקה כאשר לכלBlock
ישContract
. ברור
:יעל היית מממש כלPID
- בBlock
? מותאם אישית
:אמיר בדרך כלל לא. משתמשים בספריות מוכחות של הפלטפורמה או החברה, אך עוטפים אותן בעת הצורך כדי
לתקנןUnits
,
Modes
,
Tracking
,
Output Limits
,
Bumpless Transfer
,
Alarms
- וDiagnostics
. שימוש חוזר צריך
.להפחית שונות, לא להסתיר התנהגות קריטית
26:30-31:30
|
SFC להפוך את מצב הרצף למפורש- ומכונות מצבים
:יעל
Sequential Function Chart
? נקראת לפעמים שפת תכנות ולפעמים לא. מה מדויק

:אמיר- בIEC 61131-3:2025
,
SFC
היא קבוצת רכיבים לארגון פנימי שלPrograms
- וFunction Blocks
.
Steps
מחזיקיםState
,
Transitions
- מגדירים מתי עוברים, וActions
. משתמשות ברכיבים של השפות האחרותPLCopen
-מדגישה שSFC
- מתאימה במיוחד לתהליכים רציפים ולState Machine Behavior
.
:יעל- מה מרוויחים מState
? מפורש
:אמיר
Observability
ומעברים נשלטים. במקום לנחש איזה שילובBits
משמעותוRinsing, התוכנית מצהירה
Rinsing
:. מהמצב הזה רק מעברים מוגדרים חוקייםComplete
,
Hold
,
Abort
אוFault. אפשר לסקור, להציג ולבדוק
Entry
- וExit Behavior
.
:יעל עד כמהStates
? צריכים להיות מפורטים
:אמיר מספיק כדי לייצג התנהגות ציוד משמעותית, לא כל פעולה שלScan
. לכלState
, צריכים להיות מטרהEntry
Criteria
,
Invariants
, פעיליםCompletion Criteria
,
Timeout
- וAbnormal Exits
. אםState
קיים רק כדי להמתיןScan
.אחד, כנראה שהוא מתאר פרט מימוש ולא התנהגות תהליך
:יעל ומה לגביParallel Branches
?
:אמיר הן יכולות לייצג פעולות מקבילות, אךSynchronization
חייב להיות מפורש. אם שניBranches שולטים בציוד
משותף, בעלות וכלליCompletion
. חייבים להיות ברוריםParallelism
שנראה אלגנטי עלול ליצורRace
כאשר ענף
.אחד נכשל והשני ממשיך
:יעל
PackML
מוזכרת לעיתים יחד עםState Models
.
:אמיר
OMAC PackML
- וISA TR88
למכונות מציעות מושגים משותפים כמוStopped
,
Starting
,
Execute
,
Holding
,
Held
,
Aborting
- וAborted. הן יכולות לשפר אחידות בין מכונות, אך צריך למפות אותן לתהליך האמיתי ולא להדביק
.אותן כשכבה דקורטיבית מעל לוגיקה שאינה קשורה
:יעל , במערכת שלנוRecipe Steps
- וUnit Mode
יהיו אותהState Machine
?
:אמיר . בדרך כלל מפרידיםUnit Mode
כמוOff
,
Manual
,
Automatic
אוMaintenance
. קובע הרשאותSequence
State
. מתאר את מיקום המתכוןDevice Modules
שומריםStates
. משלהםState Machines שכבתיות מונעות
Chart
. ענק ששולט בכל פרט
## 31:30-36:30 | ארכיטקטורת אוטומציה שניתן לתחזק
:יעל- נבנה את השכבות מהTerminals
. כלפי מעלה
:אמיר , ראשיתI/O Abstraction
. ממפיםRaw Channels
,
Scaling
,
Inversion
,
Quality
- וSimulation
. בגבול אחד
,שניתDevice Modules
, למשאבות, שסתומיםHeaters
,
Drives
ומכשור. כלModule
, מחזיק פקודותPermissives
,
Interlocks
,
Feedback
,
Faults
- וDiagnostics
עבורDevice
אחד אוAssembly
. מוגדרת היטב
:יעל השכבה השלישית היאEquipment Modules
?
:אמיר . כןEquipment Module
מתאםDevices
כדי לספקCapability
,: נתיב סחרורDosing
,
Heating
,
Positioning
אוTransfer
-. הוא מבקש פעולות מהDevices
וחושףStatus
, קומפקטי. מעליוSequence
אוPhase Logic מתאמת
Capabilities
כדי לבצעRecipe
אוMachine Cycle
. שכבתSupervisory
מנהלתModes
,
Production Orders
,
Handshakes
וסיכומים עבורHMI
.
:יעל איפה נמצאPID Loop
?
:אמיר בדרך כלל בשכבתEquipment
אוBasic Control
-, קרוב לProcess Variable
- ולFinal Element
-. הSequence
מבקשתSetpoint
- וMode
-; היא לא מממשת מחדש את הבקר. כך הLoop
- יכול להישאר בManual
אוTracking
במעבריSequence
בלי לפזר לוגיקה ביןSteps
.
:יעל. אתה חוזר שוב ושוב לבעלות
:אמיר . מפני שבעלות מונעת פקודות סותרותModule
אחד כותב כלOutput פיזי. שכבות גבוהות שולחות
Requests
דרךInterfaces
. מוגדריםPump Module
יכולה לקבלAutoRequest
,
ManualRequest
- וStopRequest
,
אך היא מכריעה ביניהם לפיPriority
מתועד וחושפתCommandSource
,
Ready
,
Running
,
Faulted
-וNotPermittedReason
.

:יעל- זה גם משפר את הHMI
. שנבנה בהמשך
:אמיר בדיוק. הממשק יכול להציג למהStart
חסום בלי להרכיב מחדש לוגיקה מעשרותTags
. זה גם תומך
-בSimulation
-: מחליפים את גבול הI/O
במודל ושומרים אתInterfaces
- של הModules
.
:יעל מה צריך לעבור ביןModules
?
:אמיר
Commands
,
Status
,
Configuration
- וEvents
עםTypes
- מפורשים. נמנעים מגישה חופשית לInternal
Variables
.
Module Contract
- מגדיר מה הCaller
- רשאי לבקש, מה פירוש הFeedback
, אילו הנחותTiming קיימות
וכיצד מבצעיםAcknowledge
- לFaults
.
36:30-40:30
- | מודלי נתונים, שימוש חוזר וOOP בלי תיאטרון ארכיטקטורה
:יעל? קוד לשימוש חוזר נשמע תמיד טוב. למה לפעמים הוא מקשה על פרויקטים
:אמיר מפני שקוד מועתק נקראLibrary
-, או מפני שBlock
גנרי חושף חמישיםParameters
כדי לכסות כל מכונה
.אפשריתReuse
- עובד כאשר ההתנהגות יציבה, הInterfaces
קטנים, התיעוד מבוקר, הגרסאות ניתנות למעקב
-והפרויקט הצורך יכול לבדוק את הLibrary Release
. המדויק
:יעל- נתחיל בData Types
.
:אמיר- משתמשים בEnumerations
עבורModes
- וStates
-, בStructures
עבורDevice Commands
- וStatus
,
-ובNamed Constants
עבורLimits. Recipe
צריכה להיותStructure
שעברהValidation
עםVersion
- וChecksum
או מנגנוןIntegrity
מתאים, לא אוסףTags
רופף. מפרידיםConfiguration
- מLive State
וערכים שהמפעיל הזין
.מערכים מאושרים שבהם הבקרה משתמשת
:יעל
Function Blocks
נותניםInstances
. מה מוסיףObject-Oriented Programming
?
:אמיר , לפי הפלטפורמהMethods
,
Interfaces
,
Inheritance
אוProperties
יכולים לשפרEncapsulation
-וPolymorphism
-. לPLCopen
- יש הנחיות לObject Orientation
בבקרה תעשייתית. אבלOOP
היא כלי, לא תג
.בגרותInheritance
- עמוקה, קשרים דינמיים וSide Effects
סמויים עלולים להקשות עלOnline Troubleshooting
.
:יעל מתיInterface
? שימושי
:אמיר כאשר מימושים שונים צריכים להציג אותוContract. שסתום מדומה ושסתום פיזי יכולים לממש אותו
Command-Status Interface
. משפחותDrive
שונות יכולות לחשוףAPI
משותף כלפיEquipment Layer, כאשר
Diagnostics
ייחודיים ליצרן נשארים בתוךAdapters
.. כך ניתן להחליף מימוש בלי להעמיד פנים שהחומרה זהה
:יעל כיצד מנהלים גרסאותLibrary
?
:אמיר
Semantic Versioning
יכולה לעזור, אך הכללים החשובים הםControlled Release
, רישוםDependencies
,
מדיניותBackward Compatibility
,
Migration Notes
- וRegression Tests
. פרויקט מכונה צריך לדעת בדיוק איזו
גרסתLibrary
- יצרה את הBinary
שהורד לבקר. אסור לעדכןGlobal Library
. בשקט בכל הפרויקטים שכבר הופעלו
:יעל. וגם להימנע מהכללה מוקדמת
:אמיר- נכון. קודם הופכים תכן אחד לנכון ולObservable
. מכלילים לאחר שמשוויםVariants
- אמיתיים. הBlock
.הטוב ביותר לשימוש חוזר מתקנן את החלקים המסוכנים והחזרתיים ומשאיר את לוגיקת התהליך הייחודית גלויה
40:30-44:00
|
Version Control
, ניתוח סטטי ובדיקות ששורדותCommissioning
:יעל- צוותי אוטומציה אומרים לעיתים שפרויקט הPLC
מגובה. האם זהVersion Control
?
:אמיר . לאBackup
. שומר קובץ בנקודת זמןVersion Control
, מתעד שינויים מכוונים, מחברReview
,
Release
Tags
וקשרים ביןBranches
. הוא צריך לאפשר לענות מה השתנה, למה, מי אישר, לאיזהController הגרסה הורדה
-וכיצד משחזרים את הBuild
. ששוחרר
:יעל קשה יותר לבצעDiff
. בשפות גרפיות

:אמיר לעיתים כן. משתמשים באינטגרציותSource Control
של היצרן, בפורמטים טקסטואליים אמינים, או
-בExport
מבוקר כמוPLCopen XML
. אבלMerge טקסטואלי מוצלח אינו הוכחה שהתנהגות הבקרה נכונה. צריך
Compile
,
Analysis
- וTest
. לפרויקט שנוצר בתוך סביבת ההנדסה היעד
:יעל מה תורםStatic Analysis
?
:אמיר הוא מוצאPatterns
לפניRuntime: Variables
שאינם בשימוש, המרותType
, משתמעות, קוד לא נגיש
הפרותNaming
,
Complexity
, גבוההAssignments
, חשודיםMultiple Writes
או הפרות כלליLibrary
., לפי הכלי
CODESYS
, לדוגמה, מספקת ניתוח לפיRules
- וMetrics
-. יכולות דומות קיימות בEcosystems
אחרים. צריך
להתאים אתRule Set
. ולסקור חריגות, לא לדכא אותן אוטומטית
:יעל? ואז בדיקות. מהי היררכיה שימושית
:אמיר
Unit Tests
- לFunctions
- ולFunction Blocks
;
Module Tests
עםSimulated I/O
;
Sequence Tests המכסות
Normal
,
Hold
,
Abort
- וRecovery
;
Integration Tests
עםDrives
, רשתות ומכשור אמיתיים; ולבסוףSite
Acceptance Tests
. תחת אילוצי התהליךSimulation
מצוינת לרוחב כיסוי, אך אינה משחזרת כלTiming
, פיזי
Wiring Fault
או התנהגותFirmware
.
:יעל. אירוע נפילת המתח שלנו צריך להפוך למשפחת בדיקות
:אמיר בדיוק. מסירים מתח או מדמיםRestart
בכלSequence State
משמעותי. משנים אםFeedback
של שסתום
,ישןRecipe
- אינו תקף, הDrive
אינו זמין או המפעיל מבקשManual
-. מאמתים שהOutputs
, נשארים בטוחים
-שהState
- הופך לRecoveryRequired
-, שהסיבה גלויה ושאי אפשר להמשיך עד שהRecovery Procedure
.שהוגדרה מצליחה
:יעל ומה כוללות ראיותRelease
?
:אמיר שומריםSource Revision
, גרסתTool
- וCompiler
,
Target Firmware
,
Libraries
,
Configuration
,
Test
Report
,
Change Request
, מאושרChecksum
אוSignature
כאשר קיימים, וחבילתRestore
. שעברה בדיקה
Backup
- שמעולם לא נוסה בRestore
. הוא רק תקווה המאוחסנת על שרת
:יעל ומה לגביOnline Edits
?
:אמיר- הן עשויות להיות נדרשות בCommissioning
, אך כל אחת היא שינוי מבוקר. מתעדים אותה, ממזגים אותה
-בחזרה לMaster Source
, מריצים מחדש את הבדיקות הרלוונטיות ויוצריםRelease
- חדש. אסור שהController
.יהיה המקום היחיד שבו נמצאת האמת
## 44:00-46:00 | הארכיטקטורה המתוקנת וסיום
:יעל? נחזור למערכת. מה השתנה
:אמיר- הOutput
הפיזי של המשאבה נכתב כעת רק על ידיPumpModule
.
Manual Control
-, הAutomatic
Sequence
ולוגיקתRecovery
שולחיםRequests
-; הם אינם יכולים לכתוב ישירות לOutput. המודול מכריע
Priority
-, מוכיח את נתיב השסתומים, מאמת מפלס וDrive Readiness
, מחילStop
- וTrip Conditions
וחושף סיבה
אחת כאשרStart
. חסום
:יעל? ומה קרה למספר השלב השמור
:אמיר הוא נשמר רק כראיית ייצור, לא כהוראה להמשיך. לאחר נפילת מתח לא מבוקרת, היחידה נכנסת
-לRecoveryRequired
-. הRecipe
נטענת מחדש ועוברתValidation
-, מצב הDevices
- נבנה מחדש מFeedback
,
והמפעיל מבצעRecovery Sequence
מפורשת. סחרור אוטומטי אינו יכול להתחדש עד שמצב הציוד ותנאי
.התהליך תואמו
:יעל הקוד גם חולק לשכבותI/O
,
Device
,
Equipment
,
Sequence
- וSupervisory
, עםEnumerated States
- וTyped
Interfaces
.
:אמיר והצוות הוסיףStatic-Analysis Rules
- לMultiple Writers
,
Unit Tests
- לPumpModule
,
Sequence
Simulations
לכלAbnormal Exit
ובדיקות חומרה להתאוששות מתח. התיקון אינו עודNormally Closed Contact. זו
-תוכנה שבה בעלות וState
. גלויים

:יעל. תן לנו את הכללים האחרונים
:אמיר בוחרים את השפה שמציגה את הכוונה ההנדסית בצורה הקלה ביותר לסקירה. נותנים לכלOutput
בעלים
אחד. ממדליםModes
- וSequence States
במפורש. מפרידים ביןRetained Data
לבין החלטתRestart. שומרים
Module Interfaces
קטנים ועםTypes
-. שולטים בספריות ובReleases
-. ובודקים תקלות וRecovery
, לא רק את
-הHappy Path
.
:יעל בפרק8
- נשתמש בInterfaces
האלה כדי לבנות את החלון של המפעיל למכונה: היררכייתHMI
,
High-
Performance Graphics
,, ניווט, פקודותAlarms
וההבדל בין מסך שנראה מרשים לבין מסך שתומך בהחלטה
.נכונה
:אמיר . תוכנת בקרה טובה יודעת מה המכונה עושהHMI
. טובה עוזרת לאדם להבין למה
# 8. הערות למפיק ולמגישים
- .לשמור את התוצאה הפיזיקלית של כל מושג תוכנה גלויה: לחץ, תנועה, חום, זרימה, אנרגיה ופעולת מפעיל
- לא להציגLD
מולST
- כוויכוח תרבותי. להראות היכן כל ייצוג משפר או פוגע בReviewability
.
- -להשתמש בעקביות בPermissive
,
Interlock
- וTrip
., תוך ציון שמילון חברות עשוי להשתנות
- לא לרמוז שתאימותIEC 61131-3
יוצרת התנהגות יצרן זהה אוPortability
. אוטומטית
- להסבירSingle-Writer Ownership
כמה פעמים דרךOutput
. המשאבה, בלי לחזור על אותו ניסוח
- -לא לטעון שSimulation
אוUnit Testing
מחליפיםCommissioning
עםI/O
,
Drives
., רשתות ותהליך אמיתי
- לא לקרוא בקולURLs
אוChecklists
. צפופים. הם חומר רקע להפקה
- לשמור אתRoot Cause
המלא ואתRecovery Flow
. המתוקן למקטע הסיום
.
Checklist
הנדסי לתוכנתPLC
.
האםOperating Modes
,
Equipment States
,
Commands
-, סמכות וTransitions
? מוגדרים במפורש
.
אילוPermissives
,
Interlocks
,
Trips
- וInvariants
? חלים על כל פעולה משחררת אנרגיה
.
מהי ההתנהגות הבטוחה והרצויה לאחרWarm Restart
,
Cold Restart
?, נפילת מתח וחזרת תקשורת
.
האם לכלOutput
פיזי יש בדיוקSoftware Owner
? אחד
.
האםCommand
,
Actual State
,
Process Effect
,
Signal Quality
- וCommand Source
? מופרדים
.
?האם השפה שנבחרה היא הייצוג הברור ביותר להתנהגות ההנדסית
.
האםState Machines
- משתמשות בEnumerations
-, מעברים חוקיים מפורשים וAbnormal Exits
? שלמים
.
האםTask Period
,
Worst-Case Execution Time
, לולאות, גודל נתונים ואינטראקציותShared Data
? תחומים
.
האםScaling
ויחידות מרוכזים וללאRaw Counts
אוMagic Constants
? לא מוסברים
.
האםRecipe
- וConfiguration
עובריםValidation
- וVersioning
- ומופרדים מLive
- וRetained Control State
?
.
האםModule Interfaces
חושפיםCommand
,
Status
,
Reason
- וDiagnostics
קומפקטיים ועםTypes
?
.
האםLibrary Dependencies
- נעולות לגרסה, מתועדות, נבדקות וניתנות לשחזור עבור הRelease
?
.
האםVersion Control
שומרChange History
, משמעותיReview
,
Release Tags
- וExports
? שניתנים לשחזור
.
האם ממצאיStatic Analysis
? נסקרים וחריגות מוצדקות במקום דיכוי גורף
.
האם בדיקות מכסותStart
,
Stop
,
Hold
,
Abort
,
Timeout
,
Stale Feedback
, מידע לא תקף, נפילת מתח
-וRecovery
?
.
האםSource
,
Toolchain
,
Libraries
,
Firmware
,
Configuration
- וBackup
? שנבדק יכולים לשחזר את המערכת

# 10. מילון מונחים
מונח
משמעות בפרק
IEC 61131-3
תקןIEC
המגדיר תחביר וסמנטיקה של שפות תכנות
.לבקרים מתוכנתים
POU
Program Organization Unit
:
Program
,
Function Block או
Function
.
LD
Ladder Diagram
, שפה גרפית המבוססת על מושגיRelay
Logic
.
ST
Structured Text
, שפה טקסטואלית ברמה גבוהה לפיIEC
61131-3
.
FBD
Function Block Diagram
, ייצוג גרפי של פונקציות וזרימת
.אות
SFC
רכיביSequential Function Chart
לארגוןSteps
,
Transitions
-וActions
.
State Machine
מודל מפורש שלStates
, מעברים מותרים והתנהגות
בכלState
.
Single Writer
ארכיטקטורה שבהModule אחד בלבד מכריע וכותב
Output
. פיזי
Retentive Data
מידע שמוגדר לשרוד תנאיRestart
או אובדן מתח
.מסוימים
Invariant
תנאי שחייב להישאר נכון כל עודState
אוAction
. פעילים
Static Analysis
בדיקתSource Code
באמצעותRules
אוMetrics
ללא
.הרצת האפליקציה
Regression Test
בדיקה המאשרת שהתנהגות קיימת נשארה נכונה
.לאחר שינוי
PLCopen XML
פורמטExchange
לפיIEC 61131-10
למידע פרויקטIEC
61131-3
.
PackML
מושגיMachine State
ונתונים שלOMAC המבוססים על
ISA-88
.
# 11. מפת תקנים ומקורות
מקורות ראשוניים ורשמיים ששימשו לבניית הפרק. ייתכן שנדרשת רכישה או גישה חוזית לתקנים המלאים. יש
.לבדוק מהדורה מאומצת, גרסת כלי ודרישות פרויקט
IEC 61131-3:2025, Programmable controllers - Part 3: Programming languages, edition 4.0 - https://webstore.iec.ch/en/publication/68533
IEC TR 61131-8:2017, Guidelines for the application and implementation of programming languages - https://webstore.iec.ch/en/publication/33021
IEC 61131-10:2019, PLC open XML exchange format - https://webstore.iec.ch/en/publication/33034

PLCopen, Software Construction Guidelines: coding, compliant libraries, SFC, OOP and quality metrics - https://www.plcopen.org/guidelines/software-construction-
guidelines
/
PLCopen, Structuring with Sequential Function Chart - https://www.plcopen.org/application/files/8717/3868/2051/plcopen_structuring_with_sfc.pdf
OMAC, PackML - https://www.omac.org/packml
ISA, TR88.00.02 Machine and Unit States preview - https://www.isa.org/getmedia/300dbd50-d549-41ac-b372-a5e52f32fc97/tr_880002_preview.pdf
CODESYS Git documentation - https://content.helpme-codesys.com/en/CODESYS%20Git/index.html
CODESYS Static Analysis documentation - https://content.helpme-codesys.com/en/CODESYS%20Static%20Analysis/_san_start_page.html
CODESYS Test Manager documentation - https://content.helpme-codesys.com/en/CODESYS%20Test%20Manager/_tm_start_page.html
Siemens, SIMATIC STEP 7 / TIA Portal and TIA Portal Test Suite documentation - https://www.siemens.com/en-gb/products/tia-portal/step7
/
Rockwell Automation, Studio 5000 Logix Designer import and export documentation - https://www.rockwellautomation.com/en-us/docs/studio-5000-logix-designer
/
| כיצד להשתמש במפת המקורות משתמשים בתקנים כדי להגדיר שפה ודרישות משותפות, בחומרPLCopen
-וISA/OMAC
עבור דפוסי בנייה, ובמדריכי היצרן המדויקים עבורTask Scheduling
,שפות-, תתיSource Control
,
Online Change
, בדיקות והתנהגותTarget
. אין להסיקSafety Certification
אוPortability
. מדוגמת שפה כללית
# 12. שער איכות לפני הקלטה
- -התסריט מתאים לכ42-46
. דקות בקצב שיחה טכני טבעי של שני מגישים
- חבילת השפות הנוכחית שלIEC 61131-3:2025
מתוארת בלי להציגInstruction List
. כשפה נוכחית
- לא מומצאותPortability
,
Certification
. או תאימות ברמת סעיף
- ,האירוע המרכזי נפתר באמצעות ארכיטקטורת בעלותState
- וRecovery
ולא באמצעותPatch
קוסמטי
-בRung
.
- LD
,
ST
,
FBD
- וSFC
מקבלות חוזקות, סיכונים ושאלותReview
. נפרדות
- Retention
,
Restart
,
Recipe Validation
- וLive Equipment State
. נשמרים כמושגים נפרדים
- הבדיקות כוללות מסלוליFailure
- וRecovery
וכן את מגבלותIntegration
. עם חומרה אמיתית
- הסיום יוצר מעבר נקי לתכןHMI
- וAlarms
.
