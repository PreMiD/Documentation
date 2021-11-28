---
title: Classe Presence
description: A classe principal para cada presence do PreMiD
published: true
date: 2021-10-30T22:47:57.209Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:50.164Z
---

# Classe Presence

## Introdução

A classe `Presence` é muito útil, já que tem métodos básicos que precisamos para criar uma presence.

Ao criar uma classe você deve especificar a propriedade `clientId`.

```ts
const presence = new Presence({
  clientId: "514271496134389561" // Exemplo de clientId
});
```

### Propriedades

Existem 3 propriedades disponíveis para a classe `Presence`.

#### `clientId`

Este propriedade é obrigatória para sua presence funcionar, pois utilizamos a id do seu aplicativo para exibir a logo e os assets. Você pode obter a id do seu aplicativo na [página de aplicativos](https://discordapp.com/developers/applications).

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

### `setTrayTitle(String)` - *Deprecated since 2.2.3*

> Este método funciona apenas no Mac OS. 
> 
> {.is-warning}

Define o título da bandeja no Menubar.

### `createSlideshow()`

Cria uma nova classe `Slideshow`.

```ts
const slideshow = presence.createSlideshow();
```

É sugerido fazer isso logo após a criação da classe `Presence`:

```ts
const presence = new Presence({
    clientId: "514271496134389561" // Exemplo de clientId
  }),
  slideshow = presence.createSlideshow();
```

Você pode encontrar a documentação da classe `Slideshow` [aqui](/dev/presence/slideshow).

### `getStrings(Object)`

Um método assíncrono que permite que você pegue strings traduzidas da extensão.

Você deve fornecer o `Object` com as keys sendo a key para string, `keyValue` é o valor da string. Uma lista de strings traduzidas pode ser encontrada utilizada este endpoint: `https://api.premid.app/v2/langFile/presence/pt_BR`

```ts
// Retorna strings `Jogando` e `Pausado`
// a partir da extensão.
const strings = await presence.getStrings({
  play: "general.playing",
  pause: "general.paused"
});

const playString = strings.play; // resultado: Reproduzindo
const pauseString = strings.pause; // resultado: Pausado
```

Desde a versão 2.2.0 da extensão você pode obter as strings de uma determinada língua. Isso funciona bem com a opção de configuração também recém-adicionada `multiLanguage`.

Sugerimos que você use o seguinte código para que ele atualize automaticamente o PresenceData se o usuário alterar o idioma selecionado;

```ts
async function getStrings() {
  return presence.getStrings(
    {
      play: "general.playing",
      pause: "general.paused"
    },
    // The ID is the ID of the multiLanguage setting.
    await presence.getSetting("ID").catch(() => "en");
  );
}

let strings = getStrings(),
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

```ts
const pageVar = getPageletiable(".pageVar");
console.log(pageVar); // Isso irá registrar o "conteúdo da variável"
```

### `getExtensionVersion(Boolean)`

Retorna a versão da extensão que o usuário está usando.

```ts
getExtensionVersion(onlyNumeric?: boolean): string | number;

const numeric = presence.getExtensionVersion();
console.log(numeric); // Irá registrar 210
const version = presence.getExtensionVersion(false);
console.log(version); // Irá registrar 2.1.0
```

### `getSetting(String)`

Retorna o valor da configuração.

```ts
const setting = await presence.getSetting("pdexID"); // Substitua pdexID pelo id da configuração
console.log(setting); // Isto registrará o valor da configuração
```

### `hideSetting(String)`

Oculta determinada configuração.

```ts
presence.hideSetting("pdexID"); // Substitua pdexID pelo id da configuração
```

### `showSetting(String)`

Mostra determinada configuração (somente funciona se a configuração já estava oculta).

```ts
presence.showSetting("pdexID"); // Substitua pdexID pelo id da configuração
```

### `getLogs()`

Retorna os logs do console do site.

```ts
const logs = await presence.getLogs();
console.log(logs); // Isto registrará os últimos 100 logs (em uma array).
```

**Nota:** Requer `readLogs` ser `true` no arquivo `metadata.json`.

### `info(String)`

Registra a mensagem fornecida no console em um formato baseado na presence no estilo `info`.

```ts
presence.info("Test") // Isto registrará "test" no estilo correto.
```

### `success(String)`

Registra a mensagem fornecida no console em um formato baseado na presence no estilo `success`.

```ts
presence.success("Test") // Isto registrará "test" no estilo correto.
```

### `error(String)`

Registra a mensagem fornecida no console em um formato baseado na presence no estilo `error`.

```ts
presence.error("Test") // Isto exibirá "test" no estilo correto.
```

### `getTimestampsfromMedia(HTMLMediaElement)`

Retorna 2 timestamps no formato `snowflake` em uma `Array` que pode ser usado para `startTimestamp` e `endTimestamp`.

```ts
const timestamps = presence.getTimestampsfromMedia(document.querySelector(".video"));
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Nota:** A `String` fornecida no querySelector é um exemplo.

### `getTimestamps(Number, Number)`

Retorna 2 timestamps no formato `snowflake` em uma `Array` que pode ser usado para `startTimestamp` e `endTimestamp`.

```ts
const video = document.querySelector(".video"),
  timestamps = presence.getTimestamps(video.currentTime, video.duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Nota:** A `String` fornecida no querySelector é um exemplo.

### `timestampFromFormat(String)`

Converte uma string com formato `HH:MM:SS`, `MM:SS` ou `SS` em um número inteiro (Não retorna uma timestamp snowflake).

```ts
const currentTime = presence.timestampFromFormat(document.querySelector(".video-now").textContent),
  duration = presence.timestampFromFormat(document.querySelector(".video-end").textContent),
  timestamps = presence.getTimestamps(currentTime, duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Nota:** A `String` fornecida no querySelector é um exemplo.

## Interface `presenceData`

A interface `PresenceData` é recomendada a usar quando você estiver usando o método `setActivity()`.

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
          <br>Você deve converter seu tempo em <code>timestamp</code> ou você receberá uma contagem regressiva errada.
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
      <td style="text-align:left">Defines the text that will be shown to user when they hover over the small
        icon.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
        <tr>
      <td style="text-align:left">buttons</td>
      <td style="text-align:left">Array de botões, máx. 2, label é o texto do botão, e url é o link.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code>
      </td>
    </tr>
  </tbody>
</table>

```ts
const presenceData: PresenceData = {
  details: "Meu título",
  state: "Minha descrição",
  largeImageKey: "logo_do_serviço",
  smallImageKey: "ícone_pequeno_do_serviço",
  smallImageText: "Você passou o mouse em cima de mim, e agora?",
  startTimestamp: 1564444631188,
  endTimestamp: 1564444634734,
  buttons: [
    {
            label: "Botão de teste1",
            url: "https://premid.app/"
        },
        {
            label: "Botão de teste2",
            url: "https://premid.app/contributors"
        }
    ]
};
```

## Eventos

Os events permitem que você detecte e lide com algumas mudanças ou chamadas que foram feitas. Você pode registrar eventos usando o método `on`.

```ts
presence.on("UpdateData", async () => {
  // Faz algo quando os dados são atualizados.
});
```

Há alguns eventos disponíveis:

#### `UpdateData`

Este evento é disparado toda vez que a presence é atualizada.

#### `iFrameData`

Disparado quando os dados são recebidos do script iFrame.
