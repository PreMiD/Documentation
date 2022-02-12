---
title: Gỡ rối
description: Mọi thứ cần thiết để giúp bạn gỡ rối
published: true
date: 2021-12-20T14:27:18.034Z
tags:
editor: markdown
dateCreated: 2021-09-07T01:17:32.312Z
---

> Hãy chắc chắn rằng bạn đã có cả tiện ích mở rộng **và** ứng dụng được cài đặt! 
> 
> {.is-warning}

Được bao gồm trên trang này:
1. [Xử lý sự cố chung](https://docs.premid.app/troubleshooting#general)
2. [Xử lý sự cố cho hệ điều hành Linux](https://docs.premid.app/troubleshooting#linux)
3. [Xử lý sự cố cho hệ điều hành MacOS](https://docs.premid.app/troubleshooting#macos)

<a name="general"></a>

# Xử lý sự cố chung
> Bạn có thể sử dụng [công cụ này](https://qkeleq10.github.io/PreMiD-Troubleshooting/) để có thể xác định vấn đề dễ dàng hơn. 
> 
> {.is-info}
### Tải lại trang
Bạn có thể nhấn <kbd>CTRL+R</kbd>/<kbd>F5</kbd> (Windows) hoặc <kbd>CMD+R</kbd> (MacOS) trên bàn phím của bạn thay vì tìm kiếm nút tải lại.

### Bạn có đang sử dụng ứng dụng Discord không?
PreMiD sẽ **không** hoạt động trên phiên bản trình duyệt web của Discord, vui lòng tải xuống phiên bản ứng dụng [tại đây](https://discord.com/download).

### Hãy chắc chắn rằng bạn đã kích hoạt Hoạt động game của Discord trong phần cài đặt
**Cài đặt người dùng** > **Hoạt động trong game**
<img src="https://i.imgur.com/9SfrrWm.png" width="500px" style="max-width:100%;" />

### Hãy chắc chắn rằng Discord đang KHÔNG hoạt động ở dưới quyền quản trị viên
Rất quan trọng. Discord RPC sẽ không hoạt động nếu bạn chạy Discord dưới quyền quản trị viên.

### Bạn có đang sử dụng presence có nút cài đặt không?
Nhiều presence (bao gồm `Twitch` và `SoundCloud`) bị ảnh hưởng bởi sự cố phần mở rộng. Sự cố này khiến phần mở rộng không lấy đúng các giá trị mặc định của cài đặt.

Để giải quyết vấn đề này, tất cả những gì bạn phải làm là chuyển đổi cài đặt trên cùng:
<img src="https://i.imgur.com/JtXxTzg.gif" width="500px" style="max-width:100%;" />

### Khởi động lại trình duyệt của bạn
<kbd>Alt</kbd> + <kbd>F4</kbd> (Windows) hoặc <kbd>CMD</kbd> + <kbd>Q</kbd> (MacOS) cũng hoạt động tốt. (Rõ ràng là bạn phải khởi động lại trình duyệt của mình.)

### Khởi động lại PreMiD (Ứng dụng)
<img src="https://i.imgur.com/g3ShdnU.png" width="500px" style="max-width:100%;" />
Sau đó bạn phải khởi động lại PreMiD.

### Tải lại/khởi động lại Discord
Nhấn <kbd>CTRL+R</kbd> (Windows) hoặc <kbd>CMD+R</kbd> (MacOS) trên bàn phím của bạn để khởi động lại Discord một cách thủ công.

### Kiểm tra xem có phần mềm diệt virus hay tường lửa hoạt động trên máy tính của bạn không
Đôi lúc phần mềm diệt vi-rút và tường lửa sẽ chặn các ứng dụng nếu chúng tạo/lưu trữ máy chủ hoặc chỉ là kết nối Internet. Chúng tôi đang sử dụng máy chủ cục bộ để nhận và truyền dữ liệu giữa ứng dụng của chúng tôi và tiện ích mở rộng, nếu bạn chặn tính năng truyền dữ liệu thì PreMiD có thể sẽ không hoạt động.

### Tắt các tiện ích mở rộng
Hãy tắt các tiện ích mở rộng khác và thử lại. Nếu được, hãy mở từng tiện ích một sau đó hãy cho chúng tôi biết tiện ích nào gây xung đột với PreMiD.

### Khởi động lại máy tính của bạn
Tôi mong là bạn biết cách khởi động lại máy tính.

### Cài đặt lại PreMiD
Đôi khi các tệp có vấn đề... Hướng dẫn cài đặt có thể được tìm thấy [tại đây](/install).

### Gỡ cài đặt thủ công
Hệ điều hành Windows: Điền `%appdata%` vào trình duyệt thư mục và xóa thư mục `PreMiD`. MacOS: `~/users/USER/~Library/Application Support/` và xóa thư mục `PreMiD`.

### McAfee phát hiện PreMiD là vi-rút (Windows)
Đây là một kết quả sai từ McAfee và chúng tôi đã báo cáo vấn đề với họ, bây giờ bạn có thể loại trừ PreMiD khỏi quá trình quét bằng cách thực hiện các bước sau:

> Nếu bạn không cảm thấy đủ tự tin để thực hiện những bước này, đừng ngần ngại tạo một phiếu hỗ trợ tại [#support](https://discord.premid.app/) và một người trong Đội ngũ Hỗ trợ của chúng tôi sẽ giúp bạn! 
> 
> {.is-warning}

1. Mở ứng dụng McAfee và bấm nút cài đặt ở trên cùng phía bên phải. <img src="https://i.imgur.com/rPLZn6c.png" width="500px" style="max-width:100%;" />
2. Chọn "Tệp tin cách ly" (Thứ hai từ trên đầu).
3. Mở rộng nó, và nhấn vào nút `>` ở phía trước tệp tin với tên "settings.dat".
4. Hãy chắc chắn đường dẫn là "AppData\Local\Temp\PreMiD", sau đó chọn nó và bấm phục hồi. <img src="https://i.imgur.com/9nvHmiI.png" width="500px" style="max-width:100%;" />
5. Sau khi phục hồi xong bạn có thể đóng cửa sổ "Các tệp tin đã bị cách ly", sau đó bấm vào nút cài đặt ở trên cùng bên phải một lần nữa.
6. Chọn "Quét thời gian thực" (Thứ ba từ trên đầu).
7. Mở rộng nó và bấm "Thêm tệp tin".
8. Gõ "%appdata%" vào thanh địa chỉ của trình duyệt tệp tin sau đó bấm Enter. <img src="https://i.imgur.com/2bchwLe.png" width="500px" style="max-width:100%;" />
9. Mở thư mục "PreMiD" và chọn tệp tin "PreMiD.exe" và bấm "mở". <img src="https://i.imgur.com/aHOyv3V.png" width="500px" style="max-width:100%;" />
10. McAfee sẽ bỏ qua tệp tin này, chỉ cần mở ứng dụng của chúng tôi là xong.

### Trạng thái của PreMiD bị lỗi trên Discord
Đừng lo lắng. Nhấn tổ hợp phím <kbd>CTRL+R</kbd> (Windows) hoặc <kbd>CMD+R</kbd> (MacOS) trên cửa sổ Discord để làm mới Discord.

<a name="linux"></a>

# Xử lý sự cố cho hệ điều hành Linux
### Hệ điều hành Ubuntu/Debian và tương tự
Nếu bạn đã tải Discord qua Snapcraft, RPC sẽ không hoạt động. Bạn sẽ phải gỡ cài đặt phiên bản discord Snapcraft bằng cách thực thi lệnh `sudo snap remove discord` trong một cửa sổ lệnh, rồi tải xuống phiên bản **[Discord cho Linux](https://discordapp.com/api/download?platform=linux)** (**[hoặc Discord Canary](https://discordapp.com/api/canary/download?platform=linux)**), sau đó mở thư mục mà bạn vừa tải Discord tới (thường là `$HOME/Downloads`), sau đó cài đặt gói bằng lệnh `sudo dpkg -i discord-*.deb`. Nếu AppImage không hoạt động, bạn nên xem xét kiểm tra các gói khác của chúng tôi bằng **[liên kết này](https://packagecloud.io/premid/linux)**.

### Hệ điều hành dựa trên Arch Linux
Các distro dựa trên Arch Linux nên sử dụng gói AUR (Kho lưu trữ người dùng Arch) có tên <code mark = "crwd-mark"> premid </code> hoặc <code> premid-git </code> ( <em x-id="3">CẢNH BÁO: Kho lưu trữ này được xây dựng từ mã nguồn của chúng tôi. </em>). Nếu bạn không muốn cài đặt trình quản lý AUR (yay, v.v.), bạn có thể xem AppImage có thể tải xuống từ <strong x-id = "1" mark = "crwd-mark"> <a href = "của chúng tôi https://github.com/premid/linux/releases">Kho lưu trữ Linux</a></strong>. <em x-id = "3" mark = "crwd-mark"> Cảnh báo: gói trong kho <strong x-id = "1">AUR</strong> không được chúng tôi duy trì (với tư cách là tổ chức PreMiD), nhưng bởi những người khác.</em>

### Gắn cổng
Bạn nên biết rằng <strong x-id = "1" mark = "crwd-mark"> PreMiD </strong> tự liên kết với cổng <strong x-id = "1" mark = "crwd-mark">3020</strong>. Điều này là cần thiết để Tiện ích mở rộng và Ứng dụng giao tiếp. Nếu <strong x-id = "1" mark = "crwd-mark">PreMiD</strong> hiển thị cho bạn lỗi về cổng này, bạn nên kiểm tra xem phần mềm khác được liên kết với cổng 3020 hay không bằng cách chạy <code mark = "crwd -mark "> sudo lsof -i: 3020 </code> hoặc <code mark =" crwd-mark "> sudo netstat -tnlp | grep: 3020 </code> trong terminal của bạn. Nếu vài chương trình đã được gán vào cổng đó thì bạn nên làm trống cổng và thử chạy lại <code>PreMiD</code> lần nữa.

### PreMiD AppImage không tự khởi động khi đăng nhập
Như chúng tôi đã nêu trong **kho lưu trữ Linux** của chúng tôi, AppImage không thể tự khởi động khi đăng nhập. Bạn có thể tự thêm nó vào phần tự khởi động qua các bước sau:
1. Tạo một tệp tin tên là <strong x-id="1">rc.local</strong> ở trong thư mục <code>/etc</code>.
2. Mở tệp tin này ở trong trình soạn thảo ưa thích của bạn và chép đoạn mã sau vào với một chút thay đổi:
```bash
#!/bin/bash
# Cần thiết để chạy dưới thư mục /bin/bash (nếu bạn sử dụng zsh, vân vân. bạn có thể thay đổi nó.)

# Ví dụ: /home/PreMiD/PreMiD*.AppImage
<đường dẫn tới tệp ứng dụng>/PreMiD*.AppImage

exit 0
```
3. Lưu tệp tin lại và chạy lệnh chmod cho nó dưới dạng có thể thực thi `sudo chmod a+x /etc/rc.local`.
4. Khởi động lại máy tính của bạn và AppImage PreMiD sẽ khởi động khi đăng nhập.

<a name="macos"></a>

# Xử lý sự cố cho hệ điều hành MacOS
### Lỗi khi tạo thư mục
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

Nếu bạn gặp lỗi này, điều đó có nghĩa là tài khoản của bạn không có quyền Quản trị viên và bạn phải tự tạo thư mục bằng các bước sau:
1. Mở trình tìm kiếm và mở thư mục **Ứng dụng**.
2. Nhấp chuột phải vào khoảng trống và nhấn **Tạo thư mục**.
3. Gán tên `PreMiD` và thư mục (hãy nhớ viết hoa đầy đủ).
4. Chạy lại trình cài đặt.

# Điều đó chưa giải quyết được vấn đề của tôi
Vui lòng mở một thẻ trong kênh [#support](https://discord.premid.app/).
