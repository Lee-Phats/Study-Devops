# Hướng dẫn kết nối DHCP giữa hai máy ảo VMware thông qua Host-Only

Để máy ảo có card **Host-only** nhận được IP từ DHCP server mà bạn đã cài trên máy ảo **có card NAT**, bạn cần đảm bảo các bước sau (giống như bạn đang dựng một **router/DHCP server** trên máy NAT để cấp IP cho máy còn lại):

---

## 🧠 Tổng quan:

| Máy ảo | Vai trò | Card mạng | Ghi chú |
|--------|--------|------------|--------|
| Máy A  | DHCP Server | NAT (`ens33`) | Có internet |
|        |               | Host-only (`ens37`) | Cấp DHCP cho máy B |
| Máy B  | Client | Host-only (`ens33`) | Nhận IP từ máy A |

---

## ✅ Các bước chi tiết:

### 🔧 Bảng 1: Cấu hình máy ảo A (DHCP Server)

| Bước | Hành động |
|------|-----------|
| **1** | Kiểm tra 2 card mạng `ens33` (NAT), `ens37` (Host-only) |
| **2** | Gán IP tĩnh cho `ens33` |

```bash
sudo nano /etc/netplan/01-netcfg.yaml
```

```yaml
network:
  version: 2
  ethernets:
    ens33:
      dhcp4: yes
    ens37:
      addresses: [10.10.10.55/24]
```
![alt text](image-30.png)


> Sau đó chạy: `sudo netplan apply`

| Bước | Hành động |
|------|-----------|
| **3** | Cài DHCP server: |

```bash
sudo apt update
sudo apt install isc-dhcp-server
```
Cách kiểm tra đã cài gói isc-dhcp-server:
![alt text](image-10.png)


| **4** | Chỉnh file `/etc/default/isc-dhcp-server` |

```bash
INTERFACESv4="ens37"
```
![alt text](image-31.png)


| **5** | Chỉnh file `/etc/dhcp/dhcpd.conf` |

```
subnet 10.10.10.0 netmask 255.255.255.0 {
  range 10.10.10.64 10.10.10.100;
  option routers 10.10.10.1;
  option domain-name-servers 8.8.8.8;
}
```
![alt text](image-32.png)


| **6** | Restart dịch vụ DHCP |

```bash
sudo systemctl restart isc-dhcp-server
```

---

### 🖥️ Bảng 2: Cấu hình máy ảo B (Client)

| Bước | Hành động |
|------|-----------|
| **1** | Gắn card `host-only` (cùng VMnet với máy A) |
| **2** | Cấu hình để dùng DHCP |

```bash
sudo nano /etc/netplan/01-netcfg.yaml
```

```yaml
network:
  version: 2
  ethernets:
    ens33:
      dhcp4: true
```
![alt text](image-33.png)


> Sau đó chạy: `sudo netplan apply`

| **3** | Kiểm tra IP |

```bash
ip a
```
![alt text](image-34.png)


Bạn sẽ thấy IP nằm trong dải `10.10.10.64 – 10.10.10.100` nếu nhận đúng.

| **4** | Kiểm tra kết nối đến máy A |

```bash
ping 10.10.10.1
```

Nếu thành công → máy ảo B đã nhận DHCP từ máy ảo A.

---
![alt text](image-35.png)