---
title: "Yêu cầu tiên quyết"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---

### Yêu cầu AWS

Trước khi triển khai, cần chuẩn bị:

* Tài khoản AWS có quyền tạo hoặc cập nhật Lambda, API Gateway, RDS, ElastiCache, S3, vai trò và chính sách IAM, VPC, nhóm bảo mật và nhật ký CloudWatch.
* Một Khu vực AWS dùng thống nhất, ví dụ `ap-southeast-2`.
* Vùng lưu trữ S3 cho gói triển khai Lambda và vùng lưu ảnh của ứng dụng.
* VPC, mạng con và nhóm bảo mật cho phép Lambda kết nối RDS và Redis.
* Vai trò IAM của Lambda tuân theo nguyên tắc đặc quyền tối thiểu.

### Công cụ cục bộ

Cài đặt các công cụ sau trên máy:

* Node.js 20 trở lên.
* npm.
* AWS CLI v2.
* Git.
* Công cụ kết nối PostgreSQL để kiểm tra cơ sở dữ liệu.

Xác minh bộ công cụ:

```powershell
node --version
npm --version
aws --version
aws sts get-caller-identity
```

### Cấu hình môi trường

Tạo cấu hình môi trường dựa trên tệp ví dụ của dự án. Không đưa thông tin bí mật vào kho mã.

```env
NODE_ENV=production
DATABASE_URL=postgresql://USER:PASSWORD@RDS_ENDPOINT:5432/travelplatform
REDIS_URL=redis://REDIS_ENDPOINT:6379
JWT_SECRET=replace-with-a-long-random-secret
AWS_REGION=ap-southeast-2
S3_BUCKET_UPLOADS=replace-with-your-bucket
```

Trong môi trường vận hành thực tế, hãy sử dụng biến môi trường được bảo vệ của Lambda hoặc AWS Secrets Manager thay vì lưu thông tin xác thực trong tệp cục bộ.
