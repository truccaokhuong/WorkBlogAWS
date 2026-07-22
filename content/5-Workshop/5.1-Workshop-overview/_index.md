---
title: "Overview"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---
### Workshop Goal

This workshop guides the deployment and operation of **VTrips**, a **serverless-first** travel platform on AWS. The system allows users to register/login, browse places, write reviews, save places, plan itineraries, and handle business/booking workflows.

The deployed MVP focuses on the core AWS services: AWS Lambda, Amazon API Gateway, Amazon RDS PostgreSQL, Amazon ElastiCache Redis, Amazon S3, IAM, VPC networking, and Amazon CloudWatch.

![VTrips frontend](/images/5-Workshop/frontend-home.png)

### Main Modules

| Module | Main capabilities | API endpoints |
| --- | --- | ---: |
| Authentication | Register, login, token refresh, password recovery, profile | 7 |
| Places | Browse, search, CRUD, image upload, view tracking | 7 |
| Reviews | Ratings, helpful votes, reports, owner replies | 7 |
| Trips | Saved places, itinerary planning, public sharing | 12 |
| Business and Bookings | Business claims, bookings, status workflow, admin views | 10 |

The current implementation contains **43 documented API endpoints**.

### Deployment Scope

The MVP uses the following configured components:

* API Gateway as the public HTTPS entry point.
* Lambda for Node.js/Express API runtime and business logic.
* RDS PostgreSQL for transactional data.
* ElastiCache Redis for cache and short-lived state.
* S3 for deployment artifacts and uploaded images.
* CloudWatch for logs and diagnostics.
* IAM for least-privilege access control.

Services such as CloudFront, Cognito, SQS, SNS, SES, EventBridge, X-Ray, KMS, Secrets Manager, WAF, and OpenSearch are considered production-growth options. They should only be claimed as deployed when the corresponding AWS environment has been configured.

### Success Criteria

* Backend builds successfully and Lambda is updated with the new artifact.
* API Gateway invokes Lambda and returns valid responses.
* Lambda connects to RDS PostgreSQL, Redis, and S3 in the deployed environment.
* Frontend can call the deployed API with correct CORS/token behavior.
* Core flows such as login, place browsing, trip creation, image upload, and log inspection work reliably.
