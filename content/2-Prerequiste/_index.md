---
title : "Preparation "
date: 2025-07-02
weight : 2
chapter : false
pre : " <b> 2. </b> "
---

{{% notice info %}}
You need to create an Amazon S3 bucket to receive uploaded files, configure an EventBridge rule to capture the upload event, trigger an AWS Lambda function to process the file, and finally publish a notification using Amazon SNS.
{{% /notice %}}

To learn how to create the required AWS services for this pipeline, you can refer to the official AWS documentation:
  - [Amazon S3 – Object Storage](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)
  - [Amazon EventBridge – Event-Driven Architecture](https://docs.aws.amazon.com/eventbridge/latest/userguide/what-is-amazon-eventbridge.html)
  - [AWS Lambda – Serverless Function Compute](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)
  - [Amazon SNS – Notification Service](https://docs.aws.amazon.com/sns/latest/dg/welcome.html)

In order to allow your Lambda function to process S3 events via EventBridge and publish messages to SNS, you need to configure appropriate IAM permissions. In this preparation step, you will also create an IAM Role that grants Lambda permission to read from S3, send messages via SNS, and write logs to CloudWatch.

### Content
  - [Prepare S3 bucket, EventBridge rule, Lambda function and SNS topic](2.1-createec2/)
  - [Create IAM Role](2.2-createiamrole/)
