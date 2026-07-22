---
title: "Deployment Guide"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 5.4. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

### 1. Build the Backend

Run the following commands from the backend directory:

```powershell
cd F:\travel-platform-aws\backend
npm install
npm run build
npx prisma generate
```

![Prisma generate](/images/5-Workshop/prisma-generate.png)

Before publishing, run a local check to ensure that the backend starts correctly. In development, the application can fall back to in-memory behavior when local Redis is unavailable.

![Backend runtime check](/images/5-Workshop/12-backend-build.png)

### 2. Prepare the Database

After configuring `DATABASE_URL`, generate Prisma Client and apply the production migration:

```powershell
npx prisma generate
npx prisma migrate deploy
```

Use a non-production database for testing whenever possible.

### 3. Package and Publish Lambda

Create the deployment artifact from the backend directory:

```powershell
Compress-Archive -Path dist,prisma,package.json -DestinationPath function.zip -Force
```

Upload the artifact to S3 and update the Lambda function. Replace placeholders with actual resources from the target AWS account:

```powershell
aws s3 cp function.zip s3://ARTIFACT_BUCKET/function.zip --region ap-southeast-2

aws lambda update-function-code `
  --function-name travel-platform-api `
  --s3-bucket ARTIFACT_BUCKET `
  --s3-key function.zip `
  --region ap-southeast-2
```

Check Lambda status after the update:

```powershell
aws lambda get-function-configuration `
  --function-name travel-platform-api `
  --query '{FunctionName:FunctionName,Runtime:Runtime,Memory:MemorySize,Timeout:Timeout,LastUpdateStatus:LastUpdateStatus,State:State}' `
  --output table
```

![Lambda update status](/images/5-Workshop/lambda-update-status.png)

### 4. Configure Runtime and API

Lambda should be configured with:

* Node.js 20 runtime.
* A suitable execution role.
* VPC subnets and Security Groups for RDS/Redis access.
* Production environment variables.
* Memory/timeout values appropriate for the workload.

API Gateway should be connected to the correct Lambda handler, configured with CORS for the frontend origin, and protected with throttling when needed.

![Lambda runtime](/images/5-Workshop/03-lambda-runtime.png)

### 5. Publish the Frontend

Set the deployed API URL before building the frontend:

```env
NEXT_PUBLIC_API_URL=https://API_ID.execute-api.REGION.amazonaws.com
```

```powershell
cd F:\travel-platform-aws\frontend
npm install
npm run build
```

The frontend can be deployed through Vercel, AWS Amplify, or the hosting workflow selected by the team. After deployment, verify browser session, CORS, authentication, and direct S3 upload.

![Frontend home](/images/5-Workshop/frontend-home.png)
