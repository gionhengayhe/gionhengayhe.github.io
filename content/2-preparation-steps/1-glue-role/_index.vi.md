+++
title = "Tạo Glue Service Role"
date = 2020
weight = 1
chapter = false
pre = "<b>2.1 </b>"
+++

## Tạo Glue Service Role

Trong bước này, chúng ta sẽ điều hướng đến IAM Console và tạo một role cho dịch vụ Glue. Role này sẽ cho phép AWS Glue truy cập dữ liệu trong S3 và tạo các đối tượng cần thiết trong Glue Catalog.

1.  Truy cập [AWS Management Console]()

    - Tìm kiếm **IAM**
    - Chọn **IAM**
      ![Step1](/images/2/0001-createiamrole.png)

2.  Trong console **IAM**:

    - Chọn **Roles**
    - Chọn **Create role**
      ![](/images/2/0002-createiamrole.png)

3.  Trong bước **Select trusted entity**:

    - Chọn **AWS Service**
    - Đối với **Use case**, chọn **Glue**
    - Nhấp vào **Next**
    - ![](/images/2/0003-createiamrole.png)

4.  Trong bước **Add permissions**:

    - Tìm kiếm chính sách **AmazonS3FullAccess**
    - Chọn chính sách **AmazonS3FullAccess**
    - Nhấp vào Next
    - ![](/images/2/0004-createiamrole.png)

5.  Tương tự như bước 4:

    - Tìm kiếm chính sách **AWSGlueServiceRole**
    - Chọn chính sách **AWSGlueServiceRole**
    - ![](/images/2/0005-createiamrole.png)

6.  Trong giao diện **Role details**:
    - Đối với **Role name**, nhập `AWSGlueServiceRoleDefault`
    - ![](/images/2/0006-createiamrole.png)
7.  Trong bước **Add permissions**:
    - Xem lại hai chính sách
    - Nhấp vào **Create role**
    - ![](/images/2/0007-createiamrole.png)
8.  Chúng ta đã hoàn thành việc tạo IAM role
    - ![](/images/2/0008-createiamrole.png)
