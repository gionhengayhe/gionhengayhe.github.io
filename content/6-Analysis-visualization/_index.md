+++
title = "Analysis and visualization"
date = 2020
weight = 6
chapter = false
pre = "<b>6. </b>"
+++

#### Analysis and visualization

#### Amazon Athena Overview

**Amazon Athena** an interactive query service used to analyze data in Amazon S3 with standard SQL. We simply point to your data in Amazon S3, define the schema and start querying with the built-in query editor. Amazon Athena allows us to mine all of our data in Amazon S3 without having to set up complex ETL processes. Amazon Athena charges based on queries run.

**Amazon Athena** uses Presto with ANSI SQL support and works with many standard data formats, including CSV, JSON, ORC, Avro , and Parquet. Athena is recommended for fast querying needs, but it can also handle complex analysis, including large joins, window functions, and arrays.
![Athena](/images/1/athena.png?width=10pc)

#### Amazon QuickSight Overview

**Amazon Quick Sight** a data representation service fully managed by AWS.
![QuickSight](/images/1/quicksight.jpeg?width=10pc)

- **Data source** is an external data repository, and you need to configure how to access data in this external repository, e.g., Amazon S3, Amazon Athena, Salesforce, etc.

- **Dataset** defines the specific data within the Data source you want to use. For example, the Data source could be a table if you are connecting to a database Data source. It could be a file if you are connecting to an Amazon S3 Data source.

- **Analysis** contains a collection of Visuals and stories relevant, for instance, to a specific business objective or KPI.

- **Visual** is a graphical representation of your data. You can create different types of Visuals within an analysis, using different datasets and Visual types.

- **Dashboard** is a page that includes one or more Analyses for viewing only, which you can share with other Amazon QuickSight users for reporting purposes. The Dashboard retains the configuration of the Analysis at the time you publish it, including things like filters, parameters, controls, and sorting order.

#### Content

1. [Data Analysis with Athena](../6-Analysis-visualization/1-analysis-athena/_index.md)
2. [Visualize with AWS QuickSight](../6-Analysis-visualization/2-visualize-quicksight/_index.md)
