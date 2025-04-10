+++
title = "Tạo Lambda function"
date = 2020
weight = 2
chapter = false
pre = "<b>3.2. </b>"
+++

## Tạo Lambda function

### Tạo Lambda function cho dữ liệu bài đăng

1.  Truy cập [AWS Management Console](https://us-east-1.console.aws.amazon.com/console/home?region=us-east-1)

    - Tìm kiếm **Lambda**
    - Chọn **Lambda**
      ![](/images/3/2/1.png)

2.  Chọn **Create a function**
    ![](/images/3/2/2.png)

3.  Tại function name: `Clean-PostData`
4.  Tại runtime, chọn **Python 3.13**
    ![](/images/3/2/3.png)
5.  Thay đổi execution role mặc định, chọn **Use an existing role**
6.  Chọn **AWSLambdaRoleDefault**
7.  Nhấp vào **Create function**
    ![](/images/3/2/4.png)

8.  Thêm mã này

```
import json
import boto3

def lambda_handler(event, context):
try:
bucket_name = event['detail']['bucket']['name']
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

cleaned_file_key = file_key.replace('raw-data/post', 'cleaned-data/post')
cleaned_file_content = "\n".join(json.dumps(post) for post in cleaned_data)

s3.put_object(Bucket=bucket_name, Key=cleaned_file_key, Body=cleaned_file_content)
print(f"Cleaned data uploaded to :s3://{bucket_name}/{cleaned_file_key}")

except Exception as e:
print(f"Error processing file {file_key}: {e}")
raise e
```

{{% notice note %}}

Vì AWS Glue không thể diễn giải JSON Array như JSON Objects để ánh xạ lược đồ, chúng ta cần chuyển đổi dữ liệu thành định dạng JSON Object.  
Mã này sẽ kiểm tra dữ liệu đến, và nếu dòng dữ liệu không ở định dạng chính xác, nó sẽ bỏ qua dữ liệu đó.  
`userId` phải là số nguyên.  
`id` phải là số nguyên.  
`title` phải là một chuỗi.  
`body` phải là một chuỗi.

{{% /notice %}}

1. Nhấp vào **Deploy(Ctrl+Shift+U)**
   ![](/images/3/2/5.png)

### Tạo Lambda function cho dữ liệu bình luận

1. Tương tự như **Tạo Lambda function cho dữ liệu bài đăng**, tạo một **Lambda Function** `Clean-CommentData`

2. Sử dụng mã này:

```
import json
import boto3

def lambda_handler(event, context):
   try:
	bucket_name = event['detail']['bucket']['name']
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

	cleaned_file_key = file_key.replace('raw-data/comment', 'cleaned-data/comment')
	cleaned_file_content = "\n".join(json.dumps(comment) for post in cleaned_data)

	s3.put_object(Bucket=bucket_name, Key=cleaned_file_key, Body=cleaned_file_content)
	print(f"Cleaned data uploaded to :s3://{bucket_name}/{cleaned_file_key}")

   except Exception as e:
	print(f"Error processing file {file_key}: {e}")
	raise e
```
