---
title : "Tạo s3-bucket "
date: 2025-07-02
weight : 1
chapter : false
pre : " <b> 2.1.1 </b> "
---

#### Tạo S3 Bucket cho Serverless Data Pipeline

Trong bước này, chúng ta sẽ tạo một **Amazon S3 bucket** dùng để tiếp nhận dữ liệu đầu vào (chẳng hạn ảnh, file CSV, JSON,...). S3 bucket này sẽ được tích hợp với **Amazon EventBridge** để khi có file mới được upload, một sự kiện sẽ được phát sinh và gửi tới **AWS Lambda** để xử lý.

---

### 🪣 Bước 1: Truy cập Amazon S3

1. Truy cập [Amazon S3 Console](https://s3.console.aws.amazon.com/s3/home).
2. Click nút **Create bucket**.

![S3](images/taoS3.jpg)

---

### 📋 Bước 2: Nhập thông tin S3 Bucket

1. **Bucket name**: Nhập tên bucket, ví dụ: `fcj-upload-pipeline-demo`.
2. **Region**: Chọn khu vực gần bạn nhất, ví dụ: `Asia Pacific (Singapore) ap-southeast-1`.
3. **Block Public Access**: Đảm bảo bật **Block all public access** (theo mặc định).
4. Kéo xuống dưới cùng, chọn **Create bucket**.

![S3](images/s3TC.jpg)

---

### ✅ Kết quả

- Bạn đã tạo thành công một bucket để sử dụng làm **điểm khởi đầu trong pipeline serverless**.
- Bất kỳ file nào được upload vào bucket này sẽ phát sinh **S3 Event Notification**.
- Trong các bước tiếp theo, ta sẽ cấu hình **EventBridge Rule** để lắng nghe sự kiện từ S3 và gọi Lambda function.

---

