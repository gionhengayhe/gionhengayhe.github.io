+++
title = "Visualize with QuickSight"
date = 2020
weight = 2
chapter = false
pre = "<b>6.2 </b>"
+++

#### Visualize with QuickSight

In this step, we will perform visualization using QuickSight.

1. Log in to the Amazon QuickSight Console and complete the registration process. You can refer to the registration process [here](https://000070.awsstudygroup.com/6-quicksight/6.1-registerquicksight/).
2. Access the [AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)

   - Find **QuickSight**
   - Select **QuickSight**
     ![](/images/6/2/1.png)

   > **Note**: Pay attention to the Region you are using. Check and switch the Region if necessary to avoid errors.

   ![](/images/6/2/2.png)

3. In the **QuickSight** interface, select **Manage QuickSight**
   ![](/images/6/2/3.png)
4. Configure **Permissions**
   - Select **Security & permissions**
   - Select **Manage**
     ![](/images/6/2/4.png)
5. Select the services and choose **Amazon S3**

   - Select **S3 Buckets Linked To QuickSight Account**
   - Choose **datalake-bucket-demo**
   - Select **Finish**
     ![](/images/6/2/5.png)

6. Select and review the Role and services. Then, select **Save**
   ![](/images/6/2/6.png)
7. In the **QuickSight** interface:

   - Select **Datasets**
   - Select **New dataset**
     ![](/images/6/2/7.png)

8. In the **Create dataset** interface:

   - Choose the source from **Athena**
     ![](/images/6/2/8.png)

9. Configure the data source:

   - **Data source name**, enter `summitdemo`
   - Choose **Validate Connection**. If the connection is successful, it will display SSL is enabled
   - Select **Create data source**
     ![](/images/6/2/9.png)

10. Choose a Table:
    - **Catalog**, select **AWSDataCatalog**
    - **Database**, enter `summitdb`
    - **Table**, select **processed_data**
    - Select **Select**
      ![](/images/6/2/14.png)
11. In the **Finish dataset creation** step:
    - Select **Directly query your data**
    - Select **Visualize**
      ![](/images/6/2/15.png)
    - Select **Create**
      ![](/images/6/2/16.png)
12. Use **Amazon QuickSight** to visualize the transformed data:  
    **Count comments each post**

    - Click on **Pie Chart**
    - Group/color: **postid**
    - Value: **commentid(Count)**

    ![](/images/6/2/17.png)

    **Count post each user**

    - Group/color: **postuserid**
    - Value: **postid(Count)**
      ![](/images/6/2/18.png)

13. If you meet error like
    ![](/images/6/2/10.png)
    or
    ![](/images/6/2/10.1.png)
    - Go to **IAM Role Console**
    - Find **aws-quicksight-service-role-...**
      ![](/images/6/2/11.png)
    - Click **Add Permissions**
    - Click **Attach policies**
      ![](/images/6/2/12.png)
    - Search for **Quicksight** and choose these policies:
      ![](/images/6/2/13.png)
