---
title: "Clean-up"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

### Clean-up Principles

Before deleting resources, create backups for any data that must be retained. Never delete a shared VPC, production database, or shared S3 bucket solely because it appears in this workshop.

### Recommended Deletion Order

1. Disable frontend hosting and custom domain mappings if any.
2. Remove API Gateway after confirming that no clients still use the endpoint.
3. Delete Lambda functions, unused layers, and log groups according to retention policy.
4. Empty workshop-specific artifact/test-upload S3 buckets, then delete them if no longer needed.
5. Take a final snapshot before deleting the test RDS database.
6. Delete ElastiCache Redis resources.
7. Remove Security Groups, IAM roles/policies, and VPC resources only after confirming they are not shared.

### Post-clean-up Checks

* Check AWS Billing/Cost Explorer after 24 hours to ensure there is no abnormal cost.
* Check for leftover CloudWatch log groups.
* Check unused S3 buckets, RDS snapshots, and Elastic IPs.
* Record the deleted resource list in the handoff report.
