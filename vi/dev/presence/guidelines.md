---
title: Bộ quy tắc khi làm Presence
description: Những luật lệ mà tất cả những nhà phát triển presence phải tuân thủ nếu muốn presence của mình được thêm vào.
published: true
date: 2021-10-18T16:26:36.089Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:44:53.883Z
---

<div align="center">
    <img src="https://github.com/PreMiD.png?size=2048" width="128px" style="max-width:100%;">
    <h3 style="font-size: 2rem; margin-bottom: 0">Bộ quy tắc khi làm Presence</h3>
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

- Luôn thêm số phiên bản tuân theo [tiêu chuẩn ngữ nghĩa của số phiên bản](https://semver.org), có khuân mẫu như sau: `<NEW-FEATURE>.<HUGE-BUGFIX>.<SMALL-BUGFIX-OR-METADATA-CHANGES>`. Những thứ khác như `1.0.0.1`, `1.0`, `1`, `1.0.0-BETA` hoặc đổi từ `1.0.0` sang `2.0.0` sau một bản sửa lỗi/thay đổi nhỏ là **không** được cho phép.
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

> The code you write **must** be _well-written_ and **must** be _readable_ and all strings must be grammatically correct (grammar errors on websites can be ignored).

> Each presence follows a strict linting ruleset which will be checked during the review process. A couple of recommendations can be seen below. [TypeScript Plugin Recommendations for Strict Type Checking](https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin/docs/rules). [ESlint Recommendations](https://eslint.org/docs/rules). [Prettier](https://prettier.io/).

Here is a list of rules you must follow when writing your `presence.ts` file:

- **Always** declare a new instance of the `Presence` class before any other variable to avoid rare issues that may occur; this is not a requirement by design so it could be removed in the future.
- **Never** use custom functions when [native variants are available](https://docs.premid.app/dev/presence#files-explained); this makes sure fixes on the extension level also apply to your presences. You're free to use whatever you need if you do not find them listed in the docs.
- It is **forbidden** to code presences for a site without adding support to its primary language (for e.g., a YouTube presence coded with support only for Portueguese and Japanese, but not English itself.)
- The `smallImageKey` and `smallImageText` fields are intended to provide additional/secondary context (such as `playing/paused` for video sites, `browsing` for regular sites, and other cases) not to promote Discord profiles or anything unrelated to PreMiD.
- You are **not** allowed to access `localStorage`.
- When accessing cookies for stored data, please prefix the key with `PMD_`.
- You may only make HTTP/HTTPS requests to `premid.app` or the presence website API. If you are using external domains, you will be required to explain why it is necessary. Only allowed API to make request is [`Fetch API`](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API).
- Do **not** set fields in the presenceData object to undefined after it has been declared, use the `delete` keyword instead. (for e.g., use `delete data.startTimestamp` instead of `data.startTimestamp = undefined`)
- You are **not** allowed to write presences that change the functionality of a given website. This includes the addition, deletion, or modification of DOM elements.
- Presences that use buttons should follow extra requirements:
  - Redirects to main page are prohibited.
  - Promoting websites by them is prohibited.
  - They can't display information you couldn't fit in other fields.
  - Redirecting directly to audio/video stream is prohibited.


## [**tsconfig.json**](https://docs.premid.app/dev/presence/tsconfig)

> Do **not** write your own `tsconfig.json` file, use what has been provided on [documentation](https://docs.premid.app/dev/presence/tsconfig).

## Modification

> You **must** change the version in the **metadata** to be a higher value from the previous version when making changes to either the **presence.ts**, **iframe.ts** or **metadata.json**.

In some situations, presences may behave unexpectedly or could use some minor changes to improve their functionality. Here is a list of rules that you **must** follow while modifiying presences.

- If the presence author hasn't been contactable in over a month, you may contact a reviewer to see if you can modify the presence.
- If you make modifications to a presence and change at least a **quarter** of the presence's codebase, you are allowed to add yourself as a contributor. Contact a reviewer for more information about this subject.
- Anyone may create PRs to fix bugs. Do **not** change images if they are not outdated and are in specifications.

# Verification

> **All** code contributed to the store will be licensed under the `Mozilla Public License 2.0`.

> If you need to contact someone, please use our official Discord server. All reviewers will have the `Reviewer` role on their profile.

> Please keep in mind that the reviewers work voluntarily and manage other repositories in addition to this one, your pull request may not get reviewed until hours or even days after it has been created.

> **Always** have an up-to-date fork before creating your pull request. This will help limit false positives from the checks.

The most important process of presence development is getting your presence on the store. This is done by making a [pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request) on GitHub on the `PreMiD/Presences` repository. Our reviewers will confirm that your presence is up to standards and will push it onto the store.

<div>
  <h2 style="font-size: 2rem; margin-bottom: 0;">Presence Reviewers</h2>
  <a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a> <a href="https://github.com/Slowlife01"><img src="https://github.com/Slowlife01.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a> <a href="https://github.com/EncryptedDev"><img src="https://github.com/EncryptedDev.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
  <br />
</div>

## `Restrictions`

Repetitive offenses such as breaking guidelines, spamming pull requests, threats, or innapropriate behavior will get you banned from creating presences.

In this scenario, the following changes will occur:

- Presences under your management will be transferred to the PreMiD bot or another user (reviewer decision). The application id for each presence will be recreated under the new owner's name.
- All of your issues and pull requests (presence creation, presence contribution, etc) created following the ban will be prompty closed.
- Tickets created under your name regarding presence development will be deleted.

## `Reviewing`

A few things you should know after opening a pull request:

- It takes 2 reviewers to merge a pull request.
- If a pull request is inactive for a period of 7 days, it will be promptly closed.
- All checks **must** be passed in order to merge.
- ⚠️ You **must** provide new, unaltered screenshots (taken by you) showing a side-by-side comparison of your profile and the website to prove that your presence works. _You are allowed to stitch screenshots together for viewing pleasure_ This applies for both creation and modification.
- ⚠️ You are also **required** to include screenshots of the presence settings in the extension if supplied. An example can be seen [here](https://imgur.com/a/OD3sj5R).

## `Checks`

![Example of checks](https://i.imgur.com/vF7QpBH.png)

Currently, a presence goes through 3 separate stages of checks. All of these checks help the reviewers determine whether your presence is suitable for deployment.

- `DeepScan` is a bot that checks for code quality. If you ever receive errors for new issues, you are **required** to fix them. *Warning: DeepScan doesn't always give you errors. Please look at CodeFactor warnings instead.*
- `CodeFactor` is a bot that checks for code quality. If you ever receive errors for new issues, you are **required** to fix them.
- `Schema Validation` will scan your `metadata.json` file for any errors (for e.g., missing fields, invalid value types, etc.). If you ever see any new issues, you are also **required** to fix those. Adding a schema field to your `metadata.json` file will allow your text editor (if supported) to show you these errors during development.

## `Additional Rules`

- **Always** make sure to start your presence in the most appropriate folder, if its name starts with _any_ Latin letter then it must be under its alphabetical match (for e.g., `D/dアニメストア` or `G/Google`). Any other Unicode/non-Latin characters **must** be under the `#` folder (for e.g., `#/巴哈姆特`) and numbers under the `0-9` folder (for e.g., `0-9/4anime`).

After meeting all of the guidelines with the proper reviews and checks, your presence will be merged with the store.

# Suggestions

If you have some suggestions about our guidelines, you should contact us @ [PreMiD's Discord server](https://discord.premid.app) and we will check them!

# Contributions

`Revision 3` of the guidelines was written and was contributed to by the following individuals:

<div>
<a href="https://github.com/PreMiD"><img src="https://github.com/PreMiD.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

`Revision 2` of the guidelines was written and was contributed to by the following individuals:

<div>
<a href="https://github.com/CobyPowers"><img src="https://github.com/CobyPowers.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>

`Revision 1` was maintained by the following individuals:

<div>
<a href="https://github.com/CobyPowers"><img src="https://github.com/CobyPowers.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/Bas950"><img src="https://github.com/Bas950.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
<a href="https://github.com/i1u5"><img src="https://github.com/i1u5.png?size=2048" width="48px" style="max-width:100%; border-radius: 50%;"/></a>
</div>
