---
title: Configurare TypeScript
description: Un mic ajutor pentru TypeScript
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:45:10.473Z
---

# Configurare TypeScript

## Introducere

Când ați descărcat și despachetat spațiul de lucru, veți vedea un fișier numit `tsconfig.json` în folderele rădăcină și prezență, acest fișier este utilizat pentru configurarea **TypeScript** compilator. Este deja configurat pentru tine, așa că nu-ți face griji pentru asta.

Vrem doar să descriem câteva setări pe care ar trebui să le cunoașteți.

## Configurare rădăcină

În fișierul de configurare rădăcină veți vedea ceva de genul acesta.

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

| Proprietate                | Descriere                                                                                                                                                                                                     |
|:-------------------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **compilerOptions**        | Folosit pentru configurarea compilatorului, majoritatea proprietăților se află aici.                                                                                                                          |
| module                     | Puteți citi mai multe despre asta [aici](https://www.typescriptlang.org/docs/handbook/modules.html).                                                                                                          |
| target                     | Definește versiunea JavaScript pe care o compilați.                                                                                                                                                           |
| removeComments             | Eliminarea comentariilor din fișierele compilate.                                                                                                                                                             |
| noEmitOnError              | Nu emite ieșiri dacă au fost raportate erori.                                                                                                                                                                 |
| noFallthroughCasesInSwitch | Raportați erorile pentru cazurile de pierdere în declarația switch.                                                                                                                                           |
| noUnusedLocals             | Raportați erori privind localurile nefolosite.                                                                                                                                                                |
| noUnusedParameters         | Raportați erorile privind parametrii neutilizați.                                                                                                                                                             |
| inlineSourceMap            | Adăugări de mapare sursă                                                                                                                                                                                      |
| typeRoots                  | Puteți citi mai multe despre asta [aici](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html#types-typeroots-and-types).                                                                          |
| esModuleInterop            | Emit __importStar și __importDefault ajutoare pentru compatibilitatea cu ecosistemul Babel în timpul de execuție și activarea --allowSyntheticDefaultImports pentru compatibilitatea cu sistemele de tip. |

## Configurarea prezenței

```json
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

| Proprietate         | Descriere                                                                                               |
|:------------------- |:------------------------------------------------------------------------------------------------------- |
| **extends**         | Folosit pentru extinderea bazei `tsconfig` dosar pentru diverse sarcini.                                |
| **compilerOptions** | Vezi [**Configurare rădăcină**](/dev/presence/tsconfig#root-configuration) pentru mai multe informații. |
| outDir              | Definește directorul de ieșire pentru fișierele compilate.                                              |
