---
title: Classe Presence
description: A classe principal para cada presence do PreMiD
published: true
date: 2021-05-23T09:14:06.963Z
tags:
editor: markdown
dateCreated: 2021-02-21T21:13:14.449Z
---

# Classe Presence

## Introdução

A classe `Presence` é muito útil, já que tem métodos básicos que precisamos para criar uma presence.

Ao criar uma classe você deve especificar a propriedade `clientId`.

```typescript
const presence = new Presence({
  clientId: "514271496134389561" // Exemplo de clientId
});
```

### Propriedades

Existem 3 propriedades disponíveis para a classe `Presence`.

#### `clientId`

Este propriedade é obrigatória para sua presence funcionar, pois utilizamos a id do seu aplicativo para exibir a logo e os assets. Você pode obter sua Application ID na [página de aplicativos](https://discordapp.com/developers/applications).

#### `injectOnComplete` - *Depreciado desde a 2.2.4*

Quando a propriedade `injectOnComplete` estiver definida para `true` o primeiro evento `UpdateData` para ambos os arquivos `presence.ts` e `iframe.ts` só será disparado quando a página carregar completamente.

#### `appMode` - *Depreciado desde a 2.2.4*

Quando a propriedade `appMode`: estiver definida para `true` e a presence enviar um objeto `PresenceData` vazio, o app irá exibir a aplicação (imagem e nome) no perfil do usuário em vez de não exibir nada.

## Métodos

### `getActivity()`

Retorna um objeto `PresenceData` do que a presence está exibindo.

### `setActivity(PresenceData | Slideshow, Boolean)`

Define a atividade do seu perfil de acordo com os dados fornecidos.

O primeiro parâmetro requer uma interface[`PresenceData`](#presencedata-interface) ou uma classe [`Slideshow`](/dev/presence/slideshow) para obter todas as informações que você deseja exibir em seu perfil.

O segundo parâmetro define quando a presence está reproduzindo algo ou não. Sempre utilize `true` se você estiver utilizando timestamps na `PresenceData`.

### `clearActivity()`

Limpa sua atividade e o título atual.

### `setTrayTitle(String)`

> Este método funciona apenas no Mac OS. 
> 
> {.is-warning}

Define o título da bandeja no Menubar.

### `createSlideshow()`

Cria uma nova classe `Slideshow`.

```typescript
const slideshow = presence.createSlideshow();
```

É sugerido fazer isso logo após a criação da classe `Presence`:

```typescript
const presence = new Presence({
    clientId: "514271496134389561" // Exemplo de clientId
  }),
  slideshow = presence.createSlideshow();
```

Você pode encontrar a documentação da classe `Slideshow` [aqui](/dev/presence/slideshow).

### `getStrings(Object)`

Um método assíncrono que permite que você pegue strings traduzidas da extensão.

Você deve fornecer o `Objeto` com as chaves sendo a chave para string, `keyValue` é o valor da string. Uma lista de strings traduzidas pode ser encontrada utilizada este endpoint: `https://api.premid.app/v2/langFile/presence/pt-br`

```typescript
// Retorna strings `Jogando` e `Pausado`
// a partir da extensão.
const strings = await presence.getStrings({
  play: "general.playing",
  pause: "general.paused"
});

const playString = strings.play; // result: Playing
const pauseString = strings.pause; // result: Paused
```

Desde a versão 2.2.0 da extensão você pode obter as strings de uma determinada língua. Isso funciona bem com a opção de configuração também recém-adicionada `multiLanguage`.

Sugerimos que você use o seguinte código para que ele atualize automaticamente o PresenceData se o usuário alterar o idioma selecionado;

```typescript
// Uma interface das strings que você está recebendo (boa para qualidade de código e autocompletar).
interface LangStrings {
  play: string;
  pause: string;
}

async function getStrings(): Promise<LangStrings> {
  return presence.getStrings(
    {
      // As strings que você está recebendo, certifique-se de que isto se encaixa com sua interface LangStrings.
      play: "general.playing",
      pause: "general.paused"
    },
    // The ID is the ID of the multiLanguage setting.
    await presence.getSetting("ID").catch(() => "en");
  );
}

let strings: Promise<LangStrings> = getStrings(),
  // The ID is the ID of the multiLanguage setting.
  oldLang: string = await presence.getSetting("ID").catch(() => "en");

//! The following code must be inside the updateData event!
// The ID is the ID of the multiLanguage setting.
const newLang = await presence.getSetting("ID").catch(() => "en");
if (oldLang !== newLang) {
  oldLang = newLang;
  strings = getStrings();
}

const playString = (await strings).play, // result: Playing
  pauseString = (await strings).pause; // result: Paused
```

### `getPageletiable(String)`

Retorna uma variável a partir do site, se ela existir.

**Atenção: Essa função pode causar alta utilização de CPU e travamentos no site quando tiver sido executada várias vezes.**

```typescript
const pageVar = presence.getPageletiable("pageVar");
console.log(pageVar); // This will log the "Variable content"
```

### `getExtensionVersion(Boolean)`

Returns version of the extension the user is using.

```typescript
getExtensionVersion(onlyNumeric?: boolean): string | number;

const numeric = presence.getExtensionVersion();
console.log(numeric); // Will log 210
const version = presence.getExtensionVersion(false);
console.log(version); // Will log 2.1.0
```

### `getSetting(String)`

Returns value of setting.

```typescript
const setting = await presence.getSetting("pdexID"); //Replace pdexID with the id of the setting
console.log(setting); // This will log the value of the setting
```

### `hideSetting(String)`

Hides given setting.

```typescript
presence.hideSetting("pdexID"); // Replace pdexID with the id of the setting
```

### `showSetting(String)`

Shows given setting (Only works if the setting was already hidden).

```typescript
presence.showSetting("pdexID"); // Replace pdexID with the id of the setting
```

### `getLogs()`

Returns the logs of the websites console.

```typescript
const logs = await presence.getLogs();
console.log(logs); // This will log the latest 100 logs (in an array).
```

**Note:** Requires `readLogs` to be `true` in the `metadata.json` file.

### `info(String)`

Prints the given message in the console in a format based of the presence in the `info` style.

```typescript
presence.info("Test") // This will log "test" in the correct styling.
```

### `success(String)`

Prints the given message in the console in a format based of the presence in the `success` style.

```typescript
presence.success("Test") // This will log "test" in the correct styling.
```

### `error(String)`

Prints the given message in the console in a format based of the presence in the `error` style.

```typescript
presence.error("Test") // This will log "test" in the correct styling.
```

### `getTimestampsfromMedia(HTMLMediaElement)`

Returns 2 `snowflake` timestamps in an `Array` that can be used for `startTimestamp` and `endTimestamp`.

```typescript
const timestamps = presence.getTimestampsfromMedia(document.querySelector(".video"));
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Note:** The given `String` in querySelector is an example.

### `getTimestamps(Number, Number)`

Returns 2 `snowflake` timestamps in an `Array` that can be used for `startTimestamp` and `endTimestamp`.

```typescript
const video = document.querySelector(".video"),
  timestamps = presence.getTimestamps(video.currentTime, video.duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Note:** The given `String` in querySelector is an example.

### `timestampFromFormat(String)`

Converts a string with format `HH:MM:SS` or `MM:SS` or `SS` into an integer (Does not return snowflake timestamp).

```typescript
const currentTime = presence.timestampFromFormat(document.querySelector(".video-now").textContent),
  duration = presence.timestampFromFormat(document.querySelector(".video-end").textContent),
  timestamps = presence.getTimestamps(currentTime, duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

A interface `presenceData` é recomendada quando você usar o método `setActivity()`.

## Interface `presenceData`

The `PresenceData` interface is recommended to use when you are using the `setActivity()` method.

Essa interface possui as seguintes variáveis, todas elas são opcionais.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Variável</th>
      <th style="text-align:left">Descrição</th>
      <th style="text-align:left">Tipo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">details</td>
      <td style="text-align:left">A primeira linha da sua presence, geralmente usada como cabeçalho.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">state</td>
      <td style="text-align:left">Segunda linha da sua presence.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">startTimestamp</td>
      <td style="text-align:left">Define o tempo atual.<br>
        Usado se você quiser mostrar quantas <code>horas:minutos:segundos</code> restantes.
          <br>Você deve converter o tempo em <code>horário</code> ou você receberá uma
          contagem errada.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">endTimestamp</td>
      <td style="text-align:left">Define a duração total.
        <br>Usado se você quiser mostrar quantos <code>horas:minutos:segundos</code> faltam.
          <br>Você deve converter o tempo em <code>horário</code> ou você receberá uma
          contagem errada.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">largeImageKey</td>
      <td style="text-align:left">Define o logo para a presence.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageKey</td>
      <td style="text-align:left">Define o pequeno ícone ao lado do logo da presence.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageText</td>
      <td style="text-align:left">Define o texto que será exibido ao usuário quando ele passar o cursor no pequeno 
        ícone.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
        <tr>
      <td style="text-align:left">buttons</td>
      <td style="text-align:left">Array of buttons, max 2, label is the button text, and url is the link.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code>
      </td>
    </tr>
  </tbody>
</table>

```typescript
const presenceData: PresenceData = {
  details: "My title",
  state: "My description",
  largeImageKey: "service_logo",
  smallImageKey: "small_service_icon",
  smallImageText: "You hovered me, and what now?",
  startTimestamp: 1564444631188,
  endTimestamp: 1564444634734,
  buttons: [
    {
            label: "Test button1",
            url: "https://premid.app/"
        },
        {
            label: "Test button2",
            url: "https://premid.app/contributors"
        }
    ]
};
```

## Events

Os events permitem que você detecte e lide com algumas mudanças ou chamadas que foram feitas. You can subscribe to events using the `on` method.

```typescript
presence.on("UpdateData", async () => {
  // Do something when data gets updated.
});
```

There are few events available:

#### `UpdateData`

This event is fired every time the presence is being updated.

#### `iFrameData`

Fired when data is received from iFrame script.
