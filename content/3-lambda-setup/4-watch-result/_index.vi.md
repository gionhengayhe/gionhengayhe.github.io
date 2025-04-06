+++
title = "Tải lên dữ liệu và xem kết quả"
date = 2020
weight = 4
chapter = false
pre = "<b>3.4 </b>"
+++

## Tải lên dữ liệu

1.  - Mở thư mục: **datalake-bucket-demo/raw-data/post**
    - Nhấp vào **Upload**
      ![](/images/3/3/13.png)
2.  - Nhấp vào **Add files**
    - Chọn file post.json bạn đã tải xuống tại [3.1. Tạo S3 Bucket]({{<ref "3-lambda-setup/1-creating-bucket/_index.vi.md">}})
    - Nhấp vào **Upload**
      ![](/images/3/3/15.png)
3.  - Mở Lambda Function **Clean-PostData**, tại **Monitor**, nhấp vào **View CloudWatch logs**
      ![](/images/3/4/1.png)
4.  - Chọn **Log stream** mới nhất dựa trên dấu thời gian.
      ![](/images/3/4/2.png)
5.  - Bên trong các sự kiện log của Log Stream đã chọn, tìm thông báo:  
      **Cleaned data uploaded to s3://datalake-bucket-demo/cleaned-data/post/post.json**.
    - Điều đó có nghĩa là Lambda function của bạn đã thực thi thành công và tải lên dữ liệu đã được làm sạch.
      ![](/images/3/4/3.png)
6.  - Quay lại **S3 Console** và điều hướng đến bucket **datalake-bucket-demo**.
    - Tìm thư mục cleaned-data/post/.
    - Bên trong thư mục này, bạn sẽ tìm thấy một file có tên **post.json**.
      ![](/images/3/4/4.png)
      ![](/images/3/4/5.png)
7.  - Tải xuống file **post.json** để xem xét nội dung của nó.
    - Bạn sẽ nhận thấy rằng dữ liệu đã được làm sạch, với bất kỳ mục không hợp lệ hoặc sai định dạng nào đã bị xóa, và được cấu trúc chính xác như các đối tượng JSON.
    - Điều này đảm bảo dữ liệu đã sẵn sàng để AWS Glue suy ra lược đồ và xử lý nó một cách chính xác.
    - **raw-data/post.json** của tôi:
      ![Dữ liệu bài đăng thô](/images/3/4/6.png)

      {{% notice note %}}
      Trong file post.json raw-data của tôi, bạn sẽ thấy:

      1. Object 1 thiếu trường body.
      2. Object 2 thiếu trường title.
      3. Trường id trong object 3 là một chuỗi thay vì một số.
      4. Trường userId trong object 4 là một chuỗi thay vì một số.
      5. File raw-data là một mảng các đối tượng JSON được cấu trúc như:
         [{Object 1}, {Object 2}, ..., {Object n}].
         {{% /notice %}}

    - **cleaned-data/post.json** của tôi:
      ![Dữ liệu bài đăng đã làm sạch](/images/3/4/7.png)
      {{% notice note %}}
      Trong file cleaned-data/post.json, bạn sẽ thấy:

      1. Object 1, 2, 3, 4 đã bị xóa.
      2. Dữ liệu bây giờ được định dạng như {Object 1}, {Object 2}, ..., {Object n} mà không được bọc trong một mảng.
         {{% /notice %}}

8.  Tương tự như tải lên **post.json**, tải lên **comment.json** trong **raw-data/comment/**.

Đó là cách bạn làm sạch dữ liệu bằng **AWS Lambda** và **EventBridge**. Bây giờ, chúng ta hãy chuyển sang bước tiếp theo: [Tạo Data Catalog]({{<ref "4-create-datalog/1-create-glue-crawler/_index.vi.md">}}).
