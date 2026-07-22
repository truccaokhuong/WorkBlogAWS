---
title: "Proposal"
date: 2026-04-17
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Travel Platform
## An AWS-Based Platform for Travel Discovery and Trip Planning

### 1. Executive Summary

Travel Platform is a cloud-based web application that brings destination discovery, saved places, trip planning, itinerary management, reviews, and booking workflows into one system. It also provides dedicated functions for business owners and administrators. The project is designed for a five-member internship team, with a practical scope that can be implemented, demonstrated, and maintained within the internship period.

The frontend is delivered through Amazon CloudFront and Amazon S3. Amazon Cognito manages user authentication, while Amazon API Gateway provides the entry point for backend requests. AWS Lambda runs the application logic and background workers. Amazon RDS for PostgreSQL stores relational data, Amazon ElastiCache for Redis accelerates frequently accessed queries, and a separate S3 bucket stores uploaded images. Amazon EventBridge, Amazon SQS, and Amazon SNS support asynchronous processing, while Amazon CloudWatch provides centralized logs and monitoring.

The solution follows a modular serverless architecture. Responsibilities are separated into clear application modules, but the backend remains a unified platform behind one API layer. This design reduces operational complexity while allowing the team to gain hands-on experience with networking, serverless compute, managed databases, caching, messaging, security, and observability on AWS.

### 2. Problem Statement

#### Current Challenges

Travel planning is often fragmented across search engines, review platforms, maps, spreadsheets, and messaging applications. Users spend time moving information between tools, and it is difficult to keep saved places, daily schedules, booking details, and trip notes synchronized.

The platform must also solve several technical challenges:

- Store and retrieve place, review, booking, trip, and itinerary data efficiently.
- Protect user and business information with authentication and role-based access.
- Keep image uploads and background jobs from slowing down interactive requests.
- Support customer, business-owner, and administrator workflows in one consistent system.
- Maintain reasonable infrastructure costs for development and demonstration.

#### Proposed Solution

Travel Platform provides a unified experience where users can discover places, save favorites, create trips, arrange itinerary items by day, submit reviews, and manage bookings. Business owners can manage their listings and respond to customer activity, while administrators can review users, places, claims, and reports.

The platform uses managed AWS services to reduce infrastructure maintenance. CloudFront and S3 deliver the frontend, Cognito and API Gateway protect API access, and Lambda handles business logic. PostgreSQL stores transactional data, Redis caches frequently requested information, and S3 stores user-uploaded images. SQS, SNS, and EventBridge move slow or event-driven tasks to asynchronous workers.

#### Expected Benefits

- **Unified planning experience:** Saved places, trips, itineraries, reviews, and bookings are managed in one platform.
- **Responsive application:** Cache and asynchronous workers reduce latency for user-facing operations.
- **Secure architecture:** Authentication, least-privilege permissions, private data subnets, and encrypted secrets protect sensitive resources.
- **Scalable foundation:** Managed services can handle increasing traffic without maintaining long-running application servers.
- **Practical learning value:** The team applies real AWS architecture, infrastructure-as-code, monitoring, and cloud security practices.

### 3. Solution Architecture

![Travel Platform solution architecture](/images/5-Workshop/target-architecture.jpg)

The architecture is organized into layers, with each layer responsible for a specific part of the platform.

#### Edge and Frontend Layer

Users access the application through Amazon CloudFront. The static frontend is stored in Amazon S3 and distributed through CloudFront for faster delivery and controlled access to the origin.

#### Authentication and API Layer

Amazon Cognito manages sign-up, sign-in, and token-based authentication. Amazon API Gateway validates and routes authorized requests to the Lambda API Handler.

#### Compute Layer

The Lambda API Handler processes synchronous operations such as retrieving places, saving favorites, creating trips, updating itineraries, submitting reviews, and managing bookings. A separate Async Worker processes queued or event-driven tasks without delaying API responses.

#### Data Layer

Amazon RDS for PostgreSQL stores users, places, reviews, saved places, trips, itinerary items, bookings, claims, and administrative records. Redis caches high-read data and temporary values. User-uploaded images are stored in a dedicated S3 bucket.

#### Messaging and Monitoring Layer

Amazon SQS provides reliable buffering for background work, Amazon SNS supports event fan-out, and Amazon EventBridge coordinates scheduled or event-based workflows. Amazon CloudWatch collects logs, metrics, and alarms. IAM, KMS, Secrets Manager, and X-Ray strengthen access control, encryption, secret storage, and request tracing.

### 4. AWS Services Used

| AWS service | Purpose in the platform |
| --- | --- |
| Amazon CloudFront | Distributes the frontend and improves content delivery performance. |
| Amazon S3 | Hosts frontend assets and stores uploaded travel images. |
| Amazon Cognito | Provides user authentication and token-based access control. |
| Amazon API Gateway | Exposes secured API endpoints and routes requests to Lambda. |
| AWS Lambda | Runs the API Handler and asynchronous worker. |
| Amazon RDS for PostgreSQL | Stores relational and transactional application data. |
| Amazon ElastiCache for Redis | Caches frequently accessed data to reduce database load. |
| Amazon SQS | Queues background tasks for reliable processing. |
| Amazon SNS | Publishes notifications or events to multiple consumers. |
| Amazon EventBridge | Coordinates scheduled tasks and event-driven workflows. |
| Amazon CloudWatch | Centralizes logs, metrics, dashboards, and alarms. |
| AWS IAM | Enforces least-privilege permissions between services. |
| AWS KMS | Supports encryption for sensitive resources. |
| AWS Secrets Manager | Stores database credentials and application secrets. |
| AWS X-Ray | Traces requests through the API and dependent services. |

### 5. Component Design

#### Frontend Application

The responsive web interface provides place search, place details, saved places, trip creation, itinerary planning, reviews, bookings, business-owner pages, and administrative screens. Static assets are hosted in S3 and delivered through CloudFront.

#### Trip Planner Service

Trip Planner Service manages Saved Places, Trips, and Itinerary data. It validates user ownership, stores trip information, organizes activities by date and order, and provides APIs used by the corresponding frontend screens.

#### Platform API Handler

The main Lambda handler contains shared platform logic for users, places, reviews, bookings, business claims, and administration. It validates Cognito identity and permissions before accessing PostgreSQL or Redis.

#### Asynchronous Worker

The worker processes notifications, image-related tasks, synchronization jobs, and other operations received from SQS, SNS, or EventBridge. Failed messages can be retried or redirected to a dead-letter queue for investigation.

#### Data and Image Storage

PostgreSQL stores normalized application data and relationships. Redis stores cache entries and temporary values that can be reconstructed. S3 stores image files, while their metadata and ownership information remain in PostgreSQL.

### 6. Technical Implementation

#### Implementation Phases

1. **Requirements and design:** Define user roles, core workflows, data model, API contracts, and the AWS architecture.
2. **Infrastructure foundation:** Provision networking, security groups, Cognito, S3, CloudFront, API Gateway, Lambda, PostgreSQL, Redis, and monitoring resources with AWS CDK.
3. **Backend development:** Implement APIs for places, saved places, trips, itineraries, reviews, bookings, business functions, and administration.
4. **Frontend development:** Build the user, business-owner, and administrator interfaces and connect them to the APIs.
5. **Asynchronous integration:** Add SQS, SNS, and EventBridge workflows for background processing and notifications.
6. **Testing and deployment:** Run integration and end-to-end tests, review IAM and networking, optimize cost, fix defects, and deploy the final demonstration environment.

#### Technical Requirements

- **Frontend:** React, TypeScript, Tailwind CSS, responsive design, and authenticated API calls.
- **Backend:** TypeScript, AWS Lambda, AWS SDK, validation, and service-oriented application modules.
- **Data:** PostgreSQL, DynamoDB Single Table where appropriate for Trip Planner data, Redis caching, and S3 object storage.
- **Infrastructure:** AWS CDK for repeatable infrastructure deployment.
- **Security:** Amazon Cognito, IAM least privilege, encrypted secrets, private subnets for data services, and controlled S3 access.
- **Quality:** Automated tests, structured logging, CloudWatch alarms, and documented cleanup procedures.

### 7. Timeline and Milestones

| Period | Main activities |
| --- | --- |
| Weeks 1–2 | Learn AWS fundamentals, IAM, networking, and core compute services. |
| Weeks 3–4 | Practice storage, Lambda, DynamoDB, API Gateway, and serverless design. |
| Weeks 5–6 | Study managed databases, caching, monitoring, DNS, and supporting services. |
| Week 7 | Finalize team scope, user roles, requirements, and task assignments. |
| Week 8 | Design the system architecture, database model, and API contracts. |
| Week 9 | Implement business-owner and listing-management functions. |
| Week 10 | Implement booking and customer workflow functions. |
| Week 11 | Implement administrator dashboards and management functions. |
| Week 12 | Perform integration testing, fix defects, complete documentation, and prepare the final demonstration. |

### 8. Budget Estimation

The project targets a learning and demonstration environment. Costs should be minimized by using small resource sizes, short testing windows, Free Tier allowances where applicable, and immediate cleanup after demonstrations.

| Cost area | Cost-control approach |
| --- | --- |
| Lambda and API Gateway | Use on-demand execution and low demo traffic. |
| S3 and CloudFront | Store only necessary assets and apply suitable cache settings. |
| RDS PostgreSQL | Use a small Single-AZ instance during development. |
| Redis | Use the smallest practical cache node and stop testing promptly. |
| Messaging services | Keep SQS, SNS, and EventBridge message volume low. |
| CloudWatch | Set log retention and avoid unnecessary verbose logging. |
| Secrets and encryption | Create only the secrets and keys required by the application. |

AWS Budgets alerts should be configured before deployment. Unused databases, cache nodes, NAT-related resources, and test data must be removed after the project is completed.

### 9. Risk Assessment

| Risk | Impact | Mitigation |
| --- | --- | --- |
| Incorrect VPC or security-group configuration | High | Review subnet placement, routes, and inbound/outbound rules before integration. |
| Lambda cannot reach PostgreSQL or Redis | High | Test private connectivity early and monitor connection errors in CloudWatch. |
| Unauthorized access to data or images | High | Apply Cognito authorization, IAM least privilege, encryption, and controlled upload URLs. |
| Background messages fail repeatedly | Medium | Configure retries, dead-letter queues, idempotent handlers, and alarms. |
| Infrastructure cost exceeds the demo budget | Medium | Use AWS Budgets, small resources, limited test duration, and cleanup scripts. |
| Project scope becomes too large | Medium | Prioritize place discovery, saved places, trips, itineraries, reviews, and booking workflows. |

### 10. Expected Outcomes

The completed Travel Platform should provide a functional cloud-hosted demonstration where users can discover and save places, create trips, organize itineraries, submit reviews, and manage bookings. Business owners and administrators should be able to perform their assigned management workflows through dedicated interfaces.

The project should also demonstrate the team's ability to design AWS architecture, deploy infrastructure as code, secure API access, connect serverless compute to managed data services, use asynchronous messaging, monitor workloads, and collaborate effectively in a cloud development project.
