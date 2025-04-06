+++
title = "Phân tích với Athena"
date = 2020
weight = 1
chapter = false
pre = "<b>6.1 </b>"
+++

#### Phân tích với Athena

Vì Athena sử dụng AWS Glue Catalog để theo dõi nguồn dữ liệu, tất cả các bảng trong Glue có thể được truy vấn thông qua Athena.

1. Truy cập [AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)

   - Tìm **Athena**
   - Chọn **Athena**
     ![](/images/4/2/1.png)

2. Trong giao diện **Athena**:
   - Data Source, chọn **AwsDataCatalog**
   - Database, chọn **summitdb**
   - Chọn bảng **processed-data**
   - Chọn **Preview** Table
     ![](/images/6/1/1.png)
     ![](/images/6/1/2.png)
