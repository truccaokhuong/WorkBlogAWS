---
title: "Nhật ký Tuần 8"
date: 2026-06-05
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

### Mục tiêu tuần 8

* Thiết kế kiến trúc tổng thể cho nền tảng doanh nghiệp, đặt chỗ và quản trị.
* Thiết kế lược đồ cơ sở dữ liệu và quan hệ giữa các bảng.
* Định nghĩa các điểm cuối API theo chuẩn REST.
* Lập kế hoạch phân cấp thành phần giao diện và cấu trúc định tuyến.
* Thiết lập khung dự án và quy ước phát triển chung.

### Các công việc cần triển khai trong tuần này

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | Thiết kế kiến trúc ba tầng: React cho tầng trình bày, Node.js/Express cho tầng ứng dụng, PostgreSQL và S3 cho tầng dữ liệu. Lập kế hoạch tích hợp Cognito, S3, Lambda và CloudFront. | 05/06/2026 | 05/06/2026 | AWS Well-Architected Framework |
| 3 | Thiết kế các bảng `Users`, `Businesses`, `Places`, `Bookings`, `Reviews` và `Reports`, bao gồm trường dữ liệu, trạng thái và khóa liên kết cần thiết. | 06/06/2026 | 06/06/2026 | Tài liệu Prisma, PostgreSQL |
| 4 | Xác định quan hệ và ràng buộc toàn vẹn; hoàn thiện sơ đồ quan hệ thực thể; tạo tập lệnh di chuyển lược đồ bằng Prisma Migrate và dữ liệu mẫu phục vụ kiểm thử. | 07/06/2026 | 07/06/2026 | draw.io, Prisma Migrate |
| 5 | Định nghĩa hơn 30 điểm cuối API cho xác thực, doanh nghiệp, địa điểm, đặt chỗ, đánh giá và quản trị; mô tả yêu cầu và phản hồi bằng OpenAPI. | 08/06/2026 | 08/06/2026 | Đặc tả OpenAPI/Swagger |
| 6 | Thiết kế cây thành phần và định tuyến bằng React Router v6; tạo bố cục chung, các trang xác thực, doanh nghiệp, đặt chỗ và quản trị; thiết lập Vite, React, TypeScript, ESLint, Prettier và Tailwind CSS. | 09/06/2026 | 09/06/2026 | Tài liệu React Router và Tailwind CSS |

### Kết quả đạt được tuần 8

* ✅ Hoàn thiện sơ đồ kiến trúc ba tầng và kế hoạch tích hợp dịch vụ AWS.
* ✅ Thiết kế lược đồ gồm sáu bảng chính với khóa ngoại, chỉ mục và quy tắc toàn vẹn.
* ✅ Hoàn thành sơ đồ quan hệ thực thể, tập lệnh di chuyển lược đồ và dữ liệu mẫu.
* ✅ Định nghĩa hơn 30 điểm cuối API cùng lược đồ yêu cầu và phản hồi trong OpenAPI.
* ✅ Thiết lập cây thành phần giao diện với hơn 15 tuyến và các bố cục dùng chung.
* ✅ Khởi tạo khung dự án, quy tắc định dạng và quy trình phát triển thống nhất cho nhóm.
