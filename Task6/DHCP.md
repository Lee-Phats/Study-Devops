# **DHCP: Giao Thức Cấu Hình Động Địa Chỉ IP**  

## **1. DHCP là gì?**  
DHCP (Dynamic Host Configuration Protocol) là một giao thức mạng giúp tự động cấp phát địa chỉ IP và các thông tin cấu hình mạng khác cho các thiết bị trong hệ thống. Thay vì phải gán địa chỉ IP bằng tay (tĩnh), DHCP giúp quản lý IP động, giảm công việc thủ công và tránh xung đột địa chỉ IP.

## **2. Đặc điểm DHCP**  
| **Danh mục**       | **Nội dung** |
|--------------------|-------------|
| **Mô hình Client/Server** | - DHCP Server quản lý và cấp phát địa chỉ IP.  <br> - DHCP Client nhận địa chỉ IP và thông tin cấu hình mạng từ Server. |
| **Giao thức sử dụng** | - DHCP Server lắng nghe trên cổng 67. <br> - DHCP Client nhận phản hồi từ Server trên cổng 68. |
| **Chức năng chính** | - Cấp phát địa chỉ IP tự động. <br> - Quản lý tập trung địa chỉ IP. <br> - Tái sử dụng địa chỉ IP. <br> - Giảm thiểu xung đột IP. <br> - Hỗ trợ cấu hình mạng linh hoạt. |
| **Ưu điểm** | ✅ Giảm tải công việc quản trị mạng. <br> ✅ Hỗ trợ cấp phát địa chỉ IP động. <br> ✅ Đơn giản hóa cấu hình mạng. <br> ✅ Hỗ trợ mở rộng hệ thống mạng dễ dàng. |

Quá trình cấp phát địa chỉ IP (Lease Allocation)

![alt text](image-1.png)

Client gửi bản tin DHCP DISCOVER (Broadcast).

DHCP Server gửi bản tin DHCP OFFER.

Client phản hồi bằng DHCP REQUEST để chấp nhận.

DHCP Server gửi DHCP ACK, hoàn tất cấp phát IP.

## **3. Các loại bản tin DHCP**  

| **Loại Bản Tin**  | **Chức Năng** |
|-------------------|--------------|
| **1.DHCP DISCOVER** | Client gửi yêu cầu tìm DHCP Server. |
| **2.DHCP OFFER**    | Server phản hồi với một địa chỉ IP có sẵn. |
| **3.DHCP REQUEST**  | Client xác nhận muốn sử dụng địa chỉ IP được cung cấp. |
| **4.DHCP ACK**      | Server xác nhận và cấp phát địa chỉ IP chính thức. |
| **5.DHCP NAK**      | Server từ chối cấp địa chỉ IP. |
| **6.DHCP DECLINE**  | Client từ chối địa chỉ IP do bị trùng lặp. |
| **7.DHCP RELEASE**  | Client trả lại địa chỉ IP cho Server. |
| **8.DHCP INFORM**   | Client yêu cầu thông tin cấu hình khác ngoài địa chỉ IP. |

5. **DHCP NAK (Thông Báo Từ Chối Cấp IP)**
- Từ chối cấp phát IP, buộc Client phải xin lại IP mới.
 Ví dụ:
Máy tính A nhận IP 192.168.1.100 với Lease Time là 24 giờ. Sau 24 giờ, nếu không gia hạn được và cố sử dụng IP này, DHCP Server có thể gửi DHCP NAK, buộc A phải lấy IP mới.

6. **DHCP DECLINE (Từ Chối Địa Chỉ IP Do trùng lặp)**
- Từ chối sử dụng IP và yêu cầu IP khác.
 Ví dụ:
Máy tính B được cấp IP 192.168.1.101. Khi kiểm tra, B phát hiện rằng địa chỉ này đã được sử dụng bởi một thiết bị khác. B sẽ gửi DHCP Decline để yêu cầu IP khác.

7. **DHCP RELEASE (Trả lại Địa Chỉ IP)**
- Giải phóng IP để cấp phát lại.
 Ví dụ:
Máy tính C đang sử dụng IP 192.168.1.102. Khi tắt máy hoặc rời khỏi mạng, nó gửi DHCP Release để giải phóng IP, giúp các thiết bị khác có thể sử dụng IP này.

8. **DHCP INFORM (Yêu Cầu Thông Tin Mạng)**
- Cung cấp thông số mạng như DNS, Gateway.    
 Ví dụ:
Máy tính D có địa chỉ IP tĩnh là 192.168.1.200 nhưng không biết DNS Server của mạng. D gửi DHCP Inform đến máy chủ DHCP, và máy chủ phản hồi với địa chỉ DNS 8.8.8.8.

## **4. Tiến trình hoạt động của DHCP**  
Quá trình cấp phát địa chỉ IP

![alt text](image-2.png)
Quá trình xử lý quan trọng nhất trong DHCP là quá trình Lease Allocation, được sử dụng bởi client để yêu cầu một hợp đồng thuê IP. Client gửi broadcast một request tới DHCP server. Mỗi DHCP server sẵn sàng cung cấp cho client một hợp đồng thuê và gửi lại cho nó một bản tin Offer. Client chọn bản hợp đồng mà nó nhận được và gửi lại tới tất cả các server về sự lựa chọn của nó. Server được chọn sẽ gửi lại cho client thông tin và hợp đồng thuê. Các bước được thực hiện như sau:

Bước 1: Client tạo bản tin DHCPDISCOVER

Ban đầu, Client chưa có địa chỉ IP và nó có thể biết hoặc không biết vị trí của DHCP server trong mạng. Để tìm DHCP server, nó tạo bản tin DHCP DISCOVER, bao gồm các thông tin như sau:

Điền địa chỉ MAC vào trường CHAddr để xác nhận nó.

Sinh ra một số định danh transaction ngẫu nhiên và điền vào trường XID.

Client có thể yêu cầu một địa chỉ IP xác định sử dụng trường tùy chọn Request IP Address trong phần DHCP option.

Bước 2: Client gửi bản tin DHCP DISCOVER

Client gửi broadcast bản tin DHCP DISCOVER trên mạng nội bộ. (Broadcast lớp 2 và lớp 3)

Bước 3: Server nhận và xử lý bản tin DHCP DISCOVER

Mỗi DHCP server trên mạng LAN nhận được bản tin DHCP DISCOVER của client và kiểm tra nó. Server tìm kiếm phần địa chỉ MAC của client trong database và chọn cho nó một IP phù hợp đồng thời các thông số liên quan. Nếu client yêu cầu một IP xác định thì server sẽ xử lý yêu cầu nó. Server có thể quyết định việc nó dùng địa chỉ IP chỉ định kia là hợp lệ hay không để gửi reply về.

Bước 4: Server tạo bản tin DHCP OFFER

Mỗi server được chọn trả lời lại cho client tạo bản tin DHCP OFFER bao gồm các thông tin sau:

Địa chỉ IP cấp phát cho client trong trường YIAddr. Nếu trước đó, client đã "thuê" một địa chỉ IP và thời hạn dùng của nó vẫn còn thì sẽ sử dụng địa chỉ cũ đó cho client. Nếu không thì nó sẽ chọn một IP có sẵn bất kì cho client.

Thời hạn được sử dụng IP.

Các thông số cấu hình khác mà client yêu cầu.

Định danh của DHCP server trong phần tùy chọn DHCP Server Identifier option.

Cùng số XID được sử dụng trong bản tin DHCP DISCOVER.

Bước 5: Server dò tìm xem địa chỉ IP mà cấp phát cho client đã được một thiết bị nào khác sử dụng hay chưa.

Trước khi gửi bản tin DHCP OFFER cho client, server nên kiểm tra lại xem địa chỉ IP cấp cho client đã được sử dụng hay chưa bằng cách gửi bản tin ICMP.

Nếu IP đó đã được sử dụng thì nó sẽ chọn lại địa chỉ IP khác cho client.

Nếu IP chưa được sử dụng, server sẽ cấp phát IP cho client.

Bước 6: Các Server gửi bản tin DHCPOFFER

Mỗi server gửi bản tin DHCP OFFER của nó. Chúng có thể được gửi unicast hoặc broadcast tùy thuộc vào client (Nếu client cho phép nhận bản tin unicast khi chưa được cấu hình IP thì nó sẽ set bit B trong bản tin DHCP DISCOVER là 0, còn nếu không thì nó sẽ set bit B là 1 để biểu thị nhận bản tin broadcast)

Bước 7: Client nhận và xử lý bản tin DHCPOFFER

Client nhận bản tin DHCP OFFER và nó sẽ chọn lựa server nào mà nó nhận được bản tin DHCP OFFER đầu tiên. Nếu không nhận được bản tin DHCP OFFER nào sau một thời gian, client sẽ tạo lại bản tin DHCP DISCOVER và gửi lại từ đầu.

Bước 8: Client tạo bản tin DHCP REQUEST

Client tạo bản tin DHCP REQUEST cho server mà nó chọn nhận bản tin OFFER. Bản tin này sẽ gồm 2 mục đích chính là nói với server mà cho phép cấp phát IP cho nó là nó đồng ý dùng IP đó trong trường hợp IP đó vẫn còn dành cho nó và cũng thông báo với các DHCP server còn lại là bản tin OFFER của chúng không được nhận.

Trong bản tin này bao gồm các thông tin:

Định danh của server được chọn trong phần SEerver Identifier option.

Địa chỉ IP mà DHCP server cho phép client trong bản tin DHCP OFFER, client để vào phần Request IP Address DHCP option.

Và một số thông tin cấu hình mà nó muốn trong phần Parameter Request List option.

Bước 9: Client gửi bản tin DHCP REQUEST

Client gửi broadcast bản tin DHCP REQUEST. Sau đó chờ reply từ server.

Bước 10: Các server nhận và xử lý bản tin DHCP REQUEST

Mỗi server nhận được bản tin REQUEST của client. Các server không được chọn sẽ bỏ qua bản tin này.

Bước 11: Server gửi bản tin DHCPACK hoặc DHCPNAK.

Server được chọn sẽ kiểm tra xem địa chỉ IP nó OFFER cho còn sử dụng được hay không. Nếu không còn, nó sẽ gửi lại DHCPNAK (negative acknowledgment). Thông thường, server sẽ vẫn dành địa chỉ IP đó cho client, server sẽ gửi lại bản tin DHCPACK để xác nhận và cấp các thông số mà client yêu cầu.

Bước 12: Client nhận bản tin DHCPACK hoặc DHCPACK

Client sẽ nhận lại bản tin DHCPACK hoặc DHCPNAK từ server.

Nếu là DHCPNAK, client sẽ bắt đầu gửi lại DISCOVER từ bước 1.

Nếu là DHCPACK, client đọc địa chỉ IP trong trường YIAddr, ghi lại các thông số khác trong phần DHCP option.

Nếu không nhận được bản tin nào, client sẽ gửi lại DHCP REQUEST một hoặc vài lần nữa. Sau một khoảng thời gian vẫn không nhận được gì, nó sẽ bắt đầu lại từ Bước 1.

Bước 13: Client kiểm tra xem IP được sử dụng hay chưa.

Client sẽ kiểm tra lần cuối trước khi xác định chắc chắn IP chưa được thiết bị khác sử dụng trước khi sử dụng nó. Bước này sẽ được thực hiện bởi giao thức ARP trên mạng LAN.

Nếu có bất kì thiết bị nào phản hồi lại ARP, client sẽ gửi bản tin DHCP DECLINE lại server để thông báo với server rằng IP đó đã được máy khác sử dụng. Và client trở lại Bước 1.

Nếu không có phản hồi, client sẽ sử dụng IP. Kết thúc quá trình Lease Allocation.

Quá trình xin cấp phát lại địa chỉ IP


![alt text](image-3.png)
Có 2 trường hợp mà client thực hiện quá trình Reallocation hơn là Allocation:

Power on with Existing Lease.
Reboot
Nếu client khởi động lại và nó đã có sẵn một hợp đồng thuê, nó không cần phải thực hiện lại quá trình full lease allocation, thay vào đó, nó có thể sử dụng quá trình ngắn hơn là Reallocation. Client broadcast một request để tìm server hiện tại đang quản lý thông tin về hợp đồng mà nó đang thuê. Server đó gửi lại để xác nhận xem hợp đồng của client còn hiệu lực hay không.

Quá trình Renew và Rebind
Do thời hạn của mỗi client khi thuê IP thường đều là có hạn (trừ trường hợp Automatication Allocation) nên cần có quá trình gia hạn (renewal) lại với DHCP server quả lý và nếu quá trình renewal không thành công thì sẽ rebind lại (gửi request) tới bất kì DHCP server khác đang hoạt động để gia hạn hợp đồng.

![alt text](image-4.png)

## **5. Cơ chế phân bổ địa chỉ của DHCP Server**
DHCP có 3 cơ chế cấp phát địa chỉ IP:

1. Manual Allocation (Cấp phát thủ công)
    Người quản trị gán địa chỉ IP cố định cho từng thiết bị cụ thể.
    Thường dùng cho Server, Router, Printer, Camera IP.

2. Automatic Allocation (Cấp phát tự động)
    DHCP Server tự động gán một địa chỉ IP từ danh sách có sẵn.
    Địa chỉ được cấp sẽ cố định cho Client đó.

3. Dynamic Allocation (Cấp phát động)
    DHCP Server cấp địa chỉ IP theo yêu cầu, nhưng có thời hạn thuê.
    Khi hết hạn, địa chỉ IP có thể được tái sử dụng.

Đây là cơ chế phổ biến nhất hiện nay.

## **6. Vòng đời và thời gian "thuê"  IP của Client**
Quy trình cấp phát và quản lý địa chỉ IP gồm 5 giai đoạn:

1. Allocation (Cấp phát lần đầu)
Một client bắt đầu khi chưa từng thuê IP và do đó chưa có địa chỉ được cấp từ DHCP server. Nó yêu cầu thuê thông qua một quá trình phân bổ Allocation.

2. Reallocation (Cấp phát lại khi khởi động lại)
Nếu client đã có sẵn địa chỉ IP lần thuê hiện tại, và sau đó khi nó khởi động lại sau khi tắt, nó sẽ liên lạc với DHCP server để xác nhận việc thuê và dùng lại các thông số vận hành. Điều này được gọi là Reallocation, nó tương tự như Allocation nhưng ngắn hơn.

3. Normal Operation (Hoạt động bình thường)
Khi một hợp đồng cho thuê đang hoạt động, client được gán vào một địa chỉ mà DHCP server cấp phát, cho thuê.

4. Renewal (Gia hạn địa chỉ IP sau 50% thời gian thuê)
Sau một phần thời gian nhất định của thời gian cho thuê, client sẽ cố gắng liên lạc với máy chủ cho thuê ban đầu, gia hạn thêm hợp đồng để nó có thể tiếp tục sử dụng IP đó sau khi thời gian cho thuê kết thúc (thường sau nửa thời gian được phép sử dụng IP, client sẽ liên lạc với DHCP server để gia hạn thêm hợp đồng)

5. Rebind (Yêu cầu gia hạn từ bất kỳ DHCP Server nào sau 87.5% thời gian thuê)
Nếu việc renewal không thành (giả sử máy server bị tắt), sau đó client sẽ cố gắng kết nối lại với bất kì máy chủ DHCP nào đang hoạt động, cố gắng mở rộng thời gian cho thuê hiện tại.

6. Release
client có thể quyết định ở bất kì thời điểm nào đó nó không còn muốn sử dụng địa chỉ IP được cấp từ DHCP nữa, và có thể chấm dứt hợp đồng cho thuê, giải phóng địa chỉ IP.

## **7. Cấu Trúc Gói Tin DHCP**  

Gói tin DHCP sử dụng giao thức **UDP** trên các cổng:  
- **Cổng 67**: Máy chủ DHCP lắng nghe yêu cầu từ client.  
- **Cổng 68**: Máy khách nhận phản hồi từ máy chủ DHCP.  

![alt text](image.png)

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

## **8. Link Kham khảo**  
https://github.com/hocchudong/thuctap012017/blob/master/TamNT/DHCP/T%C3%ACm%20hi%E1%BB%83u%20giao%20th%E1%BB%A9c%20DHCP.md#1.4

