---
title: Xử lý sự cố
description: Mọi thứ cần thiết để giúp bạn xử lý sự cố
published: true
date: 2021-09-18T14:08:01.002Z
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
<img src="https://i.imgur.com/wQA15xu.png" width="500px" style="max-width:100%;" />
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
Arch Linux based distros should use AUR (Arch User Repository) package that is named <code>premid</code> or <code>premid-git</code> (<em x-id="3">WARNING: This repository builds premid from our source code.</em>). If you don't want to install an AUR manager (yay etc.), you can check out our AppImage that is downloadable from our <strong x-id="1"><a href="https://github.com/premid/linux/releases">Linux repository</a></strong>.
<em x-id="3">Warning: the package in the <strong x-id="1">AUR</strong> repository is not maintained by us (as PreMiD organization), but by other people.</em>

### Port binding
You should know that <strong x-id="1">PreMiD</strong> binds itself to the port <strong x-id="1">3020</strong>. This is necessary for the Extension and the Application communicate. If <strong x-id="1">PreMiD</strong> shows you an error about this port, you should check if something is binded to the 3020 port by running <code>sudo lsof -i:3020</code> or <code>sudo netstat -tnlp | grep :3020</code> in your terminal. If some process is binded to it you should make sure to free the port and try running <code>PreMiD</code> again.

### PreMiD's AppImage doesn't launch at login
As we stated in our **Linux repository**, AppImage can't be launched at login. You can add it to autostart manually by doing these steps:
1. Make a file named <strong x-id="1">rc.local</strong> in the <code>/etc</code> directory.
2. Open this file in your favourite editor and paste given code with changing some things:
```bash
#!/bin/bash
# Required to run as /bin/bash (if you use zsh etc. you can change it.)

# Example: /home/PreMiD/PreMiD*.AppImage
<directory to appimage>/PreMiD*.AppImage

exit 0
```
3. Save file and chmod it as executable `sudo chmod a+x /etc/rc.local`.
4. Restart your PC and PreMiD AppImage should launch at login.

<a name="macos"></a>

# Xử lý sự cố cho hệ điều hành MacOS
### Error creating directory
<img src="https://i.imgur.com/td92lf6.png" width="300px" style="max-width:100%;" />

If you get this error, it means that your account doesn't have Administrator permissions and you need to create folder manually by doing these steps:
1. Open finder and open **Applications** folder.
2. Right-click on blank space and click **Create folder**.
3. To this folder assign `PreMiD` name (remember about upper-cased letters).
4. Open installer again.

# Điều đó chưa giải quyết được vấn đề của tôi
Please open a ticket in [#support](https://discord.premid.app/).
