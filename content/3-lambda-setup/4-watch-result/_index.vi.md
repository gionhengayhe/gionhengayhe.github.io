+++
title = "Upload data and view the results"
date = 2020
weight = 4
chapter = false
pre = "<b>3.4 </b>"
+++

## Upload data

1.  - Open folder: **datalake-bucket-demo/raw-data/post**
    - Click **Upload**
      ![](/images/3/3/13.png)
2.  - Click **Add files**
    - Choose file post.json you have downloaded at [3.1. Create S3 Bucket]({{<ref "3-lambda-setup/1-creating-bucket/_index.md">}})
    - Click **Upload**
      ![](/images/3/3/15.png)
3.  - Open the Lambda Function **Clean-PostData**, at **Monitor**, click **View CloudWatch logs**
      ![](/images/3/4/1.png)
4.  - Select the latest **Log stream** based on timestamp.
      ![](/images/3/4/2.png)
5.  - Inside the log events of the selected Log Stream, look for the message:  
      **Cleaned data uploaded to s3://datalake-bucket-demo/cleaned-data/post/post.json**.
    - That means your Lambda function has successfully executed and uploaded the cleaned data.
      ![](/images/3/4/3.png)
6.  - Go back to the **S3 Console** and navigate to the **datalake-bucket-demo** bucket.
    - Locate the folder cleaned-data/post/.
    - Inside this folder, you will find a file named **post.json**.
      ![](/images/3/4/4.png)
      ![](/images/3/4/5.png)
7.  - Download the **post.json** file to review its contents.
    - You will notice that the data has been cleaned, with any invalid or malformed entries removed, and structured correctly as JSON objects.
    - This ensures the data is ready for AWS Glue to infer the schema and process it accurately.
    - My **raw-data/post.json**:
      ![Raw Post data](/images/3/4/6.png)

      {{% notice note %}}
      In my raw-data post.json, you will find:

      1. The first object is missing the body field.
      2. The second object is missing the title field.
      3. The id field in the third object is a string instead of a number.
      4. The userId field in the fourth object is a string instead of a number.
      5. The raw-data file is an array of JSON objects structured as:
         [{Object 1}, {Object 2}, ..., {Object n}].
         {{% /notice %}}

    - My **cleaned-data/post.json**
      ![Cleaned Post Data](/images/3/4/7.png)
      {{% notice note %}}
      In my cleaned-data post.json, you will see:

      1. The 1st, 2nd, 3rd, and 4th objects have been removed.
      2. The data is now formatted as {Object 1}, {Object 2}, ..., {Object n} without being wrapped in an array.
         {{% /notice %}}

8.  Similar to upload **post.json**, upload **comment.json** in **raw-data/comment/**.

That’s how you clean the data using **AWS Lambda** and **EventBridge**. Now, let’s move to the next step: [Create the Data Catalog]({{<ref "4-create-datalog/1-create-glue-crawler/_index.md">}}).
