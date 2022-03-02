---
title: TypeScript কনফিগারেশন
description: TypeScript এর জন্য একটি ছোট সহায়ক
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:45:10.473Z
---

# TypeScript কনফিগারেশন

## পরিচিতি

যখন তুমি ওয়ার্কস্পেসটিকে ডাউনলোড এবং আনপ্যাক করেছ, তুমি একটি ফাইল দেখবে রুটে যার নাম `tsconfig.json` এবং Presence ফোল্ডারগুলো, এই ফাইলটি ব্যবহৃত হয় **TypeScript** কম্পাইলারকে কনফিগার করার জন্য। এটি তোমার জন্য ইতিমধ্যেই কনফিগার করা রয়েছে, তাই সেটা নিয়ে চিন্তা করবে না।

আমরা শুধু কিছু সেটিংস বর্ণনা করতে চাই যেগুলো তোমার জানা উচিত।

## রুট কনফিগারেশন

রুট কনফিগারেশন ফাইলে তুমি এরকম কিছু দেখতে পাবে।

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

| প্রপার্টিগুলো              | ডেসক্রিপশন                                                                                                                                                           |
|:-------------------------- |:-------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **compilerOptions**        | ব্যবহার করা হয় কম্পাইলারকে কনফিগার করার জন্য, বেশিরভাগ প্রপার্টিগুলো এখানে থাকে।                                                                                     |
| module                     | তুমি সেটা সম্বন্ধে আরো পড়তে পারবে [এখানে](https://www.typescriptlang.org/docs/handbook/modules.html)।                                                                |
| target                     | নির্ধারণ করে যে JavaScript ভার্সনে তুমি কম্পাইল করবে।                                                                                                                |
| removeComments             | কম্পাইল করা ফাইল থেকে কমেন্ট সরিয়ে ফেলে।                                                                                                                             |
| noEmitOnError              | আউটপুট দেয় না যদি কোনো ত্রুটি রিপোর্ট করা হয়।                                                                                                                        |
| noFallthroughCasesInSwitch | ত্রুটি রিপোর্ট করে সুইচ স্টেটমেন্টে fall-through কেসগুলোর জন্য।                                                                                                      |
| noUnusedLocals             | ত্রুটি রিপোর্ট করে অব্যবহৃত লোকালের উপর।                                                                                                                             |
| noUnusedParameters         | ত্রুটি রিপোর্ট করে অব্যবহৃত প্যারামিটারের উপর।                                                                                                                       |
| inlineSourceMap            | সোর্স ম্যাপ যুক্ত করে                                                                                                                                                |
| typeRoots                  | তুমি সেটা সম্বন্ধে আরো পড়তে পারবে [এখানে](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html#types-typeroots-and-types)।                                |
| esModuleInterop            | __importStar এবং __importDefault হেল্পার দেয় রানটাইম Babel ইকোসিস্টেম সামঞ্জস্যতার জন্য এবং অন করে --allowSyntheticDefaultImports টাইপসিস্টেম সামঞ্জস্যতার জন্য। |

## Presence কনফিগারেশন

```json
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

| প্রপার্টিগুলো       | ডেসক্রিপশন                                                                            |
|:------------------- |:------------------------------------------------------------------------------------- |
| **extends**         | ব্যবহার করা হয় মূল `tsconfig` ফাইলটিকে প্রসারিত করা বিভিন্ন কাজের জন্য।               |
| **compilerOptions** | দেখো [**রুট কনফিগারেশন**](/dev/presence/tsconfig#root-configuration) আরো তথ্যের জন্য। |
| outDir              | কম্পাইল করা ফাইলগুলোর আউটপুট ডিরেক্টরি নির্ধারণ করে।                                  |
