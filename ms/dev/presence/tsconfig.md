---
title: Tatarajah TypeScript
description: Pembantu kecil bagi TypeScript
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:45:10.473Z
---

# Tatarajah TypeScript

## Pengenalan

Apabila anda memuat turun dan menyahpadat ruang kerja, anda akan nampak fail bernama `tsconfig.json` di akar dan dalam folder Presence, fail ini digunakan untuk menatarajah pengkompil **TypeScript**. Ia telah ditatarajah untuk anda, jadi anda tidak perlu risaukannya.

Kami cuma ingin terangkan beberapa tetapan yang anda patut tahu.

## Tatarajah Akar

Dalam fail tatarajah akar anda akan nampak sesuatu seperti ini.

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

| Sifat                      | Keterangan                                                                                                                                                                          |
|:-------------------------- |:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **compilerOptions**        | Digunakan untuk menatarajah pengkompil, kebanyakan sifat terletak di sini.                                                                                                          |
| module                     | Anda boleh baca lebih lanjut mengenainya di [sini](https://www.typescriptlang.org/docs/handbook/modules.html) (bahasa Inggeris).                                                    |
| target                     | Mentakrifkan versi JavaScript yang anda mengkompil.                                                                                                                                 |
| removeComments             | Mengalihkan ulasan daripada fail yang dikompil.                                                                                                                                     |
| noEmitOnError              | Jangan keluarkan output bagi sebarang ralat yang dilaporkan.                                                                                                                        |
| noFallthroughCasesInSwitch | Laporkan ralat bagi kes jatuh telus dalam kenyataan suis.                                                                                                                           |
| noUnusedLocals             | Laporkan ralat bagi pemboleh ubah tempatan yang tidak digunakan.                                                                                                                    |
| noUnusedParameters         | Laporkan ralat bagi parameter yang tidak digunakan.                                                                                                                                 |
| inlineSourceMap            | Tambah pemetaan sumber                                                                                                                                                              |
| typeRoots                  | Anda boleh baca lebih lanjut mengenainya di [sini](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html#types-typeroots-and-types) (bahasa Inggeris).                    |
| esModuleInterop            | Keluarkan pembantu __importStar dan __importDefault untuk keserasian ekosistem hingar waktu jalan dan membolehkan --allowSyntheticDefaultImports untuk keserasian sistem jenis. |

## Tatarajah Presence

```json
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

| Sifat               | Keterangan                                                                                   |
|:------------------- |:-------------------------------------------------------------------------------------------- |
| **extends**         | Digunakan untuk menyambung fail `tsconfig` asas bagi pelbagai tugasan.                       |
| **compilerOptions** | Lihat [**Tatarajah Akar**](/dev/presence/tsconfig#root-configuration) untuk maklumat lanjut. |
| outDir              | Mentakrifkan direktori output bagi fail yang dikompil.                                       |
