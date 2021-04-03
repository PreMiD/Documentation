---
title: Normas de las Presence
description: Reglas que todos los desarrolladores de presences deben seguir para que su presence sea añadida.
published: true
date: 2021-03-06T15:01:04.274Z
tags:
editor: markdown
dateCreated: 2021-02-26T21:54:41.573Z
---

<div align="center">
    <img src="https://github.com/PreMiD.png?size=2048" width="128px" style="max-width:100%;">
    <h3 style="font-size: 2rem; margin-bottom: 0">Normas de las presence</h3>
    <h4 style="margin-top: 0">Revisión 3</h4>
    <br />
</div>

# Directrices

Al publicar Presences en [nuestro repositorio de GitHub](https://github.com/PreMiD/Presences), necesitamos que sigas un conjunto de reglas. Para algunos, estás reglas pueden parecer estrictas. Sin embargo, la implementación de estos conjuntos de reglas nos impedirá a nosotros y a los usuarios encontrarse con cualquier problema.

# Creación

Las reglas generales del desarrollo de una presence son las siguientes:

- Las presences **deben** estar relacionadas con el sitio web que has elegido.
- Las presences **no pueden** ser para sitios ilegales. (Por ejemplo: Stressors, marketing de drogas, pornografía infantil, etc.)
- La estructura de los archivos debe ser limpia y gestionada, no incluyas archivos que no estén especificados. (Por ejemplo: Vscode y capetas git, imágenes y archivos de texto, etc.)
- Necesitas tener una estructura de archivo adecuada, los borradores **no** están permitidos.
- Presences para sitios web con TLDs (dominios de nivel superior) `.onion` o sitios web con dominios/hosts gratuitos (por ejemplo, `.TK` [todos los dominios Freenom gratuitos], `.RF`, `GD`, etc.) ** no ** están permitidos, se pueden hacer excepciones si se presentan pruebas de que se ha pagado por el dominio.
- El dominio de la presence debe tener al menos una antigüedad de 2 meses.
- Presences que tienen como destino páginas internas del navegador (como Chrome Web Store, `chrome://`, páginas `about:`, etc.) **no** están permitidas ya que requieren que se habilite una configuración experimental en el lado del usuario y podría causar daños al navegador.
- Las presences con soporte para un solo subdominio **no** se permitirán, ya que pueden parecer rotas para otras páginas (como la página de inicio), se pueden hacer excepciones para la política y las paginas de contacto (contenido que no se usa con frecuencia) o sitios donde el otro contenido no este relacionado. (por ejemplo, páginas de wikia)
- Las presences para radios en línea sólo están permitidas si la radio tiene al menos 100 oyentes semanales y 15 simultáneos. Además de esto debe tener alguna características extra aparte de mostrar el título del álbum/canción, etc.
- Las presences de baja calidad (o las que tienen poco contexto) ** no ** están permitidas (p. ej., mostrar solo un logotipo y texto pero nunca volver a cambiarlo)
- Requerimos algunas pautas con el lanzamiento de los `buttons`:
  - No están permitidas redirecciones a páginas de inicio.
  - No está permitido promover sitios web por medio de ello.
  - No puede mostrar información adicional cuando esta no puede ser mostrada en las propiedades `state` o `details`.
- Presences para servicios como listas de bots/servidores de Discord deben seguir estos requisitos adicionales:
  - El dominio debe tener al menos **6 meses** de antigüedad.
  - Visitas únicas por día:
    - Para dominios de 6 meses de antigüedad: **20.000 visitas únicas por día**.
    - Para dominios de 12 meses o más de antigüedad: **45.000 visitas únicas por día**.
  - El sitio web no puede estar en un dominio barato como `.xyz` o `.club`.
  - El sitio web debe tener una muy buena calidad, diseño, etc.
- Incluyendo la carpeta `dist` y los archivos `presence.ts`, `iframe.ts` y `metadata.json` son obligatorios para que el resultado sea lo que se representa en el siguiente esquema:

```bash
presence
├── dist
│   └── metadata.json
├── presence.ts
└── tsconfig.json
```

o si estas usando un archivo `iframe.ts`:

```bash
presence
├── dist
│   └── metadata.json
├── presence.ts
├── iframe.ts
└── tsconfig.json
```

## [**metadata.json**](/dev/presence/metadata)

> Para la conveniencia de nuestros desarrolladores de presences, hemos proporcionado un esquema que puedes usar para validar la integridad de tu archivo `metadata`. Esto es completamente opcional y no es requerido durante el proceso de revisión.

> Es altamente recomendado que organices tu archivo `metadata` en el formato mostrado abajo, y debes tener nombres de servicio, descripciones, etiquetas y campos de ajustes gramaticalmente correctos. Cualquier cosa que no esté organizada según las especificaciones, **no** será permitida.

> Presences de sitios web que tienen contenido explícito **deben** tener la etiqueta `nsfw` y el logo y etiqueta **no** deben contener contenido explícito.

Cada presence tiene un archivo para describirla llamado `metadata.json`, el metadata tiene un estándar estricto y un ejemplo de este archivo se puede ver abajo:

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.3",
  "author": {
    "name": "USUARIO",
    "id": "ID"
  },
  "contributors": [
    {
      "name": "USUARIO",
      "id": "ID"
    }
  ],
  "service": "SERVICIO",
  "altnames": ["SERVICIO"],
  "description": {
    "en": "DESCRIPCIÓN"
  },
  "url": "URL",
  "version": "VERSIÓN",
  "logo": "URL",
  "thumbnail": "URL",
  "color": "#HEX000",
  "tags": ["TAG1", "TAG2"],
  "category": "CATEGORÍA",
  "regExp": "REGEXP",
  "iFrameRegExp": "REGEXP",
  "iframe": false,
  "readLogs": false,
  "settings": [
    {
      "id": "multiLanguage",
      "multiLanguage": true
    }
    {
      "id": "ID",
      "title": "TITULO A MOSTRAR",
      "icon": "ICONO DE FONTAWESOME",
      "value": true
    },
    {
      "id": "ID",
      "if": {
        "ID": true
      },
      "title": "TITULO A MOSTRAR",
      "icon": "ICONO DE FONTAWESOME",
      "value": "\"%song%\" de %artist%",
      "placeholder": "usa %song% o %artist%"
    },
    {
      "id": "ID",
      "title": "TITULO A MOSTRAR",
      "icon": "ICONO DE FONTAWESOME",
      "value": 0,
      "values": ["1", "2", "etc."]
    }
  ]
}
```

> Si un campo está estipulado como opcional en la [documentación](https://docs.premid.app/en/dev/presence/metadata) o está marcado con un `*` al lado de la clave y tu presence usa el valor por defecto para ella, no la incluyas en el archivo `metadata`. (por ejemplo, una presence sin soporte para iframe no debe contener el campo `iframe`.)

> Todas las imágenes en el archivo de `metadata` deben estar alojadas en `i.imgur.com`. Usar contenido alojado en el sitio web **no** está permitido, ya que pueden cambiar su ubicación sin querer.

Una lista de los campos y sus reglas están listadas abajo:

### **`$schema`**

- La _llave_ del esquema **debe** incluir un signo de dolar al inicio, esto indicará a su editor de texto que tu quieres validar tu archivo JSON contra un modelo. _Tal y como se ha dicho anteriormente, no necesitas incluir un esquema, pero en caso de que lo hagas, debes tomar esto en cuenta._

### **`author`**

- El _valor_ del ID **debe** ser el snowflake de tu ID de Discord. Puedes obtenerlo activando el [modo de desarrollador](https://support.discord.com/hc/es/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-). _Por favor **no** confundas esto con la ID de la aplicación, la cual es solo para tu presence._

### **`*contributors`**

- **No** te agregues ni a ti, ni a nadie más como contribuidores al menos que hayan ayudado con la presence.

### **`service`**

- El nombre del servicio **debe** ser el nombre del directorio de la presence. Por ejemplo, si la presence esta ubicada en `/websites/Y/YouTube/`, el nombre del servicio debe ser `YouTube`.
- **No puedes** usar la url como el nombre del servicio al menos que el sitio web use la url como su nombre oficial. Si el nombre no es descriptivo y puede ser considerado impreciso, usar la url es **requerido**. (Por ejemplo: `YouTube` es permitido porque este es el nombre oficial y es descriptivo, mientras que `youtube.com` no lo es. `Top` es un nombre no descriptivo, así que usar la url `top.gg` es **requerido**.)
- Si el servicio contiene algunas reglas explicitas en su nombre, usted debe seguirlas.

### **`*altnames`**

- Usa esto **solo** en el caso de que el sitio web aparezca bajo distintos nombres (ejemplo. Versiones *acortadas* del servicio aparecerán como `etiquetas`.

### **`description`**

- **Todas** las presences **requieren** una descripción en Inglés sin importar el idioma preferido del sitio web.
- **No** intentes traducir la descripción por tu cuenta a menos que conozcas el idioma, traductores modificaran tu `metadata.json.` y cambiaran la descripción de ser necesario.

### **`url`**

- La url **debe** ser un "string" si el sitio web solo usa un dominio. Si el sitio web usa múltiples, usa un array y especifica cada una.
- **No** incluyas protocolos en la url (por ejemplo.`http` o `https`, y no incluyas parámetros "query" en la url (por ej.,`www.google.com/search?gws_rd=ssl` debería ser `www.google.com`)

### **`version`**

- Asegúrate de que el número de versión sigue [los estándares semánticos de versionado](https://semver.org/lang/es/), que se traducen al siguiente esquema: `<NUEVA-CARACTERISTICA>.<SOLUCION-DE-MULTIPLES-BUGS>.<SOLUCION-DE-PEQUEÑOS-BUGS-O-CAMBIOS-EN-METADATA>`. Cualquier cosa como `1.0.0.1`, `1.0`, `1`, `1.0.0-BETA` o cambiando `1.0.0` a `2.0.0` en una corrección de errores/cambio pequeño **no** está permitido.
- La versión **debe** empezar siempre con `1.0.0` a menos que se diga lo contrario, otras versiones **no** serán permitidas.

### **`logo`**

- El logo **debe** ser una imagen cuadrada con una relación de aspecto `1:1`.
- La imagen **requiere** una resolución mínima de `512x512` píxeles. Puedes aumentar el tamaño de la imagen usando una herramienta como [waifu2x](http://waifu2x.udp.jp/).

### **`thumbnail`**

- La miniatura **debería** ser preferiblemente una [tarjeta promocional amplia](https://i.imgur.com/3QfIc5v.jpg) o una [captura de pantalla](https://i.imgur.com/OAcBmwW.png) si la primera **no** está disponible.

### **`color`**

- El color **debe** ser un valor hexadecimal entre `#000000` y `#FFFFFF`.
- La cadena de color **debe** estar precedida con un numeral (#).

### **`tags`**

- **Todas** las presences requieren por lo menos _una_ etiqueta.
- Las etiquetas **no** deben tener espacios, slash, comillas simples o dobles, caracteres Unicode y siempre deberían ser en minúscula.
- Las etiquetas **deberían** incluir preferiblemente nombres de servicio alternativos para hacer su búsqueda mas fácil ( por ejemplo, si una presencia Amazon hubiese incluido soporte para AWS, debería tener sus etiquetas como `amazon-web-services` y `aws`)
- Estás **obligado** a añadir una etiqueta `NSFW` si la presence es para un sitio web con contenido para adultos.

### **`category`**

- La categoría **debe** ser una de las siguientes listadas en la [documentación](https://docs.premid.app/es/dev/presence/metadata#categorias-de-una-presencia).
- La presence debe utilizar una categoría que coincida con el contenido del sitio web. (por ejemplo, no utilices `anime` cuando el sitio web no esté relacionado con anime).

### **`*regExp`** <br /> **`*iFrameRegExp`**

- Las expresiones regulares **deben** ser válidas. Por favor pruebe sus expresiones con las herramientas listadas en la [documentación](https://docs.premid.app/en/dev/presence/metadata#testing).

### **`readLogs`**

- Debe ser un valor `boolean` (por ejemplo `true` o `false`).
- Habilite los registros de su presencia.

### **`warning`**

- Habilita un icono de advertencia indicando al usuario que la presence requiere de pasos adicionales además de añadirla.
- Una presence de ejemplo usando esta variable de metadata es `VLC`.

### **`settings`**

- Si decides formatear un string (por ejemplo., `%song% por%artist%`), debes rodear las variables por símbolos de porcentaje en cada lado. Variables como `%var`, `var%`, `%%var%%` o cualquier cosa intermedia **no** está permitido por el bien de la estandarización.
- El nombre de la configuración **no** debe estar completamente en mayúsculas. Por ejemplo, nombre como `MOSTRAR ESTADO` **no** serán permitidos. En cambio nombre como `Mostrar Estado` o `Mostrar estado` sí están permitidos.
- Si estás usando la opción `multiLanguage` deberías saber:
  - Un valor de tipo **boolean** habilitará sólo strings de [`general.json`](https://github.com/PreMiD/Localization/blob/master/src/Presence/general.json) del repositorio de Localization o del archivo de la presence (por ejemplo. cuando el nombre de la presence es YouTube, la extensión obtendrá también valores de `youtube.json`)
  - Un valor de tipo **string** (por ejemplo. `youtube`) especifica el nombre del archivo del cual se obtendrán los strings.
  - Un valor de tipo **Array<String>** (por ejemplo. `["youtube", "discord"`) especifica los nombres de los archivos de los cuales obtener los strings.

## [**presence.ts**](/dev/presence/class)

> El código que escribas **debe** estar _bien escrito_ y **debe** ser _entendible_ y todas las palabras deben ser gramaticalmente correctas (errores gramaticales de páginas webs pueden ser ignoradas).

> Cada presence sigue un estricto conjunto de reglas de linting que serán comprobadas durante el proceso de revisión. Un par de recomendaciones pueden ser vistas a continuación. - [Recomendaciones de plugins de TypeScript para verificaciones "Strict Type Checking"](https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin/docs/rules) - [recomendaciones de ESlint](https://eslint.org/docs/rules) [Recomendaciones de ESlint](https://eslint.org/docs/rules). [Recomendaciones de ESlint](https://eslint.org/docs/rules). [Prettier (formateo de código)](https://prettier.io/).

Aquí hay una lista de reglas que debes seguir al escribir tu archivo `presence.ts`:

- **Siempre** declare una nueva instancia de la clase `Presence` antes de cualquier otra variable para evitar problemas raros que puedan ocurrir; no es un requisito por diseño, podría ser ser eliminado en el futuro.
- **Nunca** utilices funciones personalizadas cuando [variantes nativas estén disponibles](https://docs.premid.app/dev/presence#files-explained); esto asegura que las correcciones en el nivel de extensión también se aplican a tus presences. Eres libre de usar lo que sea que necesites, si no lo encuentras listado en la documentación.
- Está **prohibido** codificar las presences de un sitio sin agregar soporte a su idioma principal(ejemplo., una presence de YouTube codificada con soporte solo para portugués y japonés, pero no inglés en sí.)
- Los campos `smallImageKey` y `smallImageText` están destinados a proporcionar contexto adicional/secundario (como `reproduciendo/pausado` para sitios de streaming, `navegando` para sitios normales, y otros casos) no para promover perfiles de Discord ni nada que no esté relacionado con PreMiD.
- **No** estás autorizado para acceder a `localStorage`.
- Al acceder a las cookies de los datos almacenados, por favor prefije la clave con `PMD_`.
- Solo podrás hacer peticiones HTTP/HTTPS a `premid.app` o el sitio para API de su presence. Si está utilizando dominios externos, tendrá que explicar por qué son necesarios. Únicamente la API permitida para realizar solicitudes es [`Obtener API`](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API).
- **No** establezcas campos de la instancia presenceData como undefined una vez declarado, utiliza en su lugar la palabra clave `delete`. (por ejemplo, usa `delete data.startTimestamp` en vez de `data.startTimestamp = undefined`)
- **No** tienes permitido escribir presences que puedan cambiar la funcionalidad de un sitio web. Esto incluye la adición, eliminación o modificación de los elementos DOM.

## [**tsconfig.json**](/dev/presence/tsconfig)

> **No** escribas tu propio `tsconfig.json`, usa el proporcionado en la [documentación](https://docs.premid.app/en/dev/presence/tsconfig).

## Modificación

> **Debes** cambiar la versión en **metadata.json** a un valor mayor de la versión anterior cuando hagas cambios en los archivos **presence.ts**, **iframe.ts** o**metadata.json**.

En algunas situaciones, las presences pueden comportarse inesperadamente o podrían realizar cambios menores para mejorar su funcionalidad. Aquí hay una lista de situaciones que **debes** tener en cuenta al modificar presences.

- Tu **No** tienes permitido reescribir una presence o cambiar su autor. Si el autor de la presence fue baneado del servidor oficial o no ha hecho los cambios requeridos en el periodo de un mes, puedes contactar con un verificador para ver si puedes reescribir la presence.
- Si haces modificaciones a una presence que afecte a al menos a un **un cuarto** del código base de la misma, tienes permitido añadirte como colaborador. Contacta a un verificador para más información sobre este tema.
- Cualquiera puede proporcionar revisiones para corregir errores; sin embargo, intente **no** realizar cambios que **no** sean necesarios. Las modificaciones válidas incluyen correcciones generales (código y tipos), adiciones (descripciones y etiquetas), archivos que faltan, etc. **No** cambie las imágenes si no están desactualizadas y están en especificaciones.

# Verificación

> **Todo** código contribuido será bajo la licencia `Mozilla Public License 2.0`.

> Si necesitas contactar con alguien, por favor usa nuestro servidor oficial de Discord. Todas los verificadores tiene el rol de `Reviewer` en su perfil.

> Por favor ten en cuenta que el trabajo de los verificadores es voluntario y gestionan otros repositorios además de este, tu pull request puede no ser revisada hasta horas o días después de haber sido creada.

> Ten **siempre** un fork actualizado antes de crear el pull request. Esto facilitará falsos positivos de los chequeos.

The most important process of presence development is getting your presence on the store. This is done by making a [pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) on GitHub on the `PreMiD/Presences` repository. Our reviewers will confirm that your presence is up to standards and will push it onto the store.

<div>
  <h2 style="font-size: 2rem; margin-bottom: 0;">Presence Reviewers</h2>
  
  <a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>  <a href="https://github.com/Timeraa"><img src="https://github.com/Timeraa.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>  <a href="https://github.com/StrikerFRFX"><img src="https://github.com/StrikerFRFX.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
  <br />
</div>

## `Restrictions`

Repetitive offenses such as breaking guidelines, spamming pull requests, threats, or innapropriate behavior will get you banned from creating presences.

In this scenerio, the following changes will occur:

- Presences under your management will be transferred to the PreMiD bot or another user (reviewer decision). La Id de la aplicación para cada presence se volverá a crear con el nombre del nuevo dueño.
- All of your issues and pull requests (presence creation, presence contribution, etc) created following the ban will be prompty closed.
- Tickets created under your name regarding presence development will be deleted.

## `Reviewing`

A few things you should know after opening a pull request:

- It takes 2 reviewers to merge a pull request.
- If a pull request is inactive for a period of 7 days, it will be promptly closed.
- All checks **must** be passed in order to merge.
- ⚠️ You **must** provide new, unaltered screenshots (taken by you) showing a side-by-side comparison of your profile and the website to prove that your presence works. _You are allowed to stitch screenshots together for viewing pleasure_ This applies for both creation and modification.
- ⚠️ You are also **required** to include screenshots of the presence settings in the extension if supplied. An example can be seen [here](https://imgur.com/a/OD3sj5R).

## `Checks`

![Checks](https://i.imgur.com/oqAakOc.png)

Currently, a presence goes through 3 separate stages of checks. All of these checks help the reviewers determine whether your presence is suitable for deployment.

- `Codacy` is a bot that checks for code quality. If you ever receive errors for new issues, you are **required** to fix them. (_WARNING: Codacy bot will be deprecated soon and you will need check errors only from DeepScan!_)
- `DeepScan` is a bot that checks for code quality. If you ever receive errors for new issues, you are **required** to fix them.
- `Schema Validation` will scan your `metadata.json` file for any errors (for e.g., missing fields, invalid value types, etc.). If you ever see any new issues, you are also **required** to fix those. Adding a schema field to your `metadata.json` file will allow your text editor (if supported) to show you these errors during development.

## `Additional Rules`

- **Always** make sure to start your presence in the most appropriate folder, if its name starts with _any_ Latin letter then it must be under its alphabetical match (for e.g., `D/dアニメストア` or `G/Google`). Any other Unicode/non-Latin characters **must** be under the `#` folder (for e.g., `#/巴哈姆特`) and numbers under the `0-9` folder (for e.g., `0-9/4anime`).

After meeting all of the guidelines with the proper reviews and checks, your presence will be merged with the store.

# Suggestions
If you have some suggestions about our guidelines, you should contact us @ [PreMiD's discord server](https://discord.premid.app) and we will check them!

# Contributions

`Revision 3` of the guidelines was written and was contributed to by the following individuals:

<div>
<a href="https://github.com/ririxidev"><img src="https://github.com/ririxidev.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

`Revision 2` of the guidelines was written and was contributed to by the following individuals:

<div>
<a href="https://github.com/Alanexei"><img src="https://github.com/Alanexei.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

`Revision 1` was maintained by the following individuals:

<div>
<a href="https://github.com/Alanexei"><img src="https://github.com/Alanexei.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/doomlerd"><img src="https://github.com/doomlerd.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>