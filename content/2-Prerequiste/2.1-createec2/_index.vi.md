---
title : "Chuẩn bị Môi trường AWS cho Kiến trúc Serverless"
date: 2025-07-02 
weight : 1 
chapter : false
pre : " <b> 2.1 </b> "
---

Trong bước này, chúng ta sẽ tạo một pipeline xử lý dữ liệu dạng **Serverless**, bao gồm các thành phần chính:  
- **Amazon S3** để nhận file upload  
- **Amazon EventBridge** để bắt sự kiện từ S3  
- **AWS Lambda** để xử lý sự kiện  
- **Amazon SNS** để gửi thông báo tới người dùng hoặc hệ thống khác


Để tìm hiểu cách triển khai từng thành phần trong pipeline này, bạn có thể tham khảo thêm các tài liệu hướng dẫn chính thức:
  - [Amazon S3 – Giới thiệu & cấu hình](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)
  - [Amazon EventBridge – Trigger theo sự kiện](https://docs.aws.amazon.com/eventbridge/latest/userguide/what-is-amazon-eventbridge.html)
  - [AWS Lambda – Xử lý không máy chủ](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)
  - [Amazon SNS – Gửi thông báo](https://docs.aws.amazon.com/sns/latest/dg/welcome.html)

> 💡 Lưu ý: Lambda cần có quyền để đọc dữ liệu từ S3, gửi thông báo qua SNS, và ghi log vào CloudWatch. Vì vậy, bạn cần tạo **IAM Role phù hợp** và gán cho Lambda.

---

### Nội dung thực hành

  - [Tạo bucket Amazon S3 để nhận dữ liệu upload](2.1.1-create-s3-bucket/)
  - [Cấu hình rule EventBridge để bắt sự kiện "PUT Object" từ S3](2.1.2-create-eventbridge-rule/)
  - [Tạo Lambda function xử lý dữ liệu](2.1.3-create-lambda-function/)
  - [Tạo SNS topic và cấu hình thông báo](2.1.4-create-sns-topic/)
  - [Tạo IAM Role cho Lambda: quyền đọc từ S3, ghi log, gửi SNS](2.1.5-create-iam-role/)

