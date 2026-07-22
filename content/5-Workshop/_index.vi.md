---
title: "Workshop"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

# Workshop

Chương này trình bày workshop triển khai dự án **VTrips** trên AWS. Nội dung dựa trên README workshop của nhóm, ảnh chụp màn hình triển khai và sơ đồ kiến trúc hệ thống.

Workshop được tổ chức theo trình tự rõ ràng: bối cảnh và mục tiêu dự án, mô tả kiến trúc, yêu cầu tiên quyết, triển khai, kiểm thử, demo sản phẩm và dọn dẹp tài nguyên.

**5.1:** [Tổng quan](5.1-Workshop-overview/)

Giới thiệu mục tiêu workshop, phạm vi MVP, các module đã hoàn thành và tiêu chí thành công cho hệ thống VTrips.

**5.2:** [Mô tả Kiến trúc](5.2-Prerequiste/)

Giải thích sơ đồ kiến trúc, các tầng hệ thống, luồng request chính, dịch vụ AWS sử dụng, bảo mật, logging/monitoring và lộ trình tiến hóa production.

**5.3:** [Yêu cầu tiên quyết](5.3-S3-vpc/)

Liệt kê tài khoản AWS, quyền IAM, region, công cụ local và cấu hình môi trường cần thiết trước khi triển khai.

**5.4:** [Hướng dẫn Triển khai](5.4-S3-onprem/)

Cung cấp các bước triển khai: build backend, chuẩn bị database, đóng gói Lambda, cấu hình runtime/API và publish frontend.

**5.5:** [Kiểm thử & Xác thực](5.5-Policy/)

Xác thực frontend, authentication, APIs, database/cache, tải ảnh, CloudWatch Logs và các vấn đề phổ biến sau triển khai.

**5.6:** [Demo](5.6-Demo/)

Demo sản phẩm VTrips qua luồng người dùng cuối (trang chủ, tìm kiếm, địa điểm đã lưu, tạo chuyến đi, đặt chỗ) và góc nhìn doanh nghiệp/quản trị (dashboard, xác minh địa điểm, tổng quan quản trị).

**5.7:** [Dọn dẹp](5.7-Cleanup/)
