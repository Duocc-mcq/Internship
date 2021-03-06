## Các cách để cài đặt 1 application trong Ubuntu ( Ví dụ Apache )

### Cài đặt tự động từ Repository

Sử dụng lệnh `sudo apt-get install apache2` trên Ubuntu, `yum install apache2` trên CentOS để cài đặt apache 

#### Ưu nhược điểm

- Ưu điểm: Việc cài đặt 1 chương trình rất dễ dàng, chỉ cần phải biết tên của chương trình đó, phù hợp với người mới bắt đầu.

- Nhược điểm: Khả năng tuỳ biến, tích hợp bị hạn chế, có những chương trình bị thiếu module mà việc cài tự động không có.

### Cài đặt bằng `make` 

- Download source từ trang chủ của application, ở đây là apache HTTP server 2.4.35 (http://httpd.apache.org/download.cgi)

<img src="img/02.jpg">

- Giải nén file source vừa download về

```
gunzip httpd-2.4.35.tar.gz
tar xvf httpd-2.4.35.tar
```

- Đọc file INSTALL để xem hướng dẫn cài đặt

- Truy cập vào thư mục vừa giải nén được và thực hiện lệnh:

```
./configure --prefix=PREFIX
```
	
	- PREFIX ở đây thay bằng đường dẫn mà bạn muốn cài đặt apache tại đó

Lệnh `./configure` này là 1 shell script để check xem hệ thống có đáp ứng đủ yêu cầu để cài đặt không, nếu thiếu các gói phụ thuộc thì phải tìm và cài đặt nó. Ở đây để cài đặt apache thì phải cần thêm các gói APR, APR-Util để cài đặt.
<img src="img/01.jpg">

<img src="img/04.jpg">

<img src="img/03.jpg">
- Sau khi configure thành công không có lỗi gì, thực hiện tiếp lệnh sau để tiến hành cài đặt:

``` 
make
make install
``` 
<img src="img/05.jpg">

	- Sử dụng lệnh `make`
	
<img src="img/06.jpg">

	- Dùng lệnh `make` thành công không gặp lỗi
	
<img src="img/07.jpg">

	- Dùng lệnh `make install` để bắt đầu quá trình cài đặt
	
<img src="img/08.jpg">

	- Cài đặt thành công
	
<img src="img/09.jpg">

#### Ưu nhược điểm

- Ưu điểm: Khả năng tuỳ biến cao, do build từ source nên có đầy đủ các module cần thiết, bảo mật cao

- Nhược điểm: Khó cài đặt đối với người mới sử dụng, phải tự tìm và cài đặt những gói phụ thuộc cần thiết cho việc cài đặt chương trình.

### Cài đặt từ file .deb .rpm

- Nếu đã có sẵn file .deb trong máy, có thể cài đặt ứng dụng bằng lệnh:

```
sudo apt install ./file.deb
```

Sau khi thực hiện lệnh này thì các gói phụ thuộc cần để cài ứng dụng sẽ được tự động download về.

- Đối với CentOS, nếu có sẵn file .rpm trong máy, có thể cài đặt bằng lệnh:

```
yum localinstall file.rpm 
```

Lệnh này sẽ cài đặt file.rpm đã có sẵn trên máy và cài đặt các gói phụ thuộc nếu cần.