---
title: "Nhật ký Tuần 11"
date: 2026-06-26
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Mục tiêu tuần 11

* Triển khai các màn hình thuộc phân hệ quản trị.
* Xây dựng bảng điều khiển với số liệu và biểu đồ toàn hệ thống.
* Phát triển chức năng quản lý người dùng, địa điểm, yêu cầu xác minh và báo cáo.
* Áp dụng kiểm soát truy cập theo vai trò cho toàn bộ tuyến quản trị.

### Các công việc cần triển khai trong tuần này

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | Xây dựng **Bảng điều khiển quản trị** với tổng số người dùng, địa điểm, lượt đặt chỗ, doanh thu; thêm biểu đồ tăng trưởng, xu hướng đặt chỗ, phân bố địa điểm, hoạt động gần đây và bộ lọc thời gian; kết nối `GET /admin/dashboard`. | 26/06/2026 | 26/06/2026 | Recharts, React DatePicker |
| 3 | Xây dựng **Trang quản lý người dùng** với tìm kiếm, bộ lọc vai trò và trạng thái, khóa hoặc mở khóa tài khoản, cửa sổ chi tiết, lịch sử hoạt động và phân trang; kết nối `GET /admin/users` và `PATCH /admin/users/:id`. | 27/06/2026 | 27/06/2026 | React Table, thư viện cửa sổ giao diện |
| 4 | Xây dựng **Trang quản lý địa điểm** với hàng đợi phê duyệt, bảng chi tiết, hành động chấp thuận hoặc từ chối, khóa hoặc mở khóa, tìm kiếm và lọc; kết nối `GET /admin/places` và `PATCH /admin/places/:id`. | 28/06/2026 | 28/06/2026 | React Hook Form, thư viện ảnh |
| 5 | Xây dựng **Luồng phê duyệt yêu cầu xác minh** với thông tin doanh nghiệp, tài liệu PDF hoặc hình ảnh, lý do từ chối, thông báo cho chủ doanh nghiệp và lịch sử xử lý; kết nối `GET /admin/claims` và `PATCH /admin/claims/:id`. | 29/06/2026 | 29/06/2026 | Trình xem PDF, xem trước tệp |
| 6 | Xây dựng **Trang quản lý báo cáo** với sắp xếp theo mức độ, bảng điều tra, hành động giải quyết hoặc bỏ qua, thông báo kết quả và thống kê xử lý; kết nối `GET /admin/reports` và `PATCH /admin/reports/:id`. Triển khai phần mềm trung gian RBAC để bảo vệ các tuyến quản trị. | 30/06/2026 | 30/06/2026 | RBAC, dịch vụ thông báo |

### Kết quả đạt được tuần 11

* ✅ Hoàn thành bảng điều khiển quản trị với chỉ số, biểu đồ, hoạt động gần đây và bộ lọc thời gian.
* ✅ Hoàn thành quản lý người dùng với tìm kiếm, lọc, khóa hoặc mở khóa và phân trang phía máy chủ.
* ✅ Hoàn thành hàng đợi phê duyệt và quản lý trạng thái địa điểm.
* ✅ Hoàn thành luồng phê duyệt yêu cầu xác minh cùng tài liệu và lịch sử xử lý.
* ✅ Hoàn thành quản lý báo cáo và thống kê kết quả xử lý.
* ✅ Tích hợp RBAC, viết hơn 50 kiểm thử đơn vị và triển khai các màn hình lên môi trường thử nghiệm.
