---
title: Lớp iFrame
description:
published: true
date: 2021-09-18T14:31:12.831Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:57.665Z
---

# Lớp iFrame

## Giới thiệu

Trong một số trường hợp, presence của bạn sẽ phải truy cập yếu tố ở bên trong `iframe`.

Đoạn mã bạn viết trong tệp `iframe.ts` được nhét vào mọi iframe trên trang.

Như presence, `iframe` có lớp riêng của nó để tự động cập nhật dữ liệu.

```ts
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    // Đưa đoạn mã vào đây...
});
```

## Phương pháp

### `send(Object)`
Gửi dữ liệu đến presence. Sử dụng phương thức này sẽ khiến presence ném vào một sự kiện `iFrameData`.

### `getUrl()`
Đưa trả URL của `iframe`.

## Sự kiện
Trong `iframe`, các sự kiện hoạt động tương tự như trong lớp `presence`.

```ts
iframe.on("UpdateData", async () => {
    // Đưa đoạn mã vào đây...
});
```

Đây là danh sách tất cả các sự kiện:

#### `UpdateData`

This event is fired every time the iframe is being updated.
