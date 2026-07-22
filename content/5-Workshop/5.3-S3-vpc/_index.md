---
title: "Prerequisite"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 5.3. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

### AWS Requirements

Before deploying the workshop, prepare:

* An AWS account with permissions to create/update Lambda, API Gateway, RDS, ElastiCache, S3, IAM roles/policies, VPC/Security Groups, and CloudWatch Logs.
* A consistent deployment region, for example `ap-southeast-2`.
* An S3 bucket for Lambda artifacts and a bucket/application storage for uploaded images.
* VPC, subnets, and Security Groups that allow Lambda to connect to RDS/Redis.
* A Lambda IAM role with least-privilege permissions.

### Local Tools

Install the following tools locally:

* Node.js 20 or later.
* npm.
* AWS CLI v2.
* Git.
* PostgreSQL client tools for database checks.

Verify the toolchain:

```powershell
node --version
npm --version
aws --version
aws sts get-caller-identity
```

### Environment Configuration

Create environment configuration based on the project example file. Never commit secrets to the repository.

```env
NODE_ENV=production
DATABASE_URL=postgresql://USER:PASSWORD@RDS_ENDPOINT:5432/travelplatform
REDIS_URL=redis://REDIS_ENDPOINT:6379
JWT_SECRET=replace-with-a-long-random-secret
AWS_REGION=ap-southeast-2
S3_BUCKET_UPLOADS=replace-with-your-bucket
```

For production, use protected Lambda environment variables or AWS Secrets Manager instead of storing credentials in local files.
