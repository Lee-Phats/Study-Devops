## Giới thiệu

Repository "what-happens-when" của Alex là một tài nguyên tuyệt vời để hiểu rõ hơn về quá trình diễn ra khi bạn nhập một URL vào trình duyệt và nhấn Enter. Nó giải thích chi tiết từng bước từ lúc bạn nhập URL cho đến khi trang web hiển thị hoàn chỉnh trên màn hình của bạn.

## Các Bước Chính trong Quy trình truy cập website

1. **DNS Lookup (Truy vấn DNS)**
   - **Mục đích:** Chuyển đổi tên miền (ví dụ: `www.example.com`) thành địa chỉ IP (ví dụ: `93.184.216.34`).
   - **Quy trình:**
     - Trình duyệt kiểm tra cache DNS nội bộ.
     - Nếu không tìm thấy, yêu cầu gửi đến DNS resolver (thường do ISP cung cấp).
     - DNS resolver truy vấn các DNS server (root, TLD, authoritative) để lấy địa chỉ IP.

2. **TCP Three-Way Handshake**
   - **Mục đích:** Thiết lập kết nối TCP giữa trình duyệt và server.
   - **Quy trình:**
     1. **SYN:** Trình duyệt gửi gói tin SYN đến server.
     2. **SYN-ACK:** Server phản hồi bằng gói tin SYN-ACK.
     3. **ACK:** Trình duyệt gửi gói tin ACK để hoàn tất kết nối.
3. **TLS Handshake (nếu sử dụng HTTPS)**
   - **Mục đích:** Thiết lập một kết nối an toàn giữa trình duyệt và server.
   - **Quy trình:**
     - Trình duyệt và server trao đổi các thông tin cần thiết để mã hóa dữ liệu.
     - Xác thực server bằng chứng chỉ SSL/TLS.
     - Tạo khóa mã hóa để bảo mật dữ liệu truyền tải.

4. **Gửi HTTP Request**
   - **Mục đích:** Trình duyệt yêu cầu tài nguyên từ server.
   - **Quy trình:**
     - Trình duyệt gửi yêu cầu HTTP (ví dụ: GET /index.html) đến server.

5. **Xử lý Yêu cầu trên Server**
   - **Mục đích:** Server xử lý yêu cầu và chuẩn bị phản hồi.
   - **Quy trình:**
     - Server nhận yêu cầu, xử lý nó (có thể bao gồm truy vấn cơ sở dữ liệu, xử lý mã nguồn phía server).
     - Server tạo phản hồi HTTP chứa tài nguyên yêu cầu.

6. **Gửi HTTP Response**
   - **Mục đích:** Server gửi phản hồi HTTP trở lại trình duyệt.
   - **Quy trình:**
     - Server gửi phản hồi HTTP (ví dụ: HTTP/1.1 200 OK) kèm theo nội dung trang web.

7. **Trình duyệt Nhận và Xử lý Phản hồi**
   - **Mục đích:** Trình duyệt nhận dữ liệu và hiển thị trang web.
   - **Quy trình:**
     - Trình duyệt nhận phản hồi HTTP, phân tích nội dung.
     - Nếu có các tài nguyên bổ sung (CSS, JS, hình ảnh), trình duyệt gửi các yêu cầu HTTP bổ sung để tải chúng.

8. **Rút Kết nối**
   - **Mục đích:** Hoàn tất quá trình truyền tải dữ liệu.
   - **Quy trình:**
     - Trình duyệt và server rút kết nối TCP sau khi truyền tải dữ liệu hoàn tất.

## Cách Áp Dụng Vào Học Tập của Bạn

### 5.1. Phân tích Quy trình truy cập website

**Bài tập 1: Sử dụng lệnh `ping` và `tracert`**

- **Mục tiêu:** Hiểu cách xác định địa chỉ IP và đường đi của gói tin.
- **Hướng dẫn:**
  1. Mở Command Prompt.
  2. Thực hiện lệnh:
     ```bash
     ping www.google.com
     tracert www.google.com
     ```
  3. Phân tích kết quả để hiểu rõ hơn về quá trình truyền tải dữ liệu qua mạng.

**Bài tập 2: Sử dụng Công cụ Developer Tools**

- **Mục tiêu:** Hiểu cách phân tích các yêu cầu HTTP và phản hồi từ server.
- **Hướng dẫn:**
  1. Mở trình duyệt (Chrome, Firefox).
  2. Mở Developer Tools (nhấn `F12`).
  3. Truy cập một website và chuyển đến tab **Network**.
  4. Quan sát các yêu cầu HTTP, phân loại loại tài nguyên, thời gian tải, v.v.

Link kham khảo:
https://github.com/alex/what-happens-when?tab=readme-ov-file
