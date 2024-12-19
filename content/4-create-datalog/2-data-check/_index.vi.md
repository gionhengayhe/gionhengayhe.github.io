+++
title = "Data check"
date = 2020
weight = 2
chapter = false
pre = "<b>4.2 </b>"
+++

### Data check

1. Go to the [AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)

   - Find **S3**
   - Select **S3**
     ![](/images/3/1/0001-creates3bucket.png)

2. In the **S3** interface

   - Select **Buckets**
   - Select **datalake-bucket-demo**

3. We will create a folder for **Athena**
   - Select **Create folder**
     ![](/images/4/2/3.png)
4. In the **Create folder** interface
   - Folder name, enter **Athena**
   - Select **Create folder**
     ![](/images/4/2/4.png)
5. Successfully created folder
6. Go to the [AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)
   - Find **Athena**
   - Select **Athena**
     ![](/images/4/2/1.png)
7. In the **Athena** interface

   - Select **View settings** to set the path to store query results
     ![](/images/4/2/5.png)

8. In the **Amazon Athena** interface
   - Select **Settings**
   - Select **Manage**
     ![](/images/4/2/6.png)
9. Select the path to the newly created Athena folder, then select Choose
10. Return to Manage settings interface, check again and select Save
    ![](/images/4/2/7.png)
11. We use **Amazon Athena** to query data

    - Data Source, select **AwsDataCatalog**
    - Database, select **summitdb**
    - Select **comment** table
    - Select **Preview** Table
      ![](/images/4/2/2.png)

12. Make a query of 10 rows of data from the **comment** table in the database summitdb
    - Query successful
    - Test data
      ![](/images/4/2/8.png)
13. Checking data of **comment** table where postid = 10
    ![](/images/4/2/9.png)
    ![](/images/4/2/10.png)

14. Checking data of **post** table limit 10;
    ![](/images/4/2/11.png)
    ![](/images/4/2/12.png)
15. Table **comment** join table **post**
    ![](/images/4/2/13.png)
    ![](/images/4/2/14.png)
