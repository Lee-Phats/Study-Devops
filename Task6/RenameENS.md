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

## 🔹 Bước 3: Kiểm tra lại giao diện mạng

```bash
ip a
```

## 🔹 Bước 4: Khởi động lại máy

```bash
sudo reboot
```

Sau khi máy khởi động lại, kiểm tra lại tên giao diện mạng bằng lệnh:

```bash
ip a
