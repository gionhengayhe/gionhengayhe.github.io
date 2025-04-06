+++
title = "Tạo một S3 Bucket"
date = 2020
weight = 1
chapter = false
pre = "<b>3.1. </b>"
+++

## Tải dữ liệu

1. Nhấp vào đây: [Post data](https://jsonplaceholder.typicode.com/posts)
2. Lưu với **Ctrl + S**
3. Nhấp vào đây: [Comment data](https://jsonplaceholder.typicode.com/comments)
4. Lưu với **Ctrl + S**
5. Trên tệp **.json** vừa tải xuống, bạn có thể thay đổi mã để kiểm tra trường hợp sử dụng Làm sạch dữ liệu

{{% notice tip %}}
Bạn có thể sửa đổi dữ liệu cho mục đích kiểm tra: xóa một số bản ghi, đặt một số trường thành null, hoặc thay đổi giá trị id hoặc postId từ số thành chuỗi.  
{{% /notice %}}

## Tạo S3 Bucket

1. Truy cập [AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)

   - Tìm kiếm **S3**
   - Chọn **S3**
     ![](/images/3/1/0001-creates3bucket.png)

2. Trong **giao diện S3**

   - Chọn **buckets**
   - Chọn **Create bucket**
     ![](/images/3/1/0002-creates3bucket.png)

3. Trong **giao diện Create bucket**
   - Đối với tên Bucket, nhập `datalake-demo-bucket`
     ![](/images/3/1/1.png)
4. Nhấp vào **Create bucket**
   ![](/images/3/1/2.png)
5. Đã tạo bucket thành công

   - Chọn bucket mới tạo
     ![](/images/3/1/3.png)

6. Trong giao diện bucket mới

   - Chọn **Create folder**
     ![](/images/3/1/4.png)

7. Trong giao diện **Create folder**
   - Đối với tên thư mục, nhập `raw-data`
     ![](/images/3/1/5.png)
8. Đã tạo thư mục thành công
   ![](/images/3/1/6.png)
9. Tại thư mục **raw-data**

- Tạo các thư mục `post` và `comment`
  ![](/images/3/1/7.png)

Sau khi tạo thành công 2 thư mục, chúng ta sẽ không tải lên tệp ngay lập tức mà sẽ tiến hành bước tiếp theo, đó là **Tạo Lambda Function** để xử lý việc làm sạch dữ liệu
