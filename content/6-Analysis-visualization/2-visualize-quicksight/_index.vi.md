+++
title = "Trực quan hóa với QuickSight"
date = 2020
weight = 2
chapter = false
pre = "<b>6.2 </b>"
+++

#### Trực quan hóa với QuickSight

Trong bước này, chúng ta sẽ thực hiện trực quan hóa bằng QuickSight.

1. Đăng nhập vào Amazon QuickSight Console và hoàn thành quá trình đăng ký. Bạn có thể tham khảo quy trình đăng ký [tại đây](https://000070.awsstudygroup.com/6-quicksight/6.1-registerquicksight/).
2. Truy cập [AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)

   - Tìm **QuickSight**
   - Chọn **QuickSight**
     ![](/images/6/2/1.png)

   > **Lưu ý**: Chú ý đến Region bạn đang sử dụng. Kiểm tra và chuyển đổi Region nếu cần thiết để tránh lỗi.

   ![](/images/6/2/2.png)

3. Trong giao diện **QuickSight**, chọn **Manage QuickSight**
   ![](/images/6/2/3.png)
4. Cấu hình **Permissions**
   - Chọn **Security & permissions**
   - Chọn **Manage**
     ![](/images/6/2/4.png)
5. Chọn dịch vụ và chọn **Amazon S3**

   - Chọn **S3 Buckets Linked To QuickSight Account**
   - Chọn **datalake-bucket-demo**
   - Chọn **Finish**
     ![](/images/6/2/5.png)

6. Chọn và xem lại Role và dịch vụ. Sau đó, chọn **Save**
   ![](/images/6/2/6.png)
7. Trong giao diện **QuickSight**:

   - Chọn **Datasets**
   - Chọn **New dataset**
     ![](/images/6/2/7.png)

8. Trong giao diện **Create dataset**:

   - Chọn nguồn từ **Athena**
     ![](/images/6/2/8.png)

9. Cấu hình nguồn dữ liệu:

   - **Data source name**, nhập `summitdemo`
   - Chọn **Validate Connection**. Nếu kết nối thành công, nó sẽ hiển thị SSL is enabled
   - Chọn **Create data source**
     ![](/images/6/2/9.png)

10. Chọn Bảng:
    - **Catalog**, chọn **AWSDataCatalog**
    - **Database**, nhập `summitdb`
    - **Table**, chọn **processed_data**
    - Chọn **Select**
      ![](/images/6/2/14.png)
11. Trong bước **Finish dataset creation**:
    - Chọn **Directly query your data**
    - Chọn **Visualize**
      ![](/images/6/2/15.png)
    - Chọn **Create**
      ![](/images/6/2/16.png)
12. Sử dụng **Amazon QuickSight** để trực quan hóa dữ liệu đã chuyển đổi:  
    **Đếm bình luận cho mỗi bài đăng**

    - Nhấp vào **Pie Chart**
    - Group/color: **postid**
    - Value: **commentid(Count)**

    ![](/images/6/2/17.png)

    **Đếm số bài đăng của mỗi người dùng**

    - Group/color: **postuserid**
    - Value: **postid(Count)**
      ![](/images/6/2/18.png)

13. Nếu bạn gặp lỗi như
    ![](/images/6/2/10.png)
    hoặc
    ![](/images/6/2/10.1.png)
    - Đi đến **IAM Role Console**
    - Tìm **aws-quicksight-service-role-...**
      ![](/images/6/2/11.png)
    - Nhấp vào **Add Permissions**
    - Nhấp vào **Attach policies**
      ![](/images/6/2/12.png)
    - Tìm kiếm **Quicksight** và chọn các chính sách này:
      ![](/images/6/2/13.png)
