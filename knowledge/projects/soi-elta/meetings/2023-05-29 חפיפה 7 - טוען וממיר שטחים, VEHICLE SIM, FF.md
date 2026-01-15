### טעינת שטחים
יש בסנדבוקס כמה סוגי שטחים שתומכים בהם
בדרך כלל שטח MFT שהומר ליוניטי
משתמשים בו בעיקר ב VRF

שכת בתצא, בניינים, 

משתמשים בכלי של חברת SIMBLOCKS - כלי שנקרא ONE WORLD SDK כדי לעשות טיענה בRUNTIME של CDB

בשונה מMFT שעושים המרה ראשונית ל ASSETBUNDLE

הONEWORLDS SDKטוען בRUNTIME מהדיסק

בנוסף יש TILE TERRAIN, שטח שנשמר בטיילים

לוקחים שטח MFT, מחלקים אותו לאיזורים קטנים יותר, כל איזור קטן נשמר בסצנה נפרדת
ואז טוענים את הסצנות הרלוונטיות, זה חוסך זכרון לשטחים גדולים

בצד של הסנדבוקסצריך להגדיר באיזה שטח משתמשים ואיזה סוג של שטח זה

איך מתמודדים עם טיילים ועם כלים שנמצאים במקומות שונים בעולם
בד"כ טוענים את הטייל שנמצא עליו + 8 מסביבו

אם יש הרבה ישויות הם עושים את זה אוטומטית לכל ישות

בסוף הם משתמכים ב TILEים שקיימםי בMFT, זה תלוי בשטח שעליו מסתמכים במקור
![](../../attachments/Pasted image 20230529140822.png)

יש כמו REFERENCE COUNTING על כל טייל וככה יודעים איזה צריך

כרגע בדיפולט טוענים את הטייל שהוא נמצא עליו + 1 לכל כיוון, זה קונפיגורבילי
אם יש כוחות אדומים בטטיל שעוד לא טעון - לא טוענים להם את הטייל, אבל הם כן שם
זה תלוי רק בישויות הלוקאליות

לכל TERRAIN LOADER יש קונפיגורציה אחרת

![](../../attachments/Pasted image 20230529141205.png)

סוגים:
![](../../attachments/Pasted image 20230529141253.png)
Simple Terrain - מימוש רגיל - ![](../../attachments/Pasted image 20230529141313.png)
מפנים אותו ל ASSET BUNDLE של שטח והוא טוען אותו

![](../../attachments/Pasted image 20230529141354.png)
טוען את הסצנה הראשונה של MANAGER והוא יודע לנהל את השטח ואיזה טיילים לטעון

![](../../attachments/Pasted image 20230529141515.png)

![](../../attachments/Pasted image 20230529141605.png)

אם כתוב 4X4 הכוונה שיהיה שימוש ב4X4 טיילים בסיסיים עבור טייל אחד ![](../../attachments/Pasted image 20230529142136.png)

SIMBLOCKS
![](../../attachments/Pasted image 20230529142337.png)

לא רצו שיהיו רפרנסים לסקריפטים של SIMBLCOKS

עשו לפי שם במקום לפרק ל PACKAGE נפרד

![](../../attachments/Pasted image 20230529143109.png)

אם נגיד רוצים נקודה ב SIMBLOCKS, אז ה ROTATION בעולם משתנה

![](../../attachments/Pasted image 20230529143238.png)
אם מסתכלים על MFT, תמדי המערכת צירים מיושרת עם יוניטי

CSIMBLOCKS אם אנחנו רוצים נקוד שהיא לא בצפון, יש ROTATION שצריך לפצות עליו

ובשביל זה יש CONVERSIONS

לאיתי לא יצא לעבוד עם זה כשהכניסו

הם קיבלו את קוד המקור של הפרויקט והיו צריכים לעשות בילד בעצמם
הדרישה שלהם הייתה שנתקין את זה על כונן D (בסקריפטים של הבילד)

![](../../attachments/Pasted image 20230529143959.png)

מאפשר גישה למיקום גאודטי של אובייקט בעולם

![](../../attachments/Pasted image 20230529144251.png)
קורא ל LOAD TERRAIN

![](../../attachments/Pasted image 20230529144420.png)

![](../../attachments/Pasted image 20230529144617.png)

![](../../attachments/Pasted image 20230529144808.png)

ממשק להמרת קורדינטות ^ בהתאם לסוג השטח

![](../../attachments/Pasted image 20230529145048.png)
יש גם למצלמה

![](../../attachments/Pasted image 20230529145311.png)


### VRLINK חדש

החליפו לפקוירט VRLINK חדש
תמיכה ב DIS ו HLA בלי שיצטרכו לקמפל מחדש

עשו שיטה חדשה וזה יעבור אלינו

![](../../attachments/Pasted image 20230529151031.png)

כשמקמפלים פרויקט צריך לקמפל או ב DIS או בHLA
הם עושים שמי שמשתמש בסיפרייה אחריא לנהל את ה STATE ואין STATE בצד של  הC++
עשו אפשרות להחזיק PUBLISHED ו REFLECTED בגישה משותפת


מקמפלים ל DIS ול HLA ואז יש משהו שעושה טעינה דינאמית

![](../../attachments/Pasted image 20230529151742.png)

![](../../attachments/Pasted image 20230529151911.png)

![](../../attachments/Pasted image 20230529152257.png)

![](../../attachments/Pasted image 20230529152514.png)
![](../../attachments/Pasted image 20230529153606.png)

![](../../attachments/Pasted image 20230529153847.png)

יש מחלקת C++
ספריית C# ("טהורה" ולא תלויה ביוניטי)
ואז PACKAGE UNITY

הם עשו הפרדה כדי שיהיה אפשר להשתמש בזה בלי יוניטי

עשו פריפאב חיבור לדוגמה
![](../../attachments/Pasted image 20230529154940.png)


![](../../attachments/Pasted image 20230529154945.png)

![](../../attachments/Pasted image 20230529155137.png)

כרגע מתחילים את הריק וטוענים בהתאם

בגרסה הזאת לא צריך לעשות בילד נפרד

משתמשים ב CMAKE לקימפול
יש 3 TARGETS והם VrLinkNativeDIS, VRLinkNativeHLA, VRLinkNative
בקוד C# משתמשים ב VRLINKNATIVE והוא טוען את הDIS או הHLA המתאים

אי אפשר לעבוד בDIS וHLA באותו הזמן ואי אפשר ליצור שנשי EXCERSICE CONNECTION במקביל

הורידו תמיכה ב EVENT REPORTS!!

![](../../attachments/Pasted image 20230529162508.png)

מצפה שיהיה VRLINK מותקן על המחשב