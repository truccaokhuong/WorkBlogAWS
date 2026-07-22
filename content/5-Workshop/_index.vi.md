---
title: "Hướng dẫn triển khai"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5. </b> "
---

Chương này hướng dẫn triển khai dự án **VTrips** trên AWS, dựa trên tài liệu của nhóm, ảnh chụp quá trình triển khai và sơ đồ kiến trúc hệ thống.

Nội dung được trình bày theo trình tự: bối cảnh và mục tiêu dự án, kiến trúc, yêu cầu tiên quyết, các bước triển khai, kiểm thử, trình diễn sản phẩm và dọn dẹp tài nguyên.

**5.1:** [Tổng quan](5.1-Workshop-overview/)

Giới thiệu mục tiêu, phạm vi sản phẩm khả dụng tối thiểu (MVP), các phân hệ đã hoàn thành và tiêu chí thành công của VTrips.

**5.2:** [Mô tả kiến trúc](5.2-Prerequiste/)

Giải thích sơ đồ kiến trúc, các tầng hệ thống, luồng yêu cầu chính, dịch vụ AWS, bảo mật, ghi log, giám sát và lộ trình phát triển cho môi trường vận hành thực tế.

**5.3:** [Yêu cầu tiên quyết](5.3-S3-vpc/)

Liệt kê tài khoản AWS, quyền IAM, Khu vực AWS, công cụ cục bộ và cấu hình môi trường cần thiết trước khi triển khai.

**5.4:** [Các bước triển khai](5.4-S3-onprem/)

Hướng dẫn biên dịch hệ thống phía máy chủ, chuẩn bị cơ sở dữ liệu, đóng gói Lambda, cấu hình môi trường chạy và API, sau đó phát hành giao diện người dùng.

**5.5:** [Kiểm thử và xác thực](5.5-Policy/)

Kiểm tra giao diện, xác thực người dùng, API, cơ sở dữ liệu, bộ nhớ đệm, tải ảnh, nhật ký CloudWatch và các vấn đề thường gặp sau triển khai.

**5.6:** [Trình diễn](5.6-Demo/)

Trình diễn VTrips qua luồng người dùng cuối và luồng dành cho doanh nghiệp, quản trị viên.

**5.7:** [Dọn dẹp](5.7-Cleanup/)
