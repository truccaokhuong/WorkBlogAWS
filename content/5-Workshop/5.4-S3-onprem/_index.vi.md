---
title: "Hướng dẫn Triển khai"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

### 1. Build Backend

Chạy các lệnh sau từ thư mục backend:

```powershell
cd F:\travel-platform-aws\backend
npm install
npm run build
npx prisma generate
```

![Prisma generate](/images/5-Workshop/prisma-generate.png)

Trước khi publish, chạy kiểm tra local để đảm bảo backend khởi động đúng. Trong môi trường development, ứng dụng có thể fallback về in-memory khi local Redis không khả dụng.

![Kiểm tra backend runtime](/images/5-Workshop/12-backend-build.png)

### 2. Chuẩn bị Database

Sau khi cấu hình `DATABASE_URL`, tạo Prisma Client và áp dụng migration production:

```powershell
npx prisma generate
npx prisma migrate deploy
```

Sử dụng database không phải production để testing bất cứ khi nào có thể.

### 3. Đóng gói và Publish Lambda

Tạo deployment artifact từ thư mục backend:

```powershell
Compress-Archive -Path dist,prisma,package.json -DestinationPath function.zip -Force
```

Tải artifact lên S3 và cập nhật Lambda function. Thay thế placeholders với tài nguyên thực từ tài khoản AWS đích:

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

### 4. Cấu hình Runtime và API

Lambda nên được cấu hình với:

* Node.js 20 runtime.
* Execution role phù hợp.
* VPC subnets và Security Groups để truy cập RDS/Redis.
* Biến môi trường production.
* Giá trị memory/timeout phù hợp với khối lượng công việc.

API Gateway nên được kết nối đến Lambda handler chính xác, cấu hình CORS cho origin frontend và bảo vệ với throttling khi cần.

![Lambda runtime](/images/5-Workshop/03-lambda-runtime.png)

### 5. Publish Frontend

Thiết lập API URL đã triển khai trước khi build frontend:

```env
NEXT_PUBLIC_API_URL=https://API_ID.execute-api.REGION.amazonaws.com
```

```powershell
cd F:\travel-platform-aws\frontend
npm install
npm run build
```

Frontend có thể được triển khai qua Vercel, AWS Amplify hoặc workflow hosting do nhóm lựa chọn. Sau khi triển khai, xác minh phiên browser, CORS, authentication và tải lên S3 trực tiếp.

![Frontend home](/images/5-Workshop/frontend-home.png)
