---
title: Solución de problemas
description: Todo para resolver tu problema
published: true
date: 2021-02-08T21:30:58.603Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:03:54.865Z
---

> ¡Asegúrate de tener la extensión **y** aplicación instaladas! 
> 
> {.is-warning}

Incluido en esta página:
1. [Solución general de problemas](https://docs.premid.app/troubleshooting#general)
2. [Solución de problemas para Linux](https://docs.premid.app/troubleshooting#linux)
3. [Solución de problemas para MacOS](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# Solución general de problemas
> Si no estás seguro de cómo seguir estos pasos, ¡Siéntete libre de abrir un ticket en [#support](https://discord.premid.app/) y uno de nuestros agentes de soporte te ayudará! 
> 
> {.is-info}
### Recarga la página
Puedes presionar <kbd>CTRL+R</kbd>/<kbd>F5</kbd> (Windows) o <kbd>CMD+R</kbd> (MacOS) en tu teclado en vez de buscar el botón de recargar.

### ¿Estás usando la aplicación de Discord?
PreMiD **no** funciona en la versión web de Discord, debes descargar la aplicación [aquí](https://discord.com/download).

### Asegúrate de haber habilitado el estado de actividad en los ajustes de Discord
**Ajustes de usuario** > **Estado de actividad**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### Asegúrate de que Discord NO se esté ejecutando como administrador
Muy importante. Discord RPC no funcionará si ejecutas Discord como administrador.

### ¿Estás usando una presence con configuraciones?
Muchas presences (Incluyendo `Twitch` y `SoundCloud`) son afectadas por un problema de la extensión. Este error causa que la extensión no agarre los valores predeterminados de las configuraciones apropiadamente.

Para resolver esto lo único que debes hacer es desactivar y activar nuevamente la configuración de la parte superior:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Reinicia tu navegador
<kbd>Alt</kbd> + <kbd>F4</kbd> (Windows) o <kbd>CMD</kbd> + <kbd>Q</kbd> (MacOS) también funciona. (Tienes que iniciar el navegador nuevamente, obvio.)

### Reinicia PreMiD (Aplicación)
<img src="https://i.imgur.com/wQA15xu.png" width="500px" style="max-width:100%;" />
Luego tienes que reiniciar PreMiD.

### Recarga/Reinicia Discord
Presiona <kbd>Ctrl + R</kbd> (Windows) o <kbd>CMD + R</kbd> (MacOS) en tu teclado o reinicia Discord manualmente.

### Comprueba si tienes antivirus o firewall ejecutándose en el ordenador
A veces los antivirus o cortafuegos pueden bloquear aplicaciones que están creando/alojando servidores o que se están conectando a internet. Utilizamos un servidor local para recibir y pasar los datos entre la aplicación y la extensión, por lo tanto no podrás utilizar PreMiD si bloqueas la habilidad de pasar datos entre ellos.

### Deshabilita tus complementos
Deshabilita todos tus complementos y verifica si funciona. Si es así , ve habilitando los complementos uno por uno e indícanos cuál es el que causa la incompatibilidad con PreMiD.

### Reiniciar tu computadora
Espero que sepa cómo reiniciar una computadora.

### Reinstalando PreMiD
A veces hay algún problema con los archivos... Los tutoriales para la instalación se pueden encontrar [aquí](/install/).

### Eliminación manual
Windows: Escribe `%appdata%` y elimina la carpeta `PreMiD`. MacOS: `~/users/USER/~Library/Application Support/` and delete the `PreMiD` folder.

### McAfee detectó a PreMiD como un virus (Windows)
Esto es un falso positivo de McAfee y les hemos informado del problema, por ahora puedes excluir a PreMiD del escaneo haciendo lo siguiente:

> Si no estás seguro de cómo seguir estos pasos, ¡Siéntete libre de abrir un ticket en [#support](https://discord.premid.app/) y uno de nuestros agentes de soporte te ayudará! 
> 
> {.is-warning}

1. Abre la aplicación McAfee y haz clic en el icono de configuración en la parte superior derecha. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. Haz clic en "Artículos en Cuarentena" (Segunda opción desde arriba).
3. Expándelo y pulsa sobre el icono `>` antes de un elemento con el nombre "settings.dat".
4. Asegúrate de que la ruta incluye "AppData\Local\Temp\PreMiD", si es así, selecciónala y pulsa "restaurar". <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. Después de restaurarlo puedes cerrar la ventana emergente "Elementos en Cuarentena", luego pulsa de nuevo sobre el icono de configuración en la parte superior derecha.
6. Haz clic en "Escaneo en tiempo real" (Tercero desde arriba).
7. Amplíalo y haz clic en "Añadir archivo".
8. Escriba "%appdata%" en la barra de URL del administrador de archivos y presiona Enter. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. Abre la carpeta "PreMiD" y selecciona el archivo "PreMiD.exe" y haz clic en abrir. <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. Ahora McAfee debe ignorar nuestro archivo, sólo tienes que abrir nuestra aplicación.

### ¡Estado de PreMiD bugeado en discord!
No te preocupes. Presiona <kbd>CTRL+R</kbd> (en Windows) o <kbd>CMD+R</kbd> (en MacOS) en tu teclado mientras estás en Discord para recargarlo.

<a name="linux"></a>

# Solución de problemas para Linux
### Distribuciones basadas en Ubuntu/Debian
If you have downloaded Discord through Snapcraft, RPC will not work. You have to uninstall the Snapcraft version by executing `sudo snap remove discord` on a terminal, download **[Discord's Linux build](https://discordapp.com/api/download?platform=linux)** (**[or Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), then navigating to the directory you downloaded Discord to (usually `$HOME/Downloads`), then installing the package using `sudo dpkg -i discord-*.deb`. Si la AppImage no funciona, deberías revisar nuestros otros paquetes en **[este enlace ](https://packagecloud.io/premid/linux)**.

### Distribuciones basadas en Arch Linux
Distribuciones basadas en Arch Linux deben usar el paquete AUR (Arch User Repository) llamado <code>premid</code> o <code>premid-git</code> (<em x-id="3">ADVERTENCIA: Este repositorio compila PreMiD desde el código fuente</em>). Si no quieres instalar un administrador AUR (yay, etc.), puedes revisar nuestra AppImage y descargarla desde nuestro <strong x-id="1"><a href="https://github.com/premid/linux/releases">repositorio de Linux</a></strong>.
<em x-id="3">Warning: the package in the <strong x-id="1">AUR</strong> repository is not maintained by us (as PreMiD organization), but by other people.</em>

### Enlace de puerto
You should know that <strong x-id="1">PreMiD</strong> binds itself to the port <strong x-id="1">3020</strong>. This is necessary for the Extension and the Application communicate. If <strong x-id="1">PreMiD</strong> shows you an error about this port, you should check if something is binded to the 3020 port by running <code>sudo lsof -i:3020</code> or <code>sudo netstat -tnlp | grep :3020</code> in your terminal. If some process is binded to it you should make sure to free the port and try running <code>PreMiD</code> again.

### La AppImage de PreMiD no se inicia al iniciar sesión
As we stated in our **Linux repository**, AppImage can't be launched at login. You can add it to autostart manually by doing these steps:
1. Crea un archivo llamado <strong x-id="1">rc.local</strong> en el directorio <code>/etc</code>.
2. Abre este archivo en tu editor favorito y pega el siguiente código con algunas modificaciones:
```bash
#!/bin/bash
# Requerido para ejecutar como /bin/bash (si usas zsh etc. puedes cambiarlo.)

# Ejemplo: /home/PreMiD/PreMiD*.AppImage
<directorio a la appimage>/PreMiD*.AppImage

exit 0
```
3. Guarda el archivo y asígnalo como ejecutable `sudo chmod a+x /etc/rc.local`.
4. Reinicia el PC, la AppImage de PreMiD debería iniciarse al iniciar sesión.

<a name="macos"></a>

# Solución de problemas para MacOS
### Error al crear el directorio
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

If you get this error, it means that your account doesn't have Administrator permissions and you need to create folder manually by doing these steps:
1. Abre el buscador y abre la carpeta **Aplicaciones**.
2. Haz clic derecho en un espacio en blanco y haz clic en **Crear carpeta**.
3. Nombra a esta carpeta `PreMiD` (debes mantener las letras mayúsculas).
4. Vuelve a abrir el instalador.

# Esto no ha resuelto mi problema
Por favor abre un ticket en [#support](https://discord.premid.app/).
