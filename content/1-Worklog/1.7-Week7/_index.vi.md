---
title: "Worklog Tuần 7"
date: 2026-05-29
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---


### Mục tiêu tuần 7:

* Thành lập nhóm đồ án và làm quen với tất cả thành viên.
* Nắm rõ phạm vi dự án: Business, Booking & Admin Service.
* Phân tích yêu cầu toàn diện cho cả ba phân hệ.
* Lựa chọn công nghệ cho frontend, backend và cơ sở dữ liệu.
* Phân công vai trò và trách nhiệm cụ thể cho từng thành viên.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | - Gặp gỡ các thành viên nhóm đồ án <br> - Xem xét hướng dẫn và kỳ vọng của dự án thực tập | 29/05/2026 | 29/05/2026 | Tóm tắt dự án, Hướng dẫn thực tập |
| 3 | - Trình bày tổng quan dự án: Nền tảng Business, Booking & Admin <br> - Thảo luận các tính năng cốt lõi và vai trò người dùng (Business Owner, Customer, Admin) | 30/05/2026 | 30/05/2026 | Tài liệu Yêu cầu Dự án |
| 4 | - Thu thập yêu cầu - **Phân hệ Business Owner:** <br>&emsp; + Đăng ký làm chủ doanh nghiệp <br>&emsp; + Claim địa điểm <br>&emsp; + Xem danh sách địa điểm đang quản lý <br>&emsp; + Cập nhật thông tin doanh nghiệp <br>&emsp; + Xem review mới <br>&emsp; + Phản hồi review <br>&emsp; + Xem thống kê cơ bản (lượt xem, số review, rating trung bình) | 31/05/2026 | 31/05/2026 | Tài liệu AWS, React Docs |
| 5 | - Thu thập yêu cầu - **Phân hệ Booking:** <br>&emsp; + Tạo booking <br>&emsp; + Xem danh sách booking của user <br>&emsp; + Xem chi tiết booking <br>&emsp; + Hủy booking <br>&emsp; + Quản lý trạng thái booking: Pending → Confirmed / Cancelled → Completed <br> - Thu thập yêu cầu - **Phân hệ Admin:** <br>&emsp; + Dashboard tổng quan <br>&emsp; + Quản lý user <br>&emsp; + Duyệt địa điểm mới <br>&emsp; + Duyệt claim business <br>&emsp; + Xử lý report review <br>&emsp; + Khóa/mở địa điểm <br>&emsp; + Khóa/mở tài khoản user | 01/06/2026 | 01/06/2026 | Figma (tham khảo UI), Tài liệu Thiết kế Hệ thống |
| 6 | - Thảo luận và lựa chọn công nghệ: <br>&emsp; + Frontend: React + Tailwind CSS <br>&emsp; + Backend: Node.js + Express <br>&emsp; + Database: PostgreSQL (AWS RDS) <br>&emsp; + Cloud: AWS (S3, Lambda, API Gateway, Cognito) <br> - Phân công nhiệm vụ: Cao Khuong Truc phụ trách 9 màn hình (Business Dashboard, Claim Listing, My Business Listings, Booking Page, My Bookings, Admin Dashboard, Admin User Management, Admin Place Management, Admin Report Management) <br> - Thiết lập Git repository và cấu trúc nhánh | 02/06/2026 | 02/06/2026 | GitHub, Jira Board |


### Kết quả đạt được tuần 7:

* ✅ Đã thành lập nhóm dự án 4 thành viên với các kênh giao tiếp rõ ràng (Slack, họp standup hàng tuần).
* ✅ Nắm vững phạm vi dự án trên ba phân hệ chính: Business Owner, Booking và Admin.
* ✅ Hoàn thành tài liệu yêu cầu chi tiết cho tất cả các tính năng, bao gồm cả yêu cầu chức năng và phi chức năng.
* ✅ Đã chốt công nghệ sử dụng:
  * **Frontend**: React 18 với TypeScript, Tailwind CSS, React Router v6, React Hook Form + Zod validation
  * **Backend**: Node.js với Express, Prisma ORM, JWT authentication, Socket.io cho cập nhật real-time
  * **Database**: PostgreSQL trên AWS RDS, Redis cho caching
  * **Hạ tầng Đám mây**: AWS S3 cho lưu trữ file, AWS Lambda cho serverless functions, AWS API Gateway, AWS Cognito cho xác thực
* ✅ Phân công nhiệm vụ rõ ràng: Tôi (Cao Khuong Truc) phụ trách 9 màn hình trải dài trên cả ba phân hệ.
* ✅ Khởi tạo Git repository với branch protection rules và thiết lập Jira board để theo dõi sprint.
* ✅ Tạo wireframe ban đầu và sơ đồ luồng người dùng cho các màn hình được phân công.
