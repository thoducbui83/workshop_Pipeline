# FCJ Internship Project Proposal

## 1. Executive Summary

Doanh nghiệp ngày nay thường cần xử lý một lượng lớn dữ liệu được tải lên từ người dùng như tài liệu, hình ảnh, video hoặc dữ liệu log. Việc xây dựng một hệ thống xử lý file realtime vừa đơn giản, vừa linh hoạt, lại tiết kiệm chi phí là một thách thức lớn cho các công ty vừa và nhỏ.

Đề tài này xây dựng một kiến trúc **Serverless Data Ingestion and Processing Pipeline** sử dụng các dịch vụ của AWS như:

- **Amazon S3** để tiếp nhận dữ liệu  
- **Amazon EventBridge** để kích hoạt theo sự kiện  
- **AWS Lambda** để xử lý realtime  

Hệ thống không cần máy chủ quản lý, tự động mở rộng theo nhu cầu, dễ triển khai và tối ưu chi phí.

**Key Features:**

- Tự động xử lý mọi file người dùng tải lên (ảnh, video, dữ liệu)
- Kiến trúc serverless, không cần quản lý hạ tầng
- Mở rộng linh hoạt, không giới hạn số lượng file
- Dễ tích hợp với các hệ thống khác

**Business Benefits:**

- Giảm chi phí vận hành hạ tầng lên đến 70%
- Tăng tốc độ xử lý dữ liệu từ hàng phút xuống còn vài giây
- Hệ thống ổn định, dễ bảo trì

**Investment & Success Metrics:**

- Chi phí: ~$5–$20/tháng (theo số lượng file)
- Xử lý thành công 99% file trong vòng <5 giây
- Không downtime, độ ổn định >99.9%

---

## 2. Problem Statement

### Current Situation

Doanh nghiệp đang xử lý file đầu vào qua server truyền thống, dễ gặp lỗi, khó mở rộng và tốn kém.

### Key Challenges

- Khó mở rộng khi traffic tăng đột biến
- Chi phí server cố định, cao
- Cấu hình phức tạp, khó vận hành
- Không đáp ứng được thời gian xử lý realtime

### Stakeholder Impact

- **DevOps:** áp lực duy trì hạ tầng 24/7  
- **Users:** phải chờ dữ liệu xử lý chậm  
- **Business:** mất cơ hội vì phản hồi chậm

### Business Consequences

Nếu không cải thiện, doanh nghiệp sẽ tiếp tục tốn kém chi phí vận hành, hiệu năng thấp, không thể cạnh tranh và khó mở rộng dịch vụ.

### Market Opportunity

Serverless đang là xu hướng: 70% startup đang dùng Lambda, EventBridge và S3 để tự động hóa xử lý dữ liệu với chi phí thấp, hiệu năng cao.

---

## 3. Solution Architecture

### Architecture Overview

[User Upload File]
      -> [Amazon S3]
          -> (Trigger) [Amazon EventBridge]
              -> [AWS Lambda Function]
                  -> [Processing Logic]
                      -> [Amazon CloudWatch / Amazon DynamoDB / S3 processed]


### AWS Services Used

- **Amazon S3:** Nơi người dùng upload file  
- **Amazon EventBridge:** Bắt sự kiện ObjectCreated từ S3  
- **AWS Lambda:** Xử lý sự kiện, chuyển định dạng, trích xuất dữ liệu  
- **Amazon CloudWatch:** Ghi log, theo dõi và kiểm tra  
- **Amazon DynamoDB / S3:** Lưu kết quả xử lý hoặc metadata (tuỳ chọn)

### Scalability Design

- Serverless 100%: Không cần EC2, tự động scale  
- Chi phí theo mức sử dụng thực tế

---

## 4. Technical Implementation

### Implementation Phases

| Giai đoạn  |   Mô tả                                    | Công cụ sử dụng         |
|------------|--------------------------------------------|-------------------------|
| Phase 1    | Tạo S3 Bucket, bật EventBridge             | AWS Console             |
| Phase 2    | Viết Lambda và test                        | AWS Lambda, Python      |
| Phase 3    | Gắn rule EventBridge và test toàn hệ thống | CloudWatch, EventBridge |
| Phase 4    | Tối ưu log, bảo mật, IAM                   | IAM, CloudWatch         |

### Technical Requirements

- IAM Role với quyền: `logs:*`, `lambda:*`, `s3:GetObject`
- Lambda runtime: Python 3.12
- Timeout: 10s, Memory: 128MB

### Testing Strategy

- Unit test bằng payload mẫu  
- Integration test: Upload file thật, kiểm log  
- Monitoring: CloudWatch log group `/aws/lambda/...`

### Deployment Plan

- Dùng AWS Console, hoặc CDK để deploy  
- Rollback: Disable rule hoặc revert Lambda version

### Configuration Management

- Dùng GitHub để version control  
- Mỗi lần deploy ghi rõ version và timestamp

---

## 5. Timeline & Milestones

| Mốc thời gian | Công việc                          | Kết quả                        |
|---------------|------------------------------------|--------------------------------|
| Ngày 1        | Chuẩn bị AWS, tạo bucket           | Có bucket nhận file            |
| Ngày 2        | Tạo EventBridge rule               | Rule bắt sự kiện ObjectCreated |
| Ngày 3        | Viết Lambda, test nội bộ           | Lambda hoạt động ổn định       |
| Ngày 4        | Tích hợp S3 + EventBridge + Lambda | Pipeline hoạt động             |
| Ngày 5        | Ghi log, test hiệu năng            | Đảm bảo độ trễ <5s             |
| Ngày 6        | Viết báo cáo và chuẩn bị slide     | Hoàn tất proposal              |

---

## 6. Budget Estimation

### Ước tính chi phí cho 10.000 file/tháng

- **S3 Storage:** ~$0.10  
- **EventBridge:** Miễn phí  
- **Lambda:** Trong giới hạn Free Tier  

→ Tổng: **~$0 – $2/tháng**

### Production scale (1 triệu file/tháng)

- ~ $5 – $15/tháng

---

## 7. Risk Assessment

| Rủi ro             | Mức độ     | Giảm thiểu                       |
|--------------------|------------|----------------------------------|
| Sai event pattern  | Trung bình | Test kỹ và log EventBridge       |
| Lambda timeout     | Thấp       | Tối ưu code, giới hạn size file  |
| IAM thiếu quyền    | Trung bình | Viết chính xác IAM policy        |
| S3 không gửi event | Thấp       | Bật EventBridge integration đúng |

---

## 8. Expected Outcomes

### Success Metrics

- Xử lý >99% file trong <5s  
- Uptime 99.9%  
- CloudWatch log đầy đủ

### Business Benefits

- Tăng tốc xử lý, giảm chi phí  
- Không cần DevOps duy trì server

### Long-Term Value

- Có thể mở rộng cho xử lý ảnh, OCR, video  
- Làm nền tảng học cloud-native chuyên sâu

---

## 📚 Appendices

### A. Kiến trúc AWS sử dụng

- S3
- EventBridge
- Lambda
- CloudWatch

### B. Chi phí tính theo AWS Calculator

### C. Tài liệu tham khảo

- AWS Well-Architected Framework  
- AWS Case Studies  
- AWS Serverless Patterns  
