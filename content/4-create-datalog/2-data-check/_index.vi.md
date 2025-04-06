+++
title = "Kiểm tra dữ liệu"
date = 2020
weight = 2
chapter = false
pre = "<b>4.2 </b>"
+++

### Kiểm tra dữ liệu

1. Truy cập [AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)

   - Tìm **S3**
   - Chọn **S3**
     ![](/images/3/1/0001-creates3bucket.png)

2. Trong giao diện **S3**

   - Chọn **Buckets**
   - Chọn **datalake-bucket-demo**

3. Chúng ta sẽ tạo một thư mục cho **Athena**
   - Chọn **Create folder**
     ![](/images/4/2/3.png)
4. Trong giao diện **Create folder**
   - Folder name, nhập **Athena**
   - Chọn **Create folder**
     ![](/images/4/2/4.png)
5. Tạo thư mục thành công
6. Truy cập [AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)
   - Tìm **Athena**
   - Chọn **Athena**
     ![](/images/4/2/1.png)
7. Trong giao diện **Athena**

   - Chọn **View settings** để thiết lập đường dẫn lưu kết quả truy vấn
     ![](/images/4/2/5.png)

8. Trong giao diện **Amazon Athena**
   - Chọn **Settings**
   - Chọn **Manage**
     ![](/images/4/2/6.png)
9. Chọn đường dẫn đến thư mục Athena vừa tạo, sau đó chọn Choose
10. Quay lại giao diện Manage settings, kiểm tra lại và chọn Save
    ![](/images/4/2/7.png)
11. Chúng ta sử dụng **Amazon Athena** để truy vấn dữ liệu

    - Data Source, chọn **AwsDataCatalog**
    - Database, chọn **summitdb**
    - Chọn bảng **comment**
    - Chọn **Preview** Table
      ![](/images/4/2/2.png)

12. Thực hiện truy vấn 10 dòng dữ liệu từ bảng **comment** trong cơ sở dữ liệu summitdb
    - Truy vấn thành công
    - Kiểm tra dữ liệu
      ![](/images/4/2/8.png)
13. Kiểm tra dữ liệu bảng **comment** nơi postid = 10
    ![](/images/4/2/9.png)
    ![](/images/4/2/10.png)

14. Kiểm tra dữ liệu bảng **post** limit 10;
    ![](/images/4/2/11.png)
    ![](/images/4/2/12.png)
15. Bảng **comment** join bảng **post**
    ![](/images/4/2/13.png)
    ![](/images/4/2/14.png)
