---
title: iFrameクラス
description: 
published: true
date: 2021-09-18T14:37:37.554Z
tags: 
editor: markdown
dateCreated: 2021-09-07T01:52:14.367Z
---

# iFrameクラス

## 説明

場合によっては、 `iframe` の内部の要素にアクセスする必要があるかもしれません。

`iframe.ts`ファイルの中に書かれたコードは、ページのすべての iFrame に挿入されます。

プレゼンスと同様に、 `iframe` はデータを自動的に更新するように設計された独自のクラスを持っています。

```typescript
let iframe = new iFrame();

iframe.on("UpdateData", async () => {
    // Code goes here...
});
```

## メソッド

### `send(Object)`
プレゼンスにデータを送ります。 この方法を使用すると、プレゼンスが`iFrameData`のeventを投下します。

### `getUrl()`
`iframe` のURLを返します。

## イベント
`iframe`のイベントは`presence`クラスでの動作と同様に動作します。

```typescript
iframe.on("UpdateData", async () => {
    // Code goes here...
});
```

イベントの一覧:

#### `UpdateData`

このイベントはiFrameが更新されるたびに呼び出されます。
