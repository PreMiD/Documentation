---
title: การกำหนดค่าไฟล์ Typescript
description: ตัวช่วยเล็กๆ สำหรับ Typescript
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:45:10.473Z
---

# การกำหนดค่าไฟล์ Typescript

## บทนำ

เมื่อคุณดาวน์โหลดและแตกไฟล์ออกมาแล้ว คุณจะพบกับไฟล์ชื่อ `tsconfig.json` ในโฟลเดอร์ดั้งเดิมและโฟลเดอร์ Presence ไฟล์นี้จะใช้ในการตั้งค่า Complier ของ **TypeScript** จริงๆ แล้วมันได้ถูกตั้งค่าไว้แล้ว ดังนั้น คุณไม่จำเป็นที่ต้องกังวลกับมัน

เราแค่ต้องการอธิบายการตั้งค่าบางอย่างที่คุณจำเป็นต้องรู้

## Root Configuration

In the root configuration file you will see something like this.

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

| Property                   | คำอธิบาย                                                                                                                                                            |
|:-------------------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **compilerOptions**        | Used for configuring the compiler, most of the properties are located here.                                                                                         |
| module                     | คุณสามารถอ่านข้อมูลเพิ่มเติมได้ [ที่นี่](https://www.typescriptlang.org/docs/handbook/modules.html).                                                                |
| target                     | Defines the JavaScript version you are compiling.                                                                                                                   |
| removeComments             | การลบคอมเม้นต์จากไฟล์ที่คอมไพล์                                                                                                                                     |
| noEmitOnError              | Do not emit outputs if any errors were reported.                                                                                                                    |
| noFallthroughCasesInSwitch | Report errors for fallthrough cases in switch statement.                                                                                                            |
| noUnusedLocals             | Report errors on unused locals.                                                                                                                                     |
| noUnusedParameters         | รายงานข้อผิดพลาดเกี่ยวกับพารามิเตอร์ที่ไม่ได้ใช้                                                                                                                    |
| inlineSourceMap            | เพิ่ม sourcemapping                                                                                                                                                 |
| typeRoots                  | คุณสามารถอ่านข้อมูลเพิ่มเติมได้ [ที่นี่](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html#types-typeroots-and-types).                                |
| esModuleInterop            | Emit __importStar and __importDefault helpers for runtime babel ecosystem compatibility and enable --allowSyntheticDefaultImports for typesystem compatibility. |

## การตั้งค่า Presence

```json
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

| Property            | คำอธิบาย                                                                                     |
|:------------------- |:-------------------------------------------------------------------------------------------- |
| **extends**         | Used for extending the base `tsconfig` file for various tasks.                               |
| **compilerOptions** | ดู [**Root Configuration**](/dev/presence/tsconfig#root-configuration) สำหรับข้อมูลเพิ่มเติม |
| outDir              | กำหนด Output สำหรับไฟล์ Compile แล้ว                                                         |
