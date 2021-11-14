---
title: Diretrizes das Presences
description: Regras que todos os presence developers devem seguir para ter sua presence adicionada.
published: true
date: 2021-10-18T16:26:36.089Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:53.883Z
---

<div align="center">
    <img src="https://github.com/PreMiD.png?size=2048" width="128px" style="max-width:100%;">
    <h3 style="font-size: 2rem; margin-bottom: 0">Diretrizes das Presences</h3>
    <h4 style="margin-top: 0">Revisão 3</h4>
    <br />
</div>

# Diretrizes

Ao publicar Presences em [nosso Repositório GitHub](https://github.com/PreMiD/Presences), nós exigimos que você siga um conjunto de diretrizes. Para alguns, estas regras rigorosas podem parecer severas. Porém, a implementação dessas regras impedirá a nós e a nossos usuários de nos depararmos com quaisquer problemas.

# Criação

The general rules of presence development are as follows:

- Presences **must** be related to the website of choice.
- As Presences **não podem** ser feitas para websites ilegais. (for e.g., stressors, drug marketing, child pornography, etc.)
- The file structure must be clean and managed, do not include files which are not specified. (for e.g., vscode and git folders, image and text files, etc.)
- You need to have a proper file structure, drafts are **not** allowed.
- Presences for websites with (`.onion` TLDs) or websites with free domains/hosts (for e.g., `.TK` [all free Freenom domains], `.RF`, `GD`, etc) are **not** permitted, exceptions can be made if a proof is presented showing that they paid for the domain.
- The domain of the presence must be at least 2 months old.
- Presences sobre páginas internas de navegadores (como a Chrome Web Store, `chrome://`, páginas `about:`, etc) **não são** permitidas por requererem uma bandeira experimental a ser ativada no lado do usuário e que poderia potencialmente causar dano aos seus navegadores.
- Presences com suporte apenas para um único subdomínio **não serão** permitidas, visto que elas podem parecer quebradas em outras páginas (como a página principal), exceções podem ser feitas para as páginas de políticas e de contato (conteúdo que não é usado com frequência) ou sites onde o outro conteúdo não é relacionado. (por exemplo, páginas da Wikia)
- Presences para rádios on-line só são permitidas se o rádio tiver pelo menos 100 ouvintes semanais e 15 simultâneos e deve ter alguns recursos além de apenas mostrar título do álbum/música, etc.
- Presences não podem executar código em JS com sua própria função para obter variáveis. Se o Firefox tiver problemas com a função embutida dentro da classe de `Presence`, você tem permissão de fazer sua própria função e precisa nos informar sobre isso na descrição da Pull Request.
- Presences de baixa qualidade (ou com pouco contexto) **não** são permitidos (por exemplo, apenas mostrar uma logo e um texto mas nunca mudá-los de novo).
- Presences para serviços como Bot de Discord/Lista de Servidores devem seguir estes requisitos extras:
  - O domínio deve ter pelo menos **6 meses**.
  - Visitantes únicos por dia:
    - For 6 to 12 month old domains: **20,000 unique visitors/day**.
    - Para domínios com mais de 12 meses: **45,000 visitantes únicos/dia**.
  - O site não pode estar em um domínio barato como `.xyz `, `.club ` e assim por diante.
  - O próprio site deve ter uma boa qualidade, design etc.
- Presences devem usar [detalhes comuns](https://api.premid.app/v2/langFile/presence/en) (strings começando com "general."). Você pode conseguir isso usando `multiLanguage` com as strings fornecidas. Se sua presença requere strings personalizadas, então você não deve usar `multiLanguage` até que a presença receba 1000 usuários. Você pode encontrar um exemplo [aqui](https://docs.premid.app/dev/presence/class#getstringsobject).
- Incluir a pasta `dist`, os arquivos `presence.ts`, `iframe.ts`, e `metadata.json` são mandatórios, então o resultado seria o que está representado no seguinte esquema:

```bash
presence
├── dist
│   └── metadata.json
├── presence.ts
└── tsconfig.json
```

or if you're using a `iframe.ts` file:

```bash
presence
├── dist
│   └── metadata.json
├── presence.ts
├── iframe.ts
└── tsconfig.json
```

## [**metadata.json**](https://docs.premid.app/dev/presence/metadata)

> For the convenience of our presence developers, we have provided a schema which you can use to validate the integrity of your `metadata` file. This is entirely optional and is not required during the review process.

> It is highly recommended that you organize your `metadata` file in the format shown below, and you must have grammatically correct service names, descriptions, tags, and setting fields. Anything not organized to specifications will **not** be permitted.

> Presences of websites that have explicit content **must** have the `nsfw` tag, and the logo/thumbnail must **not** contain any of this content.

Each presence has a descriptor file called `metadata.json`, the metadata has a strict standard and an example of this file can be seem below:

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.5",
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
      "id": "multiLanguage",
      "multiLanguage": true
    }
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

> Se algum campo for listado como opcional na [documentação](https://docs.premid.app/dev/presence/metadata) ou haver um `*` próximo a chave, e sua presence usa o valor padrão para isso, não inclua no arquivo `metadata`. (por exemplo, uma presence sem suporte iframe não precisaria de um campo `iframe`.)

> All images in the `metadata` file must be hosted on `i.imgur.com`. Using content hosted on the website is **not** permitted as they can change the paths and files unwillingly.

A list of fields and their rules are listed below:

### **`$schema`**

- The schema _key_ **must** include a dollar sign at the beginning of it, this will signal your text editor that you want to validate your JSON file against a model. _As stated earlier, you do not need to include a schema, but if you include it you must take this into account._

### **`author`**

- The ID _value_ **must** be your Discord snowflake ID. You can get it by enabling [developer mode](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-). _Please do **not** confuse this with your application ID, which is only for your presence._

### **`*contributors`**

- Do **not** add yourself as a contributor, and do not add someone else as a contributor unless they have helped with the presence.

### **`service`**

- O nome do serviço **deve** ser o nome do diretório da presence. For example, if the presence is located at `/websites/Y/YouTube/`, the service name must be `YouTube`.
- Você **não** pode usar a url como nome do serviço a menos que o site use a url como seu nome oficial. If the name is not descriptive and can be considered vague, using the url is **required**. (for e.g., `YouTube` is permitted because that is the official name and is descriptive, while `youtube.com` is not. `Top` is a non-descriptive name, so using the url `top.gg` is **required**.)
- Se o serviço tiver algumas regras explícitas de atribuição de marca, você deve segui-las.

### **`*altnames`**

- **Apenas** use isso em cenários onde o website haja vários nomes oficiais (e.g. Pokémon and 포켓몬스터). Versões _abreviadas_ dos nomes dos serviços vão sob `tags`.

### **`description`**

- **Todas** as presences tem a **obrigação** de ter uma descrição em inglês independentemente do idioma preferido do site.
- **Não** tente traduzir a descrição você mesmo a menos que você conheça esse idioma, os tradutores irão modificar seu `metadata.json` e alterar as descrições se necessário.

### **`url`**

- A url **deve** ser uma string se o site usa apenas um domínio. Se o site utiliza vários, faça disso uma array e especifique cada um deles.
- **Não** inclua protocolos na url (por exemplo, `http` ou `https`) e não inclua parâmetros query na url (por exemplo, `www.google.com/search?gws_rd=ssl` no qual deve ser `www.google.com`)

### **`version`**

- Sempre tenha certeza de que o número da versão segue os [padrões de versionamento semântico](https://semver.org), o que se traduz no seguinte esquema: `<NEW-FEATURE>.<HUGE-BUGFIX>.<SMALL-BUGFIX-OR-METADATA-CHANGES>`. Qualquer outra coisa como `1.0.0.1`, `1.0`, `1`, `1.0.0-BETA` ou mudar `1.0.0` para `2.0.0` em uma correção de bug/alteração pequena **não** é permitida.
- A versão **deve** sempre começar na versão `1.0.0` a menos que se diga o contrário, outras versões **não** serão permitidas.

### **`logo`**

- A logo **deve** ser uma imagem quadrada com uma relação de aspecto `1:1`.
- É **necessário** que a imagem tenha uma resolução mínima de `512x512` pixels. Você pode aumentá-la usando uma ferramenta como [waifu2x](http://waifu2x.udp.jp/).

### **`thumbnail`**

- A thumbnail **deve** ser de preferência um [cartão promocional](https://i.imgur.com/3QfIc5v.jpg) largo ou uma [screenshot](https://i.imgur.com/OAcBmwW.png) se a primeira opção **não** estiver disponível.

### **`color`**

- The color **must** be a hexadecimal value between `#000000` and `#FFFFFF`.
- The color string **must** be prepended with a hash symbol.

### **`tags`**

- **All** presences are required to have at least _one_ tag.
- As tags **não** devem incluir espaços, barras, aspas simples/duplas, caracteres Unicode, e devem ser sempre em minúsculas.
- Tags **devem** preferencialmente incluir nomes de serviços alternativos para facilitar a busca (p. ex., se uma presence da Amazon tiver incluído o suporte pra AWS, teria suas tags como `amazon-web-services` e `aws`)
- Você é **obrigado** a adicionar uma tag `NSFW` se a presence for para um site NSFW.

### **`category`**

- A categoria **deve** ser um dos seguintes listados na [documentação](https://docs.premid.app/en/dev/presence/metadata#presence-categories).
- A presence deve utilizar uma categoria que corresponda ao conteúdo do site. (p. ex., não use `anime` quando o site não estiver relacionado à anime).

### **`*regExp`** <br /> **`*iFrameRegExp`**

- Expressões regulares **precisam** ser validas. Por favor teste suas expressões com ferramentas listadas na [documentação](https://docs.premid.app/dev/presence/metadata#testing).

### **`readLogs`**

- Deve ser `boolean` (ex. `true` ou `false`).
- Ative os logs em sua presence.

### **`warning`**

- Habilita um ícone de aviso para avisar ao usuário que essa presence precisa de mais coisas além de apenas adicionar um presence.
- Exemplo de presence usando essa variável de metadata é `VLC`.

### **`settings`**

- Se você decidir fazer uma string formatável (por ex., `%song% por %artist%`), você deve ter as variáveis com o sinal de porcentagem em ambos lados. Variáveis como `%var`, `var%`, ou `%%var%%` e qualquer coisa do tipo **não** são permitidas para fins de padronização.
- O nome das configurações **não** devem ser todas em letras maiúsculas. Por exemplo, nomes como `MOSTRAR STATUS DE NAVEGAÇÃO` **não** serão permitidos; porém, nomes como `Mostrar Status de Navegação` ou `Mostrar status de navegação` são permitidos.
- Se você estiver utilizando a opção `multiLanguage`, ela pode ter os seguintes tipos:
  - O tipo **Boolean** que só habilita strings do arquivo [`general.json`](https://github.com/PreMiD/Localization/blob/master/src/Presence/general.json) do repositório Localization ou do arquivo de presence (ex. quando o nome da presence é YouTube, a extensão vai pegar as strings do `youtube.json` também.)
  - O tipo **String** (ex. `youtube`) que vai especificar o nome dos arquivos que você quer pegar as strings.
  - O tipo **Array** (ex. `["youtube", "discord"]`) que vai especificar o nome dos arquivos que você quer pegar as strings.

## [**presence.ts**](https://docs.premid.app/dev/presence/class)

> O código que você escreve **deve** ser _bem escrito_ e **deve** ser _legível_ e todas as strings devem ser gramaticalmente corretas (erros gramaticais no websites podem ser ignorados).

> Cada presence segue um rigoroso conjunto de regras linting que será verificado durante o processo de revisão. Um par de recomendações pode ser visto abaixo. [Recomendações de Plugins TypeScript para Checagem Estrita de Tipos](https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin/docs/rules). [Recomendações de ESlint](https://eslint.org/docs/rules). [Prettier](https://prettier.io/).

Aqui está uma lista de regras que você deve seguir ao escrever seu arquivo `presence.ts`:

- **Sempre** declare uma nova instância da classe `Presence` antes de qualquer outra variável para evitar problemas raros que possam ocorrer; isto não é uma exigência por design, portanto pode ser removido no futuro.
- **Nunca** use funções customizadas quando [variantes nativas estão disponíveis](https://docs.premid.app/dev/presence#files-explained); isso garante que as correções no nível da extensão também se apliquem às suas presences. Você está livre para usar o que quiser se você não achar ela listada na documentação.
- É **proibido** programar presences para sites sem adicionar o suporte para seu idioma primário (por ex., um presence do YouTube programada apenas para Português e Japonês, mas não Inglês em si.)
- Os campos `smallImageKey` e `smallImageText` providenciam contexto adicional/secundário (como `reproduzindo/pausado` para sites de video, `navegando` para sites normais, e outros casos) não promova Perfis do Discord ou qualquer coisa não relacionada ao PreMID.
- Você **não** tem permissão para acessar o `localStorage`.
- Ao acessar cookies para dados armazenados, por favor prefixe a key com `PMD_`.
- Você pode fazer apenas solicitações HTTP/HTTPS para `premid.app` ou para o API do site da presence. Se você estiver usando domínios externos, será necessário explicar por que é necessário. A única API permitida a fazer uma solicitação é a [`Fetch API`](https://developer.mozilla.org/pt-BR/docs/Web/API/Fetch_API).
- **Não** defina os campos no objeto presenceData como undefined depois de ser declarado, use a palavra chave `delete` ao invés. (p. ex., use `delete data.startTimestamp` ao invés de `data.startTimestamp = undefined`)
- Você **não** tem permissão de escrever presences que alteram as funcionalidades de um determinado site. Isso inclui a adição, exclusão ou modificação de elementos DOM.
- Presences que usam botões devem seguir os requisitos extras:
  - Redirecionamentos para a página principal são proibidos.
  - Promover websites através delas é proibido.
  - They can't display information you couldn't fit in other fields.
  - Redirecionamento direto á transmissão de áudio/vídeo é proibido.


## [**tsconfig.json**](https://docs.premid.app/dev/presence/tsconfig)

> **Não** escreva seu próprio arquivo `tsconfig.json`, use o que foi fornecido na [documentação](https://docs.premid.app/dev/presence/tsconfig).

## Modificação

> Você **deve** alterar a versão nos **metadados** para ter um valor mais alto em relação à versão anterior ao fazer alterações em **presence.ts**, **iframe.ts** ou **metadata.json**.

Em algumas situações, presences podem se comportar de formas inesperadas ou podem usar algumas pequenas alterações para melhorar sua funcionalidade. Aqui está uma lista de regras que você **deve** seguir enquanto modifica as presences.

- Você **não** tem permissão de reescrever uma presence ou alterar seu autor. Se o autor da presence for banido do servidor oficial ou não fez as alterações necessárias dentro de um mês, você pode entrar em contato com um revisor para pedir permissão de reescrever a presence.
- Se você fizer modificações a um presence e mudar pelo menos um **quarto** do código base da presence, você terá permissão de adicionar a si mesmo como um contribuidor. Contate um revisor para mais informações sobre este assunto.
- Qualquer usuário pode fornecer hotfixes para corrigir bugs; no entanto, tente **não** fazer alterações que **não** sejam necessárias. As alterações válidas incluem correções gerais (código e erros de digitação), adições (descrições e tags), arquivos ausentes, etc. **Não** mude as imagens se elas não estiverem desatualizadas e dentro das especificações.

# Verificação

> **Todos os** códigos contribuíram para a loja serão licenciados sob a `Mozilla Public License 2.0`.

> Se precisar entrar em contato com alguém, use nosso servidor oficial do Discord. Todos os revisores terão o cargo `Reviewer` em seus perfis.

> Tenha em mente que os revisores trabalham voluntariamente e gerenciam outros repositórios além deste, seu pull request pode não ser revisado por horas ou até mesmo dias depois de criado.

> **Sempre** tenha um fork atualizado antes de criar seu pull request. Isso ajudará a limitar os falsos positivos das checagens.

O processo mais importante de desenvolvimento da presence é conseguir sua presence na loja. Isso é feito criando um [pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) pelo GitHub no repositório `PreMiD/Presences`. Nossos revisores confirmarão que sua presence está de acordo com os padrões e a enviaram para a loja.

<div>
  <h2 style="font-size: 2rem; margin-bottom: 0;">Revisores de Presence</h2>

  <a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
  <a href="https://github.com/Slowlife01"><img src="https://github.com/Slowlife01.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
  <a href="https://github.com/EncryptedDev"><img src="https://github.com/EncryptedDev.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
  <br />
</div>

## `Restrições`

Ofensas repetitivas, tais como quebra de diretrizes, spam de pull requests, ameaças ou comportamento inapropriado farão com que você seja proibido de criar presences.

Neste cenário, ocorrerão as seguintes mudanças:

- Presences que estão sob seu gerenciamento serão transferidas para o bot do PreMiD ou algum outro usuário (decisão do revisor). O id da aplicação será recriada para cada presence sob o nome do novo dono.
- Todos os seus issues e pull requests (criação de presence, contribuição de presence, etc.) criados após o banimento serão prontamente fechados.
- Tickets criados sob seu nome referentes ao desenvolvimento de presences serão excluídos.

## `Revisando`

Algumas coisas que você deve saber após abrir uma pull request:

- São necessários 2 revisores para implementar uma pull request.
- Se uma pull request estiver inativo por um período de 7 dias, ela será fechada.
- Todas as checagens **devem** ser aprovadas para que execute o merge.
- ⚠️ Você **deve** fornecer capturas de tela novas e inalteradas (tiradas por você) mostrando uma comparação lado a lado do seu perfil e do site para provar que sua presence funciona. _Você pode juntar as capturas de tela para uma visualização melhor_ Isso se aplica tanto para criação quanto para a modificação.
- ⚠️ Você também é **obrigado** á incluir as capturas de tela das configurações de presence na extensão, se fornecido. Um exemplo pode ser visto [aqui](https://imgur.com/a/OD3sj5R).

## `Checagem`

![Example of checks](https://i.imgur.com/T8agbnB.png)

Atualmente, uma presence deve passar por 3 fases separadas de checagem. Todas essas checagens ajudam os revisores a determinar se sua presença é adequada para uso.

- `Codacy` é um bot que verifica a qualidade do código. Se você receber erros por novos problemas, é **necessário** corrigi-los. *Warning: Codacy doesn't always give you errors. Please look at CodeFactor warnings instead.*
- `CodeFactor` is a bot that checks for code quality. Se você receber erros por novos problemas, é **necessário** corrigi-los.
- O `Schema Validation` irá verificar o seu arquivo `metadata.json` para identificar quaisquer erros (por exemplo, campos vazios, tipos de valores inválidos, etc.). Se você ver quaisquer novos problemas, você também **deve** corrigi-los. Adicionando um campo de esquema ao seu arquivo `metadata.json`, permitirá que seu editor de texto (se suportado) mostre esses erros durante o desenvolvimento.

## `Regras adicionais`

- **Nunca** se esqueça de iniciar sua presence na pasta mais apropriada, se seu nome começa com _qualquer_ letra latina, então deve estar sob sua correspondência alfabética (ex.: `D/dアニメストア` ou `G/Google`). Quaisquer outros caracteres Unicode/não latinos **devem** estar sob a pasta `#` (ex.: `#/巴哈姆特`) e números sob a pasta `0-9` (ex.: `0-9/4anime`).

Após atender a todas as diretrizes e ter sua Presence revisada pelo menos duas vezes, sua Presence será fundida com a loja.

# Sugestões

If you have some suggestions about our guidelines, you should contact us @ [PreMiD's Discord server](https://discord.premid.app) and we will check them!

# Contribuições

A `Revisão 3` das diretrizes foi escrita e contribuída pelos seguintes indivíduos:

<div>
<a href="https://github.com/ririxidev"><img src="https://github.com/ririxidev.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

A `Revisão 2` das diretrizes foi escrita e contribuída pelos seguintes indivíduos:

<div>
<a href="https://github.com/CobyPowers"><img src="https://github.com/CobyPowers.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

A `Revisão 1` foi mantida pelos seguintes indivíduos:

<div>
<a href="https://github.com/CobyPowers"><img src="https://github.com/CobyPowers.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/doomlerd"><img src="https://github.com/doomlerd.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>
