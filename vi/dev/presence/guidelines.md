---
title: Bộ quy tắc làm Presence
description: Những luật lệ mà tất cả những nhà phát triển presence phải tuân thủ nếu muốn presence của mình được thêm vào.
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:53.883Z
---

<div align="center">
    <img src="https://github.com/PreMiD.png?size=2048" width="128px" style="max-width:100%;">
    <h3 style="font-size: 2rem; margin-bottom: 0">Bộ quy tắc làm Presence</h3>
    <h4 style="margin-top: 0">Sửa đổi lần thứ 3</h4>
    <br />
</div>

# Các nguyên tắc

Khi công bố Presence vào [kho lưu trữ Presence](https://github.com/PreMiD/Presences/), chúng tôi yêu cầu bạn phải tuân theo một bộ quy tắc. Đối với một số người, những quy định này có thể hà khắc. Tuy nhiên, việc đưa vào thực hiện bộ quy tắc này sẽ giúp chúng tôi và các người dùng tránh khỏi các sự cố không mong muốn.

# Khởi tạo

Những quy định chung về việc phát triển presence như sau:

- Presence **bắt buộc** phải liên quan tới trang web được lựa chọn.
- Presence **không được phép** làm cho các trang web phi pháp. (cho vd: nội dung khó chịu, buôn bán thuốc, nội dung khiêu dâm trẻ em, v.v.)
- Cấu trúc tệp phải gọn và ngăn nắp, không được thêm tệp không được chỉ định. (cho vd: thư mục vscode và git, tệp ảnh và văn bản, v.v.)
- Bạn cần có một cấu trúc tệp thích hợp, **không** được phép thêm các bản nháp.
- Presence cho các trang web như (Tên Miền Cấp Cao Nhất `.onion`) hay các trang web với tên miền/máy chủ miễn phí (cho vd., `.TK` [tất cả các tên miền Freenom], `.RF`, `GD`, v.v.) đểu **không** được phép, có thể có ngoại lệ nếu chứng minh được chủ sở hữu tên miền đó đã trả phí cho tên miền.
- Tên miền của presence phải ít nhất 2 tháng tuổi.
- Presence hướng tới các trang nội bộ của trình duyệt (như Cửa hàng Chrome, các trang `chrome://`, `about:`, v.v.) đều **không** được phép vì nó yêu cầu người dùng phải bật tính năng thử nghiệm trên trình duyệt của họ và có thể làm tổn hại đến trình duyệt.
- Presence chỉ hỗ trợ một tên miền phụ sẽ **không** được cho phép, vì chúng có thể không hoạt động cho các trang khác (như trang chủ), có thể cho phép ngoại lệ cho các trang chính sách và liên lạc (những nội dung không được sử dụng thường xuyên) hoặc các trang có nội dung không liên quan. (cho vd., các trang wikia)
- Presence cho các radio online chỉ được cho phép khi radio đó có ít nhất 100 người nghe hàng tuần và 15 người nghe hiện tại và phải có các chức năng khác ngoài chỉ hiện tên album/bài hát, v.v.
- Presence không được phép chạy đoạn mã JS của riêng nó với chức năng của riêng nó để lấy biến. Nếu Firefox có vấn đề với các chức năng có sẵn trong lớp `Presence`, bạn được phép sử dụng chức năng của riêng mình và bạn cần phải nói với chúng tôi trong đoạn mô tả Pull Request.
- Presence với chất lượng thấp (hoặc với ít nội dung) đều **không** được cho phép (cho vd., chỉ hiện logo và văn bản nhưng không thay đổi).
- Presence cho các dịch vụ như Danh sách Discord Bot/Server phải tuân theo thêm các quy định sau:
  - Tên miền phải có ít nhất **6 tháng** tuổi.
  - Số người truy cập độc nhất mỗi ngày:
    - Cho tên miền từ 6 đến 12 tháng tuổi: **20,000 người truy cập độc nhất/ngày**.
    - Cho tên miền trên 12 tháng tuổi: **45,000 người truy cập độc nhất/ngày**.
  - Trang web không được sử dụng tên miền chi phí thấp như `.xyz`, `.club` và tương tự.
  - Trang web phải có chất lượng cao, thiết kế chất lượng, v.v.
- Presence nên sử dụng [chi tiết chung](https://api.premid.app/v2/langFile/presence/en) (các chuỗi bắt đầu bằng "general."). Bạn có thể thực hiện điều này bằng cách sử dụng `multiLanguage` với các chuỗi đã cho sẵn. Nếu presence của bạn cần các chuỗi đặc biệt thì bạn không nên dùng `multiLanguage` cho đến khi presence có 1000 người dùng. Bạn có thể tìm một ví dụ tại [đây](https://docs.premid.app/dev/presence/class#getstringsobject).
- Bao gồm cả thư mục `dist`, tệp `presence.ts`, tệp `iframe.ts`, và tệp `metadate.json` bắt buộc phải có để kết quả được hiển thị như lược đồ sau:

```bash
presence
├── dist
│   └── metadata.json
├── presence.ts
└── tsconfig.json
```

hoặc nếu như bạn đang sử dụng tệp `iframe.ts`:

```bash
presence
├── dist
│   └── metadata.json
├── presence.ts
├── iframe.ts
└── tsconfig.json
```

## [**metadata.json**](https://docs.premid.app/dev/presence/metadata)

> Để thuận tiện cho các nhà phát triển presence, chúng tôi đã cung cấp lược đồ sau để bạn sử dụng để kiểm tra tính toàn vẹn của tệp `metadata` của bạn. Việc này là hoàn toàn không bắt buộc và sẽ không phải yêu cầu trong quá trình đánh giá.

> Chúng tôi khuyến nghị bạn nên sắp xếp tệp `metadata` theo định dạng dưới đây, và bạn cần phải có tên dịch vụ, đoạn mô tả, các nhãn và phần cài đặt đúng ngữ pháp. Những gì không được sắp xếp như tiêu chuẩn sẽ **không** được chấp thuận.

> Presence dành cho các trang web có nội dung mạnh **phải** có nhãn `nsfw`, và biểu tượng/hình nhỏ **không** được phép chứa nội dung này.

Mỗi presence đều có một tệp mô tả gọi là `metadata.json`, metadata có tiêu chuẩn khắt khe và một ví dụ cho tệp này có thể được xem ở dưới đây:

```json
{
  "$schema": "https://schemas.premid.app/metadata/1.7",
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
      "icon": "BIỂU TƯỢNG FONTAWESOME",
      "value": true
    },
    {
      "id": "ID",
      "if": {
        "ID": true
      },
      "title": "TIÊU ĐỀ",
      "icon": "BIỂU TƯỢNG FONTAWESOME",
      "value": "\"%song%\" bởi %artist%",
      "placeholder": "sử dụng %song% hoặc %artist%"
    },
    {
      "id": "ID",
      "title": "TIÊU ĐỀ",
      "icon": "BIỂU TƯỢNG FONTAWESOME",
      "value": 0,
      "values": ["1", "2", "v.v."]
    }
  ]
}
```

> Nếu một mục được liệt là không bắt buộc trong [tài liệu](https://docs.premid.app/dev/presence/metadata) hoặc có dấu `*` bên cạnh từ khoá, và presence của bạn sử dụng giá trị mặc định, thì không được thêm vào trong tệp `metadata`. (cho vd., presence không hỗ trợ iframe không cần thêm mục `iframe`.)

> Tất cả các hình ảnh trong tệp `metadata` phải được lưu trữ trên `i.imgur.com`. Sử dụng nội dung ở trên trang web là **không** được phép vì chúng có thể thay đổi vị trí và tệp mà không hay biết.

Danh sách các mục và quy tắc cho nó như sau:

### **`$schema`**

- _Từ khoá_ schema **phải** có ký hiệu đô la ở trước nó, điều này sẽ ký hiệu cho trình soạn thảo văn bản rằng bạn muốn đối chiếu tệp JSON của bạn với một khuôn mẫu. _Như đã nói ở trước, bạn không cần phải thêm schema, nhưng nếu bạn thêm vào thì bạn phải xét thêm nhưng điều sau._

### **`author`**

- _Giá trị_ của ID **phải** là chuỗi ID Discord của bạn. Bạn có thể lấy chúng bằng cách bật [chế độ người phát triển](https://support.discord.com/hc/en-us/articles/206346498-Where-can-I-find-my-User-Server-Message-ID-). _Xin hãy **không** nhầm lẫn nó với ID phần mềm của bạn, chúng chỉ dành cho presence của bạn._

### **`*contributors`**

- **Không** được thêm bản thân mình là người đóng góp, và không được thêm người khác trừ khi họ đã giúp phát triển presence.

### **`service`**

- Tên của dịch vụ **phải** là tên của thư mục presence. Ví dụ, nếu presence nằm ở `/websites/Y/YouTube/`, tên của dịch vụ phải là `YouTube`.
- Bạn **không** được sử dụng url làm tên dịch vụ trừ khi trang web sử dụng url làm tên chính thức. Nếu tên không mang tính mô tả hoặc mơ hồ, **bắt buộc** phải dùng url. (cho vd., `YouTube` được cho phép vì đó là tên chính thức và mang tính mô tả, trong khi đó `youtube.com` không được phép. `Top` là tên không mang tính mô tả, vì vậy **bắt buộc** phải sử dụng url `top.gg`.)
- Nếu dịch vụ có tên mang nội dung mạnh, bạn nên tuân theo nó.

### **`*altnames`**

- **Chỉ** sử dụng trong trường hợp trang web có nhiều tên chính thức (cho vd. Pokémon và 포켓몬스터). Các tên được _rút ngắn_ của dịch vụ nằm trong `tags`.

### **`description`**

- **Tất cả** presence đều **bắt buộc** phải có đoạn mô tả bằng Tiếng Anh bất kể ngôn ngữ của trang web.
- **Không** được tự dịch đoạn mô tả trừ khi bạn thông thạo ngôn ngữ đó, các phiên dịch viên sẽ thay đổi tệp `metadata.json` của bạn và thay đổi đoạn mô tả nếu cần thiết.

### **`url`**

- Url **bắt buộc** phải là một string nếu trang web chỉ sử dụng một tên miền. Nếu trang web có nhiều tên miền, hãy sử dụng array và ghi rõ cụ thể từng miền một.
- **Không** được thêm giao thức vào url (cho vd., `http` hay `https`), và không được thêm tham số truy vấn (cho vd., `www.google.com/search?gws_rd=ssl` trong khi phải là `www.google.com`)

### **`version`**

- Always make sure the version number follows [semantic versioning standards](https://semver.org), which translates to the following scheme: `<MAJOR>.<MINOR>.<PATCH>`. Những thứ khác như `1.0.0.1`, `1.0`, `1`, `1.0.0-BETA` hoặc đổi từ `1.0.0` sang `2.0.0` sau một bản sửa lỗi/thay đổi nhỏ là **không** được cho phép.
- Số hiệu phiên bản **phải** bắt đầu bằng `1.0.0` trừ khi được chỉ dẫn khác, các số phiên bản khác sẽ **không** được chấp nhận.

### **`logo`**

- Biểu tượng **phải** là một ảnh vuông với tỉ lệ `1:1`.
- Ảnh **phải** có độ phân giải tối thiểu là `512x512` điểm ảnh. Bạn có thể phóng to nó bằng công cụ như [waifu2x](http://waifu2x.udp.jp/).

### **`thumbnail`**

- Hình nhỏ **nên** là một [ảnh thẻ ngang mang tính chất quảng cáo](https://i.imgur.com/3QfIc5v.jpg) hoặc một [ảnh chụp màn hình](https://i.imgur.com/OAcBmwW.png) nếu ảnh trên **không** có sẵn.

### **`color`**

- Màu **phải** là giá trị thập lục phân từ `#000000` đến `#FFFFFF`.
- Chuỗi màu **phải** phải có dấu thăng ở trước.

### **`tags`**

- **Tất cả** presence phải có tối thiểu _một_ nhãn.
- Nhãn **không** được phép chứa dấu cách, dấu gạch chéo, dấu ngoặc đơn/kép, ký tự Unicode, và luôn được viết thường.
- Nhãn **nên** thêm các tên tương tự của dịch vụ để giúp tìm kiếm dễ hơn (cho vd., nếu presence Amazon có thêm hỗ trợ cho AWS, nó phải thêm các nhãn như `amazon-web-service` và `aws`)
- Bạn **phải** thêm nhãn `NSFW` nếu presence được làm dành cho trang web NSFW.

### **`category`**

- Danh mục **phải** nằm trong danh sách được liệt kê trong [tài liệu](https://docs.premid.app/dev/presence/metadata#presence-categories).
- Presence phải sử dụng danh mục phù hợp với nội dung của trang web. (cho vd., không được sử dụng `anime` khi trang web không liên quan tới anime).

### **`*regExp`** <br /> **`*iFrameRegExp`**

- Biểu thức chính quy **phải** hợp lệ. Hãy thử chuỗi biểu thức chính quy của bạn bằng các công cụ được liệt kê trong [tài liệu](https://docs.premid.app/dev/presence/metadata#testing).

### **`readLogs`**

- Phải có giá trị `nhị phân` (cho vd., `true` hoặc `false`).
- Cho phép ghi nhật ký cho presence của bạn.

### **`warning`**

- Cho phép sử dụng biểu tượng cảnh bảo để thông báo người dùng biết rằng presence cần nhiều bước hơn việc chỉ thêm vào.
- `VLC` là một ví dụ cho việc presence sử dụng biến trong metadata.

### **`settings`**

- Nếu bạn quyết định sử dụng chuỗi định dạng (cho vd. `%song% bởi %artist%`), bạn phải để biến được bao quanh bởi dấu phần trăm ở hai đầu. Các biến như `%var`, `var%` hay `%%var%%` và tất cả mọi thứ tương tự đều **không** được chấp nhận vì lợi ích của việc tiêu chuẩn hoá.
- Tên của cài đặt **không** được phép viết toàn bộ in hoa. Ví dụ, các tên như `HIỆN TRẠNG THÁI TRÌNH DUYỆT` là **không** được cho phép; trong khi đó các tên như `Hiện Trạng Thái Trình Duyệt` hay `Hiện trạng thái trình duyệt` được cho phép.
- Nếu bạn đang sử dụng lựa chọn `multiLanguage` nó có thể có các kiểu sau:
  - Loại **boolean** sẽ chỉ cho phép sử dụng các chuỗi từ [`general.json`](https://github.com/PreMiD/Localization/blob/master/src/Presence/general.json) từ Kho lưu trữ Bản địa hoá hoặc từ tệp presence (cho vd. khi tên của presence là YouTube, phần mở rộng cũng sẽ sử dụng các chuỗi từ `youtube.json`.)
  - Loại **string** (cho vd. `youtube`) sẽ xác định tên tệp bạn sẽ lấy chuỗi từ.
  - Loại **array<String>** (cho vd. `["youtube","discord']`) sẽ xác định tên của tệp bạn lấy chuỗi từ.

## [**presence.ts**](https://docs.premid.app/dev/presence/class)

> Đoạn mã bạn viết **phải** được _chỉn chu_ và **phải** _dễ đọc_ và tất cả các chuỗi đều phải đúng ngữ pháp (lỗi ngữ pháp ở trang web sẽ được bỏ qua).

> Mỗi presence đều phải theo bộ quy định linting khắt khe mà sẽ được kiểm tra trong qua trình đánh giá. Một số khuyên nghị được liệt kê dưới đây. [Khuyến nghị các Phần mở rộng Kiểm tra Khắt khe cho TypeScript](https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin/docs/rules). [Các khuyến nghị của ESlint](https://eslint.org/docs/rules). [Prettier](https://prettier.io/).

Đây là danh sách các quy định bạn phải tuân theo khi viết tệp `presence.ts`:

- **Luôn** khai báo trạng thái mới của lớp `Presence` trước tất cả các biến khác để tránh gặp phải các lỗi hiếm; đây không phải yêu cầu theo mặc định nên có thể được gỡ bỏ trong tương lai.
- **Không bao giờ** được sử dụng các chức năng đặc biệt khi [đã có các chức năng cho sẵn](https://docs.premid.app/dev/presence#files-explained); điều này nhằm đảm bảo các bản vá lỗi ở cấp phần mở rộng cũng được áp dụng lên presence của bạn. Bạn có thể tuỳ ý sử dụng bất sứ thứ gì bạn cần nếu bạn không thấy nó được liệt kê trong tài liệu.
- **Nghiêm cấm** viết presence cho trang web mà không hỗ trợ ngôn ngữ chính của nó (cho vd., presence cho YouTube chỉ hỗ trợ cho Tiếng Bồ Đào Nha và Tiếng Nhật, nhưng không hỗ trợ Tiếng Anh.)
- Các mục `smallImageKey` và `smallImageText` có mục đích nhằm cung cấp thông tin thêm/phụ (như `playing/paused` cho các trang web video, `browsing` cho các trang thông thường, và các trường hợp khác), không được dùng để quảng bá hồ sơ Discord hay bất cứ thứ gì không liên quan tới PreMiD.
- Bạn **không** được phép truy cập vào `localStorage`.
- Khi truy cập cookies dành cho thông tin được lưu trữ, hãy sử dụng từ khoá với đầu `PMD_`.
- Bạn chỉ được phép thực hiện yêu cầu HTTP/HTTPS tới `premid.app` hay API của trang web presence hỗ trợ. Nếu bạn sử dụng tên miền bên ngoài, bạn sẽ phải yêu cầu giải thích vì sao. API duy nhất được cho phép thực hiện yêu cầu là [`Fetch API`](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API).
- **Không** được đặt mục ở trong object presenceData thành undefined sau khi nó đã được khai báo, thay vào đó hãy sử dụng từ khoá `delete`. (cho vd., hãy sử dụng `delete data.startTimestamp` thay vì `data.startTimestamp = undefined`)
- Bạn **không** được phép viết presence có công dụng thay đổi chức năng của trang web cho sẵn. Điều này bao gồm cả việc thêm, xoá hoặc thay đổi các yếu tố DOM.
- Các presence sử dụng nút phải tuân theo thêm các quy định sau:
  - Không được phép chuyển hướng về trang chủ.
  - Không được phép dùng nút để quảng bả trang web.
  - Nó không được hiển thị thông tin mà bạn không điền được vào các mục khác.
  - Chuyển hướng trực tiếp vào bài phát âm thanh/video trực tuyến là không được phép.


## [**tsconfig.json**](https://docs.premid.app/dev/presence/tsconfig)

> **Không** được phép tự viết tệp `tsconfig.json` của mình, dùng những gì đã được cung cấp ở [tài liệu](https://docs.premid.app/dev/presence/tsconfig).

## Sửa đổi

> Bạn **phải** thay đổi số phiên bản trong **metadata** sang một giá trị cao hơn giá trị trước khi làm những thay đổi trong các tệp **presence.ts**, **iframe.ts** hoặc **metadata.json**.

Trong một số trường hợp, presence có thể hoạt động một cách không đoán trước hoặc có thể cần một vài thay đổi nhỏ để cải tiến chức năng của nó. Đây là danh sách các quy định bạn **phải** tuân theo khi thay đổi presence.

- Nếu tác giả của presence không thể liên lạc được trong vòng hơn một tháng, bạn có thể liên lạc một đánh giá viên xem bạn có thể chỉnh sửa presence được không.
- Nếu bạn chỉnh sửa presence và thay đổi ít nhất một phần **tư** đoạn mã của presence, bạn có thể thêm bản thân mình là người đóng góp. Hãy liên lạc một đánh giá viên để biết thêm thông tin về đề tài này.
- Ai cũng có thể tạo một PR để sửa lỗi. **Không** được thay đổi hình ảnh nếu chúng không lỗi thời và nằm trong tiêu chuẩn.

# Xác minh

> **Tất cả** các mã đóng góp vào cửa hàng sẽ được cấp phép dưới `Mozilla Public License 2.0`.

> Nếu bạn cần phải liên lạc với ai, hãy sử dụng máy chủ Discord chính thức của chúng tôi. Tất cả các đánh giá viên đều có thẻ vai trò `Reviewer` trên hồ sơ của họ.

> Hãy ghi nhớ rằng tất cả các đánh giá viên đều làm việc một cách tình nguyện và quản lý nhiều kho lưu trữ hơn cái này, nên pull request của bạn có thể sẽ không được đánh giá sau vài giờ hoặc có thể vài ngày từ khi được tạo ra.

> **Luôn ** cập nhật fork của bạn trước khi lập một pull request. Điều này sẽ giúp giảm thiểu trường hợp dương tính giả trong quá trình đánh giá.

Quá trình quan trọng nhất của việc phát triển presence là việc đưa presence của bạn lên cửa hàng. Điều này được thực hiện bằng cách lập một [pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) trên GitHub vào kho lưu trữ `PreMiD/Presences`. Các đánh giá viên sẽ kiểm tra xem presence của bạn có đủ tiêu chuẩn không và đưa nó lên cửa hàng.

<div>
  <h2 style="font-size: 2rem; margin-bottom: 0;">Các Presence Đánh giá viên</h2>
  <a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
  <a href="https://github.com/EncryptedDev"><img src="https://github.com/EncryptedDev.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

## `Hạn chế`

Các hình thức tái phạm liên tiếp như không tuân theo bộ quy tắc, liên tục gửi pull request rác, đe doạ hay các hành động không phù hợp sẽ khiến bạn bị cấm không được tạo presence.

Trong trường hợp này, sẽ xảy ra những thay đổi sau:

- Những presence dưới quyền quản lý của bạn sẽ được chuyển giao cho bot PreMiD hoặc người dùng khác (quyết định của đánh giá viên). Id ứng dụng cho từng presence sẽ được làm mới dưới tên của chủ mới.
- Tất cả những báo lỗi và pull request của bạn (tạo presence, đóng góp presence, v.v.) tạo ra sau khi bạn bị cấm sẽ đều bị đóng.
- Các vé tạo dưới tên bạn liên quan tới việc phát triển presence sẽ đều bị xoá.

## `Đánh giá`

Vài điều bạn nên biết trước khi mở một pull request:

- Sẽ cần 2 đánh giá viên để nhập một pull request.
- Nếu pull request không có động thái gì trong vòng 7 ngày, nó sẽ bị đóng.
- **Phải** đạt tất cả các bài kiểm tra để nhập.
- ⚠️ Bạn **phải** cung cấp các ảnh chụp màn hình mới, chưa được chỉnh sửa (chụp bởi bạn) thể hiện sự so sánh song song giữa hồ sơ của bạn và trang web để chứng minh presence hoạt động. _Bạn được phép cắt ghép ảnh chụp bàn hình với nhau để ảnh dễ nhìn hơn_ Điều này áp dụng cho cả việc tạo và chỉnh sửa.
- ⚠️ Bạn cũng được yêu cầu **phải** cung cấp ảnh chụp màn hình của phần cài đặt presence nếu có. Một ví dụ có thể xem dưới [đây](https://imgur.com/a/OD3sj5R).

## `Kiểm tra`

![Các ví dụ cho việc kiểm tra](https://i.imgur.com/vF7QpBH.png)

Hiện giờ, một presence sẽ đi qua 3 công đoạn đánh giá. Tất cả các bài kiểm tra này đều giúp các đánh giá viên quyết định xem presence của bạn nó phù hợp để phát triển không.

- `DeepScan` là một bot kiểm tra chất lượng của đoạn mã. Nếu bạn nhận được lỗi từ các bài báo lỗi, bạn được yêu cầu **phải** vá chúng. *Cảnh báo: DeepScan không luôn luôn đưa ra lỗi. Thay vào đó hãy nhìn vào các cảnh báo của CodeFactor.*
- `CodeFactor` là một bot kiểm tra chất lượng của đoạn mã. Nếu bạn nhận được lỗi từ các bài báo lỗi, bạn được yêu cầu **phải** vá chúng.
- `Schema Validation` sẽ quét tệp `metadata.json` của bạn để tìm lỗi (cho vd., thiếu mục, giá trị không hợp lệ, v.v.). Nếu bạn nhận nhận được các lỗi mới, bạn được yêu cầu **phải** vá chúng. Thêm mục schema trong tệp `metadata.json` sẽ giúp trình soạn thảo văn bản của bạn (nếu có hỗ trợ) hiển thị những lỗi này trong quá trình phát triển.

## `Luật bổ sung`

- **Luôn** chắc chắn bắt đầu presence của bạn trong thư mục hợp lệ, nếu tên của nó bát đầu bằng _bất cứ_ chữ cái Latinh nào thì nó phải nằm trong thư mục có chữ cái trùng với nó (cho vd., `D/dアニメストア` hay `G/Google`). Bất cứ ký tự Unicode/không phải Latinh khác **phải** nằm trong thư mục `#` (cho vd. `#/巴哈姆特`) và các chữ số nằm trong thư mục `0-9` (cho vd., `0-9/4anime`).

Sau khi đạt đủ tất cả các quy tắc, được đánh giá và kiểm tra đầy đủ, presence của bạn sẽ được đưa lên cửa hàng.

# Đề xuất

Nếu bạn có các đề xuất dành cho các quy định của chúng tôi, bạn có thể liên lạc chúng tôi @ [máy chủ Discord của PreMiD](https://discord.premid.app) và chúng tôi sẽ xem qua!

# Đóng góp

`Bản sửa đổi 3` của bộ quy định được viết và đóng góp bởi các cá nhân sau:

<div>
<a href="https://github.com/PreMiD"><img src="https://github.com/PreMiD.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

`Bản sửa đổi 2` của bộ quy định được viết và đóng góp bởi các cá nhân sau:

<div>
<a href="https://github.com/CobyPowers"><img src="https://github.com/CobyPowers.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

`Bản sửa đổi 1` được duy trì bởi các cá nhân sau:

<div>
<a href="https://github.com/CobyPowers"><img src="https://github.com/CobyPowers.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/i1u5"><img src="https://github.com/i1u5.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>
