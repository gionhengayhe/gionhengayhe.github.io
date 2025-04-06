+++
title = "Tạo Lambda role"
date = 2020
weight = 2
chapter = false
pre = "<b>2.2 </b>"
+++

## Tạo Glue Service Role

Trong bước này, chúng ta sẽ điều hướng đến IAM Console và tạo một role cho dịch vụ Lambda function. Role này sẽ cho phép Lambda function truy cập dữ liệu trong S3, làm sạch dữ liệu và tạo các đối tượng cần thiết trong Lambda Catalog.

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
    - Đối với **Use case**, chọn **Lambda**
    - Nhấp vào **Next**
    - ![](/images/2/2/3.png)

4.  Trong bước **Add permissions**:

    - Tìm kiếm chính sách **AmazonS3FullAccess**
    - Chọn chính sách **AmazonS3FullAccess**
    - Nhấp vào Next
    - ![](/images/2/0004-createiamrole.png)

5.  Tương tự như bước 4:

    - Tìm kiếm chính sách **AWSLambda_FullAccess**
    - Chọn chính sách **AWSLambda_FullAccess**
    - ![](/images/2/2/5.png)
    -
    - Tìm kiếm chính sách **AWSLambdaBasicExecutionRole**
    - Chọn chính sách **AWSLambdaBasicExecutionRole**
    - ![](/images/2/2/6.png)

6.  Trong giao diện **Role details**:
    - Đối với **Role name**, nhập `AWSLambdaRoleDefault`
    - ![](/images/2/2/7.png)
7.  Trong bước **Add permissions**:
    - Xem lại ba chính sách
    - Nhấp vào **Create role**
8.  Chúng ta đã hoàn thành việc tạo IAM role
    - ![](/images/2/2/8.png)
