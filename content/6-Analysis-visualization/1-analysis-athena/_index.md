+++
title = "Analysis with Athena"
date = 2020
weight = 1
chapter = false
pre = "<b>6.1 </b>"
+++

#### Analysis with Athena

As Athena uses the AWS Glue Catalog to track data sources, all tables in Glue can be queried through Athena.

1. Go to the [AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)

   - Find **Athena**
   - Select **Athena**
     ![](/images/4/2/1.png)

2. In the **Athena** interface:
   - Data Source, select **AwsDataCatalog**
   - Database, select **summitdb**
   - Select **processed-data** table
   - Select **Preview** Table
     ![](/images/6/1/1.png)
     ![](/images/6/1/2.png)
