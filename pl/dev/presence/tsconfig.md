---
title: Konfiguracja TypeScript
description: Mały pomocnik do TypeScript
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:45:10.473Z
---

# Konfiguracja TypeScript

## Wprowadzenie

Po pobraniu i rozpakowaniu obszaru roboczego, zobaczysz plik o nazwie `tsconfig.json` w folderach root i presence, ten plik jest używany do konfigurowania kompilatora **TypeScript**. Jest już dla Ciebie skonfigurowany, nie martw się o to.

Chcemy tylko opisać kilka ustawień, o których powinieneś wiedzieć.

## Konfiguracja roota

W głównym pliku konfiguracyjnym zobaczysz coś takiego.

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

| Właściwość                 | Opis                                                                                                                                                            |
|:-------------------------- |:--------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **compilerOptions**        | Używane do konfigurowania kompilatora, większość właściwości znajduje się tutaj.                                                                                |
| module                     | Więcej na ten temat znajdziesz [tu](https://www.typescriptlang.org/docs/handbook/modules.html).                                                                 |
| target                     | Określa wersję JavaScript, którą kompilujesz.                                                                                                                   |
| removeComments             | Usuwanie komentarzy ze skompilowanych plików.                                                                                                                   |
| noEmitOnError              | Nie emituj danych wyjściowych, jeśli zgłoszono jakieś błędy.                                                                                                    |
| noFallthroughCasesInSwitch | Zgłasza błędy dla przypadków awaryjnych w instrukcji switch.                                                                                                    |
| noUnusedLocals             | Zgłasza błędy na nieużywanych lokalnych.                                                                                                                        |
| noUnusedParameters         | Zgłasza błędy dotyczące nieużywanych parametrów.                                                                                                                |
| inlineSourceMap            | Dodaje sourcemapping                                                                                                                                            |
| typeRoots                  | Więcej na ten temat znajdziesz [tu](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html#types-typeroots-and-types).                                 |
| esModuleInterop            | Emituj __importStar i ___importDefault - pomoce dla kompatybilności ekosystemów babel i włącz --allowSyntheticDefaultImport dla kompatybilności typesystem. |

## Konfiguracja Presence

```json
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

| Właściwość          | Opis                                                                                                      |
|:------------------- |:--------------------------------------------------------------------------------------------------------- |
| **extends**         | Używane do rozszerzenia podstawowego pliku `tsconfig` dla różnych zadań.                                  |
| **compilerOptions** | Zobacz [**Konfigurację Root**](/dev/presence/tsconfig#root-configuration), aby uzyskać więcej informacji. |
| outDir              | Określa katalog wyjściowy skompilowanych plików.                                                          |
