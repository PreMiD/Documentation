---
title: TypeScript Configuratie
description: Een kleine helper voor TypeScript
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:45:10.473Z
---

# TypeScript configuratie

## Introductie

Wanneer je de workspace hebt gedownload en uitgepakt, zie je een bestand met de naam `tsconfig.json` in root- en presencemappen, dit bestand wordt gebruikt voor het configureren van de **TypeScript** compiler. Het is al geconfigureerd voor jou, dus maak je geen zorgen daarover.

We willen alleen enkele instellingen beschrijven die je zou moeten kennen.

## Root Configuratie

In het root configuratiebestand ziet u zoiets als deze.

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

| Eigenschappen              | Beschrijving                                                                                                                                                                        |
|:-------------------------- |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **compilerOptions**        | Gebruikt voor het configureren van de compiler, de meeste eigenschappen bevinden zich hier.                                                                                         |
| module                     | Je kunt er meer over lezen [hier](https://www.typescriptlang.org/docs/handbook/modules.html).                                                                                       |
| target                     | Definieert de JavaScript-versie die u aan het compileren bent.                                                                                                                      |
| removeComments             | Verwijder reacties uit gecompileerde bestanden.                                                                                                                                     |
| noEmitOnError              | Uitvoer niet uit als er fouten zijn gemeld.                                                                                                                                         |
| noFallthroughCasesInSwitch | Rapporteer fouten voor fallthrough gevallen in switch statements.                                                                                                                   |
| noUnusedLocals             | Rapporteer fouten bij ongebruikte localen.                                                                                                                                          |
| noUnusedParameters         | Rapporteer fouten bij ongebruikte parameters.                                                                                                                                       |
| inlineSourceMap            | Voegt sourcemapping toe                                                                                                                                                             |
| typeRoots                  | Je kunt er meer over lezen [hier](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html#types-typeroots-and-types).                                                       |
| esModuleInterop            | Laat __importStar en __importStandaard helpers los voor runtime babel ecosysteem compatibiliteit en schakel --allowSyntheticDefaultImports voor typesysteem compatibiliteit in. |

## Presence Configuratie

```json
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

| Eigenschappen       | Beschrijving                                                                           |
|:------------------- |:-------------------------------------------------------------------------------------- |
| **extends**         | Gebruikt voor het uitbreiden van het bestand `tsconfig` voor verschillende taken.      |
| **compilerOptions** | Zie [**Root Configuratie**](/dev/presence/tsconfig#root-configuration) voor meer info. |
| outDir              | Definieert de uitvoermap voor gecompileerde bestanden.                                 |
