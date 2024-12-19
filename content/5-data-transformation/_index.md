+++
title = "Data Transformation"
date = 2020
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

{{% notice info %}}
In a silly moment, I only recorded a tiny part of the screen, so a huge chunk of the footage is gone. To make things worse, I accidentally deleted all my project files, so I can't redo it quickly. A tiny recording area and a big, fat delete button? What a combo! I guess this is what they call a 'learning experience,' but it's a pretty expensive one.
{{% /notice %}}

#### Create SageMaker Notebook

1. Access the [AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)
   Find **AWS Glue**
   Select **AWS Glue**
   ![](/images/4/1/1.png)
2. Select **Notebooks**
   ![](/images/5/2.png)
3. Select **Notebook**
   ![](/images/5/3.png)
4. Enter the notebook name as `notebook`

   - Choose **IAM role**
   - Select **Create notebook**
     ![](/images/5/4.png)

5. Wait for about 2-3 minutes, and the notebook will be created.
   ![](/images/5/5.png)

#### Data Transformation

1.  In Notebook

    - Import libraries:
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

2.  Next we start exploring the data

    - Initialize Spark and Glue Contexts

    ```
      sc = SparkContext.getOrCreate()
      glueContext = GlueContext(sc)
      spark = glueContext.spark_session
      job = Job(glueContext)
    ```

    ![](/images/5/6.png)

3.  Load **Comment** table and view Schema

    ```
    comment_data = glueContext.create_dynamic_frame.from_catalog(database='summitdb', table_name='comment')
    comment_data.printSchema()
    ```

    ![](/images/5/7.png)

4.  Load **Post** table and view schema

    ```
    post_data = glueContext.create_dynamic_frame.from_catalog(database='summitdb', table_name='post')
    post_data.printSchema()
    ```

    ![](/images/5/8.png)

5.  Count Rows in Tables **post** and **comment**

    ```
    print('post_data (Count) = ' + str(post_data.count()))
    print('comment_data (Count) = ' + str(comment_data.count()))
    ```

    ![](/images/5/9.png)

6.  Preview **post_data**

    ```
    post_data.toDF().show(5)
    ```

    ![](/images/5/9.1.png)

7.  Preview **comment_data**

    ```
    comment_data.toDF().show(5)
    ```

    ![](/images/5/9.2.png)

8.  Show **Comments** where **postId = 10**

    ```
    comment_data.toDF().createOrReplaceTempView('comment')

    filter_postidDF = spark.sql("select \* from comment where postid = 10")

    print("PostId = 10 (count): " + str(filter_postidDF.count()))

    filter_postidDF.show(5)
    ```

    ![](/images/5/10.png)

9.  Show **Posts** where **userid = 10**

    ```
    post_data.toDF().createOrReplaceTempView('post')

    filter_useridDF = spark.sql("select \* from post where userid = 10")

    print("UserId = 10 (count): " + str(filter_useridDF.count()))

    filter_useridDF.show(5)
    ```

    ![](/images/5/1.png)

10. Join **comment_data(postid)** with **post_data(id)** and review **joined_data**

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

11. Rename columns for clarity

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

12. Convert DataFrame back to DynamicFrame

    ```
    from awsglue.dynamicframe import DynamicFrame
    new_joined_data = DynamicFrame.fromDF(
        renamed_df,
        glueContext,
        "new_joined_data"
    )
    ```

    ![](/images/5/15.png)

13. Write transformed Data to **S3**

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

    - Transform data have written to **datalake-bucket-demo/cleaned-data/processed-data/**
      ![](/images/5/17.png)

14. Trigger and monitor Glue Crawler

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

15. Check **Log events** of **Crawler**

    - Open **summitcrawler** in **AWS Glue Crawler** Console
      ![](/images/5/19.png)
    - Waiting 2 minutues for **summitcrawler** run
      ![](/images/5/21.png)

    - Choose the latest **Crawlers** run and **click ViewCloudWatch logs**
      ![](/images/5/20.png)
      ![](/images/5/22.png)
      {{% notice warning %}}
      Because some error i don't know, the table Processed-data doesn't create when Summitcrawler run, so we need to create a new AWS Glue Crawler for Processed-data
      {{% /notice %}}

16. Access the [AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)

- Find **AWS Glue**.
- Select **AWS Glue**.
  ![](/images/4/1/1.png)

17. In the **AWS Glue** interface, select **Crawlers**.
    Choose Create Crawler.
    ![](/images/4/1/2.png)
18. In the **Add Crawler** interface, enter **Crawler name** as `joined-crawler` and select **Next**.
    ![](/images/5/23.png)
19. For Add data source, select S3.
20. Choose **S3** path through **Browse**. Choose: **datalate-bucket-demo/cleaned-data/processed-data**. Also, select **Crawl new sub-folders only** and **Add an S3 data source**.
21. After adding the data source, select **Next**.
    ![](/images/5/24.png)
22. Other steps like creating **summitcrawler**
23. Run **joined-crawler**
    ![](/images/5/25.png)
24. Check table processed-data
    ![](/images/5/26.png)
    - You will see processed-data has schema is table **post** join table **comment**
      ![](/images/5/27.png)
