---
title: Metadata.json
description: Chứa dữ liệu cơ bản về Presence
published: true
date: 2021-02-07T17:12:06.799Z
tags:
editor: markdown
dateCreated: 2020-06-11T18:04:52.965Z
---

# Metadata.json

Nếu bạn muốn công bố một presence qua cửa hàng và tải nó qua phần mở rộng, bạn nên tạo một tệp `metadata.json` trong thư mục `dist` của bạn.

Một ví dụ cho tệp đó có thể tìm thấy dưới đây.

```ts
{
  "$schema": "https://schemas.premid.app/metadata/1.5",
  "author": {
    "name": "NGƯỜI DÙNG",
    "id": "ID"
  },
  "contributors": [{
    "name": "NGƯỜI DÙNG",
    "id": "ID"
  }],
  "service": "DỊCH VỤ",
  "altnames": ["DỊCH VỤ"],
  "description": {
    "en": "MÔ TẢ"
  },
  "url": "URL",
  "regExp": "REGEXP",
  "iFrameRegExp": "REGEXP",
  "version": "PHIÊN BẢN",
  "logo": "URL",
  "thumbnail": "URL",
  "color": "#45A8FC",
  "category": "THỂ LOẠI",
  "tags": ["TAG1", "TAG2"],
  "iframe": false,
  "settings": [
    {
      "id": "ID",
      "title": "TIÊU ĐỀ",
      "icon": "ẢNH",
      "value": true
    },
    {
      "id": "ID",
      "if": {
        "ID": true
      },
      "title": "TIÊU ĐỀ ĐƯỢC BIỂU DIỄN",
      "icon": "ẢNH",
      "value": "\"%song%\" bởi %artist%",
      "placeholder": "sử dụng %song% hoặc %artist%"
    },
    {
      "id": "ID",
      "title": "TIÊU ĐỀ",
      "icon": "ẢNH",
      "value": 0,
      "values": ["1", "2", "v.v."]
    }
  ]
}
```

## Hiểu về metadata.json

Ví dụ đó thật kì lạ nhỉ? Đừng lo, nó thực sự không khó để hiểu từng biến có công dụng gì.

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
        người phát triển và nhấp chuột phải vào hồ sơ của bạn.</td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>contributors</b></td>
      <td style="text-align:left">Nên có một object với <code>tên</code> và <code>id</code> của người đóng góp. <code>tên</code> là tên người dùng Discord của bạn không chứa số hiệu nhận dạng (#0000). <code>id</code> người dùng có thể được chép từ Discord bằng cách bật chế độ
        người phát triển và nhấp chuột phải vào hồ sơ của bạn.</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Có</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>service</b></td>
      <td style="text-align:left">Tiêu đề của dịch vụ mà presence hỗ trợ.</td>
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
      <td style="text-align:left">Đoạn mô tả của dịch vụ <b>KHÔNG PHẢI</b> của presence. Đoạn mô tả của bạn phải có giá trị đôi mấu chốt biểu thị ngôn ngữ, và đoạn mô tả bằng ngôn ngữ cụ thể đó. Viết đoạn mô tả bằng những ngôn ngữ <i>mà bạn biết</i>, các phiên dịch viên của chúng tôi sẽ chỉnh sửa vào tệp metadata của bạn. Hiển thị danh mục của các ngôn ngữ của presence trong một danh sách. </td>
      <td style="text-align:left"><code>Object</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>url</b></td>
      <td style="text-align:left">URL của dịch vụ.<br>
      <b>Ví dụ:</b><code>vk.com</code><br>
      <b>url này phải trùng với url của trang web vì nó sẽ được sử dụng để xác định xem đây có phải trang web để nhét tập lệnh vào không. Điều này chỉ nên được sử dụng như một mảng khi có nhiều hơn một url.</b></td>
      <td style="text-align:left"><code>String, Array&lt;String&gt;</code></td>
      <td style="text-align:left"><code>Không</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>regExp</b></td>
      <td style="text-align:left">Một chuỗi biểu thức chính quy được dùng để xác định các url.</td>
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
      <td style="text-align:left"><b>category</b></td>
      <td style="text-align:left">Một chuỗi được dùng để đại diện danh mục của presence.</td>
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
      <td style="text-align:left"><b>iframe</b></td>
      <td style="text-align:left">Xác định xem <code>iFrame</code> có được sử dụng không</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Có</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>iFrameRegExp</b></td>
      <td style="text-align:left">Một bộ chọn biểu thức chính quy để lựa chọn những iframe để nhét vào.</td>
      <td style="text-align:left"><code>String</code></td>
      <td style="text-align:left"><code>Có</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readLogs</b></td>
      <td style="text-align:left">Xác định xem phần mở rộng có nên đọc nhật ký hay không.</td>
      <td style="text-align:left"><code>Boolean</code></td>
      <td style="text-align:left"><code>Có</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>settings</b></td>
      <td style="text-align:left">Một mảng các cài đặt người dùng có thể thay đổi</td>
      <td style="text-align:left"><code>Array&lt;Object&gt;</code></td>
      <td style="text-align:left"><code>Có</code></td>
    </tr>
  </tbody>
</table>

## Biểu thức chính quy

Nếu bạn muốn học thêm về biểu thức chính quy, đây là một số trang web.

#### Học tập

• [Quick Starter Video](https://youtu.be/sXQxhojSdZM) • [RegexOne](https://regexone.com/) • [Regular Expressions Info](https://www.regular-expressions.info/tutorial.html)

#### Thử nghiệm

• [Regexr](https://regexr.com/) • [Regex101](https://regex101.com/)

## Ngôn ngữ của presence

PreMiD là một dịch vụ đa ngôn ngữ, nghĩa là có nhiều ngôn ngữ được cung cấp để kết nối với người dùng toàn cầu. Một danh sách đầy đủ các ngôn ngữ có thể được tìm ở [API đầu cuối](https://api.premid.app/v2/langFile/list). Để tuỳ chỉnh presence của bạn nhiều hơn nữa, bạn có thể cho phép người dùng lựa chọn ngôn ngữ hiển thị của presence. Xem [`multiLanguage`](#multilanguage) để tìm hiểu thêm.

## Cài đặt của presence
Cài đặt các lựa chọn mang tính tương tác để người dùng có thể tuỳ chỉnh presence!
```ts
"settings": [
  {
    "id": "ID",
    "multiLanguage": true //Xem https://docs.premid.app/dev/presence/metadata#multilanguage
  },
  {
    "id": "ID",
    "title": "TIÊU ĐỀ",
    "icon": "BIỂU TƯỢNG", //Ví dụ "fas fa-info"
    "value": true //Giá trị nhị phân sẽ biến nó thành một công tắc bật tắt với giá trị là giá trị mặc định
  },
  {
    "id": "ID",
    "if": {
      "ID": true //Nếu một cài đặt khác có giá trị này (true/false/0/1/v.v.) thì hiện nút này
    },
    "title": "TIÊU ĐỀ",
    "icon": "BIỂU TƯỢNG",
    "value": "\"%song%\" bởi %artist%", //Đưa vào một chuỗi sẽ biến nó thành một thanh nhập dữ liệu, nơi bạn có thể tuỳ chỉnh dữ liệu đầu ra.
    "placeholder": "sử dụng %song% hoặc %artist%" //Khi không có thông tin được đưa vào dòng này sẽ được tô xám
  },
  {
    "id": "ID",
    "title": "TIÊU ĐỀ",
    "icon": "BIỂU TƯỢNG",
    "value": 0, //Giá trị mặc định của bộ chọn
    "values": ["1", "2", "etc."] //Sẽ sử dụng giá trị của một bộ chọn khi bạn chọn một lựa chọn
  }
]
```

### `multiLanguage`

#### Giới thiệu

Cài đặt `multiLanguage` được dùng để cho phép người dùng chọn ngôn ngữ họ muốn presence hiển thị. Điều này yêu cầu bạn phải sử dụng chuỗi từ [API](https://api.premid.app/v2/langFile/presence/en) của chúng tôi, để biết thêm về cách thêm chuỗi hãy vào [đây](https://docs.premid.app/dev/presence/metadata#adding-new-strings).

#### Cài đặt

Cài đặt `multiLanguage` là một trường hợp đặc biệt, nó không yêu cầu `title` hay `icon` hay `value` hay `values` như các cài đặt khác nhưng lại yêu cầu bạn thiết lập nhiều hơn!

Từ khoá `multiLanguage` có thể được đặt các giá trị sau:

`true`: sử dụng giá trị này nếu bạn sẽ chỉ sử dụng chuỗi của tệp `general.json` và tệp `<service>.json` của [Kho lưu trữ Bản địa hoá](https://github.com/PreMiD/Localization/tree/master/src/Presence). `string`: tên của tệp trừ phần mở rộng (.json) trong [Kho lưu trữ Bản địa hoá](https://github.com/PreMiD/Localization/tree/master/src/Presence) (trừ tệp `general` vì nó luôn được sử dụng). Chỉ những ngôn ngữ thông dụng từ cả hai tệp `general` và tệp vừa đưa vào sẽ được liệt kê. `Array<String>`: nếu bạn đang sử dụng nhiều hơn một tệp trong [Kho lưu trữ Bản địa hoá](https://github.com/PreMiD/Localization/tree/master/src/Presence) bạn có thể ghi rõ tất cả giá trị trong một mảng (trừ tệp `general` vì nó luôn được sử dụng). Chỉ những ngôn ngữ thông dụng từ tất cả các tệp sẽ được liệt kê.

#### Thêm chuỗi mới

**Ghi chú:** Ghi thêm các chuỗi tuỳ chọn cho một presence sẽ chỉ được cho phép nếu nó có trên 1000 người dùng.

##### Clone project

1. Mở một terminal và gõ lệnh `git clone https://github.com/PreMiD/Localization`.
2. Chọn thư mục bạn muốn.
3. Mở nó với editor bạn chọn.

##### Tạo tệp tin

1. Vào trong thư mục `src`.
2. Vào trong thư mục `Presence`.
3. Tạo một tệp với tên `<service>.json`. (Service là **tên** (không phải URL) viết thường của dịch vụ bạn muốn hỗ trợ.)

##### Thêm chuỗi

Mỗi `string` là một `Object` tên bắt đầu bằng tên dịch vụ và tiếp đến là stringName cách nhau bằng một dấu chấm.

stringName là phương thức nhận dạng 1 từ của tin nhắn.

`Object` có 2 thuộc tính; `message` và `description`. `message` là phần văn bản cần được phiên dịch. `description` là phần mô tả văn bản để giúp các phiên dịch viên hiểu về văn bản đó.

**Ghi chú:** Không được thêm các chuỗi trùng lặp. (Ngoại trừ những chuỗi từ tệp `general.json` nhưng không phải các tệp khác.)

Trực quan về tệp:

```ts
{
  "<service>.<stringName>": {
    "message": "Nội dung cần được dịch.",
    "description": "Đoạn giải thích nội dung bên trên."
  },
  "<service>.<stringName>": {
    "message": "Nội dung cần được dịch.",
    "description": "Đoạn giải thích nội dung bên trên."
  }
}
```

Sau khi bạn đã hoàn thành tệp với đầy đủ các chuỗi bạn có thể tạo một Pull Request vào [Kho lưu trữ Bản địa hoá](https://github.com/PreMiD/Localization), trong phần mô tả bạn **phải** thêm một liên kết với Pull Request của presence bạn đã cập nhật với những chuỗi mới từ [Kho lưu trữ Presence](https://github.com/PreMiD/Presences).

#### Từ khoá mặc định
The keys you didn't have to set are automatically set to the following: `title`: "Language" **Note:** This is translated into their default language (browser language). `icon`: "fas fa-language" ([Preview](https://fontawesome.com/icons/language)) `value`: **Set to their browser language if it is available (100% translated), otherwise English.** `values`: **Set to the available languages (languages that have it 100% translated).**

**Note:** These are in no way changeable.

### Phương pháp

Use the following methods to get settings info in your presence files:
#### `getSetting(String)`
Returns value of setting.
```ts
const setting = await presence.getSetting("pdexID"); //Replace pdexID with the id of the setting
console.log(setting); // This will log the value of the setting
```

#### `hideSetting(String)`
Hides given setting.
```ts
presence.hideSetting("pdexID"); //Replace pdexID with the id of the setting
```

#### `showSetting(String)`
Hiện cài đặt được đưa ra (Chỉ hoạt động khi cài đặt đã được ẩn từ trước).
```ts
presence.showSetting("pdexID"); //Replace pdexID with the id of the setting
```

## Presence categories

When making your presence, you must specify a category which the presence falls under. This is a compiled list of the categories that you can use.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Category</th>
      <th style="text-align:left">Tên</th>
      <th style="text-align:left">Mô tả</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>anime</b></td>
      <td style="text-align:left"><b>Anime</b></td>
      <td style="text-align:left">Anything related to anime, from forums to video streaming platforms.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>games</b></td>
      <td style="text-align:left"><b>Games</b></td>
      <td style="text-align:left">Any website that has game related content, such as <code>Kahoot</code> or <code>Skribbl.io</code></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>music</b></td>
      <td style="text-align:left"><b>Nhạc</b></td>
      <td style="text-align:left">These are websites that offer music related content, whether that be streaming or downloading.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>socials</b></td>
        <td style="text-align:left"><b>Xã hội</b></td>
      <td style="text-align:left">Websites that are used for the purpose of creating and sharing content or  for participating in other forms of social networking.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>videos</b></td>
        <td style="text-align:left"><b>Video & Streams</b></td>
      <td style="text-align:left">Websites that serve the purpose of providing videos and streams.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>other</b></td>
      <td style="text-align:left"><b>Khác</b></td>
      <td style="text-align:left">Anything that does not fall under a specific category listed above.</td>
    </tr>
  </tbody>
</table>

