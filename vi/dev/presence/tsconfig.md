---
title: Cấu hình TypeScript
description: Hỗ trợ nho nhỏ cho TypeScript
published: true
date: 2021-09-18T14:31:22.005Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:45:10.473Z
---

# Cấu hình TypeScript

## Giới thiệu

Khi bạn đã tải và giải nén không gian làm việc, bạn sẽ thấy một tệp gọi là `tsconfig.json` ở thư mục gốc và các thư mục presence, tệp này được dùng làm cấu hình cho trình biên dịch **TypeScript**. Nó đã được cấu hình sẵn, nên bạn không cần phải lo.

Chúng tôi muốn mô tả một số cài đặt bạn nên biết.

## Cấu hình gốc

Ở tệp cấu hình gốc bạn sẽ thấy một thứ như này.

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

| Thuộc tính                 | Mô tả                                                                                                                                                                    |
|:-------------------------- |:------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **compilerOptions**        | Được dùng cho trình biên dịch, đa số các thuộc tính nằm tại đây.                                                                                                         |
| module                     | Bạn có thể đọc thêm tại [đây](https://www.typescriptlang.org/docs/handbook/modules.html).                                                                                |
| target                     | Xác định phiên bản JavaScript bạn đang biên dịch.                                                                                                                        |
| removeComments             | Xoá các dòng nhận xét khỏi tệp đã được biên dịch.                                                                                                                        |
| noEmitOnError              | Không được in ra thông tin nếu có lỗi.                                                                                                                                   |
| noFallthroughCasesInSwitch | Báo lỗi trong các trường hợp nguỵ biện chuyển đổi câu lệnh.                                                                                                              |
| noUnusedLocals             | Báo cáo lỗi về các hằng số không được sử dụng.                                                                                                                           |
| noUnusedParameters         | Báo cáo lỗi về các thông số không được sử dụng.                                                                                                                          |
| inlineSourceMap            | Thêm sourcemapping                                                                                                                                                       |
| typeRoots                  | Bạn có thể đọc thêm tại [đây](https://www.typescriptlang.org/docs/handbook/tsconfig-json.html#types-typeroots-and-types).                                                |
| esModuleInterop            | Thêm các trợ giúp __importStar và __importDefault để thích nghi hệ sinh thái runtime babel và bật --allowSyntheticDefaultImports để thích nghi với hệ thống sắp chữ. |

## Cấu hình presence

```javascript
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

| Thuộc tính          | Mô tả                                                                                          |
|:------------------- |:---------------------------------------------------------------------------------------------- |
| **extends**         | Được dùng để mở rộng thêm tệp `tsconfig` mặc định cho nhiều công việc.                         |
| **compilerOptions** | Xem [**Cấu Hình Mặc Định**](/dev/presence/tsconfig#root-configuration) để biết thêm thông tin. |
| outDir              | Xác định thư mục đầu ra của các tệp đã được biên dịch.                                         |
