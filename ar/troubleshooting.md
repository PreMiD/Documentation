---
title: إصلاح الاخطاء
description: كل شيء لحل مشكلتك
published: true
date: 2021-09-18T14:08:01.002Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:17:32.312Z
---

> تأكد من أن لديك الملحق **و** التطبيق مثبتين! 
> 
> {.is-warning}

المدرج في هذه الصفحة:
1. [استكشاف الأخطاء وإصلاحها بشكل عام](https://docs.premid.app/troubleshooting#general)
2. [استكشاف أخطاء لينكس وإصلاحها](https://docs.premid.app/troubleshooting#linux)
3. [استكشاف أخطاء MacOS وإصلاحها](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# استكشاف الأخطاء وإصلاحها بشكل عام
> يمكنك استعمال [ هذه](https://qkeleq10.github.io/PreMiD-Troubleshooting/) اداة قادرة على تحديد المشاكل الخاصة بك بسهولة اكبر. 
> 
> {.is-info}
### أعد تحميل الصفحة
يمكنك الضغط على <kbd>CTRL+R</kbd>/<kbd>F5</kbd> (ويندوز) أو <kbd>CMD+R</kbd> (MacOS) على لوحة المفاتيح أيضا بدلا من البحث على زر التحديث.

### هل تستخدم تطبيق ديسكورد؟
**لا يعمل** PreMiD على إصدار ديسكورد للمتصفح، يجب عليك تحميل التطبيق [هنا](https://discord.com/download).

### تأكد من أنك قمت بتفعيل نشاط لعبة في الإعدادات الديسكورد
**إعدادات المستخدم** > **نشاط العبة**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### تأكد من أن ديسكورد لا يعمل كمسؤول
Really important. لن يعمل ديسكورد RPC إذا قمت بتشغيل ديسكورد كـ administrator.

### هل تستخدم presence مع الإعدادات؟
Many presences (including `Twitch` and `SoundCloud`) are affected by an extension issue. This issue causes the extension to not grab the default values of settings properly.

To solve this, all you have to do is toggle the topmost setting:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### أعد تشغيل المتصفح
<kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) or <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) does a good job too. (You have to start your browser again obviously.)

### أعد تشغيل PreMiD (التطبيق)
<img src="https://i.imgur.com/wQA15xu.png" width="500px" style="max-width:100%;" />
You have to restart PreMiD afterwards.

### أعد تشغيل Discord
اضغط <kbd>CTRL+R</kbd> (ويندوز) او <kbd>CMD+R</kbd> (ماك) على الكيبورد او قم بإعادة تشغيل الديسكورد يدوياً.

### تحقق مما إذا كان برنامج مكافحة الفيروسات أو جدار الحماية مشتغل في الجهاز
في بعض الأحيان تمنع برامج مكافحة الفيروسات وجدران الحماية التطبيقات التي تصنع خوادم أو تستضيفها أو تتصل فقط بالإنترنت. نحن نستخدم خادم محلي لتلقي البيانات ونقلها بين تطبيقنا وملحقنا، لذلك إذا كنت ستمنع قدرة التطبيق على نقل البيانات فلن تتمكن على الأرجح من استخدام PreMiD.

### قم تعطيل الإضافات الخاصة بك
قم بتعطيل جميع الإضافات الخاصة بك وانظر إذا كان سيعمل. إذا كان الجواب نعم، حاول تشغيل الـ addons الخاصة بك واحدة تلوى الاخرة وأخبرنا عن أي إضافة جعلت PreMiD يتوقف عن العمل.

### إعادة تشغيل جهاز الكمبيوتر
آمل أنك تعرف كيفية إعادة تشغيل الكمبيوتر.

### إعادة تثبيت PreMiD
في بعض الأحيان قد يكون هناك شيء خاطئ في الملفات... يمكنك العثور على طريقة التثبيت [هنا](/install).

### إزالة يدوياً
ويندوز: اكتب`%appdata%` على مستكشف الملفات واحذف ملف الـ `PreMiD`. MacOS: `~/users/USER/~Library/Application Support/` وقم بحذف ملف الـ `PreMiD`.

### تم تحديد PreMiD على إنه فيروس من قبل McAfee (ويندوز)
This is a false positive from McAfee and we have reported the issue to them, for now you can exclude PreMiD from the scan by doing the following steps:

> وإذا لم تكن واثق من اتخاذ هذه الخطوات، لا تتردد في فتح تذكرة في [#support](https://discord.premid.app/) وسيكون أحد عملاء الدعم لدينا قادرا على مساعدتك! 
> 
> {.is-warning}

1. افتح تطبيق acAfee وانقر على أيقونة الإعدادات في أعلى اليمين. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. انقر فوق "العناصر المعزولة" (الثانية من الأعلى).
3. قم بتوسيعها، وانقر على أيقونة `>` قبل عنصر باسم "settings.dat".
4. تأكد من أن المسار يحتوي على "AppData\Local\Temp\PreMiD"، إذا كان يفعل قم بتحديده واضغط على استعادة. <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. بعد استعادته يمكنك إغلاق نافذة "العناصر المعزولة"، ثم اضغط على أيقونة الإعدادات مرة أخرى في أعلى اليمين.
6. انقر فوق "الفحص في الوقت الحقيقي" (الثالثة من الأعلى).
7. قم بتوسيعها وانقر على "إضافة ملف".
8. اكتب "%appdata%" في مكان الرابط في مدير الملفات واضغط على زر إنتر. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. افتح مجلد "PreMiD" وحدد ملف "PreMiD.exe" وانقر على فتح. <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. يجب أن يتجاهل McAfee ملفنا، فقط ابدأ تطبيقنا وينبغي أن تكون جيداً للذهاب.

### PreMiD status bugged on Discord
لا تقلق. أضغط علي <kbd>CTRL+R</kbd> (ويندوز) أو <kbd>CMD+R</kbd> (ماك) مع التركيز على نافذة الديسكورد لأعادة تحميلها.

<a name="linux"></a>

# استكشاف أخطاء لينكس وإصلاحها
### توزيعات Ubuntu/Debian
إذا قمت بتحميل الديسكورد من خلال Snapcraft، لن يعمل RPC. يجب عليك حذف نسخة Snapcraft عن طريق كتابة`sudo snap remove discord` في وحدة التحكم, قم بتحميل**[ ديسكورد للينكس](https://discordapp.com/api/download?platform=linux)**(**[ او ديسكورد كناري](https://discordapp.com/api/canary/download?platform=linux)**) ثم انتقل إلى المكان الذي قمت بتنزيل الديسكورد فيه ( عادةً `$HOME/Downloads`) ثم ثبت الحزمة بأستخدام`sudo dpkg -i discord-*.deb`. If AppImage doesn't work, you should consider checking our other packages by **[this link](https://packagecloud.io/premid/linux)**.

### التوزيع القائمة على أرش لينكس
Arch Linux based distros should use AUR (Arch User Repository) package that is named <code>premid</code> or <code>premid-git</code> (<em x-id="3">WARNING: This repository builds premid from our source code.</em>). If you don't want to install an AUR manager (yay etc.), you can check out our AppImage that is downloadable from our <strong x-id="1"><a href="https://github.com/premid/linux/releases">Linux repository</a></strong>.
<em x-id="3">Warning: the package in the <strong x-id="1">AUR</strong> repository is not maintained by us (as PreMiD organization), but by other people.</em>

### روابط المنفذ
You should know that <strong x-id="1">PreMiD</strong> binds itself to the port <strong x-id="1">3020</strong>. This is necessary for the Extension and the Application communicate. If <strong x-id="1">PreMiD</strong> shows you an error about this port, you should check if something is binded to the 3020 port by running <code>sudo lsof -i:3020</code> or <code>sudo netstat -tnlp | grep :3020</code> in your terminal. If some process is binded to it you should make sure to free the port and try running <code>PreMiD</code> again.

### لا تشغل صورة تطبيق PreMiD عند تسجيل الدخول
As we stated in our **Linux repository**, AppImage can't be launched at login. You can add it to autostart manually by doing these steps:
1. أنشئ ملف اسمه <strong x-id="1">rc.Local</strong> في الدليل <code>/ إلخ</code>.
2. افتح هذا الملف في المحرر المفضل الخاص بك ولصق التعليمات البرمجية مع تغيير بعض الأشياء:
```bash
#!/bin/bash
# مطلوب للتشغيل كـ /bin/bash (إذا كنت تستخدم zsh إلخ). يمكنك تغييره.)

# مثال: /home/PreMiD/PreMiD*.AppImage
<directory to appimage>/PreMiD*.AppImage

exit 0
```
3. حفظ الملف و chmod كقابل للتنفيذ `sudo chmod a+x /etc/rc.local`.
4. أعد تشغيل جهاز الكمبيوتر الخاص بك, صور تطبيق PreMiD يجب ان تشتغل عند تسجيل الدخول.

<a name="macos"></a>

# استكشاف أخطاء MacOS وإصلاحها
### خطأ في قائمة الدليل
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

If you get this error, it means that your account doesn't have Administrator permissions and you need to create folder manually by doing these steps:
1. افتح مجلد البحث وافتح **مجلد التطبيقات**.
2. انقر بالزر الأيمن على المساحة الفارغة وانقر فوق **إنشاء مجلد**.
3. إلى هذا المجلد يقوم بتعيين `PreMiD` الاسم (تذكر عن الأحرف الكبيرة).
4. فتح المثبت مرة أخرى.

# هذا لم يحل مشكلتي
Please open a ticket in [#support](https://discord.premid.app/).
