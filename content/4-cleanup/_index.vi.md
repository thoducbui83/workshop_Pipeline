+++  
title = "Dọn dẹp tài nguyên"  
date = 2025-07-02  
weight = 6  
chapter = false  
pre = "<b>6. </b>"  
+++  

Chúng ta sẽ tiến hành dọn dẹp tất cả các tài nguyên AWS đã được tạo trong dự án **Pipeline Thu Thập & Xử Lý Dữ Liệu Serverless**.  

---

### 🗑️ Xóa Lambda Function  

1. Truy cập [Bảng điều khiển AWS Lambda](https://console.aws.amazon.com/lambda/home)  
   + Chọn **Lambda function** đã tạo cho dự án (ví dụ: `event-processing-function`).  
   + Nhấn **Actions** → **Delete**.  
   + Xác nhận xóa bằng cách nhập tên hàm.  

---

### 🗑️ Xóa EventBridge Rule  

1. Truy cập [Bảng điều khiển Amazon EventBridge](https://console.aws.amazon.com/events/home)  
   + Nhấp vào **Rules** ở thanh bên trái.  
   + Chọn **quy tắc** đã tạo cho S3 trigger (ví dụ: `S3UploadEventRule`).  
   + Nhấn **Actions** → **Delete** → Xác nhận.  

---

### 🗑️ Xóa SNS Topic  

1. Truy cập [Bảng điều khiển Amazon SNS](https://console.aws.amazon.com/sns/v3/home)  
   + Chọn **SNS Topic** dùng để gửi sự kiện đã xử lý.  
   + Nhấn **Actions** → **Delete topic** → Xác nhận xóa.  

---

### 🗑️ Xóa IAM Role  

1. Truy cập [Bảng điều khiển IAM](https://console.aws.amazon.com/iam/)  
   + Nhấn vào **Roles**.  
   + Tìm `lambda-pipeline-role`.  
   + Nhấn vào tên role.  
   + Chọn **Delete**, sau đó nhập tên role để xác nhận.  

---

### 🗑️ Làm trống và xóa S3 Bucket  

1. Truy cập [Bảng điều khiển Amazon S3](https://s3.console.aws.amazon.com/s3/)  
   + Nhấp vào bucket bạn đã tạo (ví dụ: `fcj-serverless-pipeline-bucket`).  
   + Vào **Empty bucket**, nhập `permanently delete` và nhấn **Empty** để xóa tất cả đối tượng.  
   + Sau đó nhấn **Delete bucket**.  
   + Xác nhận bằng cách nhập tên bucket → Nhấn **Delete**.  

---

### ✅ Tùy chọn: Xóa CloudWatch Log Groups  

1. Truy cập [Bảng điều khiển CloudWatch](https://console.aws.amazon.com/cloudwatch/)  
   + Nhấn **Log groups** ở thanh bên trái.  
   + Tìm log groups của Lambda function.  
   + Chọn log group(s) → Nhấn **Actions** → **Delete log group** → Xác nhận.  

---

### ✅ Tóm tắt  

Tại thời điểm này, bạn đã:  
- Xóa tất cả các thành phần serverless (Lambda, EventBridge rule, SNS, IAM Role, S3 Bucket).  
- Xóa log thừa để tiết kiệm chi phí.  
- Dọn dẹp môi trường để tránh các khoản phí phát sinh ngoài ý muốn.  

> 🧼 Thực hiện dọn dẹp là một thói quen tốt để tránh tốn thêm chi phí và giữ cho tài khoản AWS của bạn được gọn gàng.  
