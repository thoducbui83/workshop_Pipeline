---
title : "Receive Notification via Gmail"
date: 2025-07-02
weight : 1
chapter : false
pre : " <b> 3.1. </b> "
---

#### Nhận thông báo khi upload file vào S3 qua email (Gmail)

Sau khi bạn cấu hình SNS topic để gửi thông báo khi có file mới được upload lên bucket S3, bạn sẽ nhận được email như bên dưới trong hộp thư **Primary** của Gmail.

📧 **Ví dụ email nhận được:**

- **S3 File Upload Notification**: Thông báo có file mới (ví dụ: `abc.csv`) được upload lên bucket `s3-upload-notifier-store`.
- **SNS Subscription Confirmation**: Email yêu cầu xác nhận bạn đã đăng ký nhận thông báo từ SNS topic.

🖼️ **Giao diện Gmail:**

![SNS Gmail Notification](images/Picture2.png)

![SNS Gmail Notification](images/gmal.jpg)

{{% notice note %}}
Nếu bạn không nhận được email, hãy kiểm tra cả hộp thư **Promotions** và **Spam**. Đồng thời đảm bảo đã xác nhận đăng ký trong email "Subscription Confirmation".
{{% /notice %}}
