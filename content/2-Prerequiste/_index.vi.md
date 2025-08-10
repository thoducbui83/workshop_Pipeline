---
title : "Các bước chuẩn bị"
date: 2025-07-02 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---

{{% notice info %}}
Bạn cần tạo một Amazon S3 bucket để tiếp nhận file được người dùng tải lên, cấu hình một rule trên EventBridge để bắt sự kiện upload, kích hoạt một hàm AWS Lambda để xử lý file, và cuối cùng gửi thông báo qua Amazon SNS.
{{% /notice %}}

Để tìm hiểu cách tạo các dịch vụ AWS cần thiết cho pipeline này, bạn có thể tham khảo tài liệu chính thức:
  - [Amazon S3 – Lưu trữ đối tượng](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)
  - [Amazon EventBridge – Kiến trúc theo sự kiện](https://docs.aws.amazon.com/eventbridge/latest/userguide/what-is-amazon-eventbridge.html)
  - [AWS Lambda – Tính toán không máy chủ](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)
  - [Amazon SNS – Dịch vụ thông báo](https://docs.aws.amazon.com/sns/latest/dg/welcome.html)

Để Lambda có thể xử lý sự kiện từ S3 thông qua EventBridge và gửi thông báo bằng SNS, bạn cần cấp đủ quyền cho Lambda thông qua IAM Role. Trong phần chuẩn bị này, bạn cũng sẽ tạo IAM Role cho phép Lambda:
- Đọc dữ liệu từ S3
- Gửi thông báo qua SNS
- Ghi log vào CloudWatch

### Nội dung thực hành
  - [Chuẩn bị S3 bucket, rule EventBridge, Lambda function và SNS topic](2.1-createec2/)
  - [Tạo IAM Role và cấp quyền cho Lambda](2.2-createiamrole/)

  
