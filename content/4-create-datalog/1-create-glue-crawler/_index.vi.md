+++
title = "Tạo AWS Glue Crawler"
date = 2020
weight = 1
chapter = false
pre = "<b>4.1. </b>"
+++

### Tạo Glue Crawler

1. Truy cập [AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)
   - Tìm **AWS Glue**.
   - Chọn **AWS Glue**.
     ![](/images/4/1/1.png)
2. Trong giao diện **AWS Glue**, chọn **Crawlers**.
3. Chọn Create Crawler.
   ![](/images/4/1/2.png)
4. Trong giao diện **Add Crawler**, nhập **Crawler name** là `summitcrawler` và chọn **Next**.
   ![](/images/4/1/3.png)
5. Đối với Add data source, chọn S3.
6. Chọn đường dẫn **S3** thông qua **Browse**. Chọn: **datalate-bucket-demo/cleaned-data**. Đồng thời, chọn **Crawl new sub-folders only** và **Add an S3 data source**.
7. Sau khi thêm nguồn dữ liệu, chọn **Next**.
   ![](/images/4/1/4.png)
8. Đối với **IAM role**, chọn **AWSGlueServiceDefault**. Sau đó, chọn **Next**.
   ![](/images/4/1/5.png)
9. Đối với **Target database**, thực hiện **Add database**.
   ![](/images/4/1/6.png)
10. Tạo cơ sở dữ liệu bằng cách nhập tên cơ sở dữ liệu là `summitdb` và chọn **Create database**.
    ![](/images/4/1/7.png)
11. Sau khi tạo cơ sở dữ liệu, chọn cơ sở dữ liệu và chọn **Next**.
    ![](/images/4/1/9.png)
12. Xem lại cấu hình và chọn **Create crawler**.
    ![](/images/4/1/10.png)
13. Tạo crawler thành công. Sau đó, chọn **Run crawler**.
    ![](/images/4/1/11.png)
14. Mất khoảng 2-3 phút để chạy crawler.
15. Khi bạn thấy trạng thái crawler là **Ready**.
    ![](/images/4/1/12.png)
16. Trong giao diện **AWS Glue**, chọn **Table**, và bạn sẽ thấy 2 bảng dữ liệu.
    ![](/images/4/1/13.png)
17. Chọn bảng dữ liệu **post**.
    ![](/images/4/1/14.png)
18. Chọn bảng dữ liệu **comment**.
    ![](/images/4/1/14.png)
19. Khám phá chi tiết của bảng dữ liệu.
