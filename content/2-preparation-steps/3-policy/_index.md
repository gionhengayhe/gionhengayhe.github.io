+++
title = "Create Policy"
date = 2020
weight = 2
chapter = false
pre = "<b>2.3 </b>"
+++

## Create Policy

1. Access AWS Management Console
   - First, you need to access the AWS Management Console at https://aws.amazon.com/console/.
2. Log in to your AWS account
   - Log in to your AWS account using your username and password.
3. Open the IAM (Identity and Access Management) page
   - After logging in successfully, select the “IAM” service by searching for it in the search bar or finding it in the list of services.
4. Create a Policy

   - In the IAM interface, select “Policies” from the left menu. Click on the “Create policy” button to start creating a new policy.

5. Paste JSON Policy

   - On the “Create policy” page, choose the “JSON” section and paste the JSON policy content you have provided above into the text box.
   - Ensure that the JSON policy is marked as valid and free of syntax errors.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "iam:PassRole",
            "Resource": "arn:aws:iam::AccountID:role/AWSGlueServiceRoleDefault"
        }
    ]
}
```

6. Name the Policy

   - Next, you need to name the policy. Enter the name in the “Name” field.
   - Provide a description (optional) for the policy if you wish.

7. Review and Create Policy

   - Click the “Review policy” button to review your policy information.
   - After a thorough review, if there are no errors, click the “Create policy” button to create the new policy.

8. Attach Policy to AWSGlueServiceRoleDefault

   - Once the policy has been successfully created, you need to attach it to the AWSGlueServiceRoleDefault role.
   - Select “Roles” from the left-hand menu in the IAM interface.
   - Find and select the “AWSGlueServiceRoleDefault” role.
   - On the role details page, select the “Permissions” tab and then click the “Add inline policy” button.
   - On the “Create policy” page, search for and select the policy you just created.
   - Click the “Next: Review policy” button to review again.
   - After reviewing and ensuring there are no errors, click the “Create policy” button to attach the policy to the role.

```

```
