---
title: TypeScripti seadistamine
description: Väike abimees TypeScripti jaoks
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:45:10.473Z
---

# TypeScripti seadistamine

## Sissejuhatus

Tööruumi alla laadides ja lahti pakkides näete juur- ja olekukaustades faili nimega `tsconfig.json`, seda faili kasutatakse **TypeScripti ** koostamisel. See on teie jaoks juba konfigureeritud, nii et ärge muretsege selle pärast.

Tahame lihtsalt kirjeldada mõnda seadet, mida peaksite teadma.

## Juure seadistamine

Juurkonfiguratsiooni failis näete midagi sellist.

```json
{
  "compilerOptions": {
    "module": "CommonJS",
    "target": "ES2020",
    "removeComments": true,
    "noEmitOnError": true,
    "noFallthroughCasesInSwitch": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "inlineSourceMap": true,
    "typeRoots": ["@types"],
    "esModuleInterop": true
  }
}
```

| Vara                       | Kirjeldus                                                                                                                                                                       |
|:-------------------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **compilerOptions**        | Kasutatakse kompilaatori seadistamiseks, enamik atribuute asub siin.                                                                                                            |
| module                     | Selle kohta saate lisateavet [siit](https://www.typescriptlang.org/docs/handbook/modules.html).                                                                                 |
| target                     | Määrab teie koostatava JavaScripti versiooni.                                                                                                                                   |
| removeComments             | Kommentaaride eemaldamine kompileeritud failidest.                                                                                                                              |
| noEmitOnError              | Ärge väljastage väljundeid, kui teatati vigadest.                                                                                                                               |
| noFallthroughCasesInSwitch | Teatage vigadest juhtumite korral ülemineku avalduses.                                                                                                                          |
| noUnusedLocals             | Kasutamata kohalike vigadest teatamine.                                                                                                                                         |
| noUnusedParameters         | Kasutamata parameetrite vigadest teatamine.                                                                                                                                     |
| inlineSourceMap            | Lisab lähikaardi                                                                                                                                                                |
| typeRoots                  | Selle kohta saate lisateavet [siit](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html#types-typeroots-and-types).                                                 |
| esModuleInterop            | Emitendi __importStar ja __importDefault abistajad käitamisaja Babeli ökosüsteemi ühilduvuse jaoks ja lubage tüübisüsteemi ühilduvuse jaoks --allowSyntheticDefaultImports. |

## Presence-i seadistamine

```json
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

| Vara                | Kirjeldus                                                                                           |
|:------------------- |:--------------------------------------------------------------------------------------------------- |
| **extends**         | Kasutatakse erinevate ülesannete jaoks `tsconfig` -faili laiendamiseks.                             |
| **compilerOptions** | Lisateavet leiate jaotisest [**Juurekonfiguratsioon** ](/dev/presence/tsconfig#root-configuration). |
| outDir              | Määrab kompileeritud failide väljundkataloogi.                                                      |
