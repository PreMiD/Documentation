---
title: Налаштування TypeScript
description: Маленький помічник для TypeScript
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:45:10.473Z
---

# Налаштування TypeScript

## Вступ

Коли ви завантажили та розпаковували робочу область, ви побачите файл з назвою `tsconfig.json` в теках root і presence, цей файл використовується для налаштування компіляції **TypeScript**. Він вже настроєний для вас, тому не хвилюйтеся за це.

Ми просто хочемо описати деякі налаштування, які вам слід знати.

## Налаштування root доступу

У кореневому файлі конфігурації ви побачите щось на зразок цього.

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

| Property                   | Опис                                                                                                                                                                |
|:-------------------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **compilerOptions**        | Використовується для налаштування компілятора, більшість властивостей розташовані тут.                                                                              |
| module                     | Детальніше про це ви можете прочитати [тут](https://www.typescriptlang.org/docs/handbook/modules.html).                                                             |
| target                     | Визначає версію JavaScript, яку ви збираєте.                                                                                                                        |
| removeComments             | Видалення коментарів зі скомпільованих файлів.                                                                                                                      |
| noEmitOnError              | Do not emit outputs if any errors were reported.                                                                                                                    |
| noFallthroughCasesInSwitch | Report errors for fallthrough cases in switch statement.                                                                                                            |
| noUnusedLocals             | Report errors on unused locals.                                                                                                                                     |
| noUnusedParameters         | Report errors on unused parameters.                                                                                                                                 |
| inlineSourceMap            | Adds sourcemapping                                                                                                                                                  |
| typeRoots                  | Детальніше про це ви можете прочитати [тут](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html#types-typeroots-and-types).                             |
| esModuleInterop            | Emit __importStar and __importDefault helpers for runtime babel ecosystem compatibility and enable --allowSyntheticDefaultImports for typesystem compatibility. |

## Конфігурація Presence

```json
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

| Property            | Опис                                                                                                     |
|:------------------- |:-------------------------------------------------------------------------------------------------------- |
| **extends**         | Використовується для продовження базового `tsconfig` файлу для різних завдань.                           |
| **compilerOptions** | Дивіться [**налаштування кореня**](/dev/presence/tsconfig#root-configuration) для додаткової інформації. |
| outDir              | Визначає каталог виводу для скомпільованих файлів.                                                       |
