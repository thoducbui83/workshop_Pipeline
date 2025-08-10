---
title : "create-sns-topic"
date: 2025-07-02
weight : 4
chapter : false
pre : " <b> 2.1.4 </b> "
---

#### Create an Amazon SNS Topic

In this step, we will **create an SNS Topic** which will be used by the Lambda function to **send notification messages** whenever a file is uploaded to Amazon S3 and processed via EventBridge and Lambda.

---

### 📝 Step 1: Access the SNS Management Console

1. Go to the [Amazon SNS Console](https://console.aws.amazon.com/sns/v3/home).
2. In the left menu, click **Topics**.
3. Click **Create topic**.

---

### ⚙️ Step 2: Configure the SNS Topic

1. **Topic type**: Standard  
2. **Name**: `s3-upload-events-topic`  
3. Leave all other settings default unless specified by your use case.
4. Click **Create topic**.

![SNS Topic](images/sns1.jpg)

---

### 📥 Step 3: Create a Subscription (Optional, for testing)

1. In the topic details page, scroll down to **Subscriptions**.
2. Click **Create subscription**.
3. **Protocol**: Email  
4. **Endpoint**: Enter your email address to receive notifications (e.g., `example@gmail.com`)
5. Click **Create subscription**.

> You’ll receive a confirmation email. Click the confirmation link to activate the subscription.

---

### 🔄 Step 4: Grant SNS Publish Permissions to Lambda Function

To allow your Lambda function to publish messages to SNS, ensure it has the following permission:

- Go to **IAM > Roles**
- Locate the execution role used by your Lambda function
- Attach policy: `AmazonSNSFullAccess`  
> (For production, you should create a custom policy with limited SNS topic access)

---

### ✅ Final Outcome

- You now have an SNS topic `s3-upload-events-topic` that can be used to **notify users** or systems when a file is uploaded to S3.
- This will be invoked **from your Lambda function**, forming the final notification layer in your **event-driven pipeline**.

---

