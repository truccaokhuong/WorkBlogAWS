---
title: "Test & Validation"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5.5. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

### Functional Checks

After each deployment, validate the main flows in a test environment:

| Flow | Expected result |
| --- | --- |
| Health check | API returns HTTP 200 and a valid payload |
| Register and login | API returns valid session tokens |
| Browse/search places | Filtering and pagination return correct data |
| Create/update review | Review persists and aggregate rating refreshes |
| Create trip | Day, order, and notes for each place persist |
| Share public trip | Public URL works without authentication |
| Create booking | Booking follows the expected status workflow |
| Upload place image | Browser uploads through a short-lived S3 presigned URL |

Example health check:

```powershell
curl.exe -i https://API_ID.execute-api.REGION.amazonaws.com/health
```

### API Gateway Validation

Check route configuration and stage deployment to make sure API Gateway points to the correct Lambda integration.

![API Gateway routes](/images/5-Workshop/06-api-gateway-routes.png)

![API Gateway stage](/images/5-Workshop/07-api-stage.png)

### Logs and Diagnostics

For a failed request, investigate in this order:

1. Open the Lambda CloudWatch log group.
2. Select the newest log stream for the request timestamp.
3. Identify whether the failure occurred in validation, authorization, database access, Redis access, or S3 signing.
4. Fix the smallest responsible configuration or code unit.
5. Redeploy and repeat the same test.

![CloudWatch log stream](/images/5-Workshop/21-cloudwatch-log.png)

### Signals to Monitor

* Lambda errors, duration, throttles, and timeouts.
* API Gateway latency and 4xx/5xx responses.
* RDS CPU, connection count, and connection errors.
* Redis hit rate and connection status.
* S3 upload failures.
* CloudWatch log retention to avoid unnecessary costs.
