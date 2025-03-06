Cài đặt:
https://mobaxterm.mobatek.net/download.html

![alt text](image-7.png)

Tạo một session SSH bất kỳ
![alt text](image-8.png)

![alt text](image-9.png)

![alt text](image-10.png)

Sử dụng scp:
Thông thường khi tạo session thì sẽ mặc định ở chế độ SFTP protocol, mặc dù an toàn hơn nhưng tốc độ tải xuống hoặc upload sẽ chậm hơn bình thường.
![alt text](image-11.png)

Mình sẽ chuyển sang chế độ SCP để tăng tốc độ tải và úp file.
![alt text](image-12.png)

![alt text](image-13.png)

Bây giờ ta login vào session và sử dụng tính năng SCP
![alt text](image-14.png)

Thường thì màn hình của SCP sẽ nằm bên trái, ở dưới hiển thị thư mục và các file, ở trên sẽ là các nút để thực hiện chức năng
![alt text](image-15.png)

1: Nút này dùng để lui về một thư mục trước đó

2: Nút này dùng để download file

3: Nút này dùng để úp file

4: Nút này dùng để refresh vì đôi lúc bạn tạo file ở terminal nhưng trong SCP chưa có file

5: Nút này dùng để tạo thư mục

6: Nút này dùng tạo file

7: Nút này dùng để xóa file

8: Nút này dùng hiển thị các thư mục ẩn, ví dụ như .ssh

![alt text](image-16.png)
Nút follow terminal folder sẽ hiển thị thư mục của SCP theo chỗ đứng SSH - User mà bạn đăng nhập

Sử dụng công cụ theo dõi hệ thống
Ta sẽ chọn vào Remote Monitoring để xem tổng % CPU, %RAM, tốc độ úp file, tốc độ tải file, và dung lượng ổ đĩa đang sử dụng.
![alt text](image-17.png)