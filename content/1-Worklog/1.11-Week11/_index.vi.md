---
title: "Worklog Tuần 11"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 1.11. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}


### Mục tiêu tuần 11:

* Triển khai các màn hình phân hệ Admin: Dashboard, Quản lý User, Quản lý Place và Quản lý Report.
* Xây dựng admin dashboard toàn diện với các chỉ số và biểu đồ toàn hệ thống.
* Phát triển quản lý người dùng với tìm kiếm, lọc và chức năng khóa/mở khóa.
* Tạo luồng phê duyệt địa điểm và giao diện quản lý địa điểm.
* Triển khai luồng phê duyệt claim và xử lý report.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | - **Admin Dashboard**: <br>&emsp; + Thiết kế bố cục dashboard với các chỉ số tổng quan: Tổng Users, Tổng Places, Tổng Bookings, Tổng Doanh thu <br>&emsp; + Xây dựng biểu đồ tương tác: tăng trưởng người dùng (line chart), xu hướng booking (area chart), phân bố địa điểm theo danh mục (donut chart), tổng quan doanh thu (bar chart) <br>&emsp; + Triển khai feed hoạt động gần đây hiển thị các hành động admin mới nhất <br>&emsp; + Thêm bộ lọc khoảng thời gian cho tất cả các chỉ số dashboard <br>&emsp; + Kết nối đến API endpoint GET /admin/dashboard | 26/06/2026 | 26/06/2026 | Recharts, React DatePicker |
| 3 | - **Trang Quản lý User**: <br>&emsp; + Xây dựng bảng user với các cột: ID, Tên, Email, Vai trò, Trạng thái, Ngày tham gia, Thao tác <br>&emsp; + Triển khai tìm kiếm theo tên/email và lọc theo vai trò (Customer, Business Owner, Admin) và trạng thái (Active, Locked) <br>&emsp; + Thêm chức năng khóa/mở khóa tài khoản user với dialog xác nhận <br>&emsp; + Xây dựng modal chi tiết user hiển thị hồ sơ đầy đủ và lịch sử hoạt động <br>&emsp; + Triển khai phân trang với kích thước trang có thể điều chỉnh (10/25/50) <br>&emsp; + Kết nối đến API endpoints GET /admin/users và PATCH /admin/users/:id | 27/06/2026 | 27/06/2026 | React Table, Modal UI |
| 4 | - **Trang Quản lý Place**: <br>&emsp; + Tạo hàng đợi phê duyệt địa điểm với các địa điểm pending được liệt kê trước <br>&emsp; + Xây dựng bảng đánh giá địa điểm hiển thị chi tiết địa điểm, hình ảnh và thông tin chủ sở hữu <br>&emsp; + Triển khai hành động approve/reject với input lý do cho từ chối <br>&emsp; + Thêm chức năng khóa/mở khóa cho các địa điểm đã được phê duyệt <br>&emsp; + Xây dựng tìm kiếm và lọc theo danh mục, trạng thái (Pending, Approved, Locked) <br>&emsp; + Kết nối đến API endpoints GET /admin/places và PATCH /admin/places/:id | 28/06/2026 | 28/06/2026 | React Hook Form, Image Gallery |
| 5 | - **Luồng Phê duyệt Claim**: <br>&emsp; + Xây dựng bảng yêu cầu claim với thông tin doanh nghiệp, địa điểm claim, tài liệu xác minh và trạng thái <br>&emsp; + Triển khai trình xem tài liệu cho các file xác minh đã tải lên (PDF, hình ảnh) <br>&emsp; + Thêm hành động approve/reject với lý do từ chối và thông báo đến chủ doanh nghiệp <br>&emsp; + Xây dựng theo dõi lịch sử claim hiển thị tất cả các claim trước đây với kết quả <br>&emsp; + Kết nối đến API endpoints GET /admin/claims và PATCH /admin/claims/:id | 29/06/2026 | 29/06/2026 | PDF Viewer, File Preview |
| 6 | - **Trang Quản lý Report**: <br>&emsp; + Tạo hàng đợi report với sắp xếp theo mức độ nghiêm trọng và ngày báo cáo <br>&emsp; + Xây dựng bảng điều tra report: nội dung review gốc, thông tin người báo cáo, lý do báo cáo và nút hành động <br>&emsp; + Triển khai hành động resolve/dismiss với ghi chú của admin <br>&emsp; + Thêm thông báo tự động đến người báo cáo và tác giả review khi có kết quả xử lý <br>&emsp; + Xây dựng thống kê report: tổng report, tỷ lệ đã giải quyết, thời gian giải quyết trung bình <br>&emsp; + Kết nối đến API endpoints GET /admin/reports và PATCH /admin/reports/:id <br> - Triển khai RBAC middleware để giới hạn route admin chỉ cho vai trò admin | 30/06/2026 | 30/06/2026 | RBAC Middleware, Notification Service |


### Kết quả đạt được tuần 11:

* ✅ **Admin Dashboard** đã triển khai với 4 thẻ chỉ số tổng quan, 4 loại biểu đồ tương tác, feed hoạt động real-time và lọc theo khoảng thời gian.
* ✅ **Quản lý User** hoàn chỉnh với tìm kiếm, đa bộ lọc, khóa/mở khóa tài khoản, modal chi tiết user với lịch sử hoạt động và phân trang phía server.
* ✅ **Quản lý Place** hoàn thành với hàng đợi phê duyệt, bảng đánh giá chi tiết, hành động approve/reject/lock và khả năng tìm kiếm/lọc toàn diện.
* ✅ **Luồng Phê duyệt Claim** triển khai với trình xem tài liệu xác minh, approve/reject kèm thông báo và theo dõi lịch sử claim đầy đủ.
* ✅ **Quản lý Report** cung cấp hàng đợi report với sắp xếp theo mức độ, bảng điều tra, hành động resolve/dismiss và dashboard thống kê kết quả xử lý.
* ✅ RBAC middleware đã tích hợp thành công, đảm bảo chỉ user có vai trò admin mới truy cập được các route admin.
* ✅ Đã viết 50+ unit test bao phủ tất cả các luồng admin bao gồm edge cases (hành động đồng thời, chuyển đổi trạng thái không hợp lệ).
* ✅ Tất cả các màn hình Admin đã triển khai lên staging và nhận được phản hồi tích cực từ nhóm trong buổi demo.
