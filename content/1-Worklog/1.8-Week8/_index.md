---
title: "Week 8 Worklog"
date: 2026-06-05
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---


### Week 8 Objectives:

* Design the overall system architecture for the Business, Booking & Admin platform.
* Model the database schema covering all three modules.
* Define RESTful API endpoints for the entire application.
* Plan the frontend component hierarchy and routing structure.
* Set up the development environment and project scaffolding.

### Tasks to be carried out this week:
| Day | Task | Start Date | Completion Date | Reference Material |
| --- | ---- | ---------- | --------------- | ------------------ |
| 2 | - Design system architecture: 3-tier architecture <br>&emsp; + Presentation Tier: React SPA <br>&emsp; + Application Tier: Node.js/Express REST API <br>&emsp; + Data Tier: PostgreSQL + S3 <br> - AWS integration planning: Cognito (auth), S3 (images), Lambda (serverless tasks), CloudFront (CDN) | 05/06/2026 | 05/06/2026 | AWS Well-Architected Framework |
| 3 | - Database schema design - Core tables: <br>&emsp; + **Users**: id, email, password_hash, role (customer/business_owner/admin), status, created_at <br>&emsp; + **Businesses**: id, owner_id, name, description, logo_url, verified_at <br>&emsp; + **Places**: id, business_id, name, address, category, images, status (pending/approved/locked) <br>&emsp; + **Bookings**: id, user_id, place_id, date, time, guests, status (pending/confirmed/cancelled/completed) <br>&emsp; + **Reviews**: id, user_id, place_id, rating, comment, business_reply <br>&emsp; + **Reports**: id, reporter_id, review_id, reason, status, resolved_by | 06/06/2026 | 06/06/2026 | Prisma Documentation, PostgreSQL Docs |
| 4 | - Define table relationships and constraints <br> - Design ERD (Entity Relationship Diagram) with foreign keys and indexes <br> - Create database migration scripts using Prisma Migrate <br> - Seed database with sample data for testing | 07/06/2026 | 07/06/2026 | draw.io (ERD tool), Prisma Migrate |
| 5 | - API endpoint design (RESTful): 30+ endpoints across 3 modules <br>&emsp; + **Auth**: POST /auth/register, POST /auth/login, POST /auth/refresh <br>&emsp; + **Business**: GET/POST /businesses, PUT /businesses/:id, POST /businesses/:id/claim, GET /businesses/:id/stats <br>&emsp; + **Places**: GET /places, GET /places/:id, POST /places, PUT /places/:id, PATCH /places/:id/status <br>&emsp; + **Bookings**: GET/POST /bookings, GET /bookings/:id, PATCH /bookings/:id/cancel, PATCH /bookings/:id/status <br>&emsp; + **Reviews**: GET /places/:id/reviews, POST /reviews, PUT /reviews/:id/reply <br>&emsp; + **Admin**: GET /admin/dashboard, GET/PATCH /admin/users, GET/PATCH /admin/places, GET/PATCH /admin/claims, GET/PATCH /admin/reports | 08/06/2026 | 08/06/2026 | OpenAPI/Swagger Specification |
| 6 | - Frontend component hierarchy and routing with React Router v6: <br>&emsp; + Layout components: Navbar, Sidebar, Footer <br>&emsp; + Auth pages: Login, Register <br>&emsp; + Business Owner pages: Dashboard, ClaimListing, MyListings, BusinessInfo, ReviewManagement <br>&emsp; + Booking pages: BookingPage, MyBookings, BookingDetail <br>&emsp; + Admin pages: Dashboard, UserManagement, PlaceManagement, ReportManagement <br> - Set up project scaffolding: Vite + React + TypeScript, ESLint + Prettier config, Tailwind CSS theme | 09/06/2026 | 09/06/2026 | React Router v6 Docs, Tailwind CSS Docs |


### Week 8 Achievements:

* ✅ Designed a scalable 3-tier architecture with clear separation of concerns and AWS services integration.
* ✅ Completed database schema with 6 core tables, proper indexing, and all necessary foreign key relationships.
* ✅ Created comprehensive ERD documenting all table relationships and constraints.
* ✅ Defined 30+ RESTful API endpoints with request/response schemas documented in OpenAPI format.
* ✅ Established frontend component tree with 15+ route definitions and reusable layout components.
* ✅ Scaffolded the React project with Vite, TypeScript, Tailwind CSS, ESLint, and Prettier - ready for development.
* ✅ Successfully ran Prisma migrations to create the development database on AWS RDS.
