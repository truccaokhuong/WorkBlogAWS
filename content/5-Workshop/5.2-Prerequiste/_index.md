---
title: "Architecture Description"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 5.2. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

### Overall Architecture

The VTrips architecture follows a serverless-first approach with clear separation between frontend, API, compute, data storage, messaging, and monitoring layers. Users access the application through the frontend, while business requests go through API Gateway and are handled by the Lambda API Handler.

![VTrips architecture](/images/5-Workshop/target-architecture.jpg)

### Deployed MVP Architecture

```mermaid
flowchart LR
  U[Browser] -->|HTTPS| API[Amazon API Gateway]
  API --> L[AWS Lambda<br/>Node.js 20 + Express]
  L --> RDS[(Amazon RDS<br/>PostgreSQL)]
  L --> REDIS[(ElastiCache<br/>Redis)]
  L --> S3[Amazon S3<br/>Artifacts & Images]
  CW[CloudWatch Logs] <-. logs .-> L
  IAM[IAM Role & Policies] -. permissions .-> L
```

![Lambda overview](/images/5-Workshop/02-lambda-overview.png)

### AWS Service Responsibilities

| AWS service | Responsibility |
| --- | --- |
| API Gateway | Public HTTPS entry point and request routing to Lambda |
| Lambda | TypeScript/Node.js API runtime and business logic |
| RDS PostgreSQL | Transactional data for users, places, trips, reviews, and bookings |
| ElastiCache Redis | Hot data cache and short-lived application state |
| S3 | Lambda deployment artifacts and uploaded images |
| CloudWatch | Logs and diagnostics |
| IAM | Least-privilege access control for Lambda |

![RDS overview](/images/5-Workshop/08-rds-overview.png)

![Redis overview](/images/5-Workshop/10-redis-overview.png)

### Main Request Flow

For an authenticated API request, the browser sends an HTTPS request with a Bearer token to API Gateway. API Gateway invokes Lambda, Lambda validates input, authorizes the user, queries or updates PostgreSQL/Redis/S3, and returns a JSON response to the frontend.

```mermaid
sequenceDiagram
  participant B as Browser
  participant G as API Gateway
  participant L as Lambda API
  participant D as PostgreSQL
  B->>G: HTTPS request with Bearer token
  G->>L: Invoke route handler
  L->>L: Validate input and authorize user
  L->>D: Query or update data
  D-->>L: Result
  L-->>G: JSON response
  G-->>B: HTTPS response
```

### Image Upload Flow

1. An authenticated user requests an upload URL from the API.
2. Lambda validates ownership and generates a short-lived S3 presigned URL.
3. The browser uploads the file directly to S3.
4. The frontend stores or displays the resulting image URL in the related place/review.

This keeps AWS credentials out of the browser and avoids sending large files through Lambda.

![API Gateway routes](/images/5-Workshop/06-api-gateway-routes.png)

![S3 artifact bucket](/images/5-Workshop/11-s3-artifact-bucket.png)

### Security, Logging, and Cost Optimization

* RDS and Redis should stay in private subnets and should not be exposed directly to the Internet.
* Database/cache Security Groups should allow inbound traffic only from the Lambda Security Group.
* Secrets such as database URLs and JWT secrets must not be committed to source code.
* Lambda execution roles should only have the required S3, log group, and resource permissions.
* API Gateway should configure CORS, throttling, and production frontend origin restrictions.
* CloudWatch Logs help debug Lambda errors, latency, timeouts, and database/cache connectivity issues.
* S3 lifecycle policies and log retention should be configured to control costs.

![Lambda VPC configuration](/images/5-Workshop/04-lambda-vpc.png)

![Lambda permissions](/images/5-Workshop/05-lambda-permissions.png)

![RDS network configuration](/images/5-Workshop/09-rds-network.png)
