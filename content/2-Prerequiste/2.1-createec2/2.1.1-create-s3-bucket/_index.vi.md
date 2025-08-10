---
title : "create-s3-bucket"
date: 2025-07-02
weight : 1
chapter : false
pre : " <b> 2.1.1 </b> "
---

## Tạo S3 Bucket cho Serverless Data Ingestion Pipeline

Trong bước này, bạn sẽ tạo một Amazon S3 bucket để làm điểm khởi đầu cho pipeline xử lý dữ liệu serverless dựa trên sự kiện. Khi bạn upload file vào bucket này, nó sẽ kích hoạt một sự kiện trong Amazon EventBridge, sau đó sẽ gọi Lambda function để xử lý dữ liệu.

### Bước 1: Truy cập Amazon S3 Console

1. Điều hướng đến [Amazon S3 Console](https://console.aws.amazon.com/s3/).
2. Click nút **Create bucket**.

![S3](/workshop_Pipeline/images/taoS3.jpg)

### Bước 2: Nhập thông tin Bucket

1. **Bucket name**: Nhập tên như `fcj-upload-pipeline-demo`.
2. **Region**: Chọn AWS Region ưa thích, ví dụ: Asia Pacific (Singapore) ap-southeast-1.
3. **Block Public Access**: Đảm bảo **Block all public access** được bật (cài đặt mặc định).
4. Cuộn xuống và click **Create bucket**.

![S3](/workshop_Pipeline/images/s3TC.jpg)

### Kết quả

- ✅ Bạn đã tạo thành công một bucket làm nguồn đầu vào cho pipeline serverless.
- ✅ Bất kỳ file nào được upload vào bucket này sẽ tạo ra S3 Event.
- ✅ Trong các bước tiếp theo, chúng ta sẽ cấu hình EventBridge Rules để lắng nghe S3 events và kích hoạt AWS Lambda để xử lý dữ liệu.

