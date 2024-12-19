+++
title = "Create AWS Glue Crawler"
date = 2020
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

### Create Glue Crawler

1. Access the [AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)
   - Find **AWS Glue**.
   - Select **AWS Glue**.
     ![](/images/4/1/1.png)
2. In the **AWS Glue** interface, select **Crawlers**.
3. Choose Create Crawler.
   ![](/images/4/1/2.png)
4. In the **Add Crawler** interface, enter **Crawler name** as `summitcrawler` and select **Next**.
   ![](/images/4/1/3.png)
5. For Add data source, select S3.
6. Choose **S3** path through **Browse**. Choose: **datalate-bucket-demo/cleaned-data**. Also, select **Crawl new sub-folders only** and **Add an S3 data source**.
7. After adding the data source, select **Next**.
   ![](/images/4/1/4.png)
8. For **IAM role**, choose **AWSGlueServiceDefault**. Then, select **Next**.
   ![](/images/4/1/5.png)
9. For **Target database**, perform **Add database**.
   ![](/images/4/1/6.png)
10. Create a database by entering the database name as `summitdb` and selecting **Create database**.
    ![](/images/4/1/7.png)
11. After creating the database, select the database and choose **Next**.
    ![](/images/4/1/9.png)
12. Review the configuration and select **Create crawler**.
    ![](/images/4/1/10.png)
13. Crawler creation successful. Then, choose **Run crawler**.
    ![](/images/4/1/11.png)
14. It takes about 2-3 minutes to run the crawler.
15. When you see the crawler status as **Ready**.
    ![](/images/4/1/12.png)
16. In the **AWS Glue** interface, select **Table**, and you will see 2 data tables.
    ![](/images/4/1/13.png)
17. Select the **post** data table.
    ![](/images/4/1/14.png)
18. Select the **comment** data table.
    ![](/images/4/1/14.png)
19. Explore the details of the data table.
