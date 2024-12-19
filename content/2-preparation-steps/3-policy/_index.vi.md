+++
title = "Tạo Policy"
date = 2020
weight = 3
chapter = false
pre = "<b>2.3 </b>"
+++

## Tạo Policy

1. Truy cập AWS Management Console

   - Trước tiên, bạn cần truy cập AWS Management Console tại https://aws.amazon.com/console/.

2. Đăng nhập vào tài khoản AWS

   - Đăng nhập vào tài khoản AWS của bạn bằng tên đăng nhập và mật khẩu.

3. Mở trang IAM (Identity and Access Management)
   - Sau khi đăng nhập thành công, chọn dịch vụ “IAM” bằng cách tìm kiếm nó trong thanh tìm kiếm hoặc tìm trong danh sách các dịch vụ.
4. Tạo một Policy
   - Trong giao diện IAM, chọn “Policies” ở menu bên trái. Bấm vào nút “Create policy” để tạo một policy mới.
5. Paste JSON Policy
   - Trong trang “Create policy”, chọn phần “JSON” và dán nội dung JSON policy bạn đã cung cấp ở trên vào ô văn bản.
   - Đảm bảo rằng JSON policy đã được đánh dấu là hợp lệ và không có lỗi cú pháp.

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

6. Đặt tên cho Policy
   - Tiếp theo, bạn cần đặt tên cho policy. Điền tên vào trường “Name”.
   - Cung cấp mô tả (tùy chọn) cho policy nếu bạn muốn.
7. Kiểm tra và tạo Policy
   - Bấm vào nút “Review policy” để kiểm tra lại thông tin policy của bạn.
   - Sau khi kiểm tra kỹ, nếu không có lỗi, hãy bấm vào nút “Create policy” để tạo policy mới.
8. Đính kèm Policy vào AWSGlueServiceRoleDefault
   - Sau khi policy được tạo thành công, bạn cần đính kèm nó vào role AWSGlueServiceRoleDefault.
   - Chọn “Roles” ở menu bên trái trong giao diện IAM.
   - Tìm và chọn role “AWSGlueServiceRoleDefault”.
   - Trong trang chi tiết của role, chọn tab “Permissions” và sau đó bấm vào nút “Add inline policy”.
   - Trong trang “Create policy”, tìm kiếm và chọn policy bạn vừa tạo.
   - Bấm vào nút “Next: Review policy” để kiểm tra lại.
   - Sau khi kiểm tra và không có lỗi, hãy bấm vào nút “Create policy” để đính kèm policy vào role.
