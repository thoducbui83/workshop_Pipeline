---
title : "tao-iam-role"
date: 2025-07-02
weight : 5
chapter : false
pre : " <b> 2.1.5 </b> "
---

#### Tạo IAM Role để Lambda và các dịch vụ có thể tương tác

Trong pipeline xử lý serverless, các dịch vụ như Amazon S3, Lambda và EventBridge cần quyền để **truy cập, gửi sự kiện và thực hiện xử lý dữ liệu**. Vì vậy, bước này sẽ hướng dẫn tạo IAM Role để các dịch vụ có quyền hoạt động phù hợp.

---

### 🛠️ Bước 1: Truy cập IAM

1. Truy cập [IAM Management Console](https://console.aws.amazon.com/iam/).
2. Ở thanh bên trái, chọn **Roles**.
3. Nhấn **Create role**.

---

### 📥 Bước 2: Chọn kiểu trusted entity

1. Tại trang **Select trusted entity type**:
   + Chọn **AWS service**.
   + Chọn **Lambda** (hoặc dịch vụ bạn đang gán quyền).
   + Nhấn **Next**.

---

### 🔐 Bước 3: Gắn quyền (Permissions)

1. Tìm và chọn các policy sau:
   + `AmazonS3FullAccess`
   + `AmazonSNSFullAccess`
   + `CloudWatchLogsFullAccess`
   + `AmazonEventBridgeFullAccess`

> 💡 Nếu bạn triển khai thật, nên tạo các policy tối thiểu chỉ cho phép truy cập các tài nguyên cụ thể.

2. Nhấn **Next**.

---

### 📝 Bước 4: Gán tên cho IAM Role

1. Trong phần **Role name**, nhập: `lambda-pipeline-role`
2. Mô tả: `Role cho phép Lambda truy cập S3, SNS, EventBridge và CloudWatch`
3. Nhấn **Create role** để hoàn tất.

![IAM Role](images/iam.jpg)

---

### ✅ Kết quả cuối cùng

- IAM Role `lambda-pipeline-role` đã sẵn sàng để được gán cho **Lambda Function chính trong pipeline** của bạn.
- Role này cho phép Lambda:
   + Lấy file từ S3
   + Gửi sự kiện sang SNS
   + Ghi log vào CloudWatch
   + Xử lý theo rule từ EventBridge

![IAM Role](images/iam1.jpg)

![IAM Role](images/iam2.jpg)
---

