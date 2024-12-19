+++
title = "Create an S3 Bucket"
date = 2020
weight = 1
chapter = false
pre = "<b>3.1. </b>"
+++

## Download data

1. Click on this: [Post data](https://jsonplaceholder.typicode.com/posts)
2. Save with **Ctrl + S**
3. Click on this: [Comment data](https://jsonplaceholder.typicode.com/comments)
4. Save with **Ctrl + S**
5. On the file **.json** you just downloaded, you can change the code to testing Clean Data Use Case

{{% notice tip %}}
You can modify the data for testing purposes: delete some records, set certain fields to null, or change the id or postId values from numbers to strings.  
{{% /notice %}}

## Create S3 Bucket

1. Visit the [AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)

   - Search for **S3**
   - Select **S3**
     ![](/images/3/1/0001-creates3bucket.png)

2. In the **S3 interface**

   - Choose **buckets**
   - Select **Create bucket**
     ![](/images/3/1/0002-creates3bucket.png)

3. In the **Create bucket interface**
   - For Bucket name, enter `datalake-demo-bucket`
     ![](/images/3/1/1.png)
4. Click **Create bucket**
   ![](/images/3/1/2.png)
5. Successfully created the bucket

   - Select the newly created bucket
     ![](/images/3/1/3.png)

6. In the new bucket interface

   - Select **Create folder**
     ![](/images/3/1/4.png)

7. In the **Create folder** interface
   - For Folder name, enter `raw-data`
     ![](/images/3/1/5.png)
8. Successfully created the folder
   ![](/images/3/1/6.png)
9. At folder **raw-data**

- Create `post` and `comment` folders
  ![](/images/3/1/7.png)

After successfully creating the 2 folders, we will not upload the files immediately but will proceed to the next step, which is **Creating the Lambda Function** to handle data cleaning
