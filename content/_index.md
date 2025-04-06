+++
title = "Data Lake on AWS: Clean Data with Lambda Triggers"
date = 2021
weight = 1
chapter = false
+++

# Data Lake on AWS: Clean Data with Lambda Triggers

#### Overview

This workshop guides you in creating a **Data Lake system on AWS** to **collect, process, clean** and **query data**. We will begin by collecting data from an **API**, uploading it to **S3**, then using **AWS Lambda triggers** to automatically clean the data upon upload. The data will be fed into the **Glue Data Catalog** for analysis with **Athena**, transformed through **Glue Jobs**, and visualized with **QuickSight**.

![Diagram](/images/Datalake.drawio.png?width=90pc)

#### Objectives

- Learn about **Data Lakes**: Help participants understand what a **Data Lake** is, how to build and operate a **Data Lake** on AWS.

- Automate data cleaning processes: Synchronize data uploaded to **S3** and process it immediately using **Lambda** triggers.

- Enhance data analysis skills: Learn about **Glue Data Catalog**, querying with **Athena**, and visualizing with **QuickSight**.

- Independence and flexibility: Build a unified model for various data types, with inputs from **APIs**, **S3**, or **external data**.

#### Requirements:

- **AWS Account:** User with Admin privileges and billing set up.

- **API Data:** Data links will be provided in the workshop.

#### Costs:

- [AWS Free Tier: S3, Lambda, Athena](https://aws.amazon.com/vi/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=*all&awsf.Free%20Tier%20Categories=*all)
- [AWS Glue Job: 0.44$/h for one session](https://aws.amazon.com/vi/glue/pricing/)
- [QuickSight: 30 days free](https://aws.amazon.com/vi/pm/quicksight/?gclid=CjwKCAiAjeW6BhBAEiwAdKltMnYjTIqgPUZFV-osOhJ2zn7Ww25dqqS0yj1NzUwuhCzPW6Wo4vl7jxoCs44QAvD_BwE&trk=4307e550-ebb4-40d7-a036-1a56b1d0ff3f&sc_channel=ps&ef_id=CjwKCAiAjeW6BhBAEiwAdKltMnYjTIqgPUZFV-osOhJ2zn7Ww25dqqS0yj1NzUwuhCzPW6Wo4vl7jxoCs44QAvD_BwE:G:s&s_kwcid=AL!4422!3!651510255273!e!!g!!quicksight%20pricing!19836376477!143940200301)
