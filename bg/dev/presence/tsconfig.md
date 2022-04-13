---
title: TypeScript Конфигурация
description: Малък помощник за TypeScript
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:45:10.473Z
---

# TypeScript Конфигурация

## Въведение

Когато сте изтеглили и разархивирали работното пространство, ще видите файл, наречен `tsconfig.json` в главната папка и папките на presences, този файл се използва за конфигуриране на **TypeScript** компилирането. Той вече е конфигуриран за вас, така че не се притеснявайте за това.

Искаме само да опишем някои настройки, които трябва да знаете.

## Root конфигурация

В главния конфигурационен файл ще видите нещо подобно.

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

| Property                   | Описание                                                                                                                                                                                               |
|:-------------------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **compilerOptions**        | Used for configuring the compiler, most of the properties are located here.                                                                                                                            |
| module                     | Можете да прочетете повече за това [тук](https://www.typescriptlang.org/docs/handbook/modules.html).                                                                                                   |
| target                     | Определя версията на JavaScript, която се компилира.                                                                                                                                                   |
| removeComments             | Премахване на коментари от компилираните файлове.                                                                                                                                                      |
| noEmitOnError              | Не излъчвайте изходна информация, ако са отчетени грешки.                                                                                                                                              |
| noFallthroughCasesInSwitch | Съобщаване на грешки за пропуснати случаи в декларацията switch.                                                                                                                                       |
| noUnusedLocals             | Съобщаване на грешки за неизползвани локали.                                                                                                                                                           |
| noUnusedParameters         | Съобщаване на грешки за неизползвани параметри.                                                                                                                                                        |
| inlineSourceMap            | Добавя sourcemapping                                                                                                                                                                                   |
| typeRoots                  | Можете да прочетете повече за това [тук](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html#types-typeroots-and-types).                                                                   |
| esModuleInterop            | Изпратете помощниците __importStar и __importDefault за съвместимост с екосистемата на Babel по време на изпълнение и разрешете --allowSyntheticDefaultImports за съвместимост с типовата система. |

## Presence Конфигурация

```json
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

| Property            | Описание                                                                                       |
|:------------------- |:---------------------------------------------------------------------------------------------- |
| **extends**         | Използва се за разширяване на основния файл `tsconfig` за различни задачи.                     |
| **compilerOptions** | Вижте [**Root конфигурация**](/dev/presence/tsconfig#root-configuration) за повече информация. |
| outDir              | Определя изходната директория за компилираните файлове.                                        |
