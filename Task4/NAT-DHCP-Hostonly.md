# Thay đổi card mạng trên máy ảo

## 1. Truy cập vào VMWare và Khởi chạy 2 máy ảo:
![alt text](image-19.png)

Sau khi đã khởi chạy, để thay đổi thành card mạng host-only, làm như sau:

Chuột phải vào 1 máy ảo bất kì và chọn `Settings`:

![alt text](image-20.png)

Hiện ra một cửa sổ mới:

![alt text](image-21.png)
![alt text](image-22.png)

Chọn **Network Adapter**, nếu đang ở chế độ **Host-only** thì nhấn `OK` và thoát.

Còn nếu chưa thì thay đổi ở bên cạnh thành **Host-only**:

![alt text](image-23.png)

Sau đó nhấn `OK` là xong.

Máy chủ thứ hai làm tương tự.

## 2. Thay đổi khoảng DHCP của máy ảo host-only

### 2.1. Đầu tiên, chạy một máy ảo bất kỳ.

![alt text](image-24.png)

Chọn **Edit**:

![alt text](image-25.png)

### 2.2. Chọn đến phần **Virtual Network Editor...**

![alt text](image-26.png)

Cửa sổ mới hiện ra:

![alt text](image-27.png)

### 2.3. Chọn **Change Settings** để cho phép thay đổi cài đặt.

![alt text](image-28.png)

Sau đó vào lại **Virtual Network Editor...**

![alt text](image-29.png)

### 2.4. Chọn **DHCP Settings**

![alt text](image-30.png)

Cửa sổ thay đổi khoảng DHCP hiện ra:

![alt text](image-31.png)

### 2.5. Kiểm tra kết quả

Để kiểm tra, ta sang máy ảo thứ hai và thực hiện `ping` đến địa chỉ IP trong khoảng mới của máy ảo thứ nhất.

## 3. Link tham khảo:
[Hướng dẫn thay đổi card mạng trên VMWare](https://www.youtube.com/watch?v=INVDflOtIYQ)

