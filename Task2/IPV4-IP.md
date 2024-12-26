# Tìm hiểu lý thuyết về IPv4 và các lệnh về IP trên máy tính Windows 10/11

## Mục lục

1. [Lý thuyết về IPv4](#1-lý-thuyết-về-ipv4)
    1.1. [Cấu trúc địa chỉ IPv4](#11-cấu-trúc-địa-chỉ-ipv4)
    1.2. [Phân loại địa chỉ IPv4](#12-phân-loại-địa-chỉ-ipv4)
    1.3. [Subnetting](#13-subnetting)
    1.4. [CIDR (Classless Inter-Domain Routing)](#14-cidr-classless-inter-domain-routing)
2. [Các lệnh về IP trên Windows 10/11](#2-các-lệnh-về-ip-trên-windows-1011)
    2.1. [ipconfig](#21-ipconfig)
    2.2. [ping](#22-ping)
    2.3. [tracert](#23-tracert)
    2.4. [netstat](#24-netstat)
    2.5. [nslookup](#25-nslookup)
    2.6. [route](#26-route)
    2.7. [arp](#27-arp)
    2.8. [telnet](#28-telnet)
    2.9. [PowerShell cmdlets liên quan đến mạng](#29-powershell-cmdlets-liên-quan-đến-mạng)
3. [Thực hành nâng cao và Tài liệu tham khảo](#3-thực-hành-nâng-cao-và-tài-liệu-tham-khảo)
    3.1. [Phân chia mạng (Subnetting) và CIDR](#31-phân-chia-mạng-subnetting-và-cidr)
    3.2. [Bài tập thực hành](#32-bài-tập-thực-hành)
    3.3. [Tài liệu tham khảo](#33-tài-liệu-tham-khảo)

---

## 1. Lý thuyết về IPv4

**IPv4 (Internet Protocol version 4)** là phiên bản thứ tư của giao thức Internet và là phiên bản được sử dụng rộng rãi nhất hiện nay. IPv4 sử dụng địa chỉ 32-bit, cho phép tổng cộng khoảng 4.3 tỷ địa chỉ IP duy nhất.

### 1.1. Cấu trúc địa chỉ IPv4

Địa chỉ IPv4 được biểu diễn dưới dạng bốn số thập phân, mỗi số nằm trong khoảng từ 0 đến 255, ngăn cách nhau bởi dấu chấm (ví dụ: `192.168.1.1`).

### 1.2. Phân loại địa chỉ IPv4

- **Class A:** `0.0.0.0` – `127.255.255.255`
- **Class B:** `128.0.0.0` – `191.255.255.255`
- **Class C:** `192.0.0.0` – `223.255.255.255`
- **Class D:** `224.0.0.0` – `239.255.255.255` (Multicast)
- **Class E:** `240.0.0.0` – `255.255.255.255` (Reserved)

### 1.3. Subnetting

Subnetting là quá trình phân chia một mạng lớn thành các mạng con nhỏ hơn để quản lý hiệu quả địa chỉ IP và tăng cường bảo mật.

**Ví dụ về Subnetting:**

Giả sử bạn có địa chỉ mạng `192.168.1.0/24` và muốn chia thành 4 mạng con:

1. **Bước 1:** Xác định số mạng con cần tạo: 4
2. **Bước 2:** Tính số bit cần thêm: 2 bit (vì 2² = 4)
3. **Bước 3:** Cập nhật subnet mask: `/24 + 2 = /26`

**Các mạng con sẽ là:**

- `192.168.1.0/26`
- `192.168.1.64/26`
- `192.168.1.128/26`
- `192.168.1.192/26`

### 1.4. CIDR (Classless Inter-Domain Routing)

CIDR cho phép phân chia địa chỉ IP một cách linh hoạt hơn so với các lớp truyền thống (Class A, B, C). CIDR sử dụng notations dạng `địa_chỉ/IP` để biểu thị phạm vi địa chỉ.

**Ví dụ về CIDR:**

- `192.168.1.0/24` tương đương với subnet mask `255.255.255.0`
- `10.0.0.0/8` tương đương với subnet mask `255.0.0.0`

---

## 2. Các lệnh về IP trên Windows 10/11

Windows cung cấp nhiều lệnh dòng (command-line) để quản lý và kiểm tra cấu hình mạng. Dưới đây là một số lệnh quan trọng liên quan đến IP:

### 2.1. ipconfig

- **Mô tả:** Hiển thị cấu hình mạng hiện tại của máy tính.
- **Cách sử dụng:**
  - `ipconfig` : Hiển thị địa chỉ IP, subnet mask, và default gateway cho tất cả các adapter mạng.
  - `ipconfig /all` : Hiển thị thông tin chi tiết hơn, bao gồm MAC address, DNS, DHCP,...
  - `ipconfig /release` : Giải phóng địa chỉ IP hiện tại.
  - `ipconfig /renew` : Yêu cầu địa chỉ IP mới từ DHCP.
  - `ipconfig /flushdns` : Xóa bộ nhớ đệm DNS.
- **Ví dụ:**
    ```bash
    ipconfig /all
    ```

### 2.2. ping

- **Mô tả:** Kiểm tra kết nối đến một địa chỉ IP hoặc tên miền.
- **Cách sử dụng:**
  - `ping [địa_chỉ_IP hoặc tên_miền]`
- **Ví dụ:**
    ```bash
    ping google.com
    ```

### 2.3. tracert

- **Mô tả:** Theo dõi đường đi của các gói tin đến đích, hiển thị các hop qua các router trung gian.
- **Cách sử dụng:**
  - `tracert [địa_chỉ_IP hoặc tên_miền]`
- **Ví dụ:**
    ```bash
    tracert 8.8.8.8
    ```

### 2.4. netstat

- **Mô tả:** Hiển thị các kết nối mạng hiện tại, cổng đang lắng nghe, thống kê giao thức.
- **Cách sử dụng:**
  - `netstat` : Hiển thị các kết nối TCP/UDP hiện tại.
  - `netstat -a` : Hiển thị tất cả các kết nối và cổng lắng nghe.
  - `netstat -b` : Hiển thị ứng dụng đang sử dụng các kết nối.
  - `netstat -n` : Hiển thị địa chỉ và cổng dưới dạng số.
- **Ví dụ:**
    ```bash
    netstat -an
    ```

### 2.5. nslookup

- **Mô tả:** Truy vấn DNS để tìm địa chỉ IP tương ứng với tên miền hoặc ngược lại.
- **Cách sử dụng:**
  - `nslookup [tên_miền]` : Tìm địa chỉ IP của tên miền.
  - `nslookup [địa_chỉ_IP]` : Tìm tên miền tương ứng với địa chỉ IP.
- **Ví dụ:**
    ```bash
    nslookup example.com
    ```

### 2.6. route

- **Mô tả:** Xem và chỉnh sửa bảng định tuyến mạng.
- **Cách sử dụng:**
  - `route print` : Hiển thị bảng định tuyến hiện tại.
  - `route add [địa_chỉ mạng] mask [mask] [gateway]` : Thêm một tuyến mới.
  - `route delete [địa_chỉ mạng]` : Xóa một tuyến.
- **Ví dụ:**
    ```bash
    route print
    ```

### 2.7. arp

- **Mô tả:** Hiển thị và chỉnh sửa bảng ARP (Address Resolution Protocol).
- **Cách sử dụng:**
  - `arp -a` : Hiển thị bảng ARP.
  - `arp -d [địa_chỉ_IP]` : Xóa một mục trong bảng ARP.
  - `arp -s [địa_chỉ_IP] [địa_chỉ_MAC]` : Thêm một mục tĩnh vào bảng ARP.
- **Ví dụ:**
    ```bash
    arp -a
    ```

### 2.8. telnet

- **Mô tả:** Kiểm tra kết nối đến một cổng cụ thể trên một máy chủ.
- **Cách sử dụng:**
  - `telnet [địa_chỉ_IP hoặc tên_miền] [cổng]`
- **Ví dụ:**
    ```bash
    telnet example.com 80
    ```
  - **Lưu ý:** Trên một số hệ thống, Telnet có thể không được cài đặt mặc định. Bạn có thể bật tính năng này qua Control Panel > Programs and Features > Turn Windows features on or off > chọn Telnet Client.

### 2.9. PowerShell cmdlets liên quan đến mạng

- **Get-NetIPAddress** : Hiển thị cấu hình địa chỉ IP.
- **New-NetIPAddress** : Thêm địa chỉ IP mới.
- **Remove-NetIPAddress** : Xóa địa chỉ IP.
- **Set-DNSClientServerAddress** : Cấu hình DNS.
- **Ví dụ:**
    ```powershell
    Get-NetIPAddress
    ```

### 2.10. Thực hành các lệnh

Để thực hành các lệnh trên, bạn có thể thực hiện các bước sau trên máy tính Windows 10/11:

1. **Mở Command Prompt hoặc PowerShell:**
   - Nhấn `Windows + R`, gõ `cmd` hoặc `powershell`, nhấn `Enter`.

2. **Sử dụng lệnh `ipconfig`:**
   - Gõ `ipconfig` để xem địa chỉ IP hiện tại.
   - Gõ `ipconfig /all` để xem thông tin chi tiết.

3. **Kiểm tra kết nối mạng với `ping`:**
   - Gõ `ping google.com` để kiểm tra kết nối đến Google.
   - Gõ `ping 8.8.8.8` để ping đến DNS của Google.

4. **Theo dõi đường đi với `tracert`:**
   - Gõ `tracert google.com` để xem các hop giữa máy bạn và Google.

5. **Xem các kết nối mạng hiện tại với `netstat`:**
   - Gõ `netstat -an` để xem tất cả các kết nối và cổng lắng nghe.

6. **Truy vấn DNS với `nslookup`:**
   - Gõ `nslookup example.com` để tìm địa chỉ IP của example.com.

7. **Xem bảng định tuyến với `route`:**
   - Gõ `route print` để xem bảng định tuyến hiện tại.

8. **Kiểm tra bảng ARP với `arp`:**
   - Gõ `arp -a` để xem các địa chỉ MAC liên kết với địa chỉ IP trong mạng cục bộ.

9. **Kiểm tra cổng với `telnet`:**
   - Gõ `telnet google.com 80` để kiểm tra kết nối đến cổng HTTP của Google.
   - **Lưu ý:** Trên một số hệ thống, Telnet có thể không được cài đặt mặc định. Bạn có thể bật tính năng này qua Control Panel > Programs and Features > Turn Windows features on or off > chọn Telnet Client.

10. **Sử dụng PowerShell cmdlets:**
    - Mở PowerShell và gõ `Get-NetIPAddress` để xem các địa chỉ IP cấu hình trên máy.

### 2.11. Một số lưu ý khi sử dụng các lệnh

- **Quyền quản trị:** Một số lệnh yêu cầu quyền quản trị để thực thi, ví dụ như `route add` hoặc `arp -s`. Bạn cần chạy Command Prompt hoặc PowerShell với quyền Administrator.
  
- **Cẩn thận khi thay đổi cấu hình mạng:** Khi sử dụng các lệnh để thêm hoặc xóa địa chỉ IP, hãy đảm bảo hiểu rõ tác động của các thay đổi để tránh gây gián đoạn kết nối mạng.

- **Tham khảo tài liệu:** Để hiểu rõ hơn về các tùy chọn và cú pháp của từng lệnh, bạn có thể sử dụng `/?` sau tên lệnh. Ví dụ: `ipconfig /?`

---

## 3. Thực hành nâng cao và Tài liệu tham khảo

### 3.1. Phân chia mạng (Subnetting) và CIDR

#### Phân chia mạng (Subnetting)

Subnetting là quá trình chia một mạng lớn thành các mạng con nhỏ hơn. Điều này giúp quản lý địa chỉ IP hiệu quả hơn, cải thiện hiệu suất mạng và tăng cường bảo mật.

**Ví dụ về Subnetting:**

Giả sử bạn có địa chỉ mạng `192.168.1.0/24` và muốn chia thành 4 mạng con:

1. **Bước 1:** Xác định số mạng con cần tạo: 4
2. **Bước 2:** Tính số bit cần thêm: 2 bit (vì 2² = 4)
3. **Bước 3:** Cập nhật subnet mask: `/24 + 2 = /26`

**Các mạng con sẽ là:**

- `192.168.1.0/26`
- `192.168.1.64/26`
- `192.168.1.128/26`
- `192.168.1.192/26`

#### CIDR (Classless Inter-Domain Routing)

CIDR cho phép phân chia địa chỉ IP một cách linh hoạt hơn so với các lớp truyền thống (Class A, B, C). CIDR sử dụng notations dạng `địa_chỉ/IP` để biểu thị phạm vi địa chỉ.

**Ví dụ về CIDR:**

- `192.168.1.0/24` tương đương với subnet mask `255.255.255.0`
- `10.0.0.0/8` tương đương với subnet mask `255.0.0.0`

### 3.2. Bài tập thực hành

Dưới đây là một số bài tập để bạn thực hành các lệnh và khái niệm về IPv4 trên Windows:

1. **Xác định địa chỉ IP hiện tại:**
   - Mở Command Prompt và gõ `ipconfig` để xem địa chỉ IP của máy bạn.

2. **Ping đến một địa chỉ IP và tên miền:**
   - Gõ `ping 8.8.8.8` để kiểm tra kết nối đến DNS của Google.
   - Gõ `ping google.com` để kiểm tra kết nối đến Google.

3. **Theo dõi đường đi của gói tin:**
   - Gõ `tracert google.com` và ghi lại các hop.

4. **Kiểm tra các kết nối mạng đang hoạt động:**
   - Gõ `netstat -an` và phân tích các kết nối TCP/UDP hiện tại.

5. **Truy vấn DNS với `nslookup`:**
   - Gõ `nslookup microsoft.com` để tìm địa chỉ IP của Microsoft.

6. **Thêm và xóa tuyến đường:**
   - Thêm tuyến đường mới: `route add 192.168.2.0 mask 255.255.255.0 192.168.1.1`
   - Xóa tuyến đường: `route delete 192.168.2.0`

7. **Kiểm tra bảng ARP:**
   - Gõ `arp -a` để xem bảng ARP hiện tại.

8. **Kiểm tra cổng với Telnet:**
   - Gõ `telnet google.com 80` để kiểm tra kết nối đến cổng HTTP của Google.

### 3.3. Tài liệu tham khảo

- **Sách:**
  - "Networking All-in-One For Dummies" của Doug Lowe
  
- **Trang web:**
  - [Cisco Networking Academy](https://www.netacad.com/)
  - [ChatGPT](https://chatgpt.com/)

