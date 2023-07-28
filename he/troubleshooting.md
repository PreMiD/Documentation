---
title: פתרון תקלות
description: הכל כדי לפתור את הבעיה שלך
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:17:32.312Z
---

> וודא שיש לך את התוסף ** ו ** את היישום מותקנים! 
> 
> {.is-warning}

כלול בדף זה:
1. [פתרון בעיות כללי](https://docs.premid.app/troubleshooting#general)
2. [פתרון בעיות לינוקס](https://docs.premid.app/troubleshooting#linux)
3. [פתרון בעיות ב-MacOS](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# פתרון בעיות כללי
### טען מחדש את הדף
אתה יכול ללחוץ <kbd>CTRL+R</kbd> / <kbd>f5</kbd> (Windows) או <kbd>CMD+R</kbd> (פקודות מאקרו) על המקלדת שלך מדי במקום לחפש את כפתור הרענון.

### האם אתה משתמש באפליקציית Discord?
PreMiD **לא** עובד על גרסת הדפדפן של Discord, עליך להוריד את האפליקציה [כאן](https://discord.com/download).

### ודא שיש לך סטטוס פעילות מופעל בהגדרות האפליקציה של Discord
**הגדרות משתמש** > **מצב פעילות**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### ודא כי דיסקורד לא פועל כמנהל מערכת
Really important. Discord RPC לא יעבוד אם אתה מפעיל מחלוקת כמנהל.

### האם אתה משתמש בנוכחות עם הגדרות?
נוכחות רבות (כולל `Twitch` ו-`SoundCloud`) מושפעות מבעיית הרחבה. בעיה זו גורמת לתוסף לא לתפוס כראוי את ערכי ברירת המחדל של ההגדרות.

כדי לפתור זאת, כל מה שאתה צריך לעשות הוא להחליף את ההגדרה העליונה:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Restart your browser
<kbd>Alt</kbd> + <kbd>F4</kbd> (Windows) או <kbd>CMD</kbd>+<kbd>Q</kbd> (MAC OS) עושה עבודה טובה מדי. (אתה צריך להפעיל את הדפדפן שלך שוב כמובן.)

### הפעל מחדש את PreMiD (יישום)
<img src="https://i.imgur.com/g3ShdnU.png" width="500px" style="max-width:100%;" />
עליך להפעיל מחדש את PreMiD לאחר מכן.

### טען/הפעל מחדש את Discord
לחץ על<kbd>CTRL+R </kbd> (Windows) או <kbd>CMD+R</kbd> (MacOS) על המקלדת שלך או הפעל מחדש את הדיסקורד באופן ידני.

### בדוק אם במחשב שלך פועל אנטי-וירוס או חומת אש
לפעמים תוכנות אנטי-וירוס וחומות אש חוסמות יישומים שיוצרים/מאחסנים שרתים או פשוט מתחברים לאינטרנט. אנו משתמשים בשרת מקומי כדי לקבל ולהעביר נתונים בין האפליקציה וההרחבה שלנו, כך שאם תחסום את היכולת של האפליקציה להעביר נתונים סביר להניח שלא תוכל להשתמש ב- PreMiD.

### השבת את התוספות שלך
השבת את כל התוספים שלך ובדוק אם זה עובד. אם כן, נסה להפעיל את התוספים שלך שלב אחר שלב וספר לנו איזה תוסף שבר את PreMiD.

### הפעלה מחדש של המחשב
אני מקווה שאתה יודע איך להפעיל מחדש מחשב.

### התקנה מחדש של PreMiD
לפעמים יש משהו לא בסדר עם הקבצים... ניתן למצוא מדריכים להתקנה [כאן](/install).

### הסרה ידנית
Windows: כתוב `%appdata%` בסייר הקבצים ומחק את התיקיה `PreMiD`. MacOS: `~/users/USER/~Library/Application Support/` ומחק את התיקיה `PreMiD`.

### McAfee זיהה את PreMiD כוירוס (Windows)
זהו חיובי כוזב מ- McAfee ודיווחנו להם על הבעיה, לעת עתה באפשרותך לא לכלול את PreMiD בסריקה על-ידי ביצוע השלבים הבאים:

> ניתן להשתמש בכלי [זה](https://qkeleq10.github.io/PreMiD-Troubleshooting/) כדי לזהות בקלות רבה יותר את הבעיה שלך. 
> 
> {.is-warning}

1. פתח את יישום McAfee ולחץ על סמל ההגדרות בצד השמאלי העליון. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. לחץ על "פריטים בהסגר" (שני מלמעלה).
3. Expand it, and click the `>` icon before an item with the name "settings.dat".
4. Make sure the path includes "AppData\Local\Temp\PreMiD", if so select it and press restore. <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. לאחר שחזורו באפשרותך לסגור את הפריטים המוקפצים "פריטים בהסגר", ולאחר מכן להקיש שוב על סמל ההגדרות בצד למעלה.
6. לחץ על "סריקה בזמן אמת" (שלישי מלמעלה).
7. הרחב אותו ולחץ על "הוסף קובץ".
8. הקלד "%appdata%" בשורת הכתובת של סייר הקבצים והקש Enter. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. פתח את התיקיה "PreMiD" ובחר את הקובץ "PreMiD.exe" ולחץ על פתח. <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. McAfee צריך עכשיו להתעלם הקובץ שלך, רק להפעיל את היישום שלנו ואתה צריך להיות טוב ללכת.

### מצב PreMiD מצותת ל-Discord
אל תדאג. לחץ על מקש <kbd>CTRL+R</kbd> (Windows) או <kbd>CMD+R</kbd> (פקודות מאקרו) keybind תוך התמקדות בחלון הדיסק כדי לטעון אותו מחדש.

<a name="linux"></a>

# פתרון בעיות לינוקס
### הפצה מבוססת Ubuntu/Debian
אם הורדת את Discord באמצעות Snapcraft, RPC לא יפעל. עליך להסיר את ההתקנה של גרסת Snapcraft על ידי ביצוע `sudo snap remove discord` בטרמינל, הורד את **[מבנה הלינוקס של דיסקורד](https://discordapp.com/api/ download?platform=linux)** (**[או Discord Canary](https://discordapp.com/api/canary/download?platform= linux)**), לאחר מכן נווט אל הספרייה שאליה הורדת את Discord (בדרך כלל `$HOME/Downloads`), ולאחר מכן התקנת החבילה באמצעות `sudo dpkg -i discord-*.deb`. אם AppImage לא עובד, אתה צריך לשקול לבדוק את החבילות האחרות שלנו על ידי **[קישור זה](https://packagecloud.io/premid/linux)**.

### הפצה מבוססת Arch Linux
הפצה מבוססת Arch Linux צריכה להשתמש בחבילת AUR (מאגר משתמש קשת) בשם <code>premid</code> or <code>premid-git</code> (<em x-id="3">אַזהָרָה: מאגר זה בונה קדם מקוד המקור שלנו.</em>). אם אתה לא רוצה להתקין מנהל AUR (yay וכו '), אתה יכול לבדוק AppImage שלנו כי הוא להורדה שלנו <strong x-id="1"><a href="https://github.com/premid/linux/releases">Linux מאגר</a></strong>.
<em x-id="3">אזהרה: החבילה ב <strong x-id="1">AUR</strong> המאגר אינו מתוחזק על ידינו (כמו PreMiD ארגון), אלא על ידי אנשים אחרים.</em>

### כריכת נמל
אתה צריך לדעת את זה. <strong x-id="1">PreMiD</strong> קושר את עצמו ליציאה <strong x-id="1">3020</strong>. זה הכרחי עבור ההרחבה ואת היישום לתקשר. אם <strong x-id="1">PreMiD</strong> shows אתה שגיאה ביציאה זו, עליך לבדוק אם משהו מאוגד ליציאה 3020 על-ידי הפעלה <code>sudo lsof -i:3020</code> or <code>sudo netstat -tnlp | grep :3020</code> במסוף שלך. אם תהליך מסוים מאוגד אליו אתה צריך לוודא כדי לשחרר את היציאה ולנסות לרוץ <code>PreMiD</code> שוב.

### AppImage של PreMiD אינו מופעל בכניסה
כפי שהצהרנו ב **Linux מאגר**, AppImage לא ניתן להפעיל בעת הכניסה. באפשרותך להוסיף אותו להפעלה אוטומטית באופן ידני על-ידי ביצוע השלבים הבאים:
1. יצירת קובץ בשם <strong x-id="1" mark="crwd- mark">rc.local</strong> בתוך ה
 <code>/etc</code> מַדרִיך.
2. פתח קובץ זה בעורך המועדף עליך והדבק קוד נתון עם שינוי כמה דברים:
```bash
#!/bin/bash
# נדרש לרוץ כמו /bin/bash (אם אתם משתמשים ב-zsh וכו'. אתה יכול לשנות את זה.)

# דוגמה: /home/PreMiD/PreMiD*.AppImage
<directory to appimage>/PreMiD*.AppImage
```
3. שמור קובץ ו-chmod אותו כקובץ הרצה `sudo chmod a+x /etc/rc.local`.
4. הפעל מחדש את המחשב ואת AppImage PreMiD צריך להפעיל בעת הכניסה.

<a name="macos"></a>

# פתרון בעיות ב-MacOS
### שגיאה ביצירת ספריה
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

אם אתה מקבל שגיאה זו, פירוש הדבר שלחשבון שלך אין הרשאות מנהל מערכת ועליך ליצור תיקיה באופן ידני על-ידי ביצוע השלבים הבאים:
1. פתח את הממצא ופתח **Applications** תיקייה.
2. לחץ באמצעות לחצן העכבר הימני על שטח ריק ולחץ על **צור תיקיה**.
3. להקצאת תיקיה זו `PreMiD` שם (זכור אודות אותיות-גדולות אותיות).
4. פתח התקנה שוב.

# זה לא פתר את הבעיה שלי
אנא צור פוסט חדש ב-[support#](https://discord.com/channels/493130730549805057/1019726199494279248).
