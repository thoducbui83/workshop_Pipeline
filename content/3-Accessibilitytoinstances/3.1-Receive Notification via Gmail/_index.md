---
title : "Receive Notification via Gmail"
date: 2025-07-02
weight : 1
chapter : false
pre : " <b> 3.1. </b> "
---

#### Receive notifications via email (Gmail) when a file is uploaded to S3

After configuring an SNS topic to send notifications upon new file uploads to your S3 bucket, you will receive emails like the one below in your **Primary** inbox on Gmail.

📧 **Example emails received:**

- **S3 File Upload Notification**: Notifies you that a new file (e.g., `abc.csv`) has been uploaded to the bucket `s3-upload-notifier-store`.
- **SNS Subscription Confirmation**: An email asking you to confirm your subscription to the SNS topic.

🖼️ **Gmail interface:**

![SNS Gmail Notification](images/Picture2.png)

![SNS Gmail Notification](images/gmal.jpg)


{{% notice note %}}
If you do not receive the email, check the **Promotions** or **Spam** folders. Also make sure you have confirmed your subscription by clicking the link in the "Subscription Confirmation" email.
{{% /notice %}}
