---
title: Forbairt Láithreachta
description:
published: true
date: 2021-07-08T19:12:34.449Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:02.843Z
---

> Stóráiltear gach uachtarán anseo anois: https://github.com/PreMiD/Presences 
> 
> {.is-info}

Leagan `2.x` tugtar isteach an [siopa láithreachta](https://premid.app/store). Anois tá sé de chumas ag úsáideoirí na láithreacha is fearr leo a chur leis agus a bhaint de láimh trí chomhéadan úsáideora an [láithreáin ghréasái](https://premid.app/).

> Sula dtosaíonn tú, moltar go mór duit breathnú ar ár dtreoirlínte láithreachta. 
> 
> {.is-warning}

- [Treoirlínte](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# Struchtúr

Tá gach láithreacht códaithe i [TypeScript](https://www.typescriptlang.org/). Tá roinnt sainmhínithe breise de chineál spíosrach ag [TypeScript](https://www.typescriptlang.org/) thar JavaScript, agus mar sin tá sé níos éasca fabhtanna a shocrú agus a aithint.

## Suiteáil

1. Suiteáil [Git](https://git-scm.com/).
2. Suiteáil [Node](https://nodejs.org/en/) (tagann sé le [npm](https://www.npmjs.com/)).
3. Suiteáil [TypeScript](https://www.typescriptlang.org/index.html#download-links) (oscail críochfort agus `npm install -g typecript`).

## Ag clónáil an tionscadail

1. Oscail críochfort agus cineál `git clone https://github.com/PreMiD/Presences`.
2. Roghnaigh fillteán de do rogha féin.
3. Oscail é i d’eagarthóir cód.

## Fillteáin agus comhaid a chruthú

1. Téigh san fhillteán `láithreáin ghréasáin` agus ansin téigh isteach san fhillteán leis an gcéad litir den **ainm** (ní URL) den tseirbhís is mian leat tacaíocht.
2. Cruthaigh fillteán leis an **ainm** (ní URL) den tseirbhís ar mhaith leat tacú leis.
3. Cruthaigh `presence.ts` agus comhad `tsconfig.json` taobh istigh.
4. Cruthaigh fillteán darb ainm `dist` taobh istigh.
5. Cruthaigh comhad `metadata.json` taobh istigh den fhillteán `dist`.

## Líon isteach an comhad tsconfig.json

Uir an cód seo a leanas taobh istigh den chomhad `tsconfig.json`.

```ts
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

Chun níos mó a fhoghlaim faoi chumraíocht TypeScript cliceáil [anseo](/dev/presence/tsconfig).

## Líon isteach an comhad metadata.json

Tá cruthaitheoir comhad `metadata.json` déanta againn do na peeps leisciúla [anseo](https://eggsy.xyz/projects/premid/mdcreator). Moltar fós é seo a léamh ionas go mbeidh a fhios agat conas a oibríonn sé.

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.5",
  "author": {
    "name": "úsáideoir",
    "id": "ID"
  },
  "contributors": [
    {
      "name": "úsáideoir",
      "id": "ID"
    }
  ],
  "service": "seirbhís",
  "altnames": ["seirbhís"],
  "description": {
    "en": "tuairisc"
  },
  "url": "URL",
  "version": "leagan",
  "logo": "URL",
  "thumbnail": "URL",
  "color": "#HEX000",
  "tags": ["TAG1", "TAG2"],
  "category": "tuairisc",
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
      "title": "teideal",
      "icon": "deilbhín",
      "value": true
    },
    {
      "id": "ID",
      "if": {
        "ID": true
      },
      "title": "teideal",
      "icon": "deilbhín",
      "value": "\"%song%\" by %artist%",
      "placeholder": "use %song% or %artist%"
    },
    {
      "id": "ID",
      "title": "teideal",
      "icon": "deilbhín",
      "value": 0,
      "values": ["1", "2", "etc."]
    }
  ]
}
```

Cóipeáil an cód thuas le do thoil agus cuir é i do chomhad `metadata.json`. Ní mór duit anois luachanna na n-airíonna a chur in eagar. Tabhair faoi deara le do thoil go bhfuil na hairíonna seo a leanas roghnach le bheith i do chomhad `metadata.json`, mura bhfuil sé beartaithe agat iad a úsáid is gá duit iad a bhaint.

- `contributors`
- `altnames`
- `regExp`
- `iframe`
- `iFrameRegExp`
- `readLogs`
- `settings`

**Soiléiriú a dhéanamh ar roinnt réamhshocruithe luacha:**

<table>
  <thead>
    <tr>
      <th style="text-align:left">Athróg</th>
      <th style="text-align:left">Cur síos</th>
      <th style="text-align:left">Cineál</th>
      <th style="text-align:left">Roghnach</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>author</b></td>
      <td style="text-align:left">Ba cheart go mbeadh an Cuspóir leis an <code>name</code> agus <code>id</code> an forbróir presence. <code>name</code> is é d’ainm úsáideora Discord gan an t-aitheantóir (#0000). Is <code>id</code> féidir an t- úsáideoir a chóipeáil ó Discord trí mhodh forbróra a chumasú agus cliceáil ar dheis ar do phróifíl.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Níl</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>contributors</b></td>
      <td style="text-align:left">Ba cheart go mbeadh an Cuspóir leis an <code>name</code> agus <code>id</code> an forbróir presence. <code>name</code> is é d’ainm úsáideora Discord gan an t-aitheantóir (#0000). Is <code>id</code> féidir an t- úsáideoir a chóipeáil ó Discord trí mhodh forbróra a chumasú agus cliceáil ar dheis ar do phróifíl.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Tá</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>service</b></td>
      <td style="text-align:left">Teideal na seirbhíse a dtacaíonn an láithreacht seo léi.<br>
       (Caithfidh an t-ainm céanna a bheith air agus atá san fhillteán ina bhfuil gach rud)</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Níl</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>altnames</b></td>
      <td style="text-align:left">A bheith in ann an láithreacht a chuardach ag úsáid ainm malartach.<br>
      An chiall atá le húsáid le haghaidh láithreacha a bhfuil ainmneacha difriúla orthu i dteangacha éagsúla (m.sh. Pokémon agus 포켓 몬스터).<br>
      Is féidir leat é a úsáid freisin le haghaidh láithreacha a bhfuil carachtair speisialta acu ionas nach gá duit iad sin a chlóscríobh (e.g. Pokémon agus Pokemon).</td>
      <td style="text-align:left"><code>Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Tá</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>description</b></td>
      <td style="text-align:left">Cur síos beag ar an láithreacht, is féidir leat tuairisc ar an tseirbhís a úsáid mura bhfuil smaointe agat. Caithfidh príomhluachanna beirte a bheith ag do thuairisc a léiríonn an teanga, agus an tuairisc sa teanga shonrach sin. Déan tuairiscí leis na teangacha <i>atá ar eolas agat</i>, déanfaidh ár n-aistritheoirí athruithe ar do chomhad metadata.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Níl</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>url</b></td>
      <td style="text-align:left">URL na seirbhíse. <br><b> Sampla: </b><code> vk.com </code><br>
       <b>Caithfidh an URL seo URL an láithreáin ghréasáin a mheaitseáil mar braithfidh sé an é seo an suíomh Gréasáin chun an script a instealladh dó. </b><br>Ná<b>NOT</b> cuir<code>https://</code> nó<code>http://</code> taobh istigh den URL ná slais ag an deireadh:
       <code>https://premid.app/</code> -><code>premid.app</code><br>
       <b>Nóta</b>: D’fhéadfadh go mbeadh<code>www.</code> nó rud éigin eile os comhair a bhfearainn ag roinnt URLanna. Ná déan dearmad <b>NOT</b> é a chur leis!<br>
       Is féidir leat URLanna iolracha a chur leis na rudaí seo a leanas a dhéanamh:<br>
       <code>["URL1", "URL2", "ETC."] </code><br>
       D’fhéadfá regExp ar a dtugtar Regex a úsáid don tasc seo freisin, a mhínítear tuilleadh thíos.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Níl</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>regExp</b></td>
      <td style="text-align:left">Teaghrán slonn rialta a úsáidtear chun urls a mheaitseáil.<br>
       is féidir regExp nó ar a dtugtar Regex freisin, a úsáid má tá iliomad fo-fearainn ag láithreán gréasáin.<br>
       D’fhéadfá an regExp seo a leanas a úsáid chuige sin:<br>
       <code>([a-z0-9] +) [.] fearann [.] TLD"</code><br>
       TLD ag seasamh don Fhearann Ardleibhéil mar shampla: .com .net (ach ná cuir isteach an ponc).<br>
       Ciallaíonn <code> ([a-z0-9] +) </code> aon rud ó a go z agus ó 0 go 9.<br>
       Is féidir leat tosaithe gasta a fháil ach féachaint ar an bhfíseán <a href="https://youtu.be/sXQxhojSdZM"></a>.<br>
       Féadfaidh tú do regExp a thástáil ag <a href="https://regex101.com/">Regex101</a>.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Tá</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>version</b></td>
      <td style="text-align:left">Leagan de do presence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Níl</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logo</b></td>
      <td style="text-align:left">Nasc le logotype na seirbhíse.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Níl</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>thumbnail</b></td>
      <td style="text-align:left">Nasc le do thumbnail presence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Níl</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>color</b></td>
      <td style="text-align:left"><code>#HEX</code> luach. Molaimid dath príomhúil na seirbhíse a thacaíonn do láithreacht leis a úsáid.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Níl</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>tags</b></td>
      <td style="text-align:left">Eagraigh le clibeanna, cuideoidh siad le húsáideoirí do láithreacht a chuardach ar an suíomh Gréasáin.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Níl</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">Teaghrán a úsáidtear chun an chatagóir ina bhfuil an láithreacht a léiriú. Féach na lónadóireacht bhailí <a href="https://docs.premid.app/dev/presence/metadata#presence-categories">anseo</a>.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Níl</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iframe</b></td>
      <td style="text-align:left">Sainmhínítear an <code>iFrames</code> úsáidtear iad	.</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Tá</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iFrameRegExp</b></td>
      <td style="text-align:left">Roghnóir slonn rialta a roghnaíonn iframanna le instealladh isteach. Féach regExp le haghaidh tuilleadh faisnéise.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Tá</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readLogs</b></td>
      <td style="text-align:left">Sainmhínítear ar cheart logaí léitheoireachta a bheith sa síneadh.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Tá</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>settings</b></td>
      <td style="text-align:left">Sraith socruithe is féidir leis an úsáideoir a athrú.<br>
       Léigh tuilleadh faoi shuíomhanna láithreachta <a href="https://docs.premid.app/dev/presence/metadata#presence-settings">anseo</a>.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Tá</code></td>
    </tr>
  </tbody>
</table>

## Ag tosú

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
  /*UpdateData is always firing, and therefore should be used as your refresh cycle, or `tick`. Tugtar é seo cúpla uair sa soicind nuair is féidir.

    It is recommended to set up another function outside of this event function which will change variable values and do the heavy lifting if you call data from an API.*/

  const presenceData: PresenceData = {
    //The key (file name) of the Large Image on the presence. These are uploaded and named in the Rich Presence section of your application, called Art Assets
    largeImageKey: "key",
    //The key (file name) of the Small Image on the presence. These are uploaded and named in the Rich Presence section of your application, called Art Assets
    smallImageKey: "key",
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

Is féidir leat é seo a chóipeáil isteach i do chomhad `presence.ts` agus na luachanna a chur in eagar. Déantar na luachanna go léir a shocrú taobh istigh den teagmhas updateData.

Mar shampla, molaimid breathnú ar chód na n-uachtarán mar: 1337x nó 9GAG. Le haghaidh tuilleadh faisnéise faoin rang `Presence` cliceáil [ anseo](/dev/presence/class).

Ó v2.2.0 tá Sleamhnáin ann anois, tugann sé seo deis duit comhéadain iolracha `PresenceData` a thaispeáint ar eatramh, chun tuilleadh faisnéise a fháil cliceáil faoin rang `Sleamhnán` [anseo](/dev/presence/slideshow).

## Ní féidir sonraí áirithe a fháil?!

Tá a lán suíomhanna Gréasáin ag úsáid [iframes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)). Is féidir foinsí éagsúla mar fhíseáin a bheith sna clibeanna html seo. Ach níl siad ábhartha gach uair. Tá cuid acu i bhfolach nó díreach ní úsáidtear go gníomhach iad. Seiceáil an féidir leat an fhaisnéis a theastaíonn uait a bhaint astu gan iad sula ndéanann tú obair gan ghá.

1. Seiceáil dóibh i do chonsól brabhsálaithe (bí cinnte go bhfuil tú ar an táb **Eilimintí**).
2. Cuardaigh (<kbd>CTRL</kbd>+<kbd>F</kbd> (Windows) nó <kbd>CMD</kbd>+<kbd>F</kbd> (MacOS)).
3. Rith `document.querySelectorAll ("iframe")`.

Má aimsíonn tú go bhfuil do chuid sonraí i iFrame ní mór duit na rudaí seo a leanas a dhéanamh:

1. Cruthaigh comhad `iframe.ts`.
2. Socraigh iFrame go `fíor` i do chomhad meiteashonraí.
3. Líon isteach do chomhad iFrame.

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

4. Má dhéantar do chomhad láithreachta faigh sonraí ón gcomhad iFrame.

```ts
presence.on("iFrameData", (data) => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

** Nóta:** Is gá é seo a chur lasmuigh den imeacht updateData.

## Tiomsú

Oscail consól i d’fhillteán agus clóscríobh `tsc -w` chun an `presence.ts` a thiomsú san fhillteán `/dist`.

# An luchtú a luchtú

1. Oscail an aníos aníos sa bhrabhsálaí agus coinnigh an cnaipe <kbd>Shift</kbd> ar do mhéarchlár.
2. Beidh **Láithreacht Luchtaithe** le feiceáil i roinn na nUachtarán.
3. Cliceáil air agus an cnaipe <kbd>Shift</kbd> á choinneáil agat fós.
4. Roghnaigh fillteán /dist do láithreachta.

# Roinnt rudaí cabhracha

## Athlódáil te

Tá an suíomh Gréasáin a bhfuil tú ag forbairt air á athlódáil go huathoibríoch gach uair a shábhálann tú comhad i d’fhillteán.

## Dífhabhtaithe

- Is féidir leat `console.log ("Tástáil");` a chur idir do chód agus féachaint an dtugann consól do bhrabhsálaí an t-aschur sin duit. Má tá, téigh ar aghaidh agus bain triail eile as tar éis an chéad fheidhm eile. Mura bhfuil, tá earráid thuas.
- Mura gcabhraíonn sé sin leat ach iarr ar fhorbróir láithreachta ar ár [Freastalaí Discord](https://discord.premid.app/) chun cabhair a fháil.

# Míníodh comhaid

- [Rang Láithreachta](/dev/presence/class)
- [Rang Taispeántas Sleamhnán](/dev/presence/slideshow)
- [Rang iFrame](/dev/presence/iframe)
- [Comhad Meiteashonraí](/dev/presence/metadata)
- [Cumraíocht TypeScript](/dev/presence/tsconfig ""){.links-list}
