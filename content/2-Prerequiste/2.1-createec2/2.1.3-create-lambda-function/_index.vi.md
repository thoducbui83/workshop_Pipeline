---
title : "Tạo-lambda-function"
date: 2025-07-02
weight : 3
chapter : false
pre : " <b> 2.1.3 </b> "
---

#### Tạo Lambda Function để xử lý dữ liệu upload từ S3

Trong bước này, chúng ta sẽ tạo một **Lambda function** nhằm xử lý các sự kiện "ObjectCreated" từ S3, được gửi qua Amazon EventBridge.

---

### 📝 Bước 1: Truy cập AWS Lambda Console

1. Vào [AWS Lambda Console](https://console.aws.amazon.com/lambda/home).
2. Nhấn **Create function**.

---

### ⚙️ Bước 2: Cấu hình hàm Lambda

1. **Author from scratch** (Tạo hàm từ đầu)
2. **Function name**: `S3UploadEventHandler`
3. **Runtime**: `Node.js 18.x` (hoặc phiên bản mới nhất)
4. **Permissions**:
   + Chọn **Create a new role with basic Lambda permissions**
   + Sau khi tạo, bạn có thể cập nhật thêm quyền như: `AmazonS3ReadOnlyAccess`, `CloudWatchLogsFullAccess`, nếu cần.

Nhấn **Create function**.

![Lambda Create](/workshop_Pipeline/images/lamda1.jpg)

---

### 🧠 Bước 3: Cập nhật mã xử lý

Trong phần **Function code**, thay thế nội dung mặc định bằng đoạn code sau:

```javascript
exports.handler = async (event) => {
    console.log("Event Received: ", JSON.stringify(event));

    const record = event.Records?.[0];
    const bucket = record?.s3?.bucket?.name;
    const key = record?.s3?.object?.key;

    console.log(`File uploaded: ${key} in bucket: ${bucket}`);

    // TODO: Thêm xử lý tùy mục đích (ví dụ: validate file, ghi log, gửi SNS, v.v.)

    return {
        statusCode: 200,
        body: JSON.stringify({ message: 'File processed successfully.' })
    };
};

```
