---
title: "Yêu cầu tiên quyết"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

### Yêu cầu AWS

Trước khi triển khai workshop, chuẩn bị:

* Tài khoản AWS với quyền tạo/cập nhật Lambda, API Gateway, RDS, ElastiCache, S3, IAM roles/policies, VPC/Security Groups và CloudWatch Logs.
* Region triển khai nhất quán, ví dụ `ap-southeast-2`.
* S3 bucket cho Lambda artifacts và bucket/lưu trữ ứng dụng cho ảnh tải lên.
* VPC, subnets và Security Groups cho phép Lambda kết nối đến RDS/Redis.
* Lambda IAM role với quyền least-privilege.

### Công cụ Local

Cài đặt các công cụ sau trên máy local:

* Node.js 20 trở lên.
* npm.
* AWS CLI v2.
* Git.
* PostgreSQL client tools để kiểm tra database.

Xác minh toolchain:

```powershell
node --version
npm --version
aws --version
aws sts get-caller-identity
```

### Cấu hình Môi trường

Tạo cấu hình môi trường dựa trên file ví dụ của dự án. Không bao giờ commit secrets vào repository.

```env
NODE_ENV=production
DATABASE_URL=postgresql://USER:PASSWORD@RDS_ENDPOINT:5432/travelplatform
REDIS_URL=redis://REDIS_ENDPOINT:6379
JWT_SECRET=replace-with-a-long-random-secret
AWS_REGION=ap-southeast-2
S3_BUCKET_UPLOADS=replace-with-your-bucket
```

Với production, sử dụng Lambda environment variables được bảo vệ hoặc AWS Secrets Manager thay vì lưu trữ credentials trong file local.
