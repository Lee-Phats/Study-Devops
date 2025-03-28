# **DHCP: Giao Thức Cấu Hình Động Địa Chỉ IP - Chi Tiết, Đầy Đủ & Dễ Hiểu**  

## **1. DHCP là gì?**  
DHCP (Dynamic Host Configuration Protocol) là một giao thức mạng giúp tự động cấp phát địa chỉ IP và các thông tin cấu hình mạng khác cho các thiết bị trong hệ thống. Thay vì phải gán địa chỉ IP bằng tay (tĩnh), DHCP giúp quản lý IP động, giảm công việc thủ công và tránh xung đột địa chỉ IP.

---

## **2. Các loại bản tin DHCP**  

1. **Discovery (Tìm kiếm)**  
   - Khi một thiết bị (client) muốn tham gia mạng, nó sẽ gửi gói tin **DHCP Discover** để tìm máy chủ DHCP.
  
2. **Offer (Đề xuất IP)**  
   - Máy chủ DHCP nhận được gói Discover, sau đó phản hồi bằng gói **DHCP Offer**, trong đó có một địa chỉ IP khả dụng.

3. **Request (Yêu cầu IP)**  
   - Client nhận được Offer và gửi lại **DHCP Request** để yêu cầu sử dụng địa chỉ IP đó.

4. **Acknowledge (Xác nhận)**  
   - Máy chủ DHCP xác nhận yêu cầu bằng gói **DHCP Acknowledgement (ACK)** và thiết bị được cấp phát IP.

5. **DHCP NAK ()**
    - Từ chối cấp phát IP, buộc Client phải xin lại IP mới.

6. **DHCP DECLINE ()**
    - Từ chối sử dụng IP và yêu cầu IP khác.

7. **DHCP RELEASE ()**
    - Giải phóng IP để cấp phát lại.

8. **DHCP INFORM ()**
    - Cung cấp thông số mạng như DNS, Gateway.    

⏳ **Lưu ý:** Địa chỉ IP cấp phát có thời gian thuê nhất định (**DHCP Lease Time**). Khi gần hết hạn, thiết bị phải gửi yêu cầu gia hạn.

## **3. Cấu Trúc Gói Tin DHCP**  

Gói tin DHCP sử dụng giao thức **UDP** trên các cổng:  
- **Cổng 67**: Máy chủ DHCP lắng nghe yêu cầu từ client.  
- **Cổng 68**: Máy khách nhận phản hồi từ máy chủ DHCP.  

### **Cấu trúc gói tin DHCP gồm các phần chính:**  
| Trường | Kích thước (Bytes) | Mô tả |
|--------|--------------------|------|
| **Op Code** | 1 | Loại gói tin (1 = request, 2 = reply) |
| **Hardware Type** | 1 | Loại phần cứng (Ethernet = 1) |
| **Hardware Address Length** | 1 | Độ dài địa chỉ MAC |
| **Hops** | 1 | Số lần chuyển tiếp gói tin |
| **Transaction ID** | 4 | ID để nhận diện yêu cầu |
| **Seconds Elapsed** | 2 | Thời gian trôi qua từ lúc gửi Discover |
| **Flags** | 2 | Bit Broadcast |
| **Client IP Address** | 4 | Địa chỉ IP của Client (nếu có) |
| **Your IP Address** | 4 | Địa chỉ IP DHCP cấp phát |
| **Next Server IP Address** | 4 | Địa chỉ IP của máy chủ kế tiếp |
| **Relay Agent IP Address** | 4 | Địa chỉ IP của bộ chuyển tiếp DHCP |
| **Client MAC Address** | 16 | Địa chỉ MAC của thiết bị |
| **Client Hostname** | 64 | Tên thiết bị |
| **Boot File Name** | 128 | Tên file khởi động (nếu có) |
| **Options** | Tùy biến | Chứa các thông tin mở rộng (DNS, Gateway...) |

## **4. Các Thông Số Quan Trọng Trong DHCP**  

1. **DHCP Lease Time**: Thời gian mà IP được cấp phát. Khi gần hết hạn, thiết bị phải yêu cầu gia hạn.  
2. **Default Gateway**: Địa chỉ của router giúp thiết bị kết nối ra ngoài mạng LAN.  
3. **DNS Server**: Địa chỉ máy chủ DNS giúp phân giải tên miền.  
4. **Subnet Mask**: Xác định phần mạng và phần host của địa chỉ IP.  
5. **Option 66, 67**: Dùng để chỉ định máy chủ TFTP cho các thiết bị cần khởi động từ mạng (PXE Boot).  
6. **Option 82**: Dùng trong các hệ thống mạng lớn, giúp định danh thiết bị yêu cầu DHCP.  

## **5. So Sánh DHCPv4 và DHCPv6**  

| Đặc điểm | DHCPv4 | DHCPv6 |
|----------|--------|--------|
| Sử dụng trên | IPv4 | IPv6 |
| Cách cấp phát IP | Địa chỉ IP động hoặc tĩnh | Địa chỉ Link-Local, SLAAC, hoặc DHCPv6 |
| Loại địa chỉ IP | IPv4 (32-bit) | IPv6 (128-bit) |
| Cách hoạt động | DORA (4 bước) | SARR (Solicit, Advertise, Request, Reply) |
| Hỗ trợ NAT | Có | Không cần NAT (IPv6 có đủ địa chỉ) |

💡 **Lưu ý**: IPv6 thường sử dụng **SLAAC** (Stateless Address Autoconfiguration) thay vì DHCP.

## **6. Bảo Mật DHCP: Các Nguy Cơ & Biện Pháp Bảo Vệ**  

### 🔴 **Nguy cơ tấn công DHCP**  
❌ **DHCP Spoofing**: Kẻ tấn công giả mạo máy chủ DHCP để cấp phát IP sai lệch.  
❌ **Rogue DHCP Server**: Máy chủ DHCP giả mạo trong mạng, gây gián đoạn dịch vụ.  
❌ **DHCP Starvation**: Tấn công làm cạn kiệt địa chỉ IP bằng cách gửi nhiều yêu cầu giả.  

### 🛡 **Các biện pháp bảo mật**  
✅ **DHCP Snooping**: Chỉ cho phép DHCP Server hợp lệ hoạt động trong mạng.  
✅ **Port Security**: Giới hạn số địa chỉ MAC trên cổng switch.  
✅ **IP Source Guard**: Chỉ cho phép thiết bị sử dụng địa chỉ IP được cấp phát hợp lệ.  

## **7. Cách Cấu Hình DHCP Trên Các Thiết Bị**  

### **1️⃣ Trên Windows Server**  
Bật DHCP Role trên Windows Server:  
```powershell
Install-WindowsFeature -Name DHCP -IncludeManagementTools
```
Cấu hình một Scope DHCP:  
```powershell
Add-DhcpServerv4Scope -Name "MyScope" -StartRange 192.168.1.100 -EndRange 192.168.1.200 -SubnetMask 255.255.255.0 -State Active
```

### **2️⃣ Trên Cisco Router**  
```cisco
Router(config)# ip dhcp excluded-address 192.168.1.1 192.168.1.10
Router(config)# ip dhcp pool MyPool
Router(dhcp-config)# network 192.168.1.0 255.255.255.0
Router(dhcp-config)# default-router 192.168.1.1
Router(dhcp-config)# dns-server 8.8.8.8
```

### **3️⃣ Trên Linux (Ubuntu/Debian)**  
Cài đặt DHCP Server:  
```bash
sudo apt update && sudo apt install isc-dhcp-server
```
Cấu hình file `/etc/dhcp/dhcpd.conf`:  
```bash
subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.100 192.168.1.200;
    option routers 192.168.1.1;
    option domain-name-servers 8.8.8.8;
}
```
Khởi động dịch vụ:  
```bash
sudo systemctl restart isc-dhcp-server
```

## **8. Kết Luận**  

✔ DHCP giúp quản lý địa chỉ IP tự động, tiết kiệm công sức và giảm lỗi.  
✔ Có thể sử dụng DHCP trên nhiều hệ thống khác nhau (Windows, Cisco, Linux...).  
✔ Cần có các biện pháp bảo mật như DHCP Snooping để tránh bị tấn công.  
✔ Với IPv6, DHCPv6 có thể kết hợp với SLAAC để cấp phát địa chỉ hiệu quả hơn.  
