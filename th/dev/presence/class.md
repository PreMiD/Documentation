---
title: คลาส Presence
description: คลาสหลักสำหรับทุก PreMiD Presence
published: true
date: 2021-10-30T23:15:51.123Z
tags: 
editor: markdown
dateCreated: 2021-09-07T01:59:20.885Z
---

# คลาส Presence

## แนะนำ

คลาส `Presence` มีประโยชน์มากเพราะมีวิธีการพื้นฐานที่เราต้องการสำหรับการสร้าง presence

เมื่อคุณสร้าง Class คุณต้องระบุคุณสมบัติของ `clientId`

```typescript
const presence = new Presence({
  clientId: "514271496134389561" // Example clientId
});
```

### Properties

There are three properties available for `Presence` class.

#### `clientId`

This property is required to make your presence work, because it uses your application id to display its logo and assets. คุณสามารถเข้าไปดูได้ที่ [หน้าแอปพลิเคชัน](https://discordapp.com/developers/applications)

#### `injectOnComplete` - *Deprecated since 2.2.4*

When setting `injectOnComplete` to `true` the first `UpdateData` event for both the `presence.ts` and `iframe.ts` files will only be fired when the page has fully loaded.

#### `appMode` - *Deprecated since 2.2.4*

When setting `appMode` to `true` and the presence were to send an empty `PresenceData`, the app will show the application (image and name) on the user's profile instead of nothing.

## ฟังก์ชัน

### `getActivity()`

Returns a `PresenceData` object of what the presence is displaying.

### `setActivity(PresenceData | Slideshow, Boolean)`

ตั้งค่ากิจกรรมโปรไฟล์ของคุณตามข้อมูลที่ให้ไว้

First parameter requires a [`PresenceData`](#presencedata-interface) interface or a [`Slideshow`](/dev/presence/slideshow) class to get all information that you want to display in your profile.

ตัวแปรที่สองกำหนดให้เมื่อ presence กำลังเล่นอะไรอยู่หรือไม่ Always use `true` if you provide timestamps in `PresenceData`.

### `clearActivity()`

Clears your current activity and the tray title.

### `setTrayTitle(String)` - *Deprecated since 2.2.3*

> วิธีนี้ใช้ได้เฉพาะบน Mac OS เท่านั้น 
> 
> {.is-warning}

ตั้งให้เทรย์ title อยู่บน แถบเมนู

### `createSlideshow()`

Creates a new `Slideshow` class.

```typescript
const slideshow = presence.createSlideshow();
```

It is suggested to do this right after creating the `Presence` class:

```typescript
const presence = new Presence({
    clientId: "514271496134389561" // Example clientId
  }),
  slideshow = presence.createSlideshow();
```

You can find the documentation for the `Slideshow` class [here](/dev/presence/slideshow).

### `getStrings(Object)`

วิธีการ asyncronous จะสามารถให้คุณได้ string จากส่วนขยายได้

คุณต้องระบุ `Object` ด้วยคีย์ที่เป็นกุญแจสำหรับสตริง `keyValue` คือค่าสตริง A list of translated strings can be found at this endpoint: `https://api.premid.app/v2/langFile/presence/en/`

```typescript
// คืนค่า `Playing` and `Paused` strings
// จาก ส่วนขยาย.
const strings = await presence.getStrings({
  play: "general.playing",
  pause: "general.paused"
});

const playString = strings.play; // result: Playing
const pauseString = strings.pause; // result: Paused
```

Since v2.2.0 of the extension you can now get the strings of a certain language. This works well with the also newly added `multiLanguage` setting option.

We suggest you use the following code so it automatically updates the PresenceData if the user changes the selected language;

```typescript
async function getStrings() {
  return presence.getStrings(
    {
      play: "general.playing",
      pause: "general.paused"
    },
    // The ID is the ID of the multiLanguage setting.
    await presence.getSetting("ID").catch(() => "en");
  );
}

let strings = getStrings(),
  // The ID is the ID of the multiLanguage setting.
  oldLang: string = await presence.getSetting("ID").catch(() => "en");

//! The following code must be inside the updateData event!
// The ID is the ID of the multiLanguage setting.
const newLang = await presence.getSetting("ID").catch(() => "en");
if (oldLang !== newLang) {
  oldLang = newLang;
  strings = getStrings();
}

const playString = (await strings).play, // result: Playing
  pauseString = (await strings).pause; // result: Paused
```

### `getPageletiable(String)`

คืนค่าตัวแปรจากเว็บไซต์ถ้ามันมีอยู่จริง

**Warning: This function can cause high CPU usage & site lagging when it has been executed too many times.**

```typescript
const pageVar = presence.getPageletiable("pageVar");
console.log(pageVar); // This will log the "Variable content"
```

### `getExtensionVersion(Boolean)`

Returns version of the extension the user is using.

```typescript
getExtensionVersion(onlyNumeric?: boolean): string | number;

const numeric = presence.getExtensionVersion();
console.log(numeric); // Will log 210
const version = presence.getExtensionVersion(false);
console.log(version); // Will log 2.1.0
```

### `getSetting(String)`

Returns value of setting.

```typescript
const setting = await presence.getSetting("pdexID"); //Replace pdexID with the id of the setting
console.log(setting); // This will log the value of the setting
```

### `hideSetting(String)`

Hides given setting.

```typescript
presence.hideSetting("pdexID"); // Replace pdexID with the id of the setting
```

### `showSetting(String)`

Shows given setting (Only works if the setting was already hidden).

```typescript
presence.showSetting("pdexID"); // Replace pdexID with the id of the setting
```

### `getLogs()`

Returns the logs of the websites console.

```typescript
const logs = await presence.getLogs();
console.log(logs); // This will log the latest 100 logs (in an array).
```

**Note:** Requires `readLogs` to be `true` in the `metadata.json` file.

### `info(String)`

Prints the given message in the console in a format based of the presence in the `info` style.

```typescript
presence.info("Test") // This will log "test" in the correct styling.
```

### `success(String)`

Prints the given message in the console in a format based of the presence in the `success` style.

```typescript
presence.success("Test") // This will log "test" in the correct styling.
```

### `error(String)`

Prints the given message in the console in a format based of the presence in the `error` style.

```typescript
presence.error("Test") // This will log "test" in the correct styling.
```

### `getTimestampsfromMedia(HTMLMediaElement)`

**หมายเหตุ:** `String` ที่ให้ไปใน querySelector เป็นแค่คัวอย่างเท่านั้น.

```typescript
const timestamps = presence.getTimestampsfromMedia(document.querySelector(".video"));
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Note:** The given `String` in querySelector is an example.

### `getTimestamps(Number, Number)`

**หมายเหตุ:** `String` ที่ให้ไปใน querySelector เป็นแค่คัวอย่างเท่านั้น.

```typescript
const video = document.querySelector(".video"),
  timestamps = presence.getTimestamps(video.currentTime, video.duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Note:** The given `String` in querySelector is an example.

### `timestampFromFormat(String)`

Converts a string with format `HH:MM:SS` or `MM:SS` or `SS` into an integer (Does not return snowflake timestamp).

```typescript
const currentTime = presence.timestampFromFormat(document.querySelector(".video-now").textContent),
  duration = presence.timestampFromFormat(document.querySelector(".video-end").textContent),
  timestamps = presence.getTimestamps(currentTime, duration);
presenceData.startTimestamp = timestamps[0];
presenceData.endTimestamp = timestamps[1];
```

**Note:** The given `String` in querySelector is an example.

## อินเตอร์เฟซ `PresenceData`

อินเทอร์เฟซนี้มีตัวแปรดังต่อไปนี้ทั้งหมดเป็นตัวแปรที่สามารถเลือกได้

This interface has following variables, all of them are optional.

<table>
  <thead>
    <tr>
      <th style="text-align:left">ตัวแปร</th>
      <th style="text-align:left">คำอธิบาย</th>
      <th style="text-align:left">ชนิด</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">details</td>
      <td style="text-align:left">บรรทัดแรกใน presence มักจะใช้เป็น Header</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">state</td>
      <td style="text-align:left">บรรทัดที่สองใน presence ของคุณ</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">startTimestamp</td>
      <td style="text-align:left">กำหนดเวลาปัจจุบัน<br>
        จะใช้เมื่อคุณต้องการแสดงว่าเหลือ <code>ชั่วโมง:นาที:วินาที</code> เท่าไหร่
          <br>คุณต้องแปลงเวลาของคุณเป็น <code>timestamp</code> หรือไม่งั้นคุณจะได้รับ
          เวลานับถอยหลังที่เกิดข้อผิดพลาด
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">endTimestamp</td>
      <td style="text-align:left">กำหนดระยะเวลาทั้งหมด
        <br>ใช้เมื่อคุณต้องการแสดงว่าเหลือ <code>ชั่วโมง:นาที:วินาที</code> เท่าไหร่
          <br>คุณต้องแปลงเวลาของคุณเป็น <code>timestamp</code> หรือไม่งั้นคุณจะได้รับ
          เวลานับถอยหลังที่เกิดข้อผิดพลาด
      </td>
      <td style="text-align:left"><code>Number</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">largeImageKey</td>
      <td style="text-align:left">กำหนด โลโก้ สำหรับ presence</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageKey</td>
      <td style="text-align:left">กำหนดไอคอนขนาดเล็กที่อยู่ถัดจากโลโก้ presence</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smallImageText</td>
      <td style="text-align:left">กำหนดข้อความที่จะแสดงต่อผู้ใช้เมื่อเขาเอาเมาส์ไปชี้ที่ไอคอนขนาดเล็ก</td>
      <td style="text-align:left"><code>String</code>
      </td>
    </tr>
        <tr>
      <td style="text-align:left">buttons</td>
      <td style="text-align:left">Array of buttons, max 2, label is the button text, and url is the link.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code>
      </td>
    </tr>
  </tbody>
</table>

```typescript
const presenceData: PresenceData = {
  details: "My title",
  state: "My description",
  largeImageKey: "service_logo",
  smallImageKey: "small_service_icon",
  smallImageText: "You hovered me, and what now?",
  startTimestamp: 1564444631188,
  endTimestamp: 1564444634734,
  buttons: [
    {
            label: "Test button1",
            url: "https://premid.app/"
        },
        {
            label: "Test button2",
            url: "https://premid.app/contributors"
        }
    ]
};
```

## Events

Events allow you to detect and handle some changes or calls that were made. You can subscribe to events using the `on` method.

```typescript
presence.on("UpdateData", async () => {
  // Do something when data gets updated.
});
```

เหตุการณ์นี้จะเริ่มขึ้นทุกครั้งที่มีการอัปเดต

#### `UpdateData`

จะเริ่มขึ้นเมื่อได้รับข้อมูลจากสคริปต์ iFrame

#### `iFrameData`

Fired when data is received from iFrame script.
