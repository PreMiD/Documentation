---
title: Desarrollo de presences
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:02.843Z
---

> Todas las presences ahora se almacenan aquí: https://github.com/PreMiD/Presences 
> 
> {.is-info}

La versión `2.x` introduce la [tienda de presences](https://premid.app/store). Los usuarios ahora tienen la capacidad de añadir y eliminar manualmente sus presences favoritas a través de la interfaz de usuario del [sitio web](https://premid.app/).

> Antes de empezar es muy recomendable que mires nuestras reglas para presences. 
> 
> {.is-warning}

- [Reglas](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# Estructura

Toda presence está programada en [TypeScript](https://www.typescriptlang.org/). [TypeScript](https://www.typescriptlang.org/) tiene algunos tipos definiciones más que JavaScript, así que corregir e identificar errores es mucho más fácil.

## Instalación

1. Instala [Git](https://git-scm.com/).
2. Instala [Node](https://nodejs.org/en/) (viene con [npm](https://www.npmjs.com/)).
3. Instala [TypeScript](https://www.typescriptlang.org/index.html#download-links) (abre la consola y escribe `npm install -g typescript`).

## Clonando el proyecto

1. Abre la consola y escribe `git clone https://github.com/PreMiD/Presences`.
2. Escoge una carpeta a tu gusto.
3. Ábrelo en tu editor de código.

## Creando carpetas y archivos

1. Ve a la carpeta `websites` y luego a la carpeta con la primera letra del **nombre** (no una URL) del servicio que deseas dar soporte.
2. Cree una carpeta con el **nombre** (no una URL) del servicio que desea soportar.
3. Crea un archivo de `presence.ts` y `tsconfig.json` dentro.
4. Cree una carpeta llamada `dist` en su interior.
5. Cree un archivo `metadata.json` dentro de la carpeta `dist`.

## Completando el archivo tsconfig.json

Por favor, introduzca el siguiente código dentro del archivo `tsconfig.json`.

```json
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

Para obtener más información sobre la configuración de TypeScript haga clic [aquí](/dev/presence/tsconfig).

## Completando el archivo metadata.json

Hemos hecho un generador de archivos `metadata.json` [aquí](https://eggsy.xyz/projects/premid/mdcreator) para la gente perezosa. Aún así se sugiere leerlo para que sepas cómo funciona.

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.6",
  "author": {
    "name": "USER",
    "id": "ID"
  },
  "contributors": [
    {
      "name": "USER",
      "id": "ID"
    }
  ],
  "service": "SERVICE",
  "altnames": ["SERVICE"],
  "description": {
    "en": "DESCRIPTION"
  },
  "url": "URL",
  "version": "VERSION",
  "logo": "URL",
  "thumbnail": "URL",
  "color": "#HEX000",
  "tags": ["TAG1", "TAG2"],
  "category": "CATEGORY",
  "regExp": "REGEXP",
  "iFrameRegExp": "REGEXP",
  "iframe": false,
  "readLogs": false,
  "settings": [
    {
      "id": "ID",
      "multiLanguage": true
    },
    {
      "id": "ID",
      "title": "DISPLAY TITLE",
      "icon": "FONTAWESOME ICON",
      "value": true
    },
    {
      "id": "ID",
      "if": {
        "ID": true
      },
      "title": "DISPLAY TITLE",
      "icon": "FONTAWESOME ICON",
      "value": "\"%song%\" by %artist%",
      "placeholder": "use %song% or %artist%"
    },
    {
      "id": "ID",
      "title": "DISPLAY TITLE",
      "icon": "FONTAWESOME ICON",
      "value": 0,
      "values": ["1", "2", "etc."]
    }
  ]
}
```

Por favor copia el código anterior y ponlo en tu archivo `metadata.json`. Ahora necesitas saber los valores de las propiedades. Ten en cuenta que las siguientes propiedades para poner en tu archivo `metadata.json` son opcionales, si no tienes planeado usarlas necesitas eliminarlos.

- `contributors`
- `altnames`
- `regExp`
- `iframe`
- `iFrameRegExp`
- `readLogs`
- `settings`

**Aclarando unos valores predefinidos:**

<table>
  <thead>
    <tr>
      <th style="text-align:left">Variable</th>
      <th style="text-align:left">Descripción</th>
      <th style="text-align:left">Tipo</th>
      <th style="text-align:left">Opcional</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>author</b></td>
      <td style="text-align:left">Debe contener un Object con <code>name</code> e <code>id</code> del desarrollador de la presence. <code>nombre</code> es su nombre de usuario de Discord sin el identificador(#0000). El <code>id</code> del usuario se puede copiar de Discord habilitando el modo desarrollador y haciendo clic derecho en su perfil.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>No</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>contributors</b></td>
      <td style="text-align:left">Debería contener un Object con las propiedades <code>name</code> e <code>id</code> del desarrollador de la presence. <code>nombre</code> es su nombre de usuario de Discord sin el identificador(#0000). El <code>id</code> del usuario se puede copiar de Discord habilitando el modo desarrollador y haciendo clic derecho en su perfil.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Sí</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>service</b></td>
      <td style="text-align:left">El título del servicio que soporta esta presence.<br>
      (Debe ser el mismo nombre que la carpeta donde está todo)</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>No</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>altnames</b></td>
      <td style="text-align:left"><br>Destinado a ser utilizado para presences que tienen nombres diferentes en diferentes idiomas (p. ej., Pokémon y 포켓몬스터)<br>También puedes usarlo para presences con caracteres especiales y así no tendrás que escribirlos (p. ejemplo., Pokémon y Pokemon).</td>
      <td style="text-align:left"><code>Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Sí</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>description</b></td>
      <td style="text-align:left">Una pequeña descripción de la presence, puedes usar la descripción del servicio si no se te ocurre nada. Tu descripción debe contener tuplas de valores, indicando el idioma y la descripción en dicho idioma. Escribe descripciones en los idiomas <i>que tu conozcas</i>, nuestros traductores realizarán cambios en tu archivo metadata.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>No</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>url</b></td>
      <td style="text-align:left">URL del servicio. <br><b>Ejemplo:</b><code>vk.com</code><br>
        <b>Esta URL debe coincidir con la URL del sitio web ya que se detectará si es o no el sitio web al que se inyecta el script.</b><br><b>NO</b> agregues <code>https://</code> o <code>http://</code> dentro de la URL ni un slash al final:
<code>https://premid.app/</code> -> <code>premid.app</code><br>
<b>Nota</b>: Algunas URLs pueden tener <code>www.</code> o algo parecido delante de su dominio. ¡<b>NO</b> olvides añadirlo!<br>
Puedes añadir múltiples URLs haciendo lo siguiente:<br>
<code>["URL1", "URL2", "ETC."]</code><br>
También podrías usar regExp (También conocido como Regex), las cuales son explicadas más adelante.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>No</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>regExp</b></td>
      <td style="text-align:left">Una expresión regular es para buscar URLs<br>
      expresiones regulares, también llamadas Regex, puedes ser usadas en sitios webs con múltiples subdominios.<br>
Puedes usar la siguiente expresión regular para eso:<br>
<code>([a-z0-9]+)[.]domain[.]TLD"</code><br>
TLD significa Top Level Domain, por ejemplo: .com .net<br>
<code>([a-z0-9]+)</code> significa cualquier cosa de la A a la Z y desde el 0 al 9.<br>
        Puedes pegar un vistazo rápido a este <a href="https://youtu.be/sXQxhojSdZM">video</a> para tener una idea de cómo funciona<br>
        Puedes probar tu expresión regular en <a href="https://regex101.com/">Regex101</a>.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Sí</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>version</b></td>
      <td style="text-align:left">Versión de su presence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>No</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logo</b></td>
      <td style="text-align:left">Enlace al logotipo del servicio.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>No</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>thumbnail</b></td>
      <td style="text-align:left">Enlace a la miniatura de su presence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>No</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>color</b></td>
      <td style="text-align:left">Valor <code>#HEX</code>. Recomendamos usar un color primario del servicio
        que su presence soporte.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>No</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>tags</b></td>
      <td style="text-align:left">Array con etiquetas, ayudarán a los usuarios a buscar su presence en el sitio web.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>No</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">Un string que representa la categoría a la que pertenece la presence. Mira las categorías válidas <a href="https://docs.premid.app/dev/presence/metadata#presence-categories">aquí</a>.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>No</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iframe</b></td>
      <td style="text-align:left">Define si se utilizan <code>iFrames</code>.</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Sí</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iFrameRegExp</b></td>
      <td style="text-align:left">Un selector de expresiones regulares que selecciona los iframes en donde inyectar. Mira expresiones regulares para más información.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Sí</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readLogs</b></td>
      <td style="text-align:left">Define si la extensión debe leer registros.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Sí</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>settings</b></td>
      <td style="text-align:left">Un array con configuraciones del usuario puede cambiar.<br>
      Lee más acerca configuración de presencias <a href="https://docs.premid.app/dev/presence/metadata#presence-settings">aquí</a>.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Sí</code></td>
    </tr>
  </tbody>
</table>

## Empezando

```ts
const presence = new Presence({
  //The client ID of the Application created at https://discordapp.com/developers/applications
  clientId: "000000000000000000"
  }),
  //You can use this to get translated strings in their browser language
  strings = presence.getStrings({
    play: "presence.playback.playing",
    pause: "presence.playback.paused"
  });

/*
function myOutsideHeavyLiftingFunction(){
    //Grab and process all your data here

    // element grabs //
    // api calls //
    // variable sets //
}

setInterval(myOutsideHeavyLiftingFunction, 10000);
//Run the function separate from the UpdateData event every 10 seconds to get and set the variables which UpdateData picks up
*/

presence.on("UpdateData", async () => {
  /*UpdateData is always firing, and therefore should be used as your refresh cycle, or `tick`. Esto se llama varias veces por segundo cuando es posible.

    It is recommended to set up another function outside of this event function which will change variable values and do the heavy lifting if you call data from an API.*/

  const presenceData: PresenceData = {
    //The large image on the presence. This can be a key of an image uploaded on the Discord Developer Portal - Rich Presence - Art Assets, or a URL to an image
    largeImageKey: "key",
    //The small image on the presence. This can be a key of an image uploaded on the Discord Developer Portal - Rich Presence - Art Assets, or a URL to an image
    smallImageKey: "https://mycrazywebsite.com/coolImage.png",
    //The text which is displayed when hovering over the small image
    smallImageText: "Some hover text",
     //The upper section of the presence text
    details: "Browsing Page Name",
    //The lower section of the presence text
    state: "Reading section A",
    //The unix epoch timestamp for when to start counting from
    startTimestamp: 3133657200000,
    //If you want to show Time Left instead of Elapsed, this is the unix epoch timestamp at which the timer ends
    endTimestamp: 3133700400000
    //Optionally you can set a largeImageKey here and change the rest as variable subproperties, for example presenceData.type = "blahblah"; type examples: details, state, etc.
  };
  //Update the presence with all the values from the presenceData object
  if (presenceData.details) presence.setActivity(presenceData);
  //Update the presence with no data, therefore clearing it and making the large image the Discord Application icon, and the text the Discord Application name
  else presence.setActivity();
});
```

Puedes copiar esto dentro de tu archivo `presence.ts` y editar los valores. La configuración de todos los valores se hace dentro del evento updateData.

Para ejemplos sugerimos que mires el código de presences como: 1337x o 9GAG. Para más información sobre la clase ` Presence `, haga clic [ aquí ](/dev/presence/class).

Desde la v2.2.0 ahora hay Slideshows, esto le permite mostrar múltiples interfaces de la `PresenceData` en un intervalo, para más información sobre la clase `Slideshow` haz clic [aquí](/dev/presence/slideshow).

## ¿¡No puedes obtener cierta información!?

Muchos sitios web están utilizando [ iframes ](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)). Estas etiquetas html pueden contener múltiples fuentes, como videos. Pero no son revelantes siempre. Algunos están ocultos o simplemente no se usan activamente. Compruebe si puede extraer la información que necesita sin ellos antes de realizar un trabajo innecesario.

1. Verifícalos en la consola de tu navegador (asegúrate de estar en la pestaña **Elementos**).
2. Buscar (<kbd> CTRL </kbd> + <kbd> F </kbd> (Windows) o <kbd> CMD </kbd> + <kbd> F </kbd> (MacOS)).
3. Ejecuta `document.querySelectorAll("iframe")`.

Si encuentras que los datos están en un iFrame, debes hacer lo siguiente:

1. Crea un archivo `iframe.ts`.
2. Establece iFrame a `true` en tu archivo de metadata.
3. Llenando tu archivo iFrame.

```ts
const iframe = new iFrame();
iframe.on("UpdateData", async () => {
  //Get all the data you need out of the iFrame save them in variables and then send them using iframe.send
  iframe.send({
    //sending data
    video: video,
    time: video.duration
  });
});
```

4. Configurando que el archivo de la presence reciba datos del archivo de iFrame.

```ts
presence.on("iFrameData", data => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

** Nota: ** Esto debe colocarse fuera del evento updateData.

## Compilando

Abre una consola en tu carpeta y escribe `tsc -w` para compilar `presence.ts` en la carpeta `/dist`.

# Cargando la presence

1. Abre la ventana emergente de la extensión y mantén pulsado el botón <kbd>Shift</kbd> de tu teclado.
2. **Cargar presence** aparecerá en la sección presences.
3. Haz clic en él mientras mantienes pulsado el botón <kbd>Shift</kbd>.
4. Selecciona la carpeta /dist de tu presence.

# Algunos consejos útiles

## Recarga rápida

El sitio web en el que estás desarrollando se recarga de forma automática cada vez que se actualiza un archivo de la carpeta.

## Depurando

- Puedes poner `console.log("Prueba");` entre tu código y ver si la consola de tu navegador te muestra "Prueba". Si es así entonces sigue y vuelve a intentarlo después de la siguiente función. Si no es así, hay un error arriba.
- Si eso no te ayuda entonces pide ayuda a un desarrollador de presences en nuestro [servidor de Discord](https://discord.premid.app/).

# Explicación de archivos

- [Clase de Presence](/dev/presence/class)
- [Clase SlideshowSlide](/dev/presence/slideshow)
- [Clase iFrame](/dev/presence/iframe)
- [Archivo de Metadata](/dev/presence/metadata)
- [Configuración de TypeScript](/dev/presence/tsconfig ""){.links-list}
