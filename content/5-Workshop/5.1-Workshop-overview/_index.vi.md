---
title: "Tổng quan"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

### Mục tiêu Workshop

Workshop này hướng dẫn triển khai và vận hành **VTrips**, một nền tảng du lịch **serverless-first** trên AWS. Hệ thống cho phép người dùng đăng ký/đăng nhập, duyệt địa điểm, viết đánh giá, lưu địa điểm, lập lịch trình và xử lý các workflow business/booking.

MVP đã triển khai tập trung vào các dịch vụ AWS cốt lõi: AWS Lambda, Amazon API Gateway, Amazon RDS PostgreSQL, Amazon ElastiCache Redis, Amazon S3, IAM, VPC networking và Amazon CloudWatch.

![Frontend VTrips](/images/5-Workshop/frontend-home.png)

### Các Module Chính

| Module | Chức năng chính | Số API |
| --- | --- | ---: |
| Authentication | Đăng ký, đăng nhập, refresh token, khôi phục mật khẩu, hồ sơ | 7 |
| Places | Duyệt, tìm kiếm, CRUD, tải ảnh, theo dõi lượt xem | 7 |
| Reviews | Đánh giá, bình chọn hữu ích, báo cáo, phản hồi chủ sở hữu | 7 |
| Trips | Lưu địa điểm, lập lịch trình, chia sẻ công khai | 12 |
| Business và Bookings | Claim doanh nghiệp, booking, workflow trạng thái, quản trị | 10 |

Phiên bản hiện tại có **43 API endpoint** đã được ghi nhận.

### Phạm vi Triển khai

MVP sử dụng các thành phần đã cấu hình sau:

* API Gateway làm điểm vào HTTPS công khai.
* Lambda cho runtime API Node.js/Express và business logic.
* RDS PostgreSQL cho dữ liệu giao dịch.
* ElastiCache Redis cho cache và trạng thái ngắn hạn.
* S3 cho artifacts triển khai và ảnh tải lên.
* CloudWatch cho logs và chẩn đoán.
* IAM cho kiểm soát truy cập least-privilege.

Các dịch vụ như CloudFront, Cognito, SQS, SNS, SES, EventBridge, X-Ray, KMS, Secrets Manager, WAF và OpenSearch được xem là các lựa chọn mở rộng production. Chỉ nên khai báo đã triển khai khi môi trường AWS tương ứng đã được cấu hình.

### Tiêu chí Thành công

* Backend build thành công và Lambda được cập nhật với artifact mới.
* API Gateway gọi Lambda và trả về phản hồi hợp lệ.
* Lambda kết nối được đến RDS PostgreSQL, Redis và S3 trong môi trường đã triển khai.
* Frontend có thể gọi API đã triển khai với CORS/token chính xác.
* Các luồng cốt lõi như đăng nhập, duyệt địa điểm, tạo trip, tải ảnh và kiểm tra log hoạt động đáng tin cậy.
