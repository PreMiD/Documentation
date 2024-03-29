---
title: Solução de problemas
description: Tudo para resolver o teu problema
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:17:32.312Z
---

> Verifica se tens a extensão **e** a aplicação instaladas! 
> 
> {.is-warning}

Esta página inclui:
1. [Solução de problemas gerais](https://docs.premid.app/troubleshooting#general)
2. [Solução de problemas no Linux](https://docs.premid.app/troubleshooting#linux)
3. [Solução de problemas no MacOS](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# Solução de problemas gerais
### Atualiza a página
Podes pressionar <kbd>CTRL+R</kbd>/<kbd>F5</kbd> (Windows) ou <kbd>CMD+R</kbd> (MacOS) no teu teclado em vez de procurar pelo botão de atualizar.

### Estás a usar a aplicação do Discord?
O PreMiD **não** funciona na versão do Discord para navegador, precisas de descarregar a aplicação clicando [aqui](https://discord.com/download).

### Certifica-te de que o Status de atividade está ativo nas definições da aplicação do Discord
**Definições de Utilizador** > **Status de atividade**
<img src="https://i.imgur.com/RUMoMQo.png" width="500px" style="max-width:100%;" />

### Certifica-te de que o Discord NÃO foi executado como administrador
Muito importante. O RPC do Discord não vai funcionar se executares o Discord como administrador.

### Estás a usar uma presence com definições?
Muitas presences (incluindo a da `Twitch` e do `SoundCloud`) são afetadas por um problema na extensão. Este problema faz com que a extensão não obtenha os valores pré-definidos das definições corretamente.

Para corrigir isto, tudo o que tens de fazer é alterar a primeira definição:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Reinicia o teu navegador
<kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) ou <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) também funciona. (Podes abrir o teu browser depois disto obviamente)

### Reinicia o PreMiD (Aplicação)
<img src="https://i.imgur.com/g3ShdnU.png" width="500px" style="max-width:100%;" />
You have to restart PreMiD afterwards.

### Recarregar/reiniciar o Discord
Press <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) on your keyboard or restart Discord manually.

### Verifique se tem o antivirus ou firewall em execução no seu computador
Sometimes antivirus programs and firewalls are blocking applications which are creating/hosting servers or just connecting to the internet. We are using a local server to receive and pass data between our app and extension, so if you block app's ability to pass data, you probably will not be able to use PreMiD.

### Desative os seus addons
Disable all your addons and see if it works. If yes, try to enable your addons step-by-step and tell us which addon broke PreMiD.

### Reinicie o seu computador
I hope you know how to restart a computer.

### Reinstale o PreMiD
Sometimes there is something wrong with the files... Tutorials for the installation can be found [here](/install).

### Remoção manual
Windows: Write `%appdata%` on the file explorer and delete the `PreMiD` folder. MacOS: `~/users/USER/~Library/Application Support/` and delete the `PreMiD` folder.

### O McAfee detetou o PreMiD como um vírus (Windows)
This is a false positive from McAfee and we have reported the issue to them, for now you can exclude PreMiD from the scan by doing the following steps:

> If you do not feel confident taking these steps, feel free to make a ticket in [#support](https://discord.premid.app/) and one of our Support Agents will be able to help you out! 
> 
> {.is-warning}

1. Abra o McAfee e clique no ícone de definições no canto superior direito. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. Clique em "Quarantined Items" (Segundo a partir do topo).
3. Expanda e clique no ícone `>` antes de um item com o nome "settings.dat".
4. Certifica-te de que o caminho inclui "AppData\Local\Temp\PreMiD", se não for o selecione e pressione restaurar. <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. Depois de restaurado, você pode fechar a janela de "Quarantined Items", depois pressione novamente o ícone de definições no canto superior direito.
6. Clique em "Real-Time Scanning" (Terceiro a partir do topo).
7. Expandir e clique em "Add file".
8. Type "%appdata%" in the address bar of the File Explorer and press Enter. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. Abra a pasta "PreMiD" e selecione o ficheiro "PreMiD.exe" e clique em abrir. <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. O McAfee agora deve ignorar nosso ficheiro, apenas iniciar nossa aplicação e você deve estar pronto para começar.

### PreMiD status bugged on Discord
Não te preocupes. Press the <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) keybind while focused on your Discord window to reload it.

<a name="linux"></a>

# Solução de problemas no Linux
### Ubuntu/Debian based distros
If you have downloaded Discord through Snapcraft, RPC will not work. You have to uninstall the Snapcraft version by executing `sudo snap remove discord` on a terminal, download **[Discord's Linux build](https://discordapp.com/api/download?platform=linux)** (**[or Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), then navigating to the directory you downloaded Discord to (usually `$HOME/Downloads`), then installing the package using `sudo dpkg -i discord-*.deb`. If AppImage doesn't work, you should consider checking our other packages by **[this link](https://packagecloud.io/premid/linux)**.

### Arch Linux based distros
Arch Linux based distros should use AUR (Arch User Repository) package that is named <code>premid</code> or <code>premid-git</code> (<em x-id="3">WARNING: This repository builds premid from our source code.</em>). If you don't want to install an AUR manager (yay etc.), you can check out our AppImage that is downloadable from our <strong x-id="1"><a href="https://github.com/premid/linux/releases">Linux repository</a></strong>.
<em x-id="3">Warning: the package in the <strong x-id="1">AUR</strong> repository is not maintained by us (as PreMiD organization), but by other people.</em>

### Port binding
You should know that <strong x-id="1">PreMiD</strong> binds itself to the port <strong x-id="1">3020</strong>. This is necessary for the Extension and the Application communicate. If <strong x-id="1">PreMiD</strong> shows you an error about this port, you should check if something is binded to the 3020 port by running <code>sudo lsof -i:3020</code> or <code>sudo netstat -tnlp | grep :3020</code> in your terminal. If some process is binded to it you should make sure to free the port and try running <code>PreMiD</code> again.

### PreMiD's AppImage doesn't launch at login
As we stated in our **Linux repository**, AppImage can't be launched at login. You can add it to autostart manually by doing these steps:
1. Make a file named <strong x-id="1">rc.local</strong> in the <code>/etc</code> directory.
2. Open this file in your favourite editor and paste given code with changing some things:
```bash
#!/bin/bash
# Required to run as /bin/bash (if you use zsh etc. you can change it.)

# Example: /home/PreMiD/PreMiD*.AppImage
<directory to appimage>/PreMiD*.AppImage

exit 0
```
3. Save file and chmod it as executable `sudo chmod a+x /etc/rc.local`.
4. Restart your PC and PreMiD AppImage should launch at login.

<a name="macos"></a>

# Solução de problemas no MacOS
### Error creating directory
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

If you get this error, it means that your account doesn't have Administrator permissions and you need to create folder manually by doing these steps:
1. Open finder and open **Applications** folder.
2. Right-click on blank space and click **Create folder**.
3. To this folder assign `PreMiD` name (remember about upper-cased letters).
4. Open installer again.

# Isso não resolveu o meu problema
Please create a new post in [#support](https://discord.com/channels/493130730549805057/1019726199494279248).
