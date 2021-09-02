---
title: Решение проблем
description: Всё для решения вашей проблемы
published: true
date: 2021-02-08T21:30:58.603Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:03:54.865Z
---

> Убедитесь, что у вас установлены расширение **и** приложение! 
> 
> {.is-warning}

Включено на этой странице:
1. [Общее решение неполадок](https://docs.premid.app/troubleshooting#general)
2. [Устранение неполадок Linux](https://docs.premid.app/troubleshooting#linux)
3. [Устранение неполадок MacOS](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# Общее решение неполадок
> Вы можете использовать [этот](https://qkeleq10.github.io/PreMiD-Troubleshooting/) инструмент, чтобы упростить определение вашей проблемы. 
> 
> {.is-info}
### Перезагрузите страницу
Вы также можете нажать на <kbd>CTRL+R</kbd> или <kbd>F5</kbd> (Windows) или <kbd>CMD+R</kbd> (MacOS) на клавиатуре, вместо поиска кнопки обновления страницы.

### Используете ли вы приложение Discord?
PreMiD **не** работает в браузерной версии Discord. Вы должны скачать приложение [отсюда](https://discord.com/download).

### Убедитесь, что вы включили статус активности в настройках приложения Discord
**Настройки пользователя** > **Статус активности**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### Убедитесь, что Discord запущен НЕ от имени администратора
Очень важно. Discord RPC не будет работать, если вы запустите Discord от имени администратора.

### Вы используете presence с настройками?
Проблему с расширением затрагивают многие presence (включая `Twitch` и `SoundCloud`). Из-за этой проблемы расширение не принимает значения настроек по умолчанию правильно.

Чтобы решить эту проблему, вам нужно переключить самую верхнюю настройку:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Перезапустите браузер
Также можно использовать <kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) или <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS). (вы должны перезапустить браузер)

### Перезапустить PreMiD (Приложение)
<img src="https://i.imgur.com/wQA15xu.png" width="500px" style="max-width:100%;" />
После вы должны перезапустить PreMiD.

### Перезагрузить/перезапустить Discord
Нажмите <kbd>CTRL+R</kbd> (Windows) или <kbd>CMD+R</kbd> (MacOS) на клавиатуре или перезапустите Discord вручную.

### Проверьте, запущен ли на вашем компьютере антивирус или брандмауэр
Иногда антивирусные программы и брандмауэры блокируют приложения, которые создают или размещают серверы или просто подключаются к интернету. We are using a local server to receive and pass data between our app and extension, so if you will block app's ability to pass data you probably will not be able to use PreMiD.

### Отключите ваши аддоны
Disable all your addons and see if it works. Если да, попробуйте включить по очереди свои дополнения и сообщите нам, какое дополнение сломало PreMiD.

### Перезагрузите компьютер
I hope you know how to restart a computer.

### Переустановите PreMID
Sometimes there is something wrong with the files... Tutorials for the installation can be found [here](/install).

### Ручное удаление
Windows: Write `%appdata%` on the file explorer and delete the `PreMiD` folder. MacOS: `~/users/USER/~Library/Application Support/` and delete the `PreMiD` folder.

### McAfee обнаружил PreMiD как вирус (Windows)
This is a false positive from McAfee and we have reported the issue to them, for now you can exclude PreMiD from the scan by doing the following steps:

> Если вы не чувствуете уверенности в том, что делаете эти шаги, не стесняйтесь сделать тикет в [#support](https://discord.premid.app/) и один из наших агентов поддержки сможет вам помочь! 
> 
> {.is-warning}

1. Откройте приложение McAfee и нажмите значок настроек в правом верхнем углу. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. Нажмите "Карантированные предметы" (Вторая вверху).
3. Разверните его, и нажмите значок `>` перед элементом с названием "settings.dat".
4. Убедитесь, что путь включает "AppData\Local\Temp\PreMiD", если да, выберите его и нажмите восстановить. <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. После восстановления вы можете закрыть всплывающее окно "Карантинированные предметы", затем снова нажать на значок настроек в правом верхнем углу.
6. Щелкните «Сканирование в реальном времени» (третье сверху).
7. Разверните его и нажмите "Добавить файл".
8. Тип "%appdata%" в адресной строке проводника и нажмите Enter. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. Откройте папку "PreMiD" и выберите файл "PreMiD.exe" и нажмите открыть. <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. McAfee теперь должен проигнорировать наш файл, просто запустите наше приложение и всё должно быть хорошо.

### Статус PreMiD на дискорде!
Don't worry. Press the <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) keybind while focused on your discord window to reload it.

<a name="linux"></a>

# Устранение неполадок Linux
### На дистрибутивах на основе Ubuntu/Debian
If you have downloaded Discord through Snapcraft, RPC will not work. You have to uninstall the Snapcraft version by executing `sudo snap remove discord` on a terminal, download **[Discord's Linux build](https://discordapp.com/api/download?platform=linux)** (**[or Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), then navigating to the directory you downloaded Discord to (usually `$HOME/Downloads`), then installing the package using `sudo dpkg -i discord-*.deb`. If AppImage doesn't work, you should consider checking our other packages by **[this link](https://packagecloud.io/premid/linux)**.

### Дистрибутивы на основе Arch Linux
Arch Linux based distros should use AUR (Arch User Repository) package that is named <code>premid</code> or <code>premid-git</code> (<em x-id="3">WARNING: This repository builds premid from our source code.</em>). If you don't want to install an AUR manager (yay etc.), you can check out our AppImage that is downloadable from our <strong x-id="1"><a href="https://github.com/premid/linux/releases">Linux repository</a></strong>.
<em x-id="3">Warning: the package in the <strong x-id="1">AUR</strong> repository is not maintained by us (as PreMiD organization), but by other people.</em>

### Привязка портов
You should know that <strong x-id="1">PreMiD</strong> binds itself to the port <strong x-id="1">3020</strong>. This is necessary for the Extension and the Application communicate. If <strong x-id="1">PreMiD</strong> shows you an error about this port, you should check if something is binded to the 3020 port by running <code>sudo lsof -i:3020</code> or <code>sudo netstat -tnlp | grep :3020</code> in your terminal. If some process is binded to it you should make sure to free the port and try running <code>PreMiD</code> again.

### AppImage PreMiD не запускается при входе в систему
As we stated in our **Linux repository**, AppImage can't be launched at login. You can add it to autostart manually by doing these steps:
1. Сделать файл с именем <strong x-id="1">rc.local</strong> в каталоге <code>/etc</code>.
2. Откройте этот файл в вашем любимом редакторе и вставьте данный код с изменением некоторых вещей:
```bash
#!/bin/bash
# Требуется запустить как /bin/bash (если вы используете zsh etc. вы можете изменить его.)

# Пример: /home/PreMiD/PreMiD*.AppImage
<directory to appimage>/PreMiD*.AppImage

Выход 0
```
3. Сохраните файл и chmod как исполняемый `sudo chmod a+x /etc/rc.local`.
4. Перезагрузите компьютер и PreMiD AppImage должны быть запущены при входе в систему.

<a name="macos"></a>

# Устранение неполадок MacOS
### Ошибка создания каталога
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

If you get this error, it means that your account doesn't have Administrator permissions and you need to create folder manually by doing these steps:
1. Откройте finder и откройте папку **Applications**.
2. Щелкните правой кнопкой мыши на пустом месте и нажмите **Создать папку**.
3. В эту папку назначьте `имя PreMiD` (запомните буквы в верхнем регистре).
4. Открыть программу установки заново.

# Это не решило мою проблему
Please open a ticket in [#support](https://discord.premid.app/).
