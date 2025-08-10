---
title : "create-eventbridge-rule"
date: 2025-07-02
weight : 1
chapter : false
pre : " <b> 2.1.2 </b> "
---

## Tạo EventBridge Rule cho S3 Events

Trong bước này, bạn sẽ tạo một Amazon EventBridge rule để lắng nghe các sự kiện tạo object S3 và kích hoạt Lambda function khi có file được upload vào S3 bucket.

### Bước 1: Truy cập Amazon EventBridge Console

1. Điều hướng đến [Amazon EventBridge Console](https://console.aws.amazon.com/events/).
2. Click **Rules** trong sidebar bên trái.
3. Click **Create rule**.

![EventBridge](/workshop_Pipeline/images/taoRuler.jpg)

### Bước 2: Cấu hình Rule Details

1. **Name**: Nhập tên mô tả như `s3-upload-trigger`.
2. **Description**: "Rule để kích hoạt Lambda khi có file upload lên S3".
3. **Event bus**: Chọn **default**.
4. **Rule type**: Chọn **Rule with an event pattern**.

### Bước 3: Định nghĩa Event Pattern

1. **Event source**: Chọn **AWS services**.
2. **AWS service**: Chọn **Simple Storage Service (S3)**.
3. **Event type**: Chọn **Object Level Operations**.
4. **Specific event(s)**: Chọn **Object Created**.
5. **Specific operation(s)**: Chọn **Put**, **Post**, **Copy**, **CompleteMultipartUpload**.

![Event Pattern](/workshop_Pipeline/images/ruler2.jpg)

### Bước 4: Cấu hình Target

1. **Target types**: Chọn **AWS service**.
2. **Target**: Chọn **Lambda function**.
3. **Function**: Chọn Lambda function của bạn từ dropdown.
4. Click **Add target**.

![Add Target](/workshop_Pipeline/images/ruler3.jpg)

### Bước 5: Tạo Rule

1. Xem lại cấu hình.
2. Click **Create rule**.

![Success](/workshop_Pipeline/images/ruler1.jpg)

### Kết quả

- ✅ EventBridge rule của bạn đã được cấu hình để lắng nghe S3 upload events.
- ✅ Khi có file được upload vào S3 bucket, EventBridge sẽ tự động kích hoạt Lambda function.
- ✅ Pipeline serverless giờ đây đã dựa trên sự kiện và sẽ xử lý dữ liệu tự động.
