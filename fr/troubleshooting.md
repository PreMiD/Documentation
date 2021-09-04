---
title: Dépannage
description: Tout pour résoudre votre problème
published: true
date: 2021-02-08T21:30:58.603Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:03:54.865Z
---

> Assurez-vous d'avoir l'extension **et** l'application installée! 
> 
> {.is-warning}

Inclus sur cette page :
1. [Dépannage général](https://docs.premid.app/troubleshooting#general)
2. [Dépannage sur Linux](https://docs.premid.app/troubleshooting#linux)
3. [Dépannage sur MacOS](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# Dépannage général
> Vous pouvez utiliser [cet](https://qkeleq10.github.io/PreMiD-Troubleshooting/) outil pour vous aider à mieux cibler votre problème. 
> 
> {.is-info}
### Recharger la page
Vous pouvez aussi appuyer sur <kbd>CTRL+R</kbd>/<kbd>F5</kbd> (Windows) ou <kbd>CMD+R</kbd> (MacOS) sur votre clavier au lieu de rechercher le bouton de rafraîchissement.

### Utilisez-vous l'application Discord ?
PreMiD ne fonctionne **pas** avec la version navigateur de Discord, vous devez télécharger l'application [ici](https://discord.com/download).

### Assurez-vous d'avoir activé l'activité de jeu Discord dans les paramètres
**Paramètres utilisateur** > **Activité de jeu**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### Assurez-vous que Discord n'ai PAS été lancé en tant qu'administrateur
Really important. Discord RPC will not work if you run Discord as an administrator.

### Utilisez-vous une presence avec des paramètres ?
Many presences (including `Twitch` and `SoundCloud`) are affected by an extension issue. This issue causes the extension to not grab the default values of settings properly.

Pour résoudre ce problème, il vous suffit d'activer/désactiver le paramètre le plus haut :
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Redémarrez votre navigateur
<kbd>Alt</kbd>+<kbd>F4</kbd> (Windows) or <kbd>CMD</kbd>+<kbd>Q</kbd> (MacOS) does a good job too. (You have to start your browser again obviously.)

### Redémarrer PreMiD (l'application)
<img src="https://i.imgur.com/wQA15xu.png" width="500px" style="max-width:100%;" />
You have to restart PreMiD afterwards.

### Recharger/redémarrer Discord
Press <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) on your keyboard or restart Discord manually.

### Vérifiez si vous avez un antivirus ou un pare-feu en cours d'exécution sur votre ordinateur
Sometimes antivirus programs and firewalls are blocking applications which are creating/hosting servers or just connecting to the internet. We are using a local server to receive and pass data between our app and extension, so if you will block app's ability to pass data you probably will not be able to use PreMiD.

### Désactiver vos extensions
Disable all your addons and see if it works. If yes, try to enable your addons step-by-step and tell us which addon broke PreMiD.

### Redémarrez votre ordinateur
I hope you know how to restart a computer.

### Réinstallation de PreMiD
Sometimes there is something wrong with the files... Tutorials for the installation can be found [here](/install).

### Suppression manuelle
Windows: Write `%appdata%` on the file explorer and delete the `PreMiD` folder. MacOS: `~/users/USER/~Library/Application Support/` and delete the `PreMiD` folder.

### McAfee a détecté PreMiD comme un virus (Windows)
This is a false positive from McAfee and we have reported the issue to them, for now you can exclude PreMiD from the scan by doing the following steps:

> Si vous ne vous sentez pas confiant de prendre ces mesures, n'hésitez pas à faire un ticket dans [#support](https://discord.premid.app/) et l'un de nos agents de support pourra vous aider ! 
> 
> {.is-warning}

1. Ouvrez l'application McAfee et cliquez sur l'icône Paramètres en haut à droite. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. Cliquez sur "Objets en quarantaine" (Le second à partir du haut).
3. Développez-le, et cliquez sur l'icône `>` avant un élément avec le nom "settings.dat".
4. Assurez-vous que le chemin inclut "AppData\Local\Temp\PreMiD", si c'est le cas, sélectionnez-le et appuyez sur restore. <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. Une fois restauré, vous pouvez fermer la fenêtre pop-up "Éléments en quarantaine", puis appuyer à nouveau sur l'icône de paramètres en haut à droite.
6. Cliquez sur "Analyse en temps réel" (Troisième à partir du haut).
7. Développez-le et cliquez sur "Ajouter un fichier".
8. Tapez "%appdata%" dans la barre d'adresse du gestionnaire de fichiers et appuyez sur Entrer. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. Ouvrez le dossier "PreMiD", sélectionnez le fichier "PreMiD.exe" et cliquez sur Ouvrir. <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. McAfee devrait maintenant ignorer notre dossier, lancez simplement l'application et cela devrait marcher.

### Statut PreMiD buggé sur Discord !
Don't worry. Press the <kbd>CTRL+R</kbd> (Windows) or <kbd>CMD+R</kbd> (MacOS) keybind while focused on your discord window to reload it.

<a name="linux"></a>

# Dépannage sur Linux
### Distributions basées sur Ubuntu/Debian
If you have downloaded Discord through Snapcraft, RPC will not work. You have to uninstall the Snapcraft version by executing `sudo snap remove discord` on a terminal, download **[Discord's Linux build](https://discordapp.com/api/download?platform=linux)** (**[or Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), then navigating to the directory you downloaded Discord to (usually `$HOME/Downloads`), then installing the package using `sudo dpkg -i discord-*.deb`. If AppImage doesn't work, you should consider checking our other packages by **[this link](https://packagecloud.io/premid/linux)**.

### Distributions basées sur Arch Linux
Arch Linux based distros should use AUR (Arch User Repository) package that is named <code>premid</code> or <code>premid-git</code> (<em x-id="3">WARNING: This repository builds premid from our source code.</em>). If you don't want to install an AUR manager (yay etc.), you can check out our AppImage that is downloadable from our <strong x-id="1"><a href="https://github.com/premid/linux/releases">Linux repository</a></strong>.
<em x-id="3">Warning: the package in the <strong x-id="1">AUR</strong> repository is not maintained by us (as PreMiD organization), but by other people.</em>

### Liaison aux ports
You should know that <strong x-id="1">PreMiD</strong> binds itself to the port <strong x-id="1">3020</strong>. This is necessary for the Extension and the Application communicate. If <strong x-id="1">PreMiD</strong> shows you an error about this port, you should check if something is binded to the 3020 port by running <code>sudo lsof -i:3020</code> or <code>sudo netstat -tnlp | grep :3020</code> in your terminal. If some process is binded to it you should make sure to free the port and try running <code>PreMiD</code> again.

### L'AppImage de PreMiD ne se lance pas au démarrage
As we stated in our **Linux repository**, AppImage can't be launched at login. You can add it to autostart manually by doing these steps:
1. Créez un fichier nommé <strong x-id="1">rc.local</strong> dans le dossier <code>/etc/</code>.
2. Ouvrez ce fichier dans votre éditeur favori et collez-y le code suivant en modifiant le dossier dans lequel l'AppImage est située :
```bash
#!/bin/bash
# Nécessaire pour s'exécuter en tant /bin/bash (si vous utilisez zsh etc. vous pouvez le changer.)

# Exemple: /home/PreMiD/PreMiD*.AppImage
<directory to appimage>/PreMiD*.AppImage

exit 0
```
3. Sauvegardez le fichier et rendez le exécutable avec la commande `sudo chmod a+x /etc/rc.local`.
4. Redémarrez votre PC et l'AppImage de PreMiD devrait se lancer au démarrage.

<a name="macos"></a>

# Dépannage sur MacOS
### Erreur lors de la création du dossier
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

If you get this error, it means that your account doesn't have Administrator permissions and you need to create folder manually by doing these steps:
1. Ouvrez Finder et ouvrez le dossier **Applications**.
2. Faites un clic droit dans un espace vide et cliquez sur **Créer un dossier**.
3. Assignez le nom `PreMiD` à ce dossier (la casse est importante, n'oubliez pas les majuscules).
4. Réouvrez l'installateur.

# Cela n'a pas résolu mon problème
Please open a ticket in [#support](https://discord.premid.app/).
