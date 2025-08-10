---
title : "tao-sns-topic"
date: 2025-07-02
weight : 4
chapter : false
pre : " <b> 2.1.4 </b> "
---

#### Tạo SNS Topic

Trong bước này, chúng ta sẽ **tạo một SNS Topic** để Lambda Function sử dụng nhằm **gửi thông báo** mỗi khi có tệp được tải lên Amazon S3, được xử lý thông qua EventBridge và Lambda.

---

### 📝 Bước 1: Truy cập giao diện quản lý SNS

1. Truy cập [Bảng điều khiển Amazon SNS](https://console.aws.amazon.com/sns/v3/home).
2. Ở menu bên trái, chọn **Topics**.
3. Nhấn **Create topic** để bắt đầu tạo chủ đề mới.

---

### ⚙️ Bước 2: Cấu hình SNS Topic

1. **Topic type**: Standard  
2. **Tên**: `s3-upload-events-topic`  
3. Các tùy chọn còn lại có thể giữ nguyên mặc định (trừ khi bạn có yêu cầu riêng).
4. Nhấn **Create topic** để hoàn tất.

![SNS Topic](/images/sns1.jpg)

---

### 📥 Bước 3: Tạo Subscription (tuỳ chọn – phục vụ kiểm thử)

1. Trong trang chi tiết của Topic, cuộn xuống phần **Subscriptions**.
2. Nhấn **Create subscription**.
3. **Protocol**: Email  
4. **Endpoint**: Nhập địa chỉ email của bạn để nhận thông báo (ví dụ: `example@gmail.com`)
5. Nhấn **Create subscription**.

> Bạn sẽ nhận được một email xác nhận. Nhấn vào liên kết xác nhận để kích hoạt subscription.

---

### 🔄 Bước 4: Cấp quyền cho Lambda để gửi thông báo

Để Lambda Function có thể gửi thông báo tới SNS, bạn cần cấp quyền như sau:

- Vào **IAM > Roles**
- Tìm đúng role được gán cho Lambda Function
- Gắn thêm policy: `AmazonSNSFullAccess`  
> (Lưu ý: Trong môi trường thật, bạn nên tạo policy riêng chỉ cho phép publish đến Topic này để bảo mật tốt hơn)

---

### ✅ Kết quả cuối cùng

- Bạn đã có SNS Topic tên là `s3-upload-events-topic` có thể được sử dụng để **gửi thông báo cho người dùng hoặc hệ thống** khi có tệp mới được upload lên S3.
- SNS Topic này sẽ được **gọi từ Lambda Function**, đóng vai trò là **tầng thông báo cuối** trong pipeline sự kiện của bạn.

---

