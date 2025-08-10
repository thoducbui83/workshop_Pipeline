---
title : "create-s3-bucket"
date: 2025-07-02
weight : 1
chapter : false
pre : " <b> 2.1.1 </b> "
---

## Create S3 Bucket for Serverless Data Ingestion Pipeline

In this step, you will create an Amazon S3 bucket that serves as the starting point for your serverless event-driven pipeline. When you upload a file to this bucket, it will trigger an event in Amazon EventBridge, which will then invoke a Lambda function to process the data.

### Step 1: Access Amazon S3 Console

1. Navigate to the [Amazon S3 Console](https://console.aws.amazon.com/s3/).
2. Click the **Create bucket** button.

![S3](/workshop_Pipeline/images/taoS3.jpg)

### Step 2: Enter Bucket Details

1. **Bucket name**: Enter a name such as `fcj-upload-pipeline-demo`.
2. **Region**: Choose your preferred AWS Region, e.g., Asia Pacific (Singapore) ap-southeast-1.
3. **Block Public Access**: Ensure **Block all public access** is enabled (default setting).
4. Scroll down and click **Create bucket**.

![S3](/workshop_Pipeline/images/s3TC.jpg)

### Result

- ✅ You have successfully created a bucket that acts as the input source for your serverless pipeline.
- ✅ Any file uploaded to this bucket will generate an S3 Event.
- ✅ In the next steps, we will configure EventBridge Rules to listen to S3 events and trigger AWS Lambda for data processing.
