# 1. Học thuộc tính nhẩm về IP 

# 2. Distro trong hệ điều hành Linux

## Khái niệm
Trong hệ điều hành Linux, **distro** (viết tắt của "distribution") là các phiên bản tùy chỉnh của Linux được phát triển từ **hạt nhân Linux (Linux kernel)** kết hợp với các phần mềm và công cụ hỗ trợ khác để tạo thành một hệ điều hành hoàn chỉnh.

## **Cấu trúc của một Distro Linux**
1. **Linux Kernel**: Thành phần cốt lõi, chịu trách nhiệm giao tiếp giữa phần cứng và phần mềm.
2. **Trình quản lý gói (Package Manager)**: Công cụ cài đặt, nâng cấp, và quản lý phần mềm (ví dụ: APT, YUM, Pacman).
3. **Môi trường desktop**: Giao diện đồ họa (GUI), chẳng hạn GNOME, KDE, XFCE.
4. **Phần mềm và tiện ích hệ thống**: Gồm trình soạn thảo văn bản, trình duyệt web, công cụ quản lý tệp, v.v.
5. **Công cụ quản lý khởi động (Bootloader)**: Chẳng hạn GRUB, giúp khởi động hệ điều hành.

## **Phân loại Distro Linux**
### **1. Dựa trên hệ thống gốc**
- **Debian-based**: Dùng Debian làm nền tảng, ví dụ:
  - Ubuntu (phổ biến, dễ dùng cho người mới).
  - Linux Mint (thân thiện với người dùng, giao diện đẹp).
- **Red Hat-based**: Dùng Red Hat làm nền tảng, ví dụ:
  - Fedora (cập nhật nhanh, thử nghiệm công nghệ mới).
  - CentOS / Rocky Linux (ổn định, dùng cho server).
- **Arch-based**: Ví dụ:
  - Arch Linux (tùy chỉnh sâu, dành cho người dùng nâng cao).
  - Manjaro (thân thiện hơn Arch nhưng vẫn mạnh mẽ).

### **2. Dựa trên mục đích sử dụng**
- **Distro cho người dùng cá nhân**:
  - Ubuntu, Linux Mint, Zorin OS.
- **Distro cho máy chủ (Server)**:
  - CentOS, Debian, Ubuntu Server.
- **Distro chuyên biệt**:
  - Kali Linux (dùng để kiểm thử bảo mật).
  - Tails (tập trung vào bảo mật và quyền riêng tư).
  - Raspberry Pi OS (tối ưu cho Raspberry Pi).

### **3. Dành cho người mới và chuyên gia**
- **Người mới bắt đầu**: Ubuntu, Linux Mint, Zorin OS.
- **Người dùng nâng cao**: Arch Linux, Gentoo, Slackware.

## **Đặc điểm chung của Distro Linux**
- **Mã nguồn mở**: Miễn phí, có thể chỉnh sửa theo nhu cầu.
- **Tùy biến cao**: Người dùng có thể thay đổi mọi thứ, từ giao diện đến cài đặt hệ thống.
- **Cộng đồng mạnh mẽ**: Các distro Linux đều có cộng đồng hỗ trợ đông đảo.

## **Cách hoạt động**
- **Kernel Linux**: Là nhân hệ điều hành, quản lý phần cứng và tài nguyên hệ thống.
- **Hệ thống phân cấp thư mục**: Tổ chức theo cấu trúc cây với thư mục gốc (/), chứa các thư mục hệ thống quan trọng như /bin, /etc, /home.
- **Quản lý gói APT**: Hệ thống quản lý và cài đặt phần mềm thông qua các repository.
- **Systemd**: Quản lý khởi động và các dịch vụ hệ thống.
- **Giao diện người dùng**: Có thể sử dụng qua CLI (Command Line Interface) hoặc GUI (Graphical User Interface).
- **Bảo mật**: Hệ thống phân quyền người dùng và nhóm, tường lửa UFW, và các cơ chế bảo mật khác.

---

# 3. Tìm hiểu các bước cài hệ điều hành Ubuntu Server
- Thực hành cài đặt hệ điều hành trên VMWare.

---

# 4. Tìm hiểu về phiên bản, dòng và cách đánh số

## **1. Phiên bản và dòng trong Linux**
### **Hạt nhân Linux (Linux Kernel)**
Hạt nhân Linux là trung tâm của hệ điều hành. Nó có **hệ thống đánh số phiên bản riêng**:

**Cách đánh số phiên bản kernel Linux:**
- **X.Y.Z** (ví dụ: `6.5.4`):
  - **X**: Phiên bản chính (major version): Thay đổi lớn, mang lại tính năng hoặc cải tiến đột phá.
  - **Y**: Phiên bản phụ (minor version): Thay đổi tính năng, sửa lỗi, cập nhật nhỏ.
  - **Z**: Bản vá (patch): Sửa lỗi bảo mật hoặc khắc phục các vấn đề khẩn cấp.

**Ví dụ:**
- `5.4.0`: Phiên bản chính thứ 5, cập nhật phụ thứ 4.
- `6.2.10`: Phiên bản chính thứ 6, cập nhật phụ thứ 2, bản vá thứ 10.

### **Dòng LTS (Long-Term Support):**
- Các phiên bản kernel LTS được duy trì và cập nhật trong **2-6 năm** với các bản vá bảo mật và sửa lỗi.
- Ví dụ: Kernel `5.10` và `6.1` là các bản LTS.

---

## **2. Phiên bản và cách đánh số trong Ubuntu**
Ubuntu là một bản phân phối Linux dựa trên Debian, có cách đánh số phiên bản riêng.

**Cách đánh số phiên bản của Ubuntu:**
- Định dạng: **YY.MM** (năm.tháng).
  - **YY**: Hai số cuối của năm phát hành.
  - **MM**: Tháng phát hành (thường là tháng 4 hoặc 10).

**Ví dụ:**
- **Ubuntu 22.04**: Phát hành vào tháng 4 năm 2022.
- **Ubuntu 20.10**: Phát hành vào tháng 10 năm 2020.

### **Dòng LTS (Long-Term Support):**
- Phiên bản LTS được phát hành **2 năm một lần** vào tháng 4 (ví dụ: `22.04`, `20.04`, `18.04`).
- Được hỗ trợ cập nhật bảo mật và sửa lỗi trong **5 năm** (hoặc hơn nếu sử dụng dịch vụ mở rộng).

---

# 5. Các loại giấy phép mã nguồn mở
## **So sánh Copyleft và Permissive**

| **Đặc điểm**             | **Copyleft**        | **Permissive**      |
|--------------------------|--------------------|---------------------|
| **Mức độ hạn chế**       | Cao                | Thấp                |
| **Yêu cầu chia sẻ mã**   | Có                 | Không bắt buộc      |
| **Ví dụ giấy phép**      | GPL, AGPL, MPL     | MIT, Apache, BSD    |
| **Ví dụ ứng dụng**       | Linux Kernel, Firefox | React, TensorFlow, FreeBSD |

## **Cách chọn giấy phép**
- **Muốn bảo vệ mã nguồn mở:** Chọn GPL hoặc AGPL.
- **Muốn tự do cho người dùng:** Chọn MIT hoặc **Apache**.
- **Phần mềm kết hợp mã mở và độc quyền:** MPL hoặc LGPL.

---

# 6. Notion
