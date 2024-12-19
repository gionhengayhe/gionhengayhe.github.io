+++
title = "Create Lambda function"
date = 2020
weight = 2
chapter = false
pre = "<b>3.2. </b>"
+++

## Creating lambda function

### Creating lambda function for post data

1.  Access the [AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)

    - Search for **Lambda**
    - Select **Lambda**
      ![](/images/3/2/1.png)

2.  Choose **Create a function**
    ![](/images/3/2/2.png)

3.  At function name: `Clean-PostData`
4.  At runtime, choose **Python 3.13**
    ![](/images/3/2/3.png)
5.  Change default execution role, choose **Use an existing role**
6.  Choose **AWSLambdaRoleDefault**
7.  Click **Create function**
    ![](/images/3/2/4.png)

8.  Add this code

```
import json
import boto3

def lambda_handler(event, context):
try:
bucket_name = event['detail]['bucket']['name']
file_key = event['detail']['object']['key']

response = s3.get_object(Bucket=bucket_name, Key=file_key)
raw_data = response['Body'].read().decode('utf-8')

posts = json.loads(raw_data)

cleaned_data = []
for post in posts:
   if (isinstance(post.get('userId'), int) and
   isinstance(post.get('id'), int) and
   isinstance(post.get('title'), str) and
   isinstance(post.get('body'), str) and
   cleaned_data.append(post))

cleaned_file_key = file_key.replace('raw-data/post', 'cleaned-data'/post)
cleaned_file_content = "\n".join(json.dumps(post) for post in cleaned_data)

s3.put_object(Bucket=bucket_name, Key=cleaned_file_key, Body=cleaned_file_content)
print(f"Cleaned data uploaded to :s3://{bucket_name}/{cleaned_file_key}")

except Exception as e:
print(f"Error processing file {file_key}: {e}")
raise e
```

{{% notice note %}}

Because AWS Glue cannot interpret JSON Array as JSON Objects for schema mapping, we need to convert the data into JSON Object format.  
This code will check the incoming data, and if the data line is not in the correct format, it will skip that data.  
`userId` must be an integer.  
`id` must be an integer.  
`title` must be a string.  
`body` must be a string.

{{% /notice %}}

1. Click **Deploy(Ctrl+Shift+U)**
   ![](/images/3/2/5.png)

### Creating lambda function for comment data

1. Simirlar to **Creating lambda function for post data**, create a **Lambda Function** `Clean-CommentData`

2. Using this code:

```
import json
import boto3

def lambda_handler(event, context):
   try:
	bucket_name = event['detail]['bucket']['name']
	file_key = event['detail']['object']['key']

	response = s3.get_object(Bucket=bucket_name, Key=file_key)
	raw_data = response['Body'].read().decode('utf-8')

	comments = json.loads(raw_data)

	cleaned_data = []
	for comment in comments:
	    if (isinstance(post.get('postId'), int) and
		  isinstance(post.get('id'), int) and
		  isinstance(post.get('name'), str) and
      isinstance(post.get('email'), str) and
		  isinstance(post.get('body'), str) and
		  cleaned_data.append(post))

	cleaned_file_key = file_key.replace('raw-data/comment', 'cleaned-data'/comment)
	cleaned_file_content = "\n".join(json.dumps(comment) for post in cleaned_data)

	s3.put_object(Bucket=bucket_name, Key=cleaned_file_key, Body=cleaned_file_content)
	print(f"Cleaned data uploaded to :s3://{bucket_name}/{cleaned_file_key}")

   except Exception as e:
	print(f"Error processing file {file_key}: {e}")
	raise e
```
