---
title: "Các bước triển khai"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---

### 1. Biên dịch hệ thống phía máy chủ

Chạy các lệnh sau từ thư mục `backend`:

```powershell
cd F:\travel-platform-aws\backend
npm install
npm run build
npx prisma generate
```

![Tạo Prisma Client](/images/5-Workshop/prisma-generate.png)

Trước khi phát hành, hãy kiểm tra cục bộ để đảm bảo hệ thống khởi động đúng. Trong môi trường phát triển, ứng dụng có thể dùng bộ nhớ trong tạm thời khi Redis cục bộ không khả dụng.

![Kiểm tra môi trường chạy phía máy chủ](/images/5-Workshop/12-backend-build.png)

### 2. Chuẩn bị cơ sở dữ liệu

Sau khi cấu hình `DATABASE_URL`, tạo Prisma Client và áp dụng các thay đổi lược đồ cho môi trường vận hành:

```powershell
npx prisma generate
npx prisma migrate deploy
```

Nên sử dụng cơ sở dữ liệu dành riêng cho kiểm thử, không dùng cơ sở dữ liệu đang vận hành.

### 3. Đóng gói và phát hành Lambda

Tạo gói triển khai từ thư mục `backend`:

```powershell
Compress-Archive -Path dist,prisma,package.json -DestinationPath function.zip -Force
```

Tải gói lên S3 và cập nhật hàm Lambda. Thay các giá trị mẫu bằng tài nguyên thật của tài khoản AWS đích:

```powershell
aws s3 cp function.zip s3://ARTIFACT_BUCKET/function.zip --region ap-southeast-2

aws lambda update-function-code `
  --function-name travel-platform-api `
  --s3-bucket ARTIFACT_BUCKET `
  --s3-key function.zip `
  --region ap-southeast-2
```

Kiểm tra trạng thái Lambda sau khi cập nhật:

```powershell
aws lambda get-function-configuration `
  --function-name travel-platform-api `
  --query '{FunctionName:FunctionName,Runtime:Runtime,Memory:MemorySize,Timeout:Timeout,LastUpdateStatus:LastUpdateStatus,State:State}' `
  --output table
```

![Trạng thái cập nhật Lambda](/images/5-Workshop/lambda-update-status.png)

### 4. Cấu hình môi trường chạy và API

Lambda cần được cấu hình với:

* Môi trường chạy Node.js 20.
* Vai trò thực thi phù hợp.
* Mạng con VPC và nhóm bảo mật để truy cập RDS, Redis.
* Biến môi trường dành cho hệ thống vận hành.
* Bộ nhớ và thời gian chờ phù hợp với khối lượng công việc.

API Gateway cần kết nối đúng hàm xử lý Lambda, cấu hình CORS cho miền giao diện và giới hạn lưu lượng khi cần.

![Môi trường chạy Lambda](/images/5-Workshop/03-lambda-runtime.png)

### 5. Phát hành giao diện người dùng

Thiết lập URL API đã triển khai trước khi biên dịch giao diện:

```env
NEXT_PUBLIC_API_URL=https://API_ID.execute-api.REGION.amazonaws.com
```

```powershell
cd F:\travel-platform-aws\frontend
npm install
npm run build
```

Giao diện có thể được triển khai qua Vercel, AWS Amplify hoặc nền tảng lưu trữ do nhóm lựa chọn. Sau khi triển khai, kiểm tra phiên đăng nhập trên trình duyệt, CORS, xác thực và việc tải tệp trực tiếp lên S3.

![Trang chủ của giao diện](/images/5-Workshop/frontend-home.png)
