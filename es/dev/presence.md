---
title: Desarrollo de Presences
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

Version `2.x` introduces the [Presence Store](https://premid.app/store). Los usuarios ahora tienen la capacidad de añadir y eliminar manualmente sus presences favoritas a través de la interfaz de usuario del [sitio web](https://premid.app/).

> Antes de empezar es muy recomendable que mires nuestras pautas para presences. 
> 
> {.is-warning}

- [Directrices](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# Estructura

All Presences are made using [TypeScript](https://www.typescriptlang.org/). [TypeScript](https://www.typescriptlang.org/) tiene algunos tipos definiciones más que JavaScript, así que corregir e identificar errores es mucho más fácil.

## Requisitos

1. [Git](https://git-scm.com/)
2. [Node](https://nodejs.org/en/) (comes with [npm](https://www.npmjs.com/))

## Clonando el proyecto

1. Abre la consola y escribe `git clone https://github.com/PreMiD/Presences`.
2. Escoge una carpeta a tu gusto.
3. Ábrelo en tu editor de código.

## Getting started

1. Open a new terminal in the `Presences` folder
2. Install repository dependencies using `npm i` (Or your package manager of choice)

### Creando una Presence
1. Run `npx pmd` (or run `pmd` with the package manager of your choice)
2. Select the first option
3. Fill in all prompted questions

### Compilar / Modificar una Presence
1. Run `npx pmd`
2. Select the second option
3. Introduce el nombre de la Presence que quieres editar > Comenzará un compilador TypeScript en el directorio de la Presence, recargando automáticamente cuando edites el código del archivo `presence.ts`.
{.is-info}

For inspiration or examples on how to structure your Presence's code, take a look at existing Presences like 1337x or 9GAG

For more information about the `Presence` class click [here](/dev/presence/class).

Desde v2.2.0 puedes usar "Slideshows", esto te permite mostrar múltiples interfaces `PresenceData` en un intérvalo, para más información sobre la clase `Slideshow` haz clic [aquí](/dev/presence/slideshow).

## Can't get certain data?!

A lot of websites are using [iframes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)). These html tags can contain multiple sources such as videos. But they're not relevant every time. Algunos están ocultos o simplemente no se usan. Comprueba si puedes extraer la información que necesitas sin ellos antes de trabajar de más.

1. Check for them in your browsers console (be sure that you are on the **Elements** tab).
2. Buscar (<kbd>CTRL</kbd> + <kbd>F</kbd> (Windows) o <kbd>CMD</kbd> + <kbd>F</kbd> (MacOS)).
3. Ejecuta `document.querySelectorAll("iframe")`.

Si los datos que necesitas están en un iFrame, debes hacer lo siguiente:

1. Create a `iframe.ts` file.
2. Set iFrame to `true` in your metadata file.
3. Filling in your iFrame file.

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

4. Configurando la presence para recibir datos del archivo iFrame.

```ts
presence.on("iFrameData", (data) => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

**Nota:** Esto debe ubicarse fuera del evento updateData.

# Loading your Presence

1. Abre la extensión y mantén pulsado el botón <kbd>Shift</kbd> de tu teclado.
2. Aparecerá **Cargar Presence** en la sección Presences.
3. Haz clic mientras mantienes pulsado el botón <kbd>Shift</kbd>.
4. Selecciona la carpeta /dist de tu presence.

# Algunos consejos útiles

## Hot-reloading

El sitio web sobre el que estás desarrollando se recarga de forma automática cada vez que actualizas un archivo de la carpeta.

## Debugging

- Puedes poner `console.log("Prueba");` entre tu código y ver si se muestra en la consola de tu navegador. Si es así sigue y vuelve a intentarlo después de la siguiente función. Si no es así, hay un error arriba.
- Si eso no te ayuda pide ayuda a un desarrollador de presences en nuestro [servidor de Discord](https://discord.premid.app/).

# Explicación de archivos

- [Clase Presence](/dev/presence/class)
- [Clase Slideshow](/dev/presence/slideshow)
- [Clase de iFrame](/dev/presence/iframe)
- [Archivo de Metadata](/dev/presence/metadata)
- [Configuración de TypeScript](/dev/presence/tsconfig ""){.links-list}
