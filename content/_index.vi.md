+++
title = "Data Lake on AWS: Clean Data with Lambda Triggers"
date = 2021
weight = 1
chapter = false
+++

# Data Lake on AWS: Clean Data with Lambda Triggers

#### Tổng quan

Workshop này hướng dẫn bạn tạo một **hệ thống Data Lake trên AWS** để **thu thập, xử lý, làm sạch** và **truy vấn dữ liệu**. Chúng ta sẽ bắt đầu bằng việc thu thập dữ liệu từ **API**, upload vào **S3**, sau đó kết hợp **AWS Lambda trigger** để tự động làm sạch dữ liệu ngay khi tải lên. Dữ liệu sẽ được đổ vào **Glue Data Catalog** để phân tích bằng **Athena**, chuyển đổi qua **Glue Job**, và trực quan hóa với **QuickSight**.

![Diagram](/images/Datalake.drawio.png?width=90pc)

#### Mục đích

- Tìm hiểu về **Data Lake**: Giúp người tham gia hiểu rõ **Data Lake** là gì, cách xây dựng và vận hành **Data Lake** trên AWS.

- Tự động hóa quy trình làm sạch dữ liệu: Đồng bộ các dữ liệu upload lên **S3** và xử lý ngay lập tức bằng **Lambda** trigger.

- Tăng cường kỹ năng phân tích dữ liệu: Tìm hiểu **Glue Data Catalog**, truy vấn **Athena**, và biểu diễn trực quan **QuickSight**.

- Độc lập và linh hoạt: Xây dựng mô hình hợp nhất cho nhiều loại dữ liệu, đầu vào từ **API**, **S3**, hay **dữ liệu ngoại**.

#### Yêu cầu:

- **Tài khoản AWS:** User có quyền Admin và đã thiết lập billing.

- **Dữ liệu API:** Link dữ liệu sẽ được cung cấp trong workshop.

#### Chi phí:

- [AWS Free Tier: S3, Lambda, Athena](https://aws.amazon.com/vi/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=*all&awsf.Free%20Tier%20Categories=*all)
- [AWS Glue Job: 0.44$/h for one session](https://aws.amazon.com/vi/glue/pricing/)
- [QuickSight: 30 days free](https://aws.amazon.com/vi/pm/quicksight/?gclid=CjwKCAiAjeW6BhBAEiwAdKltMnYjTIqgPUZFV-osOhJ2zn7Ww25dqqS0yj1NzUwuhCzPW6Wo4vl7jxoCs44QAvD_BwE&trk=4307e550-ebb4-40d7-a036-1a56b1d0ff3f&sc_channel=ps&ef_id=CjwKCAiAjeW6BhBAEiwAdKltMnYjTIqgPUZFV-osOhJ2zn7Ww25dqqS0yj1NzUwuhCzPW6Wo4vl7jxoCs44QAvD_BwE:G:s&s_kwcid=AL!4422!3!651510255273!e!!g!!quicksight%20pricing!19836376477!143940200301)
