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

La versión `2.x` introduce la [tienda de presences](https://premid.app/store). Los usuarios ahora tienen la capacidad de añadir y eliminar manualmente sus presences favoritas a través de la interfaz de usuario del [sitio web](https://premid.app/).

> Antes de empezar es muy recomendable que mires nuestras pautas para presences. 
> 
> {.is-warning}

- [Directrices](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# Estructura

Las Presence están programadas en [TypeScript](https://www.typescriptlang.org/). [TypeScript](https://www.typescriptlang.org/) tiene algunos tipos definiciones más que JavaScript, así que corregir e identificar errores es mucho más fácil.

## Requisitos

1. [Git](https://git-scm.com/)
2. [Node](https://nodejs.org/en/) (viene con [npm](https://www.npmjs.com/))

## Clonando el proyecto

1. Abre la consola y escribe `git clone https://github.com/PreMiD/Presences`.
2. Escoge una carpeta a tu gusto.
3. Ábrelo en tu editor de código.

## Empezando

1. Abrir una terminal en la carpeta `Presences`
2. Instala las dependencias del repositorio usando `npm i` (O tu gestor de paquetes preferido)

### Creando una Presence
1. Ejecuta `npx pmd` (o `pmd` con tu gestor de paquetes preferido)
2. Seleccione la primera opción
3. Completa todas las preguntas

### Compilar / Modificar una Presence
1. Ejecuta `npx pmd`
2. Selecciona la segunda opción
3. Introduce el nombre de la Presence que quieres editar > Comenzará un compilador TypeScript en el directorio de la Presence, recargando automáticamente cuando edites el código del archivo `presence.ts`.
{.is-info}

Para inspiración o ejemplos sobre cómo estructurar el código de la Presence, echa un vistazo a Presences existentes como 1337x o 9GAG

Para más información acerca la clase `Presence` pulsa [aquí](/dev/presence/class).

Desde v2.2.0 puedes usar "Slideshows", esto te permite mostrar múltiples interfaces `PresenceData` en un intérvalo, para más información sobre la clase `Slideshow` haz clic [aquí](/dev/presence/slideshow).

## ¡¿No puedes obtener ciertos datos?!

Muchos sitios web utilizan [iframes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)). Estas etiquetas pueden contener múltiples fuentes, como vídeos. Pero no siempre son relevantes. Algunos están ocultos o simplemente no se usan. Comprueba si puedes extraer la información que necesitas sin ellos antes de trabajar de más.

1. Comprueba si existen en la consola de tu navegador (asegúrate de que estás en la pestaña **Elementos**).
2. Buscar (<kbd>CTRL</kbd> + <kbd>F</kbd> (Windows) o <kbd>CMD</kbd> + <kbd>F</kbd> (MacOS)).
3. Ejecuta `document.querySelectorAll("iframe")`.

Si los datos que necesitas están en un iFrame, debes hacer lo siguiente:

1. Crea un archivo `iframe.ts`.
2. Establece iFrame a `true` en tu archivo de metadatos.
3. Completando el archivo iFrame.

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

# Cargando la Presence

1. Abre la extensión y mantén pulsado el botón <kbd>Shift</kbd> de tu teclado.
2. Aparecerá **Cargar Presence** en la sección Presences.
3. Haz clic mientras mantienes pulsado el botón <kbd>Shift</kbd>.
4. Selecciona la carpeta /dist de tu presence.

# Algunos consejos útiles

## Recarga en caliente

El sitio web sobre el que estás desarrollando se recarga de forma automática cada vez que actualizas un archivo de la carpeta.

## Depurando

- Puedes poner `console.log("Prueba");` entre tu código y ver si se muestra en la consola de tu navegador. Si es así sigue y vuelve a intentarlo después de la siguiente función. Si no es así, hay un error arriba.
- Si eso no te ayuda pide ayuda a un desarrollador de presences en nuestro [servidor de Discord](https://discord.premid.app/).

# Explicación de archivos

- [Clase Presence](/dev/presence/class)
- [Clase Slideshow](/dev/presence/slideshow)
- [Clase de iFrame](/dev/presence/iframe)
- [Archivo de Metadata](/dev/presence/metadata)
- [Configuración de TypeScript](/dev/presence/tsconfig ""){.links-list}
