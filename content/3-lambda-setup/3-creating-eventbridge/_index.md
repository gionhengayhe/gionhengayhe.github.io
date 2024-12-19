+++
title = "Setup EventBridge and S3 Trigger"
date = 2020
weight = 3
chapter = false
pre = "<b>3.3 </b>"
+++

## Creating EventBridge

1.  Access the [AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)

    - Search for **EventBridge**
    - Select **Amazon EventBridge**
      ![](/images/3/3/4.png)

2.  At the **Amazon EventBridge Console**, choose **Create Rule**
    ![](/images/3/3/5.png)
3.  - At name: `TriggerCommentData`
    - Click **Next**
      ![](/images/3/3/6.png)
4.  - At creation method, choose **Custom pattern**
    - At event pattern:
      ```
      {
        "source": ["aws.s3"],
        "detail-type": ["Object Created"],
        "detail":{
            "bucket":{
                "name": ["datalake-bucket-demo"]
            },
            "object":{
                "key":[{
                    "prefix": "raw-data/comment"
                }]
            }
        }
      }
      ```
    - Click **Next**
      ![](/images/3/3/7.png)

5.  - At Select a target: **Lambda function**
    - Function: **Clean-CommentData**
    - Click **Next**
      ![](/images/3/3/8.png)
6.  Review rule, click **Create rule**
    ![](/images/3/3/9.png)
7.  - Similar to Step **2-6**, Create `TriggerPostData` rule
    - Using this pattern:

      ```
      {
        "source": ["aws.s3"],
        "detail-type": ["Object Created"],
        "detail":{
            "bucket":{
                "name": ["datalake-bucket-demo"]
            },
            "object":{
                "key":[{
                    "prefix": "raw-data/post"
                }]
            }
        }
      }
      ```

8.  After create **TriggerPostData** rule, we will have:
    ![](/images/3/3/10.png)
9.  Comeback to the **Clean-PostData and Clean-CommentData Lambda Function**, you will see:
    ![](/images/3/3/11.png)
    ![](/images/3/3/12.png)

## Setup send notifications to EventBridge for all events in S3

1.  Open the **S3 datalake-bucket-demo** console, Click **Properties**
    ![](/images/3/3/1.png)
2.  At Amazon EventBridge, click **Edit**
    ![](/images/3/3/2.png)
3.  Turn on **Send notifications to EventBridge for all events in this bucket**, then click **Save changes**
    ![](/images/3/3/3.png)
    Congratulations, you've successfully created a **trigger** to activate **Lambda** when listening to the **S3** upload event with **EventBridge**. Now we'll move on to the next step: **Uploading data and viewing the results**.
