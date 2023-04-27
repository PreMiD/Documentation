---
title: Treoirlínte Láithreachta
description: Rialacha nach mór do gach forbróir láithreachta a leanúint chun a láithreacht a chur leis.
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:53.883Z
---

<div align="center">
    <img src="https://github.com/PreMiD.png?size=2048" width="128px" style="max-width:100%;">
    <h3 style="font-size: 2rem; margin-bottom: 0">Treoirlínte Láithreachta</h3>
    <h4 style="margin-top: 0">Athbhreithniú 3</h4>
    <br />
</div>

# Treoirlínte

Agus Presences á bhfoilsiú ag ár [Stór GitHub](https://github.com/PreMiD/Presences), éilímid ort tacar treoirlínte a leanúint. I gcás roinnt daoine, d’fhéadfadh go mbeadh cuma dhian ar na rialacha dochta seo. Mar sin féin, coimeádfaidh cur i bhfeidhm na dtacar rialacha seo muid féin agus ár n-úsáideoirí ó shaincheisteanna.

# Cruthú

Is iad seo a leanas rialacha ginearálta fhorbairt láithreachta:

- Caithfidh Láithreachtaí a bheith bainteach leis an suíomh Gréasáin is rogha leat.
- Ní féidir láithreacha a dhéanamh do láithreáin ghréasáin neamhdhleathacha. (mar shampla, strusóirí, margaíocht drugaí, pornagrafaíocht leanaí, srl.)
- Caithfidh struchtúr na gcomhad a bheith glan agus bainistithe, ná cuir comhaid nach bhfuil sonraithe san áireamh. (le haghaidh e.g. fillteáin vscode agus git, comhaid íomhá agus téacs, srl.)
- Ní mór duit struchtúr ceart comhad a bheith agat, ní cheadaítear **dréachtaí**.
- **Ní cheadaítear** láithreacha do shuíomhanna Gréasáin le (`.onion` TLDs) nó láithreáin ghréasáin le fearainn/óstach saor in aisce (mar shampla `.TK` [gach fearann Freenom saor in aisce], `.RF`, `GD`, srl), is féidir eisceachtaí a dhéanamh má chuirtear cruthúnas i láthair a thaispeánann go bhfuil d’íoc siad as an bhfearann.
- Caithfidh fearann an láithreachta a bheith 2 mhí d'aois ar a laghad.
- Láithreacht a dhíríonn ar leathanaigh inmheánacha brabhsálaí (cosúil le Chrome Web Store, `chrome://`, `faoi:` leathanaigh, srl) ná ** ní **ceadaítear/láidir de réir mar a éilíonn siad bratach turgnamhach a chumasú ag deireadh an úsáideora agus d’fhéadfadh sé damáiste a dhéanamh dá mbrabhsálaithe.
- ** Ní cheadófar** láithreacha nach dtacaíonn ach le haon fho-fhearann amháin, mar is cosúil go bhfuil siad briste do leathanaigh eile (cosúil leis an leathanach baile), is féidir eisceachtaí a dhéanamh maidir leis an mbeartas agus an teagmháil leathanaigh (ábhar nach n-úsáidtear go minic) nó suíomhanna nach bhfuil baint ag an ábhar eile leo. (le haghaidh e.g., leathanaigh wikia)
- Ní cheadaítear láithreacha do raidiónna ar líne ach má tá 100 éisteoir seachtainiúil ar a laghad agus 15 comhthráthach ag an raidió agus ní mór go mbeadh roinnt gnéithe ann seachas teideal albam/amhrán, etc. a thaispeáint.
- Ní cheadaítear do láithreacha cód JS a reáchtáil lena bhfeidhm féin chun athróga a fháil. Má tá fadhbanna ag Firefox le feidhm ionsuite laistigh de rang `Láithreachta`, tá cead agat d’fheidhm féin a dhéanamh agus ní mór duit é a insint dúinn sa tuairisc Iarratas Tarraingthe.
- Ní cheadaítear uachtaráin ar cháilíocht íseal (nó cinn nach bhfuil mórán comhthéacs acu) **ní cheadaítear** (mar shampla, gan ach lógó agus téacs a thaispeáint ach gan iad a athrú arís).
- Caithfidh láithreacha do sheirbhísí cosúil le Discord Bot/Liostaí Freastalaí na riachtanais bhreise seo a leanúint:
  - Ba chóir go mbeadh an fearann ar a laghad **6 mhí** d'aois.
  - Cuairteoirí uathúla in aghaidh an lae:
    - Maidir le fearainn 6 go 12 mhí d'aois: **20,000 cuairteoir/lá uathúil**.
    - Maidir le fearainn 12+ mí: ** 45,000 cuairteoir/lá uathúil **.
  - Ní féidir an suíomh Gréasáin a bheith ar fhearann saor mar `.xyz`, `.club` agus mar sin de.
  - Caithfidh cáilíocht, dearadh, srl an-mhaith a bheith ag an suíomh Gréasáin féin.
- Ba cheart go n-úsáidfeadh láithreacha [sonraí coitianta](https://api.premid.app/v2/langFile/presence/en) (teaghráin ag tosú le "ginearálta."). Is féidir leat é seo a bhaint amach trí `multiLanguage` a úsáid leis na teaghráin a chuirtear ar fáil. Má tá teaghráin shaincheaptha de dhíth ar do láithreacht, níor cheart duit `multiLanguage` a úsáid go dtí go bhfaighidh 1000 úsáideoir an láithreacht. Is féidir leat sampla [a fháil anseo](https://docs.premid.app/dev/presence/class#getstringsobject).
- Lena n-áirítear an fillteán `dist`, tá comhad `presence.ts`, comhad `iframe.ts`, agus comhad `metadata.json` éigeantach mar sin bheadh an toradh ar an méid a léirítear sa scéimre seo a leanas:

```bash
presence
├── dist
│   └── metadata.json
├── presence.ts
└── tsconfig.json
```

nó má tá tú ag úsáid comhad `iframe.ts`:

```bash
presence
├── dist
│   └── metadata.json
├── presence.ts
├── iframe.ts
└── tsconfig.json
```

## [**metadata.json**](https://docs.premid.app/dev/presence/metadata)

> Ar mhaithe le caoithiúlacht ár bhforbróirí láithreachta, tá scéimre curtha ar fáil againn is féidir leat a úsáid chun sláine do chomhad `meiteashonraí` a bhailíochtú. Tá sé seo roghnach go hiomlán agus ní theastaíonn sé le linn an phróisis athbhreithnithe.

> Moltar go mór duit do chomhad `meiteashonraí` a eagrú san fhormáid a thaispeántar thíos, agus caithfidh ainmneacha seirbhíse, tuairiscí, clibeanna agus réimsí suímh atá ceart ó thaobh gramadaí de a bheith agat. Aon rud nach bhfuil eagraithe de réir sonraíochtaí ** ní cheadófar**.

> Ní mór go mbeadh an chlib `nsfw` ag láithreacha suíomhanna Gréasáin a bhfuil ábhar sainráite **acu, agus caithfidh an lógó/mionsamhail** **níl** aon chuid den ábhar seo ann.

Tá comhad tuairiscithe ag gach láithreacht ar a dtugtar `metadata.json`, tá caighdeán docht ag na meiteashonraí agus is féidir sampla den chomhad seo a fheiceáil thíos:

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.7",
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

> Má tá réimse liostaithe mar réimse roghnach ar andoiciméadacht<a> nó má tá <code>*</code> in aice leis an eochair, agus má úsáideann do láithreacht an luach réamhshocraithe dó, ná cuir san áireamh í sa chomhad <code>meiteashonraí</code>. (mar shampla, ní bheadh an réimse <code>iframe</code> de dhíth ar láithreacht gan tacaíocht iframe.)</p> </blockquote> 
> 
> <blockquote spaces-before="0">
>   <p spaces-before="0">
>     Caithfear gach íomhá sa chomhad <code>meiteashonraí</code> a óstáil ar <code>i.imgur.com</code>. <strong x-id="1">Ní cheadaítea</strong> ábhar a óstáiltear ar an suíomh Gréasáin toisc gur féidir leo na cosáin agus na comhaid a athrú go toilteanach.
>   </p>
> </blockquote>
> 
> <p spaces-before="0">
>   Tá liosta de na réimsí agus a rialacha liostaithe thíos:
> </p>
> 
> <h3 spaces-before="0">
>   <strong x-id="1"><code>$schema</code></strong>
> </h3>
> 
> <ul>
>   <li>
>     <strong x-id="1">Ní mór</strong> go mbeadh comhartha dollar ag an scéimre <em x-id = "4">eochair</em> cuirfidh sé seo in iúl d’eagarthóir téacs go bhfuil tú ag iarraidh do chomhad JSON a bhailíochtú i gcoinne samhail. <em x-id = "4"> Mar a dúradh cheana, ní gá duit scéimre a áireamh, ach má chuireann tú san áireamh é caithfidh tú é sin a chur san áireamh. </em>
>   </li>
> </ul>
> 
> <h3 spaces-before="0">
>   <strong x-id="1"><code>author</code></strong>
> </h3>
> 
> <ul>
>   <li>
>     <strong x-id="1">Ní mór</strong> gurb é an ID <em x-id = "4"> luach </em> ID sciathán sneachta Discord. Is féidir leat é a fháil trí <a href = "https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID- " >modh forbróra</a>. <em x-id = "4">Ná déan<strong x-id = "1"> le do thoil </strong> déan é seo a mheascadh le d’aitheantas iarratais, nach bhfuil ann ach do láithreacht. </em>
>   </li>
> </ul>
> 
> <h3 spaces-before="0">
>   <strong x-id="1"><code>*contributors</code></strong>
> </h3>
> 
> <ul>
>   <li>
>     <strong x-id="1">Ná cuir</strong> tú féin mar ranníocóir, agus ná cuir duine eile mar ranníocóir mura chuidigh siad leis an láithreacht.
>   </li>
> </ul>
> 
> <h3 spaces-before="0">
>   <strong x-id="1"><code>service</code></strong>
> </h3>
> 
> <ul>
>   <li>
>     <strong x-id="1">Ní mór</strong> gurb é ainm na seirbhíse ainm an eolaire láithreachta. Mar shampla, má tá an láithreacht suite ag <code>/websites/Y/YouTube/</code>, ní mór ainm na seirbhíse a bheith <code>YouTube</code>.
>   </li>
>   <li>
>     <strong x-id="1">Ní féidir</strong> leat an url a úsáid mar ainm seirbhíse mura n-úsáideann an suíomh Gréasáin an url mar ainm oifigiúil. Mura bhfuil an t-ainm tuairisciúil agus más féidir é a mheas doiléir, <strong x-id="1">tá gá</strong> an url a úsáid. (le haghaidh e.g., ceadaítear <code>YouTube</code> toisc gurb é sin an t-ainm oifigiúil agus go bhfuil sé tuairisciúil, cé nach bhfuil <code>youtube.com</code>. Is ainm neamh-thuairisciúil é <code>Top</code>, mar sin tá <strong x-id = "1">riachtanach</strong> ag baint úsáide as an url <code>top.gg</code>)
>   </li>
>   <li>
>     Má tá roinnt rialacha brandála follasacha ag a n-ainm, ba cheart duit iad a leanúint.
>   </li>
> </ul>
> 
> <h3 spaces-before="0">
>   <strong x-id="1"><code>*altnames</code></strong>
> </h3>
> 
> <ul>
>   <li>
>     <strong x-id = "1">Amháin</strong> úsáid é seo i gcásanna ina dtéann suíomh Gréasáin faoi iliomad ainmneacha oifigiúla (e.g. Pokémon agus 포켓 몬스터). <em x-id = "4">Téann leaganacha giorraithe</em> d’ainmneacha seirbhíse faoi <code>chlibeanna</code>.
>   </li>
> </ul>
> 
> <h3 spaces-before="0">
>   <strong x-id="1"><code>description</code></strong>
> </h3>
> 
> <ul>
>   <li>
>     <strong x-id="1">Tá gá</strong> le <strong x-id="1">gach láithreachta</strong> tuairisc Bhéarla a bheith acu beag beann ar an rogha teanga ar an suíomh Gréasáin.
>   </li>
>   <li>
>     <strong x-id="1">Ná déan</strong> iarracht an tuairisc a aistriú leat féin mura bhfuil an teanga sin ar eolas agat, athróidh aistritheoirí do <code>metadata.json</code> agus athróidh siad na tuairiscí más gá.
>   </li>
> </ul>
> 
> <h3 spaces-before="0">
>   <strong x-id="1"><code>url</code></strong>
> </h3>
> 
> <ul>
>   <li>
>     <strong x-id="1">Ní mór</strong> sreangán a bheith san url mura n-úsáideann an suíomh Gréasáin ach fearann amháin. Má úsáideann an láithreán gréasáin iolrach, déan eagar air seo agus sonraigh gach ceann acu.
>   </li>
>   <li>
>     <strong x-id="1">Ná cuir</strong> prótacail san url (mar shampla, <code>http</code> nó<code>https</code>), agus ná cuir paraiméadair fiosrúcháin san url (mar shampla, <code>www.google.com/search?gws_rd=ssl</code> ba chóir a bheith <code> www.google.com</code>)
>   </li>
> </ul>
> 
> <h3 spaces-before="0">
>   <strong x-id="1"><code>version</code></strong>
> </h3>
> 
> <ul>
>   <li>
>     Always make sure the version number follows <a href="https://semver.org">semantic versioning standards</a>, which translates to the following scheme: <code>&lt;MAJOR&gt;.&lt;MINOR&gt;.&lt;PATCH&gt;</code>. Rud ar bith eile cosúil le <code>1.0.0.1</code>, <code>1.0</code>, <code>1</code>, <code>1.0.0-BETA</code> nó ag athrú <code>1.0. 0</code> go <code>2.0.0</code> ar shocrú fabht/tá athrú beag <strong x-id="1">ní cheadaítear</strong>.
>   </li>
>   <li>
>     <strong x-id="1">Ní mór</strong> tús a chur leis an leagan i gcónaí ag <code>1.0.0</code> mura n-insítear a mhalairt, <strong x-id="1">ní cheadófar</strong> leaganacha eile.
>   </li>
> </ul>
> 
> <h3 spaces-before="0">
>   <strong x-id="1"><code>logo</code></strong>
> </h3>
> 
> <ul>
>   <li>
>     <strong x-id="1">Ní mór</strong> íomhá chearnach a bheith ar an lógó le cóimheas gné <code>1:1</code>.
>   </li>
>   <li>
>     The image is <strong x-id="1">required</strong> to have a resolution of <code>512x512</code> pixels. You can resize it using a tool like <a href="https://imageresizer.com/">imageresizer</a>.
>   </li>
> </ul>
> 
> <h3 spaces-before="0">
>   <strong x-id="1"><code>thumbnail</code></strong>
> </h3>
> 
> <ul>
>   <li>
>     <strong x-id="1">Ba chóir</strong> go mbeadh an mionsamhail b'fhearr a bheith ina <a href="https://i.imgur.com/3QfIc5v.jpg">cárta poiblíochta leathan</a> nó <a href="https://i.imgur.com/OAcBmwW.png">pictiúr</a> <strong x-id="1">mura bhfuil</strong> an chéad cheann ar fáil.
>   </li>
> </ul>
> 
> <h3 spaces-before="0">
>   <strong x-id="1"><code>color</code></strong>
> </h3>
> 
> <ul>
>   <li>
>     <strong x-id="1">Ní mór</strong> an dath a bheith ina luach heicsidheachúlach idir <code>#000000</code> agus <code>#FFFFFF</code>.
>   </li>
>   <li>
>     <strong x-id="1">Ní mór</strong> an tsreang datha a chaitheamh le siombail hash.
>   </li>
> </ul>
> 
> <h3 spaces-before="0">
>   <strong x-id="1"><code>tags</code></strong>
> </h3>
> 
> <ul>
>   <li>
>     Ceanglaítear ar <strong x-id="1">gach</strong> láithreachta clib <em x-id="4">amháin</em> ar a laghad a bheith acu.
>   </li>
>   <li>
>     <strong x-id="1">Ní mór</strong> do ní clibeanna aon spásanna, slashes, comharthaí athfhriotail singil/dúbailte, carachtair Unicode a áireamh, agus ba chóir go mbeadh siad i gcónaí i litreacha beaga.
>   </li>
>   <li>
>     B’fhearr le clibeanna <strong x-id="1">ba chóir</strong> ainmneacha malartacha seirbhíse a áireamh chun cuardach a dhéanamh níos éasca (mar shampla, dá mbeadh tacaíocht AWS san áireamh i láithreacht Amazon, bheadh a chlibeanna air mar <code>amazon-web-services</code> agus <code>aws</code>)
>   </li>
>   <li>
>     Tá tú <strong x-id="1">cead</strong> chun clib <code>NSFW</code> a chur leis má tá tú i láthair ar shuíomh Gréasáin NSFW.
>   </li>
> </ul>
> 
> <h3 spaces-before="0">
>   <strong x-id="1"><code>category</code></strong>
> </h3>
> 
> <ul>
>   <li>
>     <strong x-id="1">Ní mór</strong> an chatagóir a bheith ar cheann de na rudaí seo a leanas atá liostaithe ar an <a href="https://docs.premid.app/dev/presence/metadata#presence-categories">doiciméadacht</a>.
>   </li>
>   <li>
>     Caithfidh an láithreacht catagóir a úsáid a oireann d’ábhar an láithreáin ghréasáin. (mar shampla, ná bain úsáid as <code>anime</code> nuair nach bhfuil baint ag an suíomh Gréasáin le hanam).
>   </li>
> </ul>
> 
> <h3 spaces-before="0">
>   <strong x-id="1"><code>*regExp</code></strong> <br /> <strong x-id="1"><code>*iFrameRegExp</code></strong>
> </h3>
> 
> <ul>
>   <li>
>     <strong x-id="1">Ní mór</strong> nathanna rialta a bheith bailí. Déan do chuid nathanna a thástáil leis na huirlisí atá liostaithe ar an <a href="https://docs.premid.app/dev/presence/metadata#testing">doiciméadacht</a>.
>   </li>
> </ul>
> 
> <h3 spaces-before="0">
>   <strong x-id="1"><code>readLogs</code></strong>
> </h3>
> 
> <ul>
>   <li>
>     Ní mór luach <code>boolean</code> a bheith aige (e.g. <code>true</code> nó <code>false</code>).
>   </li>
>   <li>
>     Cumasaíonn sé logaí do do láithreacht.
>   </li>
> </ul>
> 
> <h3 spaces-before="0">
>   <strong x-id="1"><code>warning</code></strong>
> </h3>
> 
> <ul>
>   <li>
>     Cumasaíonn sé deilbhín rabhaidh chun an t-úsáideoir a spreagadh go gcaithfidh an láithreacht seo níos mó céimeanna ná láithreacht a chur leis.
>   </li>
>   <li>
>     Sampla de láithreacht ag baint úsáide as an athróg meiteashonraí seo is ea <code>VLC</code>.
>   </li>
> </ul>
> 
> <h3 spaces-before="0">
>   <strong x-id="1"><code>settings</code></strong>
> </h3>
> 
> <ul>
>   <li>
>     Má shocraíonn tú sreang formáide a dhéanamh (mar shampla, <code>%song% leis an %artist%</code>), caithfidh na hathróga a bheith timpeallaithe ag comhartha faoin gcéad ar gach taobh. Tá athróga cosúil le <code>%var</code>, <code>var%</code>, nó <code>%%var%%</code> agus aon rud eatarthu <strong x-id = "1">ní cheadaítear</strong> ar mhaithe le caighdeánú.
>   </li>
>   <li>
>     Ní mór ainm na socruithe <strong x-id = "1">ní</strong> a bheith i ngach ceannlitir. Mar shampla, <strong x-id="1">ní cheadófar</strong> ainmneacha mar <code>TAISPEÁIN STÁDAS BRABHSÁLA</code>; áfach, ceadaítear ainmneacha mar <code>Taispeáin Stádas Brabhsála </code>nó<code> Taispeáin stádas brabhsála</code>.
>   </li>
>   <li>
>     Má tá an rogha <code>multiLanguage</code> á úsáid agat féadfaidh na cineálacha seo a leanas a bheith aige: <ul>
>       <li>
>         <strong x-id = "1">Boole</strong> cineál nach gcumasóidh ach teaghráin ó <a href = "https://github.com/PreMiD/Localization/blob/master/src/Presence/general.json "><code>general.json</code></a> ón repo Logánú nó ón gcomhad láithreachta (m.sh. nuair is YouTube ainm na láithreachta, gheobhaidh an síneadh teaghráin ó <code>youtube.json</code> freisin.)
>       </li>
>       <li>
>         <strong x-id = "1">Teaghrán</strong> cineál (e.g. <code>youtube</code>) a shonróidh ainm na gcomhad ar mhaith leat teaghráin a fháil uathu.
>       </li>
>       <li>
>         <strong x-id = "1"> Eagar<String></strong> cineál (m.sh. <code>["youtube", "discord"]</code>) a shonróidh ainm na gcomhad a theastaíonn uait a dhéanamh faigh teaghráin ó.
>       </li>
>     </ul>
>   </li>
> </ul>
> 
> <h2 spaces-before="0">
>   <a href="https://docs.premid.app/dev/presence/class"><strong x-id="1">presence.ts</strong></a>
> </h2>
> 
> <blockquote spaces-before="0">
>   <p spaces-before="0">
>     <strong x-id="1">Ní mór</strong> an cód a scríobhann tú a bheith <em x-id = "4"> dea-scríofa </em> agus <strong x-id = "1"> ní mór </strong>a<em x-id = "4">inléite</em> agus caithfidh gach sreang a bheith ceart ó thaobh na gramadaí de (is féidir neamhaird a dhéanamh ar earráidí gramadaí ar láithreáin ghréasáin).
>   </p>
> </blockquote>
> 
> <blockquote spaces-before="0">
>   <p spaces-before="0">
>     Leanann gach láithreacht tacar rialacha dian linting a seiceálfar le linn an phróisis athbhreithnithe. Is féidir cúpla moladh a fheiceáil thíos. <a href="https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin/docs/rules">Moltaí Breiseán TypeScript maidir le Seiceáil Cineál Dian</a>. <a href="https://eslint.org/docs/rules">Moltaí ESlint</a>. <a href="https://prettier.io/">Prettier</a>.
>   </p>
> </blockquote>
> 
> <p spaces-before="0">
>   Seo liosta de na rialacha a chaithfidh tú a leanúint agus do chomhad <code>presence.ts</code> á scríobh:
> </p>
> 
> <ul>
>   <li>
>     <strong x-id = "1"> I gcónaí </strong> dearbhaigh sampla nua den aicme <code>Presence</code> roimh aon athróg eile chun saincheisteanna neamhchoitianta a d’fhéadfadh tarlú a sheachaint; ní riachtanas de réir dearaidh é seo agus d’fhéadfaí é a bhaint amach anseo.
>   </li>
>   <li>
>     <strong x-id = "1">Ná</strong> bain úsáid as feidhmeanna saincheaptha nuair a bhíonn <a href="https://docs.premid.app/dev/presence#files-explained"> leaganacha dúchasacha ar fáil </a>; déanann sé seo cinnte go mbaineann socruithe ar leibhéal an fhadaithe le do láithreachtaí freisin. Tá cead agat gach rud a theastaíonn uait a úsáid mura bhfaigheann tú iad liostaithe sna docs.
>   </li>
>   <li>
>     Tá sé <strong x-id="1">cosc láidir</strong> uachtaráin a chódú do shuíomh gan tacaíocht a chur lena phríomhtheanga (mar shampla, láithreacht YouTube atá códaithe le tacaíocht do Portueguese agus Seapáinis amháin, ach ní an Béarla féin.)
>   </li>
>   <li>
>     Tá sé i gceist ag na réimsí <code>smallImageKey</code> agus <code>smallImageText</code> comhthéacs breise/tánaisteach a sholáthar (mar shampla <code>seinm/sos</code> do shuíomhanna físe, <code>brabhsáil</code> do shuímh rialta, agus cásanna eile) gan próifílí Discord nó aon rud nach mbaineann le PreMiD a chur chun cinn.
>   </li>
>   <li>
>     <strong x-id="1">Ní cheadaítear</strong> duit rochtain a fháil ar <code>localStorage</code>.
>   </li>
>   <li>
>     Agus fianáin á rochtain agat ar shonraí stóráilte, cuir an eochair le <code>PMD_</code> le do thoil.
>   </li>
>   <li>
>     Ní féidir leat ach iarratais HTTP/HTTPS a dhéanamh ar <code>premid.app</code> nó API an láithreáin ghréasáin láithreachta. Má tá fearainn sheachtracha á n-úsáid agat, iarrfar ort a mhíniú cén fáth go bhfuil gá leis. Is é an t-aon API a cheadaítear iarratas a dhéanamh ná <a href="https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API"><code>Fetch API</code></a>.
>   </li>
>   <li>
>     <strong x-id="1">Ná</strong> leag réimsí sa réad láithreachtData atá neamhshainithe tar éis a dhearbhú, bain úsáid as an eochairfhocal <code>scriosadh</code> ina ionad. (mar shampla, bain úsáid as <code>scrios data.startTimestamp</code> in ionad <code>data.startTimestamp = undefined</code>)
>   </li>
>   <li>
>     <strong x-id="1">Ní cheadaítear</strong> duit uachtaráin a scríobh a athraíonn feidhmiúlacht láithreán gréasáin ar leith. Áirítear leis seo eilimintí DOM a chur leis, a scriosadh nó a mhodhnú.
>   </li>
>   <li>
>     Ba cheart go leanfadh láithreacha a úsáideann cnaipí riachtanais bhreise: <ul>
>       <li>
>         Tá cosc ar atreoruithe chuig an bpríomhleathanach.
>       </li>
>       <li>
>         Tá cosc ar láithreáin ghréasáin a chur chun cinn.
>       </li>
>       <li>
>         Ní féidir leo faisnéis nach raibh tú oiriúnach i réimsí eile a thaispeáint.
>       </li>
>       <li>
>         Tá cosc ar atreorú díreach chuig sruth fuaime/físe.
>       </li>
>     </ul>
>   </li>
> </ul>
> 
> <h2 spaces-before="0">
>   <a href="https://docs.premid.app/dev/presence/tsconfig"><strong x-id="1">tsconfig.json</strong></a>
> </h2>
> 
> <blockquote spaces-before="0">
>   <p spaces-before="0">
>     Ná <strong x-id="1">ní</strong> scríobh do chomhad <code>tsconfig.json</code> féin, bain úsáid as an méid atá curtha ar fáil ar <a href="https://docs.premid.app/dev/presence/tsconfig">doiciméadú</a>.
>   </p>
> </blockquote>
> 
> <h2 spaces-before="0">
>   Modhnú
> </h2>
> 
> <blockquote spaces-before="0">
>   <p spaces-before="0">
>     <strong x-id="1">Ní mór</strong> duit an leagan sa <strong x-id="1">mheiteashonraí</strong> a athrú chun go mbeidh luach níos airde ón leagan roimhe seo agus athruithe á ndéanamh agat ar an <strong x-id="1"> presence.ts </strong>, <strong x-id="1">iframe.ts</strong> nó <strong x-id="1"> metadata.json</strong>.
>   </p>
> </blockquote>
> 
> <p spaces-before="0">
>   I roinnt cásanna, d’fhéadfadh láithreachta iad féin a iompar gan choinne nó d’fhéadfaidís roinnt mionathruithe a úsáid chun a bhfeidhmiúlacht a fheabhsú. Seo liosta de na rialacha <strong x-id="1">ní mór</strong> duit a leanúint agus tú ag athrú uachtaráin.
> </p>
> 
> <ul>
>   <li>
>     Murar féidir teagmháil a dhéanamh le húdar na láithreachta le breis agus mí, féadfaidh tú teagmháil a dhéanamh le hathbhreithneoir le fáil amach an féidir leat an láithreacht a mhodhnú.
>   </li>
>   <li>
>     Má dhéanann tú modhnuithe ar láithreacht agus má athraíonn tú <strong x-id = "1">ráithe</strong> ar a laghad de bhunchód an láithreachta, tá cead agat tú féin a chur mar ranníocóir. Téigh i dteagmháil le hathbhreithneoir chun tuilleadh faisnéise a fháil faoin ábhar seo.
>   </li>
>   <li>
>     Féadfaidh duine ar bith PR a chruthú chun fabhtanna a shocrú. <strong x-id="1">Ná</strong> athraigh íomhánna mura bhfuil siad as dáta agus má tá siad i sonraíochtaí.
>   </li>
> </ul>
> 
> <h1 spaces-before="0">
>   Deimhniú
> </h1>
> 
> <blockquote spaces-before="0">
>   <p spaces-before="0">
>     <strong x-id="1"> Beidh gach cód </strong> a chuirtear leis an siopa ceadúnaithe faoin <code> Ceadúnas Poiblí Mozilla 2.0 </code>.
>   </p>
> </blockquote>
> 
> <blockquote spaces-before="0">
>   <p spaces-before="0">
>     Más gá duit teagmháil a dhéanamh le duine, bain úsáid as ár bhfreastalaí Discord oifigiúil. Beidh ról <code>Reviewer</code> ag gach athbhreithneoir ar a bpróifíl.
>   </p>
> </blockquote>
> 
> <blockquote spaces-before="0">
>   <p spaces-before="0">
>     Coinnigh i gcuimhne, le do thoil, go n-oibríonn na hathbhreithneoirí go deonach agus go ndéanann siad stórtha eile a bhainistiú sa bhreis ar an gceann seo, b’fhéidir nach ndéanfar athbhreithniú ar d’iarratas tarraingthe go dtí uaireanta nó fiú laethanta tar éis a chruthaithe.
>   </p>
> </blockquote>
> 
> <blockquote spaces-before="0">
>   <p spaces-before="0">
>     <strong x-id="1"> I gcónaí </strong> bíodh forc cothrom le dáta agat sula ndéanann tú d’iarratas tarraingthe a chruthú. Cabhróidh sé seo le rudaí dearfacha bréagacha a theorannú ó na seiceálacha.
>   </p>
> </blockquote>
> 
> <p spaces-before="0">
>   Is é an próiseas is tábhachtaí d’fhorbairt láithreachta ná do láithreacht a fháil ar an siopa. Déantar é seo trí iarraidh <a href="https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request">pull request</a> a dhéanamh ar GitHub ar an stór <code> PreMiD/Presences </code>. Deimhneoidh ár n-athbhreithneoirí go bhfuil do láithreacht de réir na gcaighdeán agus brúfaidh siad ar an siopa é.
> </p>

<div>
  <h2 style="font-size: 2rem; margin-bottom: 0;">Athbhreithneoirí Láithreachta</h2>
  <a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
  <a href="https://github.com/EncryptedDev"><img src="https://github.com/EncryptedDev.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

> 
> <h2 spaces-before="0">
>   <code>Srianta</code>
> </h2>
> 
> <p spaces-before="0">
>   Cuirfidh cionta athchleachtacha amhail treoirlínte a bhriseadh, iarrataí tarraingthe spamála, bagairtí nó iompar míchuí cosc ort uachtaráin a chruthú.
> </p>
> 
> <p spaces-before="0">
>   Sa chás seo, tarlóidh na hathruithe seo a leanas:
> </p>
> 
> <ul>
>   <li>
>     Aistreofar láithreacha faoi do bhainistíocht chuig bot PreMiD nó chuig úsáideoir eile (cinneadh an athbhreithnitheora). Athchruthófar an id iarratais do gach láithreacht faoi ainm an úinéara nua.
>   </li>
>   <li>
>     Dúnfar go pras do chuid saincheisteanna agus iarratais tarraingthe go léir (cruthú láithreachta, ranníocaíocht láithreachta, srl.) A cruthaíodh tar éis an toirmisc.
>   </li>
>   <li>
>     Scriosfar ticéid a cruthaíodh faoi d’ainm maidir le forbairt láithreachta.
>   </li>
> </ul>
> 
> <h2 spaces-before="0">
>   <code>Athbhreithniú</code>
> </h2>
> 
> <p spaces-before="0">
>   Cúpla rud ba chóir a bheith ar eolas agat tar éis duit iarratas tarraingthe a oscailt:
> </p>
> 
> <ul>
>   <li>
>     Tógann sé ar 2 athbhreithneoir iarratas tarraingthe a chumasc.
>   </li>
>   <li>
>     Má tá iarratas tarraingthe neamhghníomhach ar feadh tréimhse 7 lá, dúnfar é go pras.
>   </li>
>   <li>
>     <strong x-id="1">Ní mór</strong> gach seic a rith chun cumasc.
>   </li>
>   <li>
>     ⚠️ <strong x-id="1">Ní mór</strong> duit scáileáin scáileáin nua gan athrú a thógáil (tógtha agat) a thaispeánann comparáid taobh le taobh ar do phróifíl agus ar an suíomh Gréasáin chun a chruthú go n-oibríonn do láithreacht. <em x-id = "4"> Tá cead agat scáileáin scáileáin a chur le chéile chun pléisiúr a fheiceáil </em> Baineann sé seo le cruthú agus modhnú araon.
>   </li>
>   <li>
>     ⚠️ Tá tú freisin <strong x-id = "1">ceach</strong> chun scáileáin scáileáin de na socruithe láithreachta a áireamh sa síneadh má sholáthraítear iad. Is féidir sampla a fheiceáil <a href="https://imgur.com/a/OD3sj5R"> anseo </a>.
>   </li>
> </ul>
> 
> <h2 spaces-before="0">
>   <code>Seiceálacha</code>
> </h2>
> 
> <p spaces-before="0">
>   <img src="https://i.imgur.com/vF7QpBH.png" alt="Sampla de sheiceálacha" />
> </p>
> 
> <p spaces-before="0">
>   Faoi láthair, téann láithreacht trí 3 chéim ar leithligh de sheiceálacha. Cuidíonn na seiceálacha seo go léir leis na hathbhreithneoirí a chinneadh an bhfuil do láithreacht oiriúnach le himscaradh.
> </p>
> 
> <ul>
>   <li>
>     Is bot é <code>DeepScan</code> a dhéanann seiceáil ar cháilíocht an chóid. Má fhaigheann tú earráidí riamh maidir le saincheisteanna nua, tá tú <strong x-id = "1"> ag teastáil </strong> chun iad a shocrú. <em x-id = "3"> Rabhadh: Ní thugann DeepScan earráidí duit i gcónaí. Féach rabhaidh CodeFactor ina ionad. </em>
>   </li>
>   <li>
>     Is bot é <code> CodeFactor </code> a dhéanann seiceáil ar cháilíocht an chóid. Má fhaigheann tú earráidí riamh maidir le saincheisteanna nua, tá tú <strong x-id = "1"> ag teastáil </strong> chun iad a shocrú.
>   </li>
>   <li>
>     Déanfaidh <code> Schema Validation </code> do chomhad <code> metadata.json </code> a scanadh le haghaidh aon earráidí (mar shampla, réimsí atá in easnamh, cineálacha luacha neamhbhailí, srl.). Má fheiceann tú aon cheisteanna nua riamh, tá tú <strong x-id = "1"> ceacht </strong> chun iad sin a shocrú. Trí réimse scéimre a chur le do chomhad <code> metadata.json </code> ligfidh d’eagarthóir téacs (má thacaítear leis) na hearráidí seo a thaispeáint duit le linn na forbartha.
>   </li>
> </ul>
> 
> <h2 spaces-before="0">
>   <code>Rialacha Breise</code>
> </h2>
> 
> <ul>
>   <li>
>     <strong x-id = "1"> I gcónaí </strong> déan cinnte do láithreacht a thosú san fhillteán is oiriúnaí, má thosaíonn a ainm le <em x-id = "4"> aon </em> litir Laidineach ansin caithfidh sé a bheith faoina mheaitseáil aibítreach (mar shampla, <code> D/dア ニ メ ス ト ア </code> nó <code> G/Google </code>). <strong x-id="1">Ní mór</strong> aon charachtair Unicode/neamh-Laidine eile a bheith faoin bhfillteán <code>#</code> (mar shampla, <code> #/巴哈姆特 </code>) agus uimhreacha faoin <code>0-9 fillteán </code> (mar shampla, <code> 0-9/4anime</code>).
>   </li>
> </ul>
> 
> <p spaces-before="0">
>   Tar éis duit na treoirlínte go léir a chomhlíonadh leis na hathbhreithnithe agus na seiceálacha cearta, déanfar do láithreacht a chumasc leis an siopa.
> </p>
> 
> <h1 spaces-before="0">
>   Moltaí
> </h1>
> 
> <p spaces-before="0">
>   Tá roinnt moltaí agat maidir lenár dtreoirlínte, ba cheart duit teagmháil a dhéanamh linn @ <a href="https://discord.premid.app"> Freastalaí Discord PreMiD </a> agus déanfaimid iad a sheiceáil!
> </p>
> 
> <h1 spaces-before="0">
>   Ranníocaíochtaí
> </h1>
> 
> <p spaces-before="0">
>   Scríobhadh <code>Athbhreithniú 3</code> de na treoirlínte agus chuir na daoine seo a leanas leis:
> </p>

<div>
<a href="https://github.com/PreMiD"><img src="https://github.com/PreMiD.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

> 
> <p spaces-before="0">
>   Scríobhadh <code>Athbhreithniú 2</code> de na treoirlínte agus chuir na daoine seo a leanas leis:
> </p>

<div>
<a href="https://github.com/CobyPowers"><img src="https://github.com/CobyPowers.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

> 
> <p spaces-before="0">
>   Choinnigh na daoine seo a leanas <code>Athbhreithniú 1</code>:
> </p>

<div>
<a href="https://github.com/CobyPowers"><img src="https://github.com/CobyPowers.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/i1u5"><img src="https://github.com/i1u5.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>
