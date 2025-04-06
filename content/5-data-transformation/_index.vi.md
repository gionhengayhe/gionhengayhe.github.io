+++
title = "Chuyển đổi dữ liệu"
date = 2020
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

{{% notice info %}}
Trong một khoảnh khắc ngớ ngẩn, tôi chỉ ghi lại một phần nhỏ của màn hình, vì vậy một phần lớn cảnh quay đã biến mất. Để làm cho mọi thứ tồi tệ hơn, tôi vô tình xóa tất cả các tệp dự án của mình, vì vậy tôi không thể làm lại nhanh chóng. Một khu vực ghi nhỏ và một nút xóa to, béo? Thật là một sự kết hợp! Tôi đoán đây là điều mà người ta gọi là 'trải nghiệm học tập', nhưng nó khá đắt đỏ.
{{% /notice %}}

#### Tạo SageMaker Notebook

1. Truy cập [AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)
   Tìm **AWS Glue**
   Chọn **AWS Glue**
   ![](/images/4/1/1.png)
2. Chọn **Notebooks**
   ![](/images/5/2.png)
3. Chọn **Notebook**
   ![](/images/5/3.png)
4. Nhập tên notebook là `notebook`

   - Chọn **IAM role**
   - Chọn **Create notebook**
     ![](/images/5/4.png)

5. Đợi khoảng 2-3 phút, và notebook sẽ được tạo.
   ![](/images/5/5.png)

#### Chuyển đổi dữ liệu

1.  Trong Notebook

    - Import thư viện:
      - SparkContext
      - GlueContext
      - boto3
      - awsglue

    ```
    import sys
    from awsglue.transforms import *
    from awsglue.utils import getResolvedOptions
    from pyspark.context import SparkContext
    from awsglue.context import GlueContext
    from awsglue.job import Job
    import boto3
    import time
    ```

    ![](/images/5/0.png)

2.  Tiếp theo chúng ta bắt đầu khám phá dữ liệu

    - Khởi tạo Spark và Glue Contexts

    ```
      sc = SparkContext.getOrCreate()
      glueContext = GlueContext(sc)
      spark = glueContext.spark_session
      job = Job(glueContext)
    ```

    ![](/images/5/6.png)

3.  Tải bảng **Comment** và xem Schema

    ```
    comment_data = glueContext.create_dynamic_frame.from_catalog(database='summitdb', table_name='comment')
    comment_data.printSchema()
    ```

    ![](/images/5/7.png)

4.  Tải bảng **Post** và xem schema

    ```
    post_data = glueContext.create_dynamic_frame.from_catalog(database='summitdb', table_name='post')
    post_data.printSchema()
    ```

    ![](/images/5/8.png)

5.  Đếm số dòng trong bảng **post** và **comment**

    ```
    print('post_data (Count) = ' + str(post_data.count()))
    print('comment_data (Count) = ' + str(comment_data.count()))
    ```

    ![](/images/5/9.png)

6.  Xem trước **post_data**

    ```
    post_data.toDF().show(5)
    ```

    ![](/images/5/9.1.png)

7.  Xem trước **comment_data**

    ```
    comment_data.toDF().show(5)
    ```

    ![](/images/5/9.2.png)

8.  Hiển thị **Comments** nơi **postId = 10**

    ```
    comment_data.toDF().createOrReplaceTempView('comment')

    filter_postidDF = spark.sql("select \* from comment where postid = 10")

    print("PostId = 10 (count): " + str(filter_postidDF.count()))

    filter_postidDF.show(5)
    ```

    ![](/images/5/10.png)

9.  Hiển thị **Posts** nơi **userid = 10**

    ```
    post_data.toDF().createOrReplaceTempView('post')

    filter_useridDF = spark.sql("select \* from post where userid = 10")

    print("UserId = 10 (count): " + str(filter_useridDF.count()))

    filter_useridDF.show(5)
    ```

    ![](/images/5/1.png)

10. Join **comment_data(postid)** với **post_data(id)** và xem xét **joined_data**

    ```
    joined_data = Join.apply(comment_data, post_data, 'postId', 'id')
    ```

    ![](/images/5/11.png)

    ```
    joined_data.printSchema()
    ```

    ![](/images/5/12.png)

    ```
    joined_data.toDF().show(5)
    ```

    ![](/images/5/13.png)

11. Đổi tên cột để rõ ràng hơn

    ```
    renamed_df = (
        joined_data.toDF()
        .withColumnRenamed(".id", "commentId")
        .withColumnRenamed(".body", "commentBody")
        .withColumnRenamed("id", "postId")
        .withColumnRenamed("title", "postTitle")
        .withColumnRenamed("name", "commenterName")
        .withColumnRenamed("email", "commenterEmail")
        .withColumnRenamed("body", "postBody")
        .withColumnRenamed("userId", "postUserId"))
    renamed_df.show(5)
    ```

    ![](/images/5/14.png)

12. Chuyển đổi DataFrame trở lại DynamicFrame

    ```
    from awsglue.dynamicframe import DynamicFrame
    new_joined_data = DynamicFrame.fromDF(
        renamed_df,
        glueContext,
        "new_joined_data"
    )
    ```

    ![](/images/5/15.png)

13. Ghi dữ liệu đã chuyển đổi vào **S3**

    ```
    try:
        datasink = glueContext.write dynamic from options(
            frame=new_joined_data,
            connection_type="s3",
            connection_options={
                "path": "s3://datalake-bucket-demo/cleaned-data/processed-data/"},
            format="parquet")
        print("Transform data written to S3")
    except Exception as e:
        print("Error writing to S3: " + str(e))
    ```

    ![](/images/5/16.png)

    - Dữ liệu đã chuyển đổi đã được ghi vào **datalake-bucket-demo/cleaned-data/processed-data/**
      ![](/images/5/17.png)

14. Kích hoạt và giám sát Glue Crawler

    ```
    glueclient = boto3.client('glue', region_name='us-ease-1')
    response = glueclient.start_crawler(Name="summitcrawler")
    print('---')
    crawler_state = ''
    while crawler_state 1= 'STOPPING':
        response = glueclient.get_crawler(Name="summitcrawler")
        crawler_state = str(response['Crawler']['State'])
        time.sleep(1)
    print('Crawler stopped')
    print ('---')
    ```

    ![](/images/5/18.png)

15. Kiểm tra **Log events** của **Crawler**

    - Mở **summitcrawler** trong Console **AWS Glue Crawler**
      ![](/images/5/19.png)
    - Đợi 2 phút để **summitcrawler** chạy
      ![](/images/5/21.png)

    - Chọn lần chạy **Crawlers** mới nhất và **nhấp vào ViewCloudWatch logs**
      ![](/images/5/20.png)
      ![](/images/5/22.png)
      {{% notice warning %}}
      Vì một số lỗi tôi không biết, bảng Processed-data không được tạo khi Summitcrawler chạy, vì vậy chúng ta cần tạo một AWS Glue Crawler mới cho Processed-data
      {{% /notice %}}

16. Truy cập [AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)

- Tìm **AWS Glue**.
- Chọn **AWS Glue**.
  ![](/images/4/1/1.png)

17. Trong giao diện **AWS Glue**, chọn **Crawlers**.
    Chọn Create Crawler.
    ![](/images/4/1/2.png)
18. Trong giao diện **Add Crawler**, nhập **Crawler name** là `joined-crawler` và chọn **Next**.
