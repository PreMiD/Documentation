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

La versión `2.x` introduce la [Tienda de Presences](https://premid.app/store). Los usuarios ahora tienen la capacidad de añadir y eliminar manualmente sus presences favoritas a través de la interfaz de usuario del [sitio web](https://premid.app/).

> Antes de empezar es muy recomendable que mires nuestras reglas para presences. 
> 
> {.is-warning}

- [Reglas](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# Estructura

Todas las presences están programadas en [TypeScript](https://www.typescriptlang.org/). [TypeScript](https://www.typescriptlang.org/) tiene algunos tipos definiciones más que JavaScript, así que corregir e identificar errores es mucho más fácil.

## Requisitos

1. [Git](https://git-scm.com/)
2. Instala [Node](https://nodejs.org/en/) (viene con [npm](https://www.npmjs.com/))

## Clonando el proyecto

1. Abre la consola y escribe `git clone https://github.com/PreMiD/Presences`.
2. Escoge una carpeta a tu gusto.
3. Ábrelo en tu editor de código.

## Para empezar

1. Abre una nueva terminal en la carpeta `Presences`
2. Instala las dependencias del repositorio usando `npm i` (o el administrador de paquetes de tu elección)

### Creando una Presence
1. Ejecuta `npx pmd` (o ejecuta`pmd` con el administrador de paquetes de tu elección)
2. Selecciona la primera opción
3. Completa todas las preguntas solicitadas

### Compilar / Modificar una Presence
1. Ejecuta `npx pmd`
2. Selecciona la segunda opción
3. Introduce el nombre de la Presence que quieres editar > Comenzará un compilador TypeScript en el directorio de la Presence, recargando automáticamente cuando edites el código del archivo `presence.ts`.
{.is-info}

Para obtener inspiración o ejemplos sobre cómo estructurar el código de tu presence, echa un vistazo a las presences que ya existen como lo son 1337x o 9GAG.

Para más información sobre la clase ` Presence `, haz clic [ aquí ](/dev/presence/class).

Desde v2.2.0 puedes usar "Slideshows", esto te permite mostrar múltiples interfaces `PresenceData` en un intérvalo, para más información sobre la clase `Slideshow` haz clic [aquí](/dev/presence/slideshow).

## ¿¡No puedes obtener cierta información!?

Muchos sitios web están utilizando [ iframes ](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)). Estas etiquetas html pueden contener múltiples fuentes, como videos. Pero no son revelantes siempre. Algunos están ocultos o simplemente no se usan. Comprueba si puedes extraer la información que necesitas sin ellos antes de hacer trabajo innecesario.

1. Verifícalos en la consola de tu navegador (asegúrate de estar en la pestaña **Elementos**).
2. Buscar (<kbd>CTRL</kbd> + <kbd>F</kbd> (Windows) o <kbd>CMD</kbd> + <kbd>F</kbd> (MacOS)).
3. Ejecuta `document.querySelectorAll("iframe")`.

Si los datos que necesitas están en un iFrame, debes hacer lo siguiente:

1. Crea un archivo `iframe.ts`.
2. Establece iFrame en `true` en tu archivo metadata.
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

4. Configurando la presence para recibir datos del archivo iFrame.

```ts
presence.on("iFrameData", data => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

**Nota:** Esto debe ubicarse fuera del evento updateData.

# Cargando tu Presence

1. Abre la extensión en tu navegador y mantén presionado el botón <kbd>Shift</kbd> en tu teclado.
2. Aparecerá **Cargar Presence** en la sección Presences.
3. Haz clic mientras mantienes pulsado el botón <kbd>Shift</kbd>.
4. Selecciona la carpeta /dist de tu presence.

# Algunos consejos útiles

## Recarga rápida

El sitio web sobre el que estás desarrollando se recarga de forma automática cada vez que actualizas un archivo de la carpeta.

## Depurando

- Puedes poner `console.log("Prueba");` en tu código y ver si se muestra en la consola de tu navegador. Si es así, entonces sigue y vuelve a intentarlo después de la siguiente función. Si no es así, hay un error arriba.
- Si eso no te ayuda, pide ayuda a un desarrollador de presences en nuestro [servidor de Discord](https://discord.premid.app/).

# Explicación de archivos

- [Clase de Presence](/dev/presence/class)
- [Clase Slideshow](/dev/presence/slideshow)
- [Clase de iFrame](/dev/presence/iframe)
- [Archivo de Metadata](/dev/presence/metadata)
- [Configuración de TypeScript](/dev/presence/tsconfig ""){.links-list}
