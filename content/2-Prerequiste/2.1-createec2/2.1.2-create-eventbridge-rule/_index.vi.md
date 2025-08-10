---
title : "tao-eventbridge-rule"
date: 2025-07-02
weight : 2
chapter : false
pre : " <b> 2.1.2 </b> "
---

#### Tạo Rule EventBridge để kích hoạt Lambda khi có file mới trên S3

Trong bước này, chúng ta sẽ tạo một **EventBridge Rule** để theo dõi sự kiện khi một file mới được tải lên bucket S3 (ví dụ: `fcj-upload-pipeline-demo`). Khi sự kiện này xảy ra, rule sẽ tự động kích hoạt Lambda function để xử lý file đó.

---

### 📌 Bước 1: Mở giao diện quản lý EventBridge

1. Truy cập [Amazon EventBridge Console](https://console.aws.amazon.com/events/home).
2. Ở thanh điều hướng bên trái, chọn **Rules**.
3. Nhấn nút **Create rule** để tạo mới.

![EventBridge](/images/taoRuler.jpg)

---

### 📝 Bước 2: Nhập thông tin Rule

1. **Tên Rule**: `s3-upload-trigger`
2. **Mô tả**: Tự động kích hoạt Lambda khi có file mới tải lên S3
3. **Event bus**: Giữ mặc định là **default**

Nhấn **Next** để tiếp tục.

---

### 🎯 Bước 3: Định nghĩa điều kiện sự kiện (Event Pattern)

1. **Nguồn sự kiện (Event Source)**: chọn **AWS services**
2. **Dịch vụ AWS**: `Simple Storage Service (S3)`
3. **Loại sự kiện (Event type)**: `Object Created`
4. **Sự kiện cụ thể**: `PutObject` (hoặc để mặc định nếu không chắc)
5. (Tuỳ chọn) **Lọc theo tên bucket**: nhập tên bucket của bạn, ví dụ: `fcj-upload-pipeline-demo`

Nhấn **Next**.

![Event Pattern](/images/ruler2.jpg)

---

### ⚙️ Bước 4: Thêm đích (Target)

1. **Loại đích (Target type)**: Dịch vụ AWS
2. **Chọn đích**: `Lambda function`
3. **Hàm Lambda**: Chọn tên hàm xử lý, ví dụ: `S3UploadEventHandler`
4. (Tuỳ chọn) Có thể thêm input transformer nếu cần.

Nhấn **Next**.

![Add Target](/images/ruler3.jpg)

---

### ✅ Bước 5: Xác nhận và tạo rule

1. Kiểm tra lại toàn bộ cấu hình của rule.
2. Nhấn **Create rule** để hoàn tất.

![Success](/images/ruler1.jpg)

---

### 🎉 Kết quả

Bạn đã tạo thành công một **EventBridge Rule**.  
Mỗi khi có một file mới được tải lên bucket `fcj-upload-pipeline-demo`, sự kiện sẽ được gửi tới EventBridge và tự động kích hoạt **Lambda function** để xử lý.

---
