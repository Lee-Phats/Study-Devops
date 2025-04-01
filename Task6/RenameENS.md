# Đổi ens38 thành ens35

## 🔹 Bước 1: 
Mở file `/etc/udev/rules.d/10-network.rules`:

```bash
sudo nano /etc/udev/rules.d/10-network.rules
```

Điền vào nội dung sau (thay `<MAC_ADDRESS_OF_ENS38>` bằng địa chỉ MAC của `ens38`):

```bash
SUBSYSTEM=="net", ACTION=="add", ATTR{address}=="<MAC_ADDRESS_OF_ENS38>", NAME="ens35"
```

Lưu và thoát file (`Ctrl + X → Y → Enter`).

## 🔹 Bước 2: Reload lại udev

```bash
sudo udevadm control --reload
```
## 🔹 Bước 3: Tắt và bật lại giao diện ens38: 
Sau khi áp dụng quy tắc, tắt và bật lại giao diện ens38:

```bash
sudo ip link set ens38 down
sudo ip link set ens38 up 
```

## 🔹 Bước 4: Khởi động lại máy

Sau khi máy khởi động lại, bạn có thể thử khởi động lại hệ thống:

```bash
sudo reboot
```

## 🔹 Bước 5: Kiểm tra lại tên giao diện

```bash
ip a
```