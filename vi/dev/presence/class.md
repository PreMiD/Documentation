---
title: Lớp Presence
description: Lớp chính cho mọi presence của PreMiD
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:50.164Z
---

# Lớp Presence

## Giới thiệu

Lớp `Presence` rất hữu ích vì nó có các phương thức cơ bản mà chúng ta cần để tạo một presence.

Khi tạo một lớp, bạn phải chỉ định thuộc tính `clientId`.

```ts
const presence = new Presence({
  clientId: "514271496134389561" // clientID mẫu
});
```

### Thuộc tính

Có ba thuộc tính có sẵn cho lớp `Presence`.

#### `clientId`

Thuộc tính phải được cung cấp để làm cho Presence của bạn hoạt động, bởi vì nó sử dụng id ứng dụng của bạn để hiển thị biểu tượng và các giá trị. Bạn có thể tải nó trên [ trang ứng dụng ](https://discordapp.com/developers/applications).

#### `injectOnComplete` - *Không được sử dụng từ 2.2.4*

Khi đặt `injectOnComplete` sang `true` sự kiện `UpdateData` đầu tiên cho cả hai tệp `presence.ts` và `iframe.ts` sẽ chỉ được tải lên khi trang đã tải xong.

#### `appMode` - *Không được sử dụng từ 2.2.4*

Khi đặt `appMode` sang `true` và presence gửi đi một `PresenceData` rỗng, ứng dụng sẽ hiện lên (ảnh và tên) hồ sơ người dùng thay vì không có gì.

## Phương pháp

### `getActivity()`

Đưa trả object `PresenceData` của presence đang được hiển thị.

### `setActivity(PresenceData | Slideshow, Boolean)`

Đặt hoạt động trên hồ sơ của bạn dựa theo dữ liệu đã được đưa.

Tham số đầu tiên yêu cầu một giao diện [`PresenceData`](#presencedata-interface) hoặc một lớp [`Slideshow`](/dev/presence/slideshow) để lấy tất cả các thông tin bạn muốn hiển thị lên hồ sơ của mình.

Tham số thứ hai quyết định xem presence có đang hoạt động hay không. Luôn sử dụng `true` nếu bạn sử dụng mốc thời gian trong `PresenceData`.

### `clearActivity()`

Đặt lại hoạt động hiện tại của bạn và tiêu đề thanh.

### `setTrayTitle(String)` - *Không được sử dụng từ 2.2.3*

> Phương thức này chỉ hoạt động trên Mac OS.
>
> {.is-warning}

Đặt tiêu đề thanh trên Menubar.

### `createSlideshow()`

Tạo một lớp `Slideshow` mới.

```ts
const slideshow = presence.createSlideshow();
```

Bạn nên làm điều này ngay sau khi tạo lớp `Presence`:

```ts
const presence = new Presence({
    clientId: "514271496134389561" // clientId mẫu
  }),
  slideshow = presence.createSlideshow();
```

Bạn có thể tìm tài liệu cho lớp `Slideshow` [tại đây](/dev/presence/slideshow).

### `getStrings(Object)`

Một phương thức không đồng bộ để giúp bạn lấy các chuỗi đã được phiên dịch từ phần mở rộng.

Bạn phải cung cấp `Object` với từ khoá dành cho chuỗi, `keyValue` là giá trị của chuỗi. Một danh sách các chuỗi đã được phiên dịch có thể được tìm thấy ở điểm đầu cuối này: `https://api.premid.app/v2/langFile/presence/vi_VN/`

```ts
// Đưa lại chuỗi `Đang phát` và `Đã dừng`
// từ phần mở rộng.
const strings = await presence.getStrings({
  play: "general.playing",
  pause: "general.paused"
});

const playString = strings.play; // kết quả: Đang phát
const pauseString = strings.pause; // kết quả: Đã dừng
```

Từ v2.2.0 của phần mở rộng bạn có thể lấy chuỗi của một ngôn ngữ nhất định. Chức năng này hoạt động tốt với cài đặt mới được thêm `multiLanguage`.

Chúng tôi khuyên bạn nên sử dụng đoạn mã sau để nó tự động cập nhật PresenceData nếu người dùng thay đổi ngôn ngữ được chọn;

```ts
async function getStrings() {
  return presence.getStrings(
    {
      play: "general.playing",
      pause: "general.paused"
    },
    // ID là ID của cài đặt multiLanguage.
    await presence.getSetting("ID").catch(() => "en");
  );
}

let strings = getStrings(),
  // ID là ID của cài đặt multiLanguage.
  oldLang: string = await presence.getSetting("ID").catch(() => "en");

//! Đoạn mã này phải nằm trong sự kiện updateData!
// The ID is the ID of the multiLanguage setting.
const newLang = await presence.getSetting("ID").catch(() => "en");
if (oldLang !== newLang) {
  oldLang = newLang;
  strings = getStrings();
}

const playString = (await strings).play, // kết quả: Đang phát
  pauseString = (await strings).pause; // kết quả: Đã dừng
```

### `getPageletiable(String)`

Đưa trả một biến từ trang web nếu nó xuất hiện.

**Cảnh báo: Chức năng này có thể gây ra lượng sử dụng CPU cao & trang web chậm lại khi lệnh đã được thực thi quá nhiều lần.**

```ts
const pageVar = presence.getPageletiable("pageVar");
console.log(pageVar); // Đoạn mã này sẽ ghi lại "Nội dung có thể làm biến"
```

### `getExtensionVersion(Boolean)`

Đưa trả phiên bản của phần mở rộng người dùng đang sử dụng.

```ts
getExtensionVersion(onlyNumeric?: boolean): string | number;

const numeric = presence.getExtensionVersion();
console.log(numeric); // Sẽ ghi lại 210
const version = presence.getExtensionVersion(false);
console.log(version); // Sẽ ghi lại 2.1.0
```

### `getSetting(String)`

Đưa ra giá trị của cài đặt.

```ts
const setting = await presence.getSetting("pdexID"); //Thay pdexID bằng id trong cài đặt
console.log(setting); // Mã này sẽ ghi lại giá trị của cài đặt
```

### `hideSetting(String)`

Ẩn cài đặt được đưa ra.

```ts
presence.hideSetting("pdexID"); // Thay pdexID bằng id của cài đặt
```

### `showSetting(String)`

Hiện cài đặt được đưa ra (Chỉ hoạt động khi cài đặt đã được ẩn từ trước).

```ts
presence.showSetting("pdexID"); // Thay pdexID bằng id của cài đặt
```

### `getLogs()`

Đưa trả các ghi chép của bảng điều khiển trang web.

```ts
const logs = await presence.getLogs();
console.log(logs); // Đoạn mã này sẽ ghi lại 100 ghi chép gần nhất (trong một mảng).
```

**Ghi chú:** Yêu cầu `readLogs` phải là `true` trong tệp `metadata.json`.

### `info(String)`

In tin nhắn đã được đưa ra vào trong bảng điều khiển trong định dạng dựa theo kiểu `info` của presence.

```ts
presence.info("Test") // Đoạn mã sẽ ghi lại "test" trong định dạng phù hợp.
```

### `success(String)`

In tin nhắn đã được đưa ra vào trong bảng điều khiển trong định dạng dựa theo kiểu ` success` của presence.

```ts
presence.success("Test") // Đoạn mã sẽ ghi lại "test" trong định dạng phù hợp.
```

### `error(String)`

In tin nhắn đã được đưa ra vào trong bảng điều khiển trong định dạng dựa theo kiểu `error` của presence.

```ts
presence.error("Test") // Đoạn mã sẽ ghi lại "test" trong định dạng phù hợp.
```

### `getTimestampsfromMedia(HTMLMediaElement)`

Đưa trả 2 mốc thời gian `snowflake` trong một `Array` có thể sử dụng được cho `startTimestamp` và `endTimestamp`.

```ts
const timestamps = presence.getTimestampsfromMedia(document.querySelector(".video"));
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Ghi chú:** Đoạn `String` được đưa ra trong querySelector là một ví dụ.

### `getTimestamps(Number, Number)`

Đưa trả 2 mốc thời gian `snowflake` trong một `Array` có thể sử dụng được cho `startTimestamp` và `endTimestamp`.

```ts
const video = document.querySelector(".video"),
  timestamps = presence.getTimestamps(video.currentTime, video.duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Ghi chú:** Đoạn `String` được đưa ra trong querySelector là một ví dụ.

### `timestampFromFormat(String)`

Chuyển đổi một chuỗi có định dạng `HH:MM:SS` hoặc `MM:SS` hoặc `SS` thành một số nguyên (Không đưa trả mốc thời gian snowflake).

```ts
const currentTime = presence.timestampFromFormat(document.querySelector(".video-now").textContent),
  duration = presence.timestampFromFormat(document.querySelector(".video-end").textContent),
  timestamps = presence.getTimestamps(currentTime, duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Ghi chú:** Đoạn `String` được đưa ra trong querySelector là một ví dụ.

## Giao diện `PresenceData`

Giao diện `PresenceData` được khuyên dùng khi bạn đang sử dụng phương thức `setActivity()`.

Giao diện này có những biến sau, tất cả đều không bắt buộc.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Biến số</th>
      <th style="text-align:left">Mô tả</th>
      <th style="text-align:left">Kiểu</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">details</td>
      <td style="text-align:left">Dòng đầu tiên trong presence của bạn, thông thường là tiêu đề.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">state</td>
      <td style="text-align:left">Dòng thứ hai trong presence của bạn.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">startTimestamp</td>
      <td style="text-align:left">Xác định thời gian hiện tại<br>
        Được dùng nếu bạn muốn hiển thị còn bao nhiêu <code>giờ:phút:giây</code>.
          <br>Bạn phải chuyển đổi thời gian sang <code>timestamp</code> hoặc sẽ có thời gian đếm ngược
          không chính xác.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">endTimestamp</td>
      <td style="text-align:left">Xác định thời lượng đầy đủ.
        <br>Được dùng nếu bạn muốn hiển thị còn bao nhiêu <code>giờ:phút:giây</code>.
          <br>Bạn phải chuyển đổi thời gian sang <code>timestamp</code> hoặc sẽ có thời gian đếm ngược
          không chính xác.
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">largeImageKey</td>
      <td style="text-align:left">Xác định biểu tượng của presence.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageKey</td>
      <td style="text-align:left">Xác định ảnh nhỏ bên cạnh biểu tượng của presence.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageText</td>
      <td style="text-align:left">Xác định nội dung sẽ được hiển thị khi người dùng di chuột lên trên
        ảnh nhỏ.</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
        <tr>
      <td style="text-align:left">buttons</td>
      <td style="text-align:left">Mảng các nút, tối đa 2, nhãn là nội dung của nút, url là đường liên kết.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code>
      </td>
    </tr>
  </tbody>
</table>

```ts
const presenceData: PresenceData = {
  details: "Tiêu đề của tôi",
  state: "Đoạn mô tả của tôi",
  largeImageKey: "biểu_tượng_dịch_vụ",
  smallImageKey: "ảnh_nhỏ_dịch_vụ",
  smallImageText: "Bạn vừa di chuột lên tôi",
  startTimestamp: 1564444631188,
  endTimestamp: 1564444634734,
  buttons: [
    {
            label: "Nút thử 1",
            url: "https://premid.app/"
        },
        {
            label: "Nút thử 2",
            url: "https://premid.app/contributors"
        }
    ]
};
```

## Sự kiện

Các sự kiện cho phép bạn xác định và xử lí một số thay đổi hoặc lời gọi đã được thực thi. Bạn có thể theo dõi các sự kiên bằng cách sử dụng phương thức `on`.

```ts
presence.on("UpdateData", async () => {
  // Sẽ thực thi khi dữ liệu được cập nhật.
});
```

Có một số sự kiện có sẵn:

#### `UpdateData`

Sự kiện này hoạt động mỗi khi presence được cập nhật.

#### `iFrameData`

Hoạt động khi nhận được dữ liệu từ tập lệnh iFrame.
