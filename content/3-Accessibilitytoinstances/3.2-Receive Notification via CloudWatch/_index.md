---
title : "Receive Notification via CloudWatch"
date: 2025-07-02
weight : 2
chapter : false
pre : " <b> 3.2. </b> "
---

#### Viewing Lambda Execution Logs in CloudWatch

After a file is uploaded to the S3 bucket, the event triggers a Lambda function via EventBridge. The Lambda function then runs and logs its execution to **Amazon CloudWatch Logs**.

👉 This allows you to verify whether the Lambda was triggered and executed correctly.

🖼️ **Example of log group in CloudWatch:**

![CloudWatchLogGroup](/workshop_Pipeline/images/upload1.jpg)

![CloudWatchLogGroup](/workshop_Pipeline/images/uploadTC.jpg)


![CloudWatchLogGroup](/workshop_Pipeline/images/cloudwhat1.jpg)

- The log group is automatically created based on the Lambda function name:  
  `/aws/lambda/S3UploadEventHandler`
- You can click on the log group to explore individual log streams and check:
  - The file name received from S3
  - Whether the SNS message was successfully published
  - Execution time and any possible errors

{{% notice note %}}
If no logs appear, ensure the Lambda function has the correct permissions (`AWSLambdaBasicExecutionRole`) and has been properly triggered by the S3 event.
{{% /notice %}}
