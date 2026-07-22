---
title: "Tổng quan"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

### Mục tiêu hướng dẫn

Phần này hướng dẫn triển khai và vận hành **VTrips**, một nền tảng du lịch ưu tiên kiến trúc phi máy chủ trên AWS. Hệ thống cho phép người dùng đăng ký, đăng nhập, duyệt địa điểm, viết đánh giá, lưu địa điểm, lập lịch trình và xử lý các quy trình doanh nghiệp, đặt chỗ.

Sản phẩm khả dụng tối thiểu (MVP) tập trung vào các dịch vụ AWS cốt lõi: AWS Lambda, Amazon API Gateway, Amazon RDS for PostgreSQL, Amazon ElastiCache for Redis, Amazon S3, IAM, VPC và Amazon CloudWatch.

![Giao diện VTrips](/images/5-Workshop/frontend-home.png)

### Các phân hệ chính

| Phân hệ | Chức năng chính | Số API |
| --- | --- | ---: |
| Xác thực | Đăng ký, đăng nhập, làm mới mã thông báo, khôi phục mật khẩu, hồ sơ | 7 |
| Địa điểm | Duyệt, tìm kiếm, thêm/sửa/xóa, tải ảnh, theo dõi lượt xem | 7 |
| Đánh giá | Đánh giá, bình chọn hữu ích, báo cáo, phản hồi của chủ sở hữu | 7 |
| Chuyến đi | Lưu địa điểm, lập lịch trình, chia sẻ công khai | 12 |
| Doanh nghiệp và đặt chỗ | Xác minh doanh nghiệp, đặt chỗ, quản lý trạng thái, quản trị | 10 |

Phiên bản hiện tại có **43 điểm cuối API** đã được ghi nhận.

### Phạm vi triển khai

MVP sử dụng các thành phần đã cấu hình sau:

* API Gateway làm điểm vào HTTPS công khai.
* Lambda chạy API Node.js/Express và xử lý logic nghiệp vụ.
* RDS for PostgreSQL lưu dữ liệu giao dịch.
* ElastiCache for Redis lưu dữ liệu đệm và trạng thái ngắn hạn.
* S3 lưu gói triển khai và ảnh được tải lên.
* CloudWatch ghi nhật ký và hỗ trợ chẩn đoán.
* IAM kiểm soát truy cập theo nguyên tắc đặc quyền tối thiểu.

CloudFront, Cognito, SQS, SNS, SES, EventBridge, X-Ray, KMS, Secrets Manager, WAF và OpenSearch là các lựa chọn mở rộng cho môi trường vận hành thực tế. Chỉ nên ghi nhận là đã triển khai khi môi trường AWS tương ứng đã được cấu hình.

### Tiêu chí thành công

* Hệ thống phía máy chủ được biên dịch thành công và Lambda nhận gói triển khai mới.
* API Gateway gọi Lambda và trả về phản hồi hợp lệ.
* Lambda kết nối được với RDS for PostgreSQL, Redis và S3.
* Giao diện gọi được API đã triển khai với cấu hình CORS và mã thông báo chính xác.
* Các luồng đăng nhập, duyệt địa điểm, tạo chuyến đi, tải ảnh và kiểm tra nhật ký hoạt động ổn định.
