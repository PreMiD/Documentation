---
title: Konfigurácia TypeScriptu
description: Malilinký pomocník pre TypeScript
published: true
date: 2021-09-18T14:42:32.522Z
tags: 
editor: markdown
dateCreated: 2021-09-07T01:57:58.454Z
---

# Konfigurácia TypeScriptu

## Úvod

Keď ste si stiahli a rozbalili pracovnú plochu, uvidíte súbor nazývaný sa `tsconfig.json` v koreni a v priečinkoch prítomnosti, tento súbor je určený na konfigurovanie **TypeScript** spracovávateľa. Je už dopredu nakonfigurovaný pre vás, takže nemusíte sa obávať.

Chceme vám len popísať niektoré nastavenia ktoré by ste mali vedieť.

## Konfigurácia Koreňa

V koreni konfiguračného súboru uvidíte niečo takéto podobné.

```javascript
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

| Property                   | Popis                                                                                                                                                               |
|:-------------------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **compilerOptions**        | Používaný na konfiguráciu kompiliera, väčšina vlastností sa nachádza tu.                                                                                            |
| module                     | Môžete si prečítať viacej o tom [tu](https://www.typescriptlang.org/docs/handbook/modules.html).                                                                    |
| target                     | Definuje verziu JavaScriptu ktorú kompilujete.                                                                                                                      |
| removeComments             | Odstránenie komentárov z už kompilovaných súborov.                                                                                                                  |
| noEmitOnError              | Do not emit outputs if any errors were reported.                                                                                                                    |
| noFallthroughCasesInSwitch | Report errors for fallthrough cases in switch statement.                                                                                                            |
| noUnusedLocals             | Report errors on unused locals.                                                                                                                                     |
| noUnusedParameters         | Report errors on unused parameters.                                                                                                                                 |
| inlineSourceMap            | Adds sourcemapping                                                                                                                                                  |
| typeRoots                  | Môžete si prečítať viacej o tom [tu](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html#types-typeroots-and-types).                                    |
| esModuleInterop            | Emit __importStar and __importDefault helpers for runtime babel ecosystem compatibility and enable --allowSyntheticDefaultImports for typesystem compatibility. |

## Konfigurácia Prítomnosti

```javascript
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

| Property            | Popis                                                                                            |
|:------------------- |:------------------------------------------------------------------------------------------------ |
| **extends**         | Používa sa na rozšírenie základného súboru `tsconfig` na rôzne úlohy.                            |
| **compilerOptions** | Pozrite [**Koreň Konfigurácie**](/dev/presence/tsconfig#root-configuration) pre viac informácii. |
| outDir              | Definuje výstupný adresár pre kompilované súbory.                                                |
