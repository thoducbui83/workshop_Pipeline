---
title : "create-lambda-function"
date: 2025-07-02
weight : 3
chapter : false
pre : " <b> 2.1.3 </b> "
---

#### Create a Lambda Function to Handle S3 Upload Events

In this step, we will create an **AWS Lambda function** that is triggered by S3 upload events ("ObjectCreated"), sent through Amazon EventBridge.

---

### 📝 Step 1: Access the AWS Lambda Console

1. Go to the [AWS Lambda Console](https://console.aws.amazon.com/lambda/home).
2. Click **Create function**.

---

### ⚙️ Step 2: Configure the Lambda Function

1. Select **Author from scratch**
2. **Function name**: `S3UploadEventHandler`
3. **Runtime**: `Node.js 18.x` (or latest available)
4. **Permissions**:
   + Choose **Create a new role with basic Lambda permissions**
   + Later, update the role to include policies like:
     - `AmazonS3ReadOnlyAccess`
     - `CloudWatchLogsFullAccess`
     - `AmazonSNSFullAccess` (if needed)

Click **Create function**.

![Lambda Create](/workshop_Pipeline/images/lamda1.jpg)

---

### 🧠 Step 3: Add the Handler Code

In the **Function code** section, replace the default code with the following:

```javascript
exports.handler = async (event) => {
    console.log("Event Received: ", JSON.stringify(event));

    const record = event.Records?.[0];
    const bucket = record?.s3?.bucket?.name;
    const key = record?.s3?.object?.key;

    console.log(`File uploaded: ${key} in bucket: ${bucket}`);

    // TODO: Add your logic here (e.g., validate file, send notification, store metadata)

    return {
        statusCode: 200,
        body: JSON.stringify({ message: 'File processed successfully.' })
    };
};

```
