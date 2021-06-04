---
title: Presence Development
description:
published: true
date: 2021-02-07T17:11:34.449Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:02.843Z
---

> All presences are now stored here: https://github.com/PreMiD/Presences 
> 
> {.is-info}

Version `2.x` introduces the [presence store](https://premid.app/store). Users now have the ability to manually add and remove their favourite presences through the user interface of the [website](https://premid.app/).

> Antes de começar, é altamente recomendado que você olhe as nossas diretrizes de presence. 
> 
> {.is-warning}

- [Diretrizes](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# Estrutura

Todas as Presences são codificadas em [TypeScript](https://www.typescriptlang.org/). O [TypeScript](https://www.typescriptlang.org/) tem algumas definições de tipo extra apimentadas sobre o JavaScript, portanto, corrigir e identificar bugs é muito mais fácil.

## Instalação

1. Instale o [Git](https://git-scm.com/).
2. Instale o [Node](https://nodejs.org/en/) (vem com [npm](https://www.npmjs.com/)).
3. Instale o [TypeScript](https://www.typescriptlang.org/index.html#download-links) (abra um terminal e `npm install -g typescript`).

## Clonando o projeto

1. Abra o terminal e digite `git clone https://github.com/PreMiD/Presences`.
2. Escolha uma pasta que preferir.
3. Abra isso no seu editor de código.

## Criando pastas e arquivos

1. Vá na pasta `websites` e então vá para a pasta com a primeira letra do **nome** (não um URL) do serviço que você deseja contribuir.
2. Crie uma pasta com o **nome** (não uma URL) do serviço que você deseja suportar.
3. Crie um arquivo `presence.ts` e um arquivo `tsconfig.json` dentro dela.
4. Crie uma pasta chamada `dist` dentro.
5. Crie um arquivo `metadata.json` dentro da pasta `dist`.

## Preenchendo o arquivo tsconfig.json

Por favor, coloque o seguinte código dentro do arquivo ` tsconfig.json `.

```typescript
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

Para saber mais sobre a configuração do TypeScript, clique [aqui](/dev/presence/tsconfig).

## Preenchendo o arquivo metadata.json

Nós fizemos um `metadata.json` criador de arquivos para os preguiçosos [aqui](https://eggsy.xyz/projects/premid/mdcreator). Ainda é sugerido ler isso para que você saiba como funciona.

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.3",
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

Por favor copie o código acima e coloque-o em seu arquivo de `metadata.json`. Agora você precisa editar os valores das propriedades. Note que as seguintes propriedades são opcionais para ter no seu `metadata.json`, se você não planeja usá-los, você precisa removê-los.

- `contributors`
- `altnames`
- `regExp`
- `iframe`
- `iFrameRegExp`
- `readLogs`
- `settings`

**Esclarecimento algumas predefinições de valores:**

<table>
  <thead>
    <tr>
      <th style="text-align:left">Variável</th>
      <th style="text-align:left">Descrição</th>
      <th style="text-align:left">Tipo</th>
      <th style="text-align:left">Opcional</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>author</b></td>
      <td style="text-align:left">Deve conter um Objeto com o <code>nome</code> e o <code>id</code> do desenvolvedor da Presence. <code>name</code> is your Discord username without the identifier(#0000). O <code>id</code> do Usuário pode ser copiado no Discord ao ativar o modo de desenvolvedor e com o botão direito do mouse no seu perfil.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Não</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>contributors</b></td>
      <td style="text-align:left">Deve conter um Objeto com o <code>nome</code> e o <code>id</code> do desenvolvedor da Presence. <code>name</code> é seu nome de usuário no Discord sem seu identificador(#0000). O <code>id</code> do Usuário pode ser copiado no Discord ao ativar o modo de desenvolvedor e com o botão direito do mouse no seu perfil.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Sim</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>service</b></td>
      <td style="text-align:left">O título do serviço que essa Presence suporta.<br>
      (Deve possuir o mesmo nome da pasta na qual está tudo)</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Não</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>altnames</b></td>
      <td style="text-align:left">Seja capaz de pesquisar a Presence usando um nome alternativo.<br>
      Significa ser usado em Presences que têm nomes diferentes em línguas diferentes. (ex. Pokémon e 포켓몬스터).<br>
      Você também pode usar isso para Presences que possuem caracteres especiais e você não precisa digitá-los (ex. Pokémon e Pokemon).</td>
      <td style="text-align:left"><code>Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Sim</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>description</b></td>
      <td style="text-align:left">Descrição curta da Presence, você pode usar a descrição do serviço se estiver sem ideias. Sua descrição deve ter valores de key pair que indicam o idioma e a descrição nesse idioma específico. Faça descrições com os idiomas <i>que você conhece</i>, nossos tradutores farão alterações ao seu arquivo de metadados.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Não</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>url</b></td>
      <td style="text-align:left">URL do serviço.<br><b>Exemplo:</b><code>vk.com</code><br>
      <b>Esse URL deve corresponder ao URL do website, pois irá detectar se o usuário está ou não no website para injetar o script.</b><br> <b>NÃO</b> adicione <code>https://</code> ou <code>http://</code> no URL ou barra no final:
      <code>https://premid.app/</code> -> <code>premid.app</code><br>
      <b>Nota:</b>: Alguns URLs têm de possuir <code>www.</code> ou outra coisa na frente do domínio. <b>NÃO</b> esqueça de adicioná-lo!<br>
      Você pode adicionar múltiplos URLs fazendo o seguinte:<br>
      <code>["URL1", "URL2", "ETC."]</code><br>
      Você também pode usar o regExp, também conhecido como Regex para isso, a explicação está abaixo.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Não</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>regExp</b></td>
      <td style="text-align:left">A regular expression string used to match urls.<br>
      regExp or also known as Regex, can be used if a website has multiple subdomains.<br>
      You could use the following regExp for that:<br>
      <code>([a-z0-9]+)[.]domain[.]TLD"</code><br>
      TLD standing for Top Level Domain for example: .com .net (but do not enter the dot).<br>
      <code>([a-z0-9]+)</code> means anything from a to z and from 0 to 9.<br>
      You can get a quick starter by watching this <a href="https://youtu.be/sXQxhojSdZM">video</a>.<br>
      You can test your regExp at <a href="https://regex101.com/">Regex101</a>.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Sim</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>version</b></td>
      <td style="text-align:left">Versão da sua presence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Não</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logo</b></td>
      <td style="text-align:left">Link para o logotipo do serviço.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Não</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>thumbnail</b></td>
      <td style="text-align:left">Link para sua miniatura da presence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Não</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>color</b></td>
      <td style="text-align:left">Valor <code>#HEX</code>. Recomendamos usar uma cor primária do serviço que a sua presence suporta.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Não</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>tags</b></td>
      <td style="text-align:left">Array com tags, eles ajudarão os usuários a pesquisar sua presence no site.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Não</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">Uma string usada para representar a categoria na qual a presence cai. Veja as categorias válidas <a href="https://docs.premid.app/dev/presence/metadata#presence-categories">aqui</a>.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Não</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iframe</b></td>
      <td style="text-align:left">Define se <code>iFrames</code> são usados.</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Sim</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iFrameRegExp</b></td>
      <td style="text-align:left">Um seletor de expressão regular que seleciona <code>iFrames</code> para injetar. Consulte regExp para obter mais informações.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Sim</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readLogs</b></td>
      <td style="text-align:left">Define se a extensão deve estar lendo os logs.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Sim</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>settings</b></td>
      <td style="text-align:left">Uma matriz de configurações que o usuário pode alterar. <br>
      Leia mais sobre as configurações de presence <a href="https://docs.premid.app/dev/presence/metadata#presence-settings">aqui </a>.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Sim</code></td>
    </tr>
  </tbody>
</table>

## Primeiros passos

```typescript
const presence = new Presence({
    clientId: "000000000000000000", //O client ID do Aplicativo criado no https://discordapp.com/developers/applications
    mediaKeys: false //Ativar o uso e detecção de pressionamentos de teclas de mídia
}),

strings = presence.getStrings({
    play: "presence.playback.playing",
    pause: "presence.playback.paused"
    //Você pode usar isso para obter strings traduzidas
});

/*

function myOutsideHeavyLiftingFunction(){
    //Pegue e processe todos os seus dados aqui


    // element grabs //
    // api calls //
    // variable sets //
}

setInterval(10000, myOutsideHeavyLiftingFunction); 
//Execute a função separada do evento UpdateData a cada 10 segundos para obter e definir as variáveis ​​que o UpdateData seleciona

*/


presence.on("UpdateData", async () => {
    /*UpdateData está sempre disparando e, portanto, deve ser usado como seu ciclo de atualização ou `tick`. Isso é chamado várias vezes por segundo, sempre que possível.

    É recomendável configurar outra função fora desta função de evento que irá alterar os valores das variáveis e fazer o levantamento pesado se você chamar dados de uma API.*/

    const presenceData: presenceData = {
        largeImageKey: "key", /*A key (nome do arquivo) da Imagem Grande sobre a presence. These are uploaded and named in the Rich Presence section of your application, called Art Assets*/,
    smallImageKey:
      "key" /*The key (file name) of the Small Image on the presence. Estes são enviados e nomeados na seção Rich Presence de sua aplicação, chamada Art Assets*/,
    smallImageText: "Some hover text", //O texto que é exibido ao cobrir sobre a pequena imagem
    details: "Browsing Page Name", //A seção superior do texto da presence
    state: "Reading section A", //A seção inferior do texto da presence
    startTimestamp: 1577232000, //O unix epoch timestamp para quando começar a contar a partir
    endTimestamp: 1577151472000 //Se você quiser mostrar o Time Left em vez de Elapsed, este é o unix epoch timestamp em que o timer termina
  }; /*Opcionalmente você pode definir aqui uma largeImageKey e alterar o resto como sub-propriedades variáveis, por exemplo presenceData.type = "blahblah"; exemplos de type: details, state, etc..*/

  if (presenceData.details == null) {
    //Isto irá disparar se você não definir details da presence
    presence.setTrayTitle(); //Limpa o tray title para usuários Mac
    presence.setActivity(); /*Atualizar a presence sem dados, portanto limpando-a e tornando a imagem grande o ícone do Aplicativo Discord, e o texto o nome do Aplicativo Discord*/
  } else {
    //Isto irá disparar se você definir details da presence
    presence.setActivity(presenceData); //Atualizar a presence com todos os valores do presenceData object
  }
});
```

Você pode copiar isso no arquivo `presence.ts` e editar os valores. Configurar todos os valores é feito dentro do evento updateData.

For examples we suggest to look at the code of presences like: 1337x or 9GAG. For more information about the `Presence` class click [here](/dev/presence/class).

Since v2.2.0 there are now Slideshows, this allows you to show multiple `PresenceData` interfaces on an interval, for more information click about the `Slideshow` class [here](/dev/presence/slideshow).

## Can't get certain data?!

Muitos sites estão usando [iframes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)). These html tags can contain multiple sources such as videos. But they're not relevant every time. Some are hidden or just not actively used. Check if you can extract the information you need without them before you do unnecessary work.

1. Cheque por elas no console do navegador (certifique-se de que você está na guia **Elementos**).
2. Pesquisa (<kbd>CTRL</kbd>+<kbd>F</kbd> (Windows) ou <kbd>CMD</kbd>+<kbd>F</kbd> (MacOS)).
3. Execute `document.querySelectorAll("iframe")`.

Se perceber que seus dados estão em um iFrame, você precisa fazer o seguinte:

1. Crie um arquivo `iframe.ts`.
2. Defina o iFrame como `true` no seu arquivo de metadados.
3. Preenchendo o seu arquivo iFrame.

```typescript
const iframe = new iFrame();
iframe.on("UpdateData", async () => {
  /*
  Obtenha todos os dados que você precisa do iframe, salve-os em variáveis
  e os enviou usando iframe.send
  */
  iframe.send({
    //sending data
    video: video,
    time: video.duration
  });
});
```

4. Faça com que seu arquivo de presence receba dados do arquivo iFrame.

```typescript
presence.on("iFrameData", (data) => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

**Note:** This needs to be placed outside of the updateData event.

## Compilando

Open a console in your folder and type `tsc -w` to compile the `presence.ts` into the `/dist` folder.

# Carregando a presence

1. Clique no ícone da extensão e segure o botão <kbd>Shift</kbd> em seu teclado.
2. O botão **Carregar presence** aparecerá na seção das Presences.
3. Clique nele enquanto estiver segurando o botão <kbd>Shift</kbd>.
4. Selecione a pasta /dist da sua presence.

# Algumas coisas úteis

## Hot-reloading

The website you are developing on is automatically reloading every time you save a file in your folder.

## Depuração

- Você pode colocar `console.log("Test");` entre seu código e ver se o console do seu navegador lhe dá essa saída. Se sim, então continue e tente novamente depois da próxima função. Se não, então há um erro acima.
- Se isso não te ajudar, peça ajuda a um desenvolvedor de presences no nosso [servidor do Discord](https://discord.premid.app/).

# Arquivos explicados

- [Classe Presence](/dev/presence/class)
- [Classe de Slideshow](/dev/presence/slideshow)
- [Classe iFrame](/dev/presence/iframe)
- [Arquivo Metadata](/dev/presence/metadata)
- [Configuração do TypeScript](/dev/presence/tsconfig ""){.links-list}
