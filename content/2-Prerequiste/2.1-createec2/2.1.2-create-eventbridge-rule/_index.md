---
title : "create-eventbridge-rule"
date: 2025-07-02
weight : 1
chapter : false
pre : " <b> 2.1.2 </b> "
---

## Create EventBridge Rule for S3 Events

In this step, you will create an Amazon EventBridge rule that listens for S3 object creation events and triggers your Lambda function when files are uploaded to your S3 bucket.

### Step 1: Access Amazon EventBridge Console

1. Navigate to the [Amazon EventBridge Console](https://console.aws.amazon.com/events/).
2. Click **Rules** in the left sidebar.
3. Click **Create rule**.

![EventBridge](/workshop_Pipeline/images/taoRuler.jpg)

### Step 2: Configure Rule Details

1. **Name**: Enter a descriptive name like `s3-upload-trigger`.
2. **Description**: "Rule to trigger Lambda when files are uploaded to S3".
3. **Event bus**: Select **default**.
4. **Rule type**: Select **Rule with an event pattern**.

### Step 3: Define Event Pattern

1. **Event source**: Select **AWS services**.
2. **AWS service**: Select **Simple Storage Service (S3)**.
3. **Event type**: Select **Object Level Operations**.
4. **Specific event(s)**: Select **Object Created**.
5. **Specific operation(s)**: Select **Put**, **Post**, **Copy**, **CompleteMultipartUpload**.

![Event Pattern](/workshop_Pipeline/images/ruler2.jpg)

### Step 4: Configure Target

1. **Target types**: Select **AWS service**.
2. **Target**: Select **Lambda function**.
3. **Function**: Select your Lambda function from the dropdown.
4. Click **Add target**.

![Add Target](/workshop_Pipeline/images/ruler3.jpg)

### Step 5: Create Rule

1. Review your configuration.
2. Click **Create rule**.

![Success](/workshop_Pipeline/images/ruler1.jpg)

### Result

- ✅ Your EventBridge rule is now configured to listen for S3 upload events.
- ✅ When a file is uploaded to your S3 bucket, EventBridge will automatically trigger your Lambda function.
- ✅ The serverless pipeline is now event-driven and will process data automatically.