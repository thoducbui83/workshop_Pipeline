---
title : "Preparing AWS Environment for Serverless Pipeline"
date: 2025-07-02
weight : 1
chapter : false
pre : " <b> 2.1 </b> "
---

In this step, we will build a **Serverless Data Ingestion and Processing Pipeline** using core AWS services. This architecture enables automatic file processing without managing servers. The pipeline includes the following components:

- **Amazon S3**: Receives and stores uploaded files.
- **Amazon EventBridge**: Listens for object-created events from S3.
- **AWS Lambda**: Processes incoming events automatically.
- **Amazon SNS**: Sends real-time notifications to users or external systems.


To learn how to implement each component of this serverless pipeline, you can refer to the official documentation:
- [Amazon S3 – Introduction & Configuration](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)
- [Amazon EventBridge – Event Routing](https://docs.aws.amazon.com/eventbridge/latest/userguide/what-is-amazon-eventbridge.html)
- [AWS Lambda – Serverless Processing](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)
- [Amazon SNS – Notification Service](https://docs.aws.amazon.com/sns/latest/dg/welcome.html)

> 💡 **Note**: Lambda requires appropriate IAM permissions to read from S3, send messages via SNS, and write logs to CloudWatch. Ensure you create a suitable **IAM Role** and attach it to your Lambda function.

---

### Lab Content

- [Create an S3 bucket to receive uploaded files](2.1.1-create-s3-bucket/)
- [Configure an EventBridge rule to trigger on “PUT Object” events from S3](2.1.2-create-eventbridge-rule/)
- [Create a Lambda function to process the incoming events](2.1.3-create-lambda-function/)
- [Create an SNS topic and configure notifications](2.1.4-create-sns-topic/)
- [Create an IAM Role for Lambda (with S3, SNS, and CloudWatch access)](2.1.5-create-iam-role/)
