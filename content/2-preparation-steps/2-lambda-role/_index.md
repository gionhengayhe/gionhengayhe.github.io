+++
title = "Create Lambda role"
date = 2020
weight = 2
chapter = false
pre = "<b>2.2 </b>"
+++

## Creating an Glue Service Role

In this step, we will navigate to the IAM Console and create a role for the Lambda function service. This role will allow Lambda function to access data in S3, clean data and and create necessary objects in the Lambda Catalog.

1.  Access the [AWS Management Console]()

    - Search for **IAM**
    - Select **IAM**
      ![Step1](/images/2/0001-createiamrole.png)

2.  In the **IAM** console:

    - Select **Roles**
    - Choose **Create role**
      ![](/images/2/0002-createiamrole.png)

3.  In the **Select trusted entity** step:

    - Choose **AWS Service**
    - For **Use case**, select **Lambda**
    - Click **Next**
    - ![](/images/2/2/3.png)

4.  In the **Add permission**s step:

    - Search for the **AmazonS3FullAccess** policy
    - Select the **AmazonS3FullAccess** policy
    - Click Next
    - ![](/images/2/0004-createiamrole.png)

5.  Similar to step 4:

    - Look for the **AWSLambda_FullAccess** policy
    - Select the **AWSLambda_FullAccess** policy
    - ![](/images/2/2/5.png)
    -
    - Look for the **AWSLambdaBasicExecutionRole** policy
    - Select the **AWSLambdaBasicExecutionRole** policy
    - ![](/images/2/2/6.png)

6.  In the **Role details** interface:
    - For **Role name**, enter `AWSLambdaRoleDefault`
    - ![](/images/2/2/7.png)
7.  In the **Add permissions** step:
    - Review the three policies
    - Click **Create role**
8.  We have now completed creating the IAM role
    - ![](/images/2/2/8.png)
