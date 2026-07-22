---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

# Workshop

This chapter presents the workshop for deploying the **VTrips** project on AWS. The content is based on the team workshop README, deployment screenshots, and the system architecture diagram.

The workshop follows a clear progression: project context and goals, architecture description, prerequisites, deployment, validation, product demo, and resource clean-up.

**5.1:** [Overview](5.1-Workshop-overview/)

Introduces the workshop goal, MVP scope, completed modules, and success criteria for the VTrips system.

**5.2:** [Architecture Description](5.2-Prerequiste/)

Explains the architecture diagram, system layers, main request flows, AWS services used, security, logging/monitoring, and production evolution path.

**5.3:** [Prerequisite](5.3-S3-vpc/)

Lists the AWS account, IAM permissions, region, local tools, and environment configuration required before deployment.

**5.4:** [Deployment Guide](5.4-S3-onprem/)

Provides the deployment steps for building the backend, preparing the database, packaging Lambda, configuring runtime/API, and publishing the frontend.

**5.5:** [Test & Validation](5.5-Policy/)

Validates the frontend, authentication, APIs, database/cache, image upload, CloudWatch Logs, and common post-deployment issues.

**5.6:** [Demo](5.6-Demo/)

Demonstrates the VTrips product through end-user flows (home page, place search, saved places, trip creation, booking) and business/admin views (dashboard, place verification, admin overview).

**5.7:** [Clean-up](5.7-Cleanup/)
