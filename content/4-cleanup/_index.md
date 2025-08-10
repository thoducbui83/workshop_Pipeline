+++
title = "Clean up resources"
date = 2025-07-02
weight = 6
chapter = false
pre = "<b>6. </b>"
+++

We will now clean up all the AWS resources that were provisioned as part of the **Serverless Data Ingestion & Processing Pipeline** project.

---

### 🗑️ Delete Lambda Function

1. Go to [AWS Lambda Console](https://console.aws.amazon.com/lambda/home)
   + Select the **Lambda function** created for this project (e.g., `event-processing-function`).
   + Click **Actions** → **Delete**.
   + Confirm deletion by typing the function name.

---

### 🗑️ Delete EventBridge Rule

1. Go to [Amazon EventBridge Console](https://console.aws.amazon.com/events/home)
   + Click **Rules** on the left panel.
   + Select the **rule** created for S3 trigger (e.g., `S3UploadEventRule`).
   + Click **Actions** → **Delete** → Confirm.

---

### 🗑️ Delete SNS Topic

1. Go to [Amazon SNS Console](https://console.aws.amazon.com/sns/v3/home)
   + Select the **SNS Topic** used to publish processed events.
   + Click **Actions** → **Delete topic** → Confirm deletion.

---

### 🗑️ Delete IAM Role

1. Go to [IAM Management Console](https://console.aws.amazon.com/iam/)
   + Click **Roles**.
   + Search for `lambda-pipeline-role`.
   + Click the role name.
   + Click **Delete**, then type the role name to confirm.

---

### 🗑️ Empty and Delete S3 Bucket

1. Go to [Amazon S3 Console](https://s3.console.aws.amazon.com/s3/)
   + Click on the bucket you created (e.g., `fcj-serverless-pipeline-bucket`).
   + Go to **Empty bucket**, enter `permanently delete`, and click **Empty** to clear all objects.
   + Then click **Delete bucket**.
   + Confirm by typing the bucket name → Click **Delete**.

---

### ✅ Optional: Delete CloudWatch Log Groups

1. Go to [CloudWatch Console](https://console.aws.amazon.com/cloudwatch/)
   + Click **Log groups** in the left panel.
   + Locate the log groups for your Lambda function.
   + Select the log group(s) → Click **Actions** → **Delete log group** → Confirm.

---

### ✅ Summary

At this point, you have:
- Deleted all serverless components (Lambda, EventBridge rule, SNS, IAM Role, S3 Bucket).
- Removed residual logs to save cost.
- Cleaned up the environment to prevent unintended charges.

> 🧼 Performing clean-up is good practice to avoid incurring extra cost and keeping your AWS account organized.

---
