# So sánh mô hình OSI và mô hình TCP/IP

## Mục lục

1. [Giới thiệu về hai mô hình](#1-giới-thiệu-về-hai-mô-hình)
2. [So sánh chi tiết](#2-so-sánh-chi-tiết)
3. [Mapping giữa các tầng](#3-mapping-giữa-các-tầng)
4. [Ưu và nhược điểm](#4-ưu-và-nhược-điểm)
5. [Tài liệu tham khảo](#5-tài-liệu-tham-khảo)

---

## 1. Giới thiệu về hai mô hình

- **Mô hình OSI (Open Systems Interconnection)**: Được phát triển bởi Tổ chức Tiêu chuẩn hóa Quốc tế (ISO) vào những năm 1980, mô hình OSI có **7 tầng** nhằm mục đích chuẩn hóa giao tiếp mạng giữa các hệ thống khác nhau.

- **Mô hình TCP/IP (Transmission Control Protocol/Internet Protocol)**: Được phát triển bởi Bộ Quốc phòng Hoa Kỳ vào cuối những năm 1970, mô hình TCP/IP có **4 tầng** và là nền tảng của Internet hiện đại.

## 2. So sánh chi tiết

| **Đặc điểm**           | **Mô hình OSI**                                            | **Mô hình TCP/IP**                                          |
|------------------------|------------------------------------------------------------|-------------------------------------------------------------|
| **Số tầng**            | 7 tầng                                                      | 4 tầng                                                       |
| **Tên các tầng**       | 1. Vật lý (Physical) <br>2. Liên kết dữ liệu (Data Link) <br>3. Mạng (Network) <br>4. Vận chuyển (Transport) <br>5. Phiên (Session) <br>6. Trình diễn (Presentation) <br>7. Ứng dụng (Application) | 1. Vật lý (Link) <br>2. Internet (Internet) <br>3. Vận chuyển (Transport) <br>4. Ứng dụng (Application) |
| **Phạm vi ứng dụng**   | Mô hình lý thuyết, giáo dục                                | Thực tiễn, được sử dụng rộng rãi trên Internet               |
| **Phát triển**        | Độc lập, không dựa trên các chuẩn giao tiếp thực tế      | Dựa trên các giao thức thực tế như TCP, IP, UDP, HTTP...     |
| **Tính linh hoạt**    | Rất chi tiết, giúp phân tích sâu các chức năng mạng      | Tập trung vào chức năng chính, dễ triển khai và ứng dụng    |
| **Sự tương thích**    | Ít được sử dụng trong thực tế hiện nay                    | Là nền tảng của Internet, tương thích rộng rãi               |

## 3. Mapping giữa các tầng

| **Mô hình OSI**                | **Mô hình TCP/IP**         |
|--------------------------------|----------------------------|
| 7. Ứng dụng (Application)      | 4. Ứng dụng (Application)  |
| 6. Trình diễn (Presentation)    |                            |
| 5. Phiên (Session)             |                            |
| 4. Vận chuyển (Transport)      | 3. Vận chuyển (Transport)  |
| 3. Mạng (Network)              | 2. Internet (Internet)     |
| 2. Liên kết dữ liệu (Data Link)| 1. Vật lý (Link)           |
| 1. Vật lý (Physical)           |                            |

**Lưu ý:** Các tầng **Presentation** và **Session** của mô hình OSI thường được tích hợp vào tầng **Ứng dụng** của mô hình TCP/IP.

## 4. Ưu và nhược điểm

- **Mô hình OSI:**
  - *Ưu điểm:* Chi tiết, phân tách rõ ràng các chức năng mạng, hữu ích trong giáo dục và phân tích.
  - *Nhược điểm:* Phức tạp, ít được sử dụng trong thực tế.

- **Mô hình TCP/IP:**
  - *Ưu điểm:* Đơn giản, linh hoạt, được áp dụng rộng rãi trong thực tế.
  - *Nhược điểm:* Ít chi tiết hơn, không phù hợp cho việc phân tích sâu các chức năng mạng.

## 5. Tài liệu tham khảo

- **Trang web:**
  - [Cisco Networking Academy](https://www.netacad.com/)
  - [ChatGPT](https://chatgpt.com/)
- **Sách:**
 - "TCP/IP Illustrated" của W. Richard Stevens
