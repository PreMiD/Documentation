---
title: Konfigurasi TypeScript
description: Bantuan kecil untuk TypeScript
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:45:10.473Z
---

# Konfigurasi TypeScript

## Perkenalan

Ketika kamu telah mendownload dan mengunpack workspace, kamu akan melihat file bernama `tsconfig.js` pada root dan folder presence, file ini digunakan untuk mengatur compiler **TypeScript**. Itu sudah terkonfigurasi untukmu, jadi tidak perlu khawatir.

Kami hanya ingin menjelaskan beberapa pengaturan yang harus kamu ketahui.

## Konfigurasi Root

Pada file konfigurasi root kamu akan melihat hal seperti ini.

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

| Properti                   | Deskripsi                                                                                                                                                         |
|:-------------------------- |:----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **compilerOptions**        | Digunakan untuk mengatur compiler, sebagian besar dari property disimpan disini.                                                                                  |
| module                     | Anda dapat membacanya lebih lanjut tentang hal tersebut [disini](https://www.typescriptlang.org/docs/handbook/modules.html).                                      |
| target                     | Menentukan versi JavaScript yang sedang dicompile.                                                                                                                |
| removeComments             | Menghapus komentar dari file telah dicompile.                                                                                                                     |
| noEmitOnError              | Tidak memberikan output jika ada eror yang terlaporkan.                                                                                                           |
| noFallthroughCasesInSwitch | Melaporkan eror untuk fallthrough case di pernyataan peralihan.                                                                                                   |
| noUnusedLocals             | Melaporkan eror pada unused locals.                                                                                                                               |
| noUnusedParameters         | Melaporkan eror pada unused parameter.                                                                                                                            |
| inlineSourceMap            | Menambahkan sourcemapping                                                                                                                                         |
| typeRoots                  | Kamu bisa membacanya lebih lanjut [disini](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html#types-typeroots-and-types).                            |
| esModuleInterop            | Emit __importStar dan __importDefault helpers untuk kompatibilitas babel ecosystem dan enable --allowSyntheticDefaultImports untuk kompatibilitas typesystem. |

## Konfigurasi Presence

```json
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

| Properti            | Deskripsi                                                                                        |
|:------------------- |:------------------------------------------------------------------------------------------------ |
| **extends**         | Digunakan untuk menambahkan base file `tsconfig` untuk berbagai macam tugas.                     |
| **compilerOptions** | Lihat [**Konfigurasi Root**](/dev/presence/tsconfig#root-configuration) untuk info lebih lanjut. |
| outDir              | Menentukan direktori output dari file terkompilasi.                                              |
