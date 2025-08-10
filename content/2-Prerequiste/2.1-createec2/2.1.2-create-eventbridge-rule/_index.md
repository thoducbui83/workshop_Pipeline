---
title : "create-eventbridge-rule"
date: 2025-07-02
weight : 2
chapter : false
pre : " <b> 2.1.2 </b> "
---

#### Create EventBridge Rule for S3 Upload Trigger

In this step, we will create an **Amazon EventBridge Rule** to detect when a new object is uploaded to the S3 bucket (e.g. `fcj-upload-pipeline-demo`). Once this rule is triggered, it will invoke the Lambda function to process the file.

---

### 📌 Step 1: Open Amazon EventBridge Console

1. Go to the [Amazon EventBridge Console](https://console.aws.amazon.com/events/home).
2. In the left sidebar, select **Rules**.
3. Click **Create rule**.

![EventBridge](/images/taoRuler.jpg)

---

### 📝 Step 2: Enter Rule Details

1. **Name**: `s3-upload-trigger`
2. **Description**: Trigger Lambda when a file is uploaded to S3
3. **Event bus**: Leave it as **default**

Click **Next**.

---

### 🎯 Step 3: Define Event Pattern

1. Select **Event Source**: **AWS services**
2. **AWS service**: `Simple Storage Service (S3)`
3. **Event type**: `Object Created`
4. **Specific event(s)**: `PutObject` (or leave default if unsure)
5. (Optional) **Bucket name filter**: enter your bucket name, e.g. `fcj-upload-pipeline-demo`

Click **Next**.

![Event Pattern](/images/ruler2.jpg)

---

### ⚙️ Step 4: Add Target

1. **Target type**: AWS service
2. **Select a target**: `Lambda function`
3. **Function**: Select your function name (e.g. `S3UploadEventHandler`)
4. (Optional) Add constant or input transformer, if needed.

Click **Next**.

![Add Target](/images/ruler3.jpg)

---

### ✅ Step 5: Review and Create

1. Review your rule configuration.
2. Click **Create rule** to finish.

![Success](/images/ruler1.jpg)

---

### 🎉 Result

Now, your **EventBridge Rule** is ready.  
When a new file is uploaded to the S3 bucket `fcj-upload-pipeline-demo`, an event will be sent to EventBridge and automatically invoke the corresponding **Lambda function** to process the file.

---