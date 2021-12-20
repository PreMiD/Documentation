---
title: Phát triển Presence
description:
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:02.843Z
---

> Tất cả presence hiện được chứa ở đây: https://github.com/PreMiD/Presences
>
> {.is-info}

Phiên bản `2.x` đã thêm tính năng [cửa hàng presence](https://premid.app/store). Người dùng đã có thể thêm hoặc gỡ presence yêu thích của họ thông qua [website](https://premid.app/).

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

## Sao chép dự án

1. Mở một terminal và gõ lệnh `git clone https://github.com/PreMiD/Presences`.
2. Chọn thư mục bạn muốn.
3. Mở nó với trình soạn thảo của bạn.

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
      <td style="text-align:left">Đoạn mô tả ngắn của presence, bạn có thể sử dụng đoạn mô tả của dịch vụ nếu bạn bí ý tưởng. Đoạn mô tả của bạn phải có giá trị đôi mấu chốt biểu thị ngôn ngữ, và đoạn mô tả bằng ngôn ngữ cụ thể đó. Viết đoạn mô tả bằng những ngôn ngữ <i>mà bạn biết</i>, các phiên dịch viên của chúng tôi sẽ chỉnh sửa vào tệp metadata của bạn.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>url</b></td>
      <td style="text-align:left">URL của dịch vụ.<br><b>Ví dụ:</b><code>vk.com</code><br>
      <b>URL này phải trùng với URL của trang web vì nó sẽ được dùng để nhận biết đây có phải trang web để thực thi tập lệnh hay không.</b><br> <b>KHÔNG</b> được thêm <code>https://</code> hoặc <code>http://</code> vào trong URL hay gạch chéo ở cuối:
      <code>https://premid.app/</code> -> <code>premid.app</code><br>
      <b>Note</b>: Một số URL có thể có <code>www.</code> hoặc cái gì đó khác được thêm ở trước tên miền. <b>KHÔNG</b> được quên thêm nó vào!<br>
      Bạn có thể thêm nhiều URL bằng cách sau:<br>
      <code>["URL1", "URL2", "ETC."]</code><br>
      Bạn cũng có thể sử dụng regExp hay còn được biết đến là Regex cho việc này, được giải thích kĩ hơn ở dưới.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>regExp</b></td>
      <td style="text-align:left">Một chuỗi biểu thức chính quy được dùng để nhận biết url.<br>
      regExp hay còn biết đến là Regex, có thể được dùng nếu trang web có nhiều tên miền phụ.<br>
      Bạn có thể dùng chuỗi regExp sau cho việc đó:<br>
      <code>([a-z0-9]+)[.]tênmiền[.]TMCCN"</code><br>
      TMCCN là viết tắt cho Tên Miền Cấp Cao Nhất, ví dụ: .com .net (nhưng không thêm đấu chấm vào).<br>
      <code>([a-z0-9]+)</code> nghĩa là tất cả mọi thứ từ a-z và từ 0-9.<br>
      Bạn có thể khởi động nhanh bằng cách xem video <a href="https://youtu.be/sXQxhojSdZM">này</a>.<br>
      Bạn có thể thử nghiệm regExp của mình tại <a href="https://regex101.com/">Regex101</a>.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Có</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>version</b></td>
      <td style="text-align:left">Phiên bản presence của bạn.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logo</b></td>
      <td style="text-align:left">Liên kết tới logotype của dịch vụ.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>thumbnail</b></td>
      <td style="text-align:left">Liên kết với hình thu nhỏ presence của bạn.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>color</b></td>
      <td style="text-align:left">Giá trị <code>#HEX</code>. Chúng tôi khuyên bạn sử dụng tông màu chủ đạo của dịch vụ
        mà presence của bạn hỗ trợ.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>tags</b></td>
      <td style="text-align:left">Mảng với các nhãn, chúng sẽ giúp người dùng tìm kiếm presence của bạn trên trang web.</td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">Một chuỗi được dùng để đại diện danh mục của presence. Xem các danh mục hợp lệ tại <a href="https://docs.premid.app/dev/presence/metadata#presence-categories">đây</a>.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iframe</b></td>
      <td style="text-align:left">Xác định xem <code>iFrame</code> có được sử dụng không.</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Có</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iFrameRegExp</b></td>
      <td style="text-align:left">Một bộ chọn biểu thức chính quy để lựa chọn những iframe để nhét vào. Xem regExp để biết thêm thông tin.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Có</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readLogs</b></td>
      <td style="text-align:left">Xác định xem phần mở rộng có nên đọc nhật ký hay không.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Có</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>settings</b></td>
      <td style="text-align:left">Một mảng các cài đặt người dùng có thể thay đổi.<br>
      Đọc thêm về cài đặt của presence <a href="https://docs.premid.app/dev/presence/metadata#presence-settings"> tại đây</a>.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Có</code></td>
    </tr>
  </tbody>
</table>

## Bắt đầu

```ts
const presence = new Presence({
  //Client ID của ứng dụng được tạo ở https://discordapp.com/developers/applications
  clientId: "000000000000000000"
  }),
  //Bạn có thể sử dụng cái này để lấy chuỗi đã được dịch ở ngôn ngữ trình duyệt của họ
  strings = presence.getStrings({
    play: "presence.playback.playing",
    pause: "presence.playback.paused"
  });

/*
function myOutsideHeavyLiftingFunction(){
    //Rút và xử lý tất cả thông tin của bạn ở đây

    // element grabs //
    // api calls //
    // variable sets //
}

setInterval(myOutsideHeavyLiftingFunction, 10000);
//Chạy chức năng này độc lập với UpdateData mỗi 10 giây để lấy và đặt biến mà UpdateData sẽ dùng
*/

presence.on("UpdateData", async () => {
  /*UpdateData luôn hoạt động, vậy nên được sử dụng làm chu kỳ làm mới của bạn, hay `tick`. Nó được gọi vài lần mỗi một giây khi có thể.

    Bạn nên đặt một chức năng độc lập với sự kiện chức năng này đẻ nó thay đổi giá trị của biến và gánh vác công việc nặng nếu bạn thu thập dữ liệu từ một API.*/

  const presenceData: PresenceData = {
    //Từ khoá (tên tệp) của Ảnh lớn trên presence. Những thứ này được tải lên và đặt tên trong mục Rich Presence của ứng dụng của bạn, được gọi là Art Assets
    largeImageKey: "key",
    // Từ khoá (tên) của Ảnh nhỏ trên presence. Những thứ này được tải lên và đặt tên trong mục Rich Presence của ứng dụng của bạn, được gọi là Art Assets
    smallImageKey: "key",
    // Nội dung sẽ được biểu thị khi di chuột qua ảnh nhỏ.
    smallImageText: "Một văn bản nổi lên gì gì đó",
     //Phần trên của nội dung presence
    details: "Tên Trang Web Đang Truy Cập",
    //Phần dưới của nội dung presence
    state: "Đang đọc phần A",
    //Mốc thời gian unix epoch mà sẽ được chọn để bắt đầu đếm
    startTimestamp: 3133657200000,
    //Nếu bạn muốn sử dụng Thời gian còn lại thay vì Thời gian đã qua, đây là mốc thời gian unix epoch sẽ kết thúc
    endTimestamp: 3133700400000
    //Bạn có thể tuỳ ý đặt largeImageKey tại đây vài đổi tất cả các thứ còn lại thành biến tính chất phụ, như presenceData.type = "blabla", các type ví dụ: details, state, v.v.
  };
  //Cập nhật presence bằng tất cả các giá trị trong đối tượng presenceData
  if (presenceData.details) presence.setActivity(presenceData);
  //Cập nhật presence với không dữ liệu, từ đó dọn sạch và để ảnh lớn là biểu tượng Ứng dụng Discord, và nội dung là tên Ứng dụng Discord
  else presence.setActivity();
});
```

Bạn có thể chép nội dung này vào tệp `presence.ts` và chỉnh sửa giá trị. Việc đặt tất cả giá trị được thực hiện trong sự kiện updataData.

Ta có thể lấy đoạn mã của các presence như sau làm ví dụ: 1337x hay 9GAG. Để biết thêm thông tin về lớp `Presence` nhấp vào [đây](/dev/presence/class).

Từ bản v2.2.0 đã xuất hiện Trình chiếu, cho phép bạn chiếu nhiều giao diện của `PresenceData` cách một khoảng thời gian, để biết thêm thông tin về lớp </code>Slideshow` <a href="/dev/presence/slideshow">nhấp vào đây</a>.</p>

<h2 spaces-before="0">Không thể lấy một số dữ liệu nhất định?!</h2>

<p spaces-before="0">Rất nhiều website đang sử dụng <a href="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe">iframe</a> (<a href="https://en.wikipedia.org/wiki/HTML_element#Frames">Inlineframe</a>). Các thẻ html này có thể chứa được nhiều nguồn như các videos. Nhưng không phải lúc nào chúng cũng liên quan. Một số bị ẩn hoặc không được sử dụng thường xuyên. Hãy kiểm tra xem bạn có thể rút ra được thông tin bạn cần trước khi bạn thực hiện các công việc không cần thiết.</p>

<ol start="1">
<li>Kiểm tra chúng ở bảng điều khiển trong trình duyệt của bạn (hãy chắc chắn bạn ở trong tab <strong x-id="1">Elements</strong>).</li>
<li>Tìm kiếm (<kbd>CTRL</kbd>+<kbd>F</kbd> (Windows) hoặc <kbd>CMD</kbd>+<kbd>F</kbd> (MacOS)).</li>
<li>Thực thi <code>document.querySelectorAll("iframe")`.</li> </ol>

Nếu bạn thấy dữ liệu bạn cần nằm trong iFrame bạn cần làm như sau:

1. Tạo một tệp `iframe.ts`.
2. Đặt iFrame thành `true` trong tệp metadata của bạn.
3. Điền vào tệp iFrame của bạn.

```ts
const iframe = new iFrame();
iframe.on("UpdateData", async () => {
  //Chọn tất cả dữ liệu bạn cần từ iFrame và lưu chúng thành các biến và gửi chúng bằng iframe.send
  iframe.send({
    //sending data
    video: video,
    time: video.duration
  });
});
```

4. Thiết lập tệp presence để nhận dữ liệu từ tệp iFrame.

```ts
presence.on("iFrameData", (data) => {
  iFrameVideo = data.video;
  currentTime = data.time;
});
```

**Ghi chú:** Mã cần được đặt bên ngoài sự kiện updateData.

## Biên dịch

Mở một bảng điều khiển trong tệp của bạn và gõ `tsc -w` để biên dịch tệp `presence.ts` vào thư mục `/dist`.

# Tải presence

1. Mở tiện ích ở dạng pop-up trong trình duyệt của bạn và bấm giữ phím <kbd>Shift</kbd> trên bàn phím của bạn.
2. **Load Presence** sẽ xuất hiện trong mục Presences.
3. Nhấp vào nó khi bạn vẫn đang giữ phím <kbd>Shift</kbd>.
4. Chọn thư mục /dist của presence của bạn.

# Một số thứ hữu ích

## Hot-reloading

Trang web bạn đang phát triển trên sẽ tự động tải lại mỗi khi bạn lưu tệp trong thư mục.

## Gỡ lỗi

- Bạn có thể đặt `console.log("Test");` giữa đoạn mã của bạn vào xem bảng điều khiển trong trình duyệt của bạn có in ra đúng thông tin đó không. Nếu đúng thì hãy tiếp tục và thử lại với chức năng tiếp theo. Nếu không tìm thấy thì sẽ có lỗi ở bên trên.
- Nếu điều đó không giúp ích thì bạn có thể hỏi một nhà phát triển presence trong [máy chủ Discord](https://discord.premid.app/) để trợ giúp bạn.

# Giải thích các tệp

- [Lớp Presence](/dev/presence/class)
- [Lớp Slideshow](/dev/presence/slideshow)
- [Lớp iFrame](/dev/presence/iframe)
- [Tệp Metadata](/dev/presence/metadata)
- [Cấu hình TypeScript](/dev/presence/tsconfig ""){.links-list}
