---
title : "create-iam-role"
date: 2025-07-02
weight : 5
chapter : false
pre : " <b> 2.1.5 </b> "
---

#### Create IAM Role for Lambda and Services Integration

In a serverless data ingestion and processing pipeline, services such as Amazon S3, Lambda, and EventBridge need appropriate permissions to **access resources, send/receive events, and process data**. This step walks you through creating an IAM Role that allows Lambda to interact securely with other AWS services.

---

### 🛠️ Step 1: Access IAM Console

1. Go to the [IAM Management Console](https://console.aws.amazon.com/iam/).
2. In the left sidebar, select **Roles**.
3. Click **Create role**.

---

### 📥 Step 2: Select Trusted Entity Type

1. On the **Select trusted entity type** page:
   + Choose **AWS service**.
   + Choose **Lambda** (or the service you want to assign this role to).
   + Click **Next**.

---

### 🔐 Step 3: Attach Permissions Policies

1. Search and attach the following AWS managed policies:
   + `AmazonS3FullAccess`
   + `AmazonSNSFullAccess`
   + `CloudWatchLogsFullAccess`
   + `AmazonEventBridgeFullAccess`

> 💡 In a real-world deployment, it's recommended to use custom policies with least-privilege access specific to your resources.

2. Click **Next**.

---

### 📝 Step 4: Name and Describe the IAM Role

1. Under **Role name**, enter: `lambda-pipeline-role`
2. Description: `Role that allows Lambda to access S3, SNS, EventBridge, and CloudWatch`
3. Click **Create role** to finish.

![IAM Role](/workshop_Pipeline/images/iam.jpg)

---

### ✅ Final Result

- The `lambda-pipeline-role` is now ready to be attached to the **main Lambda function in your pipeline**.
- This role enables Lambda to:
   + Retrieve files from S3
   + Publish events to SNS
   + Write logs to CloudWatch
   + React to rules from EventBridge

![IAM Role](/workshop_Pipeline/images/iam1.jpg)

![IAM Role](/workshop_Pipeline/images/iam2.jpg)
---

