---
title: "Worklog Tuần 8"
date: 2026-06-05
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---


### Mục tiêu tuần 8:

* Thiết kế kiến trúc tổng thể cho nền tảng Business, Booking & Admin.
* Mô hình hóa sơ đồ cơ sở dữ liệu cho cả ba phân hệ.
* Định nghĩa các API endpoint theo chuẩn RESTful cho toàn bộ ứng dụng.
* Lập kế hoạch phân cấp component frontend và cấu trúc routing.
* Thiết lập môi trường phát triển và khung dự án (project scaffolding).

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | - Thiết kế kiến trúc hệ thống: kiến trúc 3 tầng <br>&emsp; + Tầng Trình bày: React SPA <br>&emsp; + Tầng Ứng dụng: Node.js/Express REST API <br>&emsp; + Tầng Dữ liệu: PostgreSQL + S3 <br> - Lập kế hoạch tích hợp AWS: Cognito (xác thực), S3 (hình ảnh), Lambda (tác vụ serverless), CloudFront (CDN) | 05/06/2026 | 05/06/2026 | AWS Well-Architected Framework |
| 3 | - Thiết kế sơ đồ cơ sở dữ liệu - Các bảng chính: <br>&emsp; + **Users**: id, email, password_hash, role (customer/business_owner/admin), status, created_at <br>&emsp; + **Businesses**: id, owner_id, name, description, logo_url, verified_at <br>&emsp; + **Places**: id, business_id, name, address, category, images, status (pending/approved/locked) <br>&emsp; + **Bookings**: id, user_id, place_id, date, time, guests, status (pending/confirmed/cancelled/completed) <br>&emsp; + **Reviews**: id, user_id, place_id, rating, comment, business_reply <br>&emsp; + **Reports**: id, reporter_id, review_id, reason, status, resolved_by | 06/06/2026 | 06/06/2026 | Prisma Documentation, PostgreSQL Docs |
| 4 | - Xác định quan hệ giữa các bảng và ràng buộc toàn vẹn <br> - Thiết kế ERD (Sơ đồ Quan hệ Thực thể) với khóa ngoại và chỉ mục <br> - Tạo migration scripts sử dụng Prisma Migrate <br> - Seed dữ liệu mẫu vào database để phục vụ testing | 07/06/2026 | 07/06/2026 | draw.io (công cụ vẽ ERD), Prisma Migrate |
| 5 | - Thiết kế API endpoint (RESTful): 30+ endpoints trên 3 phân hệ <br>&emsp; + **Auth**: POST /auth/register, POST /auth/login, POST /auth/refresh <br>&emsp; + **Business**: GET/POST /businesses, PUT /businesses/:id, POST /businesses/:id/claim, GET /businesses/:id/stats <br>&emsp; + **Places**: GET /places, GET /places/:id, POST /places, PUT /places/:id, PATCH /places/:id/status <br>&emsp; + **Bookings**: GET/POST /bookings, GET /bookings/:id, PATCH /bookings/:id/cancel, PATCH /bookings/:id/status <br>&emsp; + **Reviews**: GET /places/:id/reviews, POST /reviews, PUT /reviews/:id/reply <br>&emsp; + **Admin**: GET /admin/dashboard, GET/PATCH /admin/users, GET/PATCH /admin/places, GET/PATCH /admin/claims, GET/PATCH /admin/reports | 08/06/2026 | 08/06/2026 | OpenAPI/Swagger Specification |
| 6 | - Phân cấp component frontend và routing với React Router v6: <br>&emsp; + Layout components: Navbar, Sidebar, Footer <br>&emsp; + Trang Auth: Login, Register <br>&emsp; + Trang Business Owner: Dashboard, ClaimListing, MyListings, BusinessInfo, ReviewManagement <br>&emsp; + Trang Booking: BookingPage, MyBookings, BookingDetail <br>&emsp; + Trang Admin: Dashboard, UserManagement, PlaceManagement, ReportManagement <br> - Thiết lập khung dự án: Vite + React + TypeScript, cấu hình ESLint + Prettier, theme Tailwind CSS | 09/06/2026 | 09/06/2026 | React Router v6 Docs, Tailwind CSS Docs |


### Kết quả đạt được tuần 8:

* ✅ Thiết kế kiến trúc 3 tầng có khả năng mở rộng với phân tách rõ ràng và tích hợp các dịch vụ AWS.
* ✅ Hoàn thành sơ đồ cơ sở dữ liệu với 6 bảng chính, đánh chỉ mục phù hợp và tất cả các quan hệ khóa ngoại cần thiết.
* ✅ Tạo ERD toàn diện ghi nhận tất cả các mối quan hệ và ràng buộc giữa các bảng.
* ✅ Định nghĩa 30+ RESTful API endpoint với request/response schema được ghi nhận ở định dạng OpenAPI.
* ✅ Thiết lập cây component frontend với 15+ route và các layout component có thể tái sử dụng.
* ✅ Khởi tạo dự án React với Vite, TypeScript, Tailwind CSS, ESLint và Prettier - sẵn sàng cho phát triển.
* ✅ Chạy thành công Prisma migrations để tạo database phát triển trên AWS RDS.
