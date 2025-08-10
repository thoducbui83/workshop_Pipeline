---
title : "Receive Notification via CloudWatch"
date: 2025-07-02
weight : 2
chapter : false
pre : " <b> 3.2. </b> "
---

#### Xem thông báo từ Lambda qua CloudWatch Logs

Sau khi file được upload lên S3, sự kiện sẽ kích hoạt Lambda function thông qua EventBridge. Lambda sẽ thực thi và ghi log lại quá trình xử lý. Bạn có thể xem các log này trong dịch vụ **Amazon CloudWatch**.

👉 Đây là cách kiểm tra Lambda hoạt động chính xác hay không.

🖼️ **Ví dụ log hiển thị trong CloudWatch:**

![CloudWatchLogGroup](images/upload1.jpg)

![CloudWatchLogGroup](images/uploadTC.jpg)


![CloudWatchLogGroup](images/cloudwhat1.jpg)

- Log group được tạo tự động theo tên hàm Lambda:  
  `/aws/lambda/S3UploadEventHandler`
- Bạn có thể click vào log group để xem chi tiết từng lần thực thi (log stream), giúp kiểm tra thông tin như:
  - Tên file nhận được từ S3
  - Thông báo đã gửi qua SNS thành công hay chưa
  - Thời gian thực thi và lỗi (nếu có)

{{% notice note %}}
Nếu bạn không thấy log hiện lên, hãy đảm bảo Lambda có quyền ghi log (`AWSLambdaBasicExecutionRole`) và đã được gọi bởi sự kiện S3 đúng cách.
{{% /notice %}}
