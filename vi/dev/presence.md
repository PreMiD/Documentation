---
title: Nhà phát triển Presence
description:
published: true
date: 2021-07-08T19:12:34.449Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:02.843Z
---

> Tất cả presence hiện được chứa ở đây: https://github.com/PreMiD/Presences 
> 
> {.is-info}

Phiên bản `2.x` đã thêm tính năng [cửa hàng presence](https://premid.app/store). Người dùng đã có thể thêm hoặc gỡ presences yêu thích của họ thông qua [website](https://premid.app/).

> Trước khi bắt đầu, chúng tôi khuyên bạn nên xem bộ quy tắc về presence của chúng tôi. 
> 
> {.is-warning}

- [Bộ quy tắc](https://docs.premid.app/dev/presence/guidelines)
{.links-list}

# Cấu trúc

Tất cả presence đều được lập trình bằng [TypeScript](https://www.typescriptlang.org/). [TypeScript](https://www.typescriptlang.org/) có các định nghĩa thú vị hơn so với JavaScript, nên việc tìm và sửa lỗi trở nên dễ dàng hơn nhiều.

## Cài đặt

1. Cài đặt [Git](https://git-scm.com/).
2. Cài [Node](https://nodejs.org/en/) (có sẵn với [npm](https://www.npmjs.com/)).
3. Cài [TypeScript](https://www.typescriptlang.org/index.html#download-links) (mở terminal và nhập `npm install -g typescript`).

## Clone project

1. Mở một terminal và gõ lệnh `git clone https://github.com/PreMiD/Presences`.
2. Chọn thư mục bạn muốn.
3. Mở nó với editor bạn chọn.

## Tạo thư mục và tệp

1. Mở thư mục `websites` và tiếp tục mở thư mục có chữ cái bắt đầu của **tên** (không phải URL) của dịch vụ bạn muốn hỗ trợ.
2. Tạo một thư mục với **tên** (không phải URL) của dịch vụ bạn muốn hỗ trợ.
3. Tạo một tệp `presence.ts` và một tệp `tsconfig.json` ở bên trong.
4. Tạo một thư mục tên`dist` bên trong.
5. Tạo một tệp `metadata.json` ở bên trong thư mục `dist`.

## Điền tệp tsconfig.json

Hãy điền đoạn mã sau vào trong tệp `tsconfig.json`.

```ts
{
  "extends": "../../../tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist/"
  }
}
```

Để biết thêm về các cấu hình của TypeScript nhấn vào [đây](/dev/presence/tsconfig).

## Điền tệp metadata.json

Chúng tôi đã dựng một trình tạo tệp `metadata.json` cho những người lười nhác [tại đây](https://eggsy.xyz/projects/premid/mdcreator). Chúng tôi vẫn khuyên bạn nên đọc qua để có thể hiểu cách nó hoạt động.

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.5",
  "author": {
    "name": "NGƯỜI DÙNG",
    "id": "ID"
  },
  "contributors": [
    {
      "name": "NGƯỜI DÙNG",
      "id": "ID"
    }
  ],
  "service": "DỊCH VỤ",
  "altnames": ["DỊCH VỤ"],
  "description": {
    "en": "MÔ TẢ"
  },
  "url": "URL",
  "version": "PHIÊN BẢN",
  "logo": "URL",
  "thumbnail": "URL",
  "color": "#HEX000",
  "tags": ["NHÃN1", "NHÃN2"],
  "category": "DANH MỤC",
  "regExp": "REGEXP",
  "iFrameRegExp": "REGEXP",
  "iframe": false,
  "readLogs": false,
  "settings": [
    {
      "id": "multiLanguage",
      "multiLanguage": true
    }
    {
      "id": "ID",
      "title": "TIÊU ĐỀ",
      "icon": "BIỂU TƯỢNG",
      "value": true
    },
    {
      "id": "ID",
      "if": {
        "ID": true
      },
      "title": "TIÊU ĐỀ",
      "icon": "BIỂU TƯỢNG",
      "value": "\"%song%\" bởi %artist%",
      "placeholder": "sử dụng %song% hoặc %artist%"
    },
    {
      "id": "ID",
      "title": "TIÊU ĐỀ",
      "icon": "BIỂU TƯỢNG",
      "value": 0,
      "values": ["1", "2", "etc."]
    }
  ]
}
```

Hãy chép đoạn mã trên và dán nó vào tệp `metadata.json`. Bạn cần thay đổi giá trị của các tính chất. Hãy ghi chú rằng những tính chất này là không bắt buộc phải có trong tệp `metadata.json`, nếu bạn không có ý định sử dụng bạn có thể xóa chúng.

- `contributors`
- `altnames`
- `regExp`
- `iframe`
- `iFrameRegExp`
- `readLogs`
- `settings`

**Làm rõ một số giá trị được đặt trước:**

<table>
  <thead>
    <tr>
      <th style="text-align:left">Biến số</th>
      <th style="text-align:left">Mô tả</th>
      <th style="text-align:left">Kiểu</th>
      <th style="text-align:left">Tùy chọn</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>author</b></td>
      <td style="text-align:left">Nên có một Object với <code>tên</code> và <code>id</code> của người phát triển presence. <code>tên</code> là tên người dùng Discord của bạn không chứa số hiệu nhận dạng (#0000). <code>id</code> người dùng có thể được chép từ Discord bằng cách bật chế độ
        người phát triển vào nhấp chuột phải vào hồ sơ của bạn.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>contributors</b></td>
      <td style="text-align:left">Nên có một Object với <code>tên</code> và <code>id</code> của người phát triển presence. <code>tên</code> là tên người dùng Discord của bạn không chứa số hiệu nhận dạng (#0000). <code>id</code> người dùng có thể được chép từ Discord bằng cách bật chế độ
        người phát triển vào nhấp chuột phải vào hồ sơ của bạn.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Có</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>service</b></td>
      <td style="text-align:left">Tên của dịch vụ mà presence hỗ trợ.<br>
      (Phải cùng tên với thư mục chứa mọi thứ)</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>altnames</b></td>
      <td style="text-align:left">Có thể tìm kiếm presence bằng một tên tương tự.<br>
      Nhằm để sử dụng cho các presence có tên khác nhau ở các ngôn ngữ khác nhau (vd. Pokémon và 포켓몬스터).<br>
      Bạn cũng có thể dùng nó cho các presence với ký tự đặc biệt để bạn không phải gõ chúng ra (vd. Pokémon và Pokemon).</td>
      <td style="text-align:left"><code>Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Có</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>description</b></td>
      <td style="text-align:left">Đoạn mô tả ngắn của presence, bạn có thể sử dụng đoạn mô tả của dịch vụ nếu bạn bí ý tưởng. Your description must have key pair values which indicate the language, and the description in that specific language. Make descriptions with the languages <i>that you know</i>, our translators will make changes to your metadata file.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>url</b></td>
      <td style="text-align:left">URL of the service.<br><b>Example:</b><code>vk.com</code><br>
      <b>This URL must match the URL of the website as it will detect whether or not this is the website to inject the script to.</b><br> Do <b>NOT</b> add <code>https://</code> or <code>http://</code> inside of the URL nor a slash at the end:
      <code>https://premid.app/</code> -> <code>premid.app</code><br>
      <b>Note</b>: Some URLs may have <code>www.</code> or something else in front of their domain. Do <b>NOT</b> forget to add it!<br>
      You can add multiple URLs by doing the following:<br>
      <code>["URL1", "URL2", "ETC."]</code><br>
      You could also use regExp also known as Regex for this task, explained further below.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>regExp</b></td>
      <td style="text-align:left">A regular expression string used to match urls.<br>
      regExp or also known as Regex, can be used if a website has multiple subdomains.<br>
      You could use the following regExp for that:<br>
      <code>([a-z0-9]+)[.]domain[.]TLD"</code><br>
      TLD standing for Top Level Domain for example: .com .net (but do not enter the dot).<br>
      <code>([a-z0-9]+)</code> means anything from a to z and from 0 to 9.<br>
      You can get a quick starter by watching this <a href="https://youtu.be/sXQxhojSdZM">video</a>.<br>
      You can test your regExp at <a href="https://regex101.com/">Regex101</a>.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Có</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>version</b></td>
      <td style="text-align:left">Version of your presence.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logo</b></td>
      <td style="text-align:left">Link to service&apos;s logotype.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>thumbnail</b></td>
      <td style="text-align:left">Link to your presence thumbnail.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>color</b></td>
      <td style="text-align:left"><code>#HEX</code> value. We recommend to use a primary color of the service
        that your presence supports.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>tags</b></td>
      <td style="text-align:left">Array with tags, they will help users to search your presence on the website.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">A string used to represent the category the presence falls under. See the valid catergories <a href="https://docs.premid.app/dev/presence/metadata#presence-categories">here</a>.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iframe</b></td>
      <td style="text-align:left">Defines whether <code>iFrames</code> are used.</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Có</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iFrameRegExp</b></td>
      <td style="text-align:left">A regular expression selector that selects iframes to inject into. See regExp for more info.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Có</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readLogs</b></td>
      <td style="text-align:left">Defines whether the extension should be reading logs.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Có</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>settings</b></td>
      <td style="text-align:left">An array of settings the user can change.<br>
      Read more about presence settings <a href="https://docs.premid.app/dev/presence/metadata#presence-settings">here</a>.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Có</code></td>
    </tr>
  </tbody>
</table>

## Getting started

```ts
const presence = new Presence({
  //The client ID of the Application created at https://discordapp.com/developers/applications
  clientId: "000000000000000000"
  }),
  //You can use this to get translated strings in their browser language
  strings = presence.getStrings({
    play: "presence.playback.playing",
    pause: "presence.playback.paused"
  });

/*
function myOutsideHeavyLiftingFunction(){
    //Grab and process all your data here

    // element grabs //
    // api calls //
    // variable sets //
}

setInterval(myOutsideHeavyLiftingFunction, 10000);
//Run the function separate from the UpdateData event every 10 seconds to get and set the variables which UpdateData picks up
*/

presence.on("UpdateData", async () => {
  /*UpdateData is always firing, and therefore should be used as your refresh cycle, or `tick`. This is called several times a second where possible.

    It is recommended to set up another function outside of this event function which will change variable values and do the heavy lifting if you call data from an API.*/

  const presenceData: PresenceData = {
    //The key (file name) of the Large Image on the presence. These are uploaded and named in the Rich Presence section of your application, called Art Assets
    largeImageKey: "key",
    //The key (file name) of the Small Image on the presence. These are uploaded and named in the Rich Presence section of your application, called Art Assets
    smallImageKey: "key",
    //The text which is displayed when hovering over the small image
    smallImageText: "Some hover text",
     //The upper section of the presence text
    details: "Browsing Page Name",
    //The lower section of the presence text
    state: "Reading section A",
    //The unix epoch timestamp for when to start counting from
    startTimestamp: 3133657200000,
    //If you want to show Time Left instead of Elapsed, this is the unix epoch timestamp at which the timer ends
    endTimestamp: 3133700400000
    //Optionally you can set a largeImageKey here and change the rest as variable subproperties, for example presenceData.type = "blahblah"; type examples: details, state, etc.
  };
  //Update the presence with all the values from the presenceData object
  if (presenceData.details) presence.setActivity(presenceData);
  //Update the presence with no data, therefore clearing it and making the large image the Discord Application icon, and the text the Discord Application name
  else presence.setActivity(); 
});
```

You can copy this into your `presence.ts` file and edit the values. Setting all the values is done inside of the updataData event.

For examples we suggest to look at the code of presences like: 1337x or 9GAG. For more information about the `Presence` class click [here](/dev/presence/class).

Since v2.2.0 there are now Slideshows, this allows you to show multiple `PresenceData` interfaces on an interval, for more information click about the `Slideshow` class [here](/dev/presence/slideshow).

## Can't get certain data?!

A lot of websites are using [iframes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe) ([Inlineframes](https://en.wikipedia.org/wiki/HTML_element#Frames)). These html tags can contain multiple sources such as videos. But they're not relevant every time. Some are hidden or just not actively used. Check if you can extract the information you need without them before you do unnecessary work.

1. Check for them in your browsers console (be sure that you are on the **Elements** tab).
2. Search (<kbd>CTRL</kbd>+<kbd>F</kbd> (Windows) or <kbd>CMD</kbd>+<kbd>F</kbd> (MacOS)).
3. Execute `document.querySelectorAll("iframe")`.

If you find that your data is in a iFrame you need to do the following:

1. Create a `iframe.ts` file.
2. Set iFrame to `true` in your metadata file.
3. Filling in your iFrame file.

```ts
const iframe = new iFrame();
iframe.on("UpdateData", async () => {
  //Get all the data you need out of the iFrame save them in variables and then send them using iframe.send
  iframe.send({
    //sending data
    video: video,
    time: video.duration
  });
});
```

4. Making your presence file receive data from the iFrame file.

```ts
presence.on("iFrameData", (data) => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

**Note:** This needs to be placed outside of the updateData event.

## Compiling

Open a console in your folder and type `tsc -w` to compile the `presence.ts` into the `/dist` folder.

# Loading the presence

1. Open the extension popup in the browser and hold the <kbd>Shift</kbd> button on your keyboard.
2. **Load Presence** will appear in the Presences section.
3. Click on it while you are still holding the <kbd>Shift</kbd> button.
4. Select the /dist folder of your presence.

# Some helpful things

## Hot-reloading

The website you are developing on is automatically reloading every time you save a file in your folder.

## Debugging

- You can put `console.log("Test");` between your code and see if your browser console gives you that output. If yes then go on and try again after the next function. If not then there is an error above.
- If that doesn't help you either then ask a presence developer on our [Discord server](https://discord.premid.app/) for help.

# Files explained

- [Lớp hiện diện](/dev/presence/class)
- [Slideshow Class](/dev/presence/slideshow)
- [iFrame Class](/dev/presence/iframe)
- [Metadata File](/dev/presence/metadata)
- [TypeScript Configuration](/dev/presence/tsconfig ""){.links-list}
