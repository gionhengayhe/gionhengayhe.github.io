+++
title = "Creating an Glue Service Role"
date = 2020
weight = 1
chapter = false
pre = "<b>2.1 </b>"
+++

## Creating an Glue Service Role

In this step, we will navigate to the IAM Console and create a role for the Glue service. This role will allow AWS Glue to access data in S3 and create necessary objects in the Glue Catalog.

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
    - For **Use case**, select **Glue**
    - Click **Next**
    - ![](/images/2/0003-createiamrole.png)

4.  In the **Add permission**s step:

    - Search for the **AmazonS3FullAccess** policy
    - Select the **AmazonS3FullAccess** policy
    - Click Next
    - ![](/images/2/0004-createiamrole.png)

5.  Similar to step 4:

    - Look for the **AWSGlueServiceRole** policy
    - Select the **AWSGlueServiceRole** policy
    - ![](/images/2/0005-createiamrole.png)

6.  In the **Role details** interface:
    - For **Role name**, enter `AWSGlueServiceRoleDefault`
    - ![](/images/2/0006-createiamrole.png)
7.  In the **Add permissions** step:
    - Review the two policies
    - Click **Create role**
    - ![](/images/2/0007-createiamrole.png)
8.  We have now completed creating the IAM role
    - ![](/images/2/0008-createiamrole.png)
