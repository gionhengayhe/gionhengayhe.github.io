+++
title = "Thiết lập EventBridge và S3 Trigger"
date = 2020
weight = 3
chapter = false
pre = "<b>3.3 </b>"
+++

## Tạo EventBridge

1.  Truy cập [AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)

    - Tìm kiếm **EventBridge**
    - Chọn **Amazon EventBridge**
      ![](/images/3/3/4.png)

2.  Tại **Amazon EventBridge Console**, chọn **Create Rule**
    ![](/images/3/3/5.png)
3.  - Tại name: `TriggerCommentData`
    - Nhấp vào **Next**
      ![](/images/3/3/6.png)
4.  - Tại creation method, chọn **Custom pattern**
    - Tại event pattern:
      ```
      {
        "source": ["aws.s3"],
        "detail-type": ["Object Created"],
        "detail":{
            "bucket":{
                "name": ["datalake-bucket-demo"]
            },
            "object":{
                "key":[{
                    "prefix": "raw-data/comment"
                }]
            }
        }
      }
      ```
    - Nhấp vào **Next**
      ![](/images/3/3/7.png)

5.  - Tại Select a target: **Lambda function**
    - Function: **Clean-CommentData**
    - Nhấp vào **Next**
      ![](/images/3/3/8.png)
6.  Xem lại rule, nhấp vào **Create rule**
    ![](/images/3/3/9.png)
7.  - Tương tự như bước **2-6**, tạo rule `TriggerPostData`
    - Sử dụng pattern này:

      ```
      {
        "source": ["aws.s3"],
        "detail-type": ["Object Created"],
        "detail":{
            "bucket":{
                "name": ["datalake-bucket-demo"]
            },
            "object":{
                "key":[{
                    "prefix": "raw-data/post"
                }]
            }
        }
      }
      ```

8.  Sau khi tạo rule **TriggerPostData**, chúng ta sẽ có:
    ![](/images/3/3/10.png)
9.  Quay lại **Lambda Function Clean-PostData và Clean-CommentData**, bạn sẽ thấy:
    ![](/images/3/3/11.png)
    ![](/images/3/3/12.png)

## Thiết lập gửi thông báo đến EventBridge cho tất cả sự kiện trong S3

1.  Mở **console S3 datalake-bucket-demo**, nhấp vào **Properties**
    ![](/images/3/3/1.png)
2.  Tại Amazon EventBridge, nhấp vào **Edit**
    ![](/images/3/3/2.png)
3.  Bật **Send notifications to EventBridge for all events in this bucket**, sau đó nhấp vào **Save changes**
    ![](/images/3/3/3.png)
    Chúc mừng, bạn đã tạo thành công một **trigger** để kích hoạt **Lambda** khi lắng nghe sự kiện tải lên của **S3** với **EventBridge**. Bây giờ chúng ta sẽ chuyển sang bước tiếp theo: **Tải lên dữ liệu và xem kết quả**.
