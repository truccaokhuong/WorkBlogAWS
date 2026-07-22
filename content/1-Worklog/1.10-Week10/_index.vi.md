---
title: "Worklog Tuần 10"
date: 2026-06-19
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---


### Mục tiêu tuần 10:

* Triển khai các màn hình phân hệ Booking: Booking Page và My Bookings.
* Xây dựng giao diện xem chi tiết booking với timeline trạng thái.
* Phát triển chức năng hủy booking với luồng xác nhận.
* Triển khai quản lý state machine cho trạng thái booking.
* Tích hợp cập nhật booking real-time qua WebSocket.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | - **Trang Booking**: <br>&emsp; + Thiết kế date/time picker hiển thị các khung giờ trống <br>&emsp; + Xây dựng bộ chọn số lượng khách và input yêu cầu đặc biệt <br>&emsp; + Triển khai kiểm tra tình trạng còn chỗ real-time để tránh đặt trùng <br>&emsp; + Thêm tóm tắt giá và bước xác nhận trước khi gửi <br>&emsp; + Kết nối đến API endpoint POST /bookings với form validation | 19/06/2026 | 19/06/2026 | React DatePicker, Zod Validation |
| 3 | - **Trang My Bookings**: <br>&emsp; + Tạo danh sách booking với các tab trạng thái: Tất cả, Pending, Confirmed, Cancelled, Completed <br>&emsp; + Triển khai sắp xếp theo ngày, trạng thái và tên địa điểm <br>&emsp; + Xây dựng component thẻ booking với ảnh địa điểm, ngày, huy hiệu trạng thái và nút thao tác <br>&emsp; + Thêm hình minh họa trạng thái trống cho mỗi tab <br>&emsp; + Kết nối đến API endpoint GET /bookings?user_id=me với phân trang | 20/06/2026 | 20/06/2026 | React Query Pagination, Tailwind Tabs |
| 4 | - **Trang Chi tiết Booking**: <br>&emsp; + Thiết kế bố cục chi tiết với thông tin địa điểm, thông tin booking và timeline trạng thái <br>&emsp; + Xây dựng component stepper trạng thái: Pending → Confirmed → Completed (hoặc Cancelled) <br>&emsp; + Thêm tùy chọn chỉnh sửa booking dựa trên trạng thái hiện tại <br>&emsp; + Triển khai tạo mã QR cho xác nhận booking <br>&emsp; + Kết nối đến API endpoint GET /bookings/:id | 21/06/2026 | 21/06/2026 | QR Code Library, Timeline UI |
| 5 | - **Luồng Hủy Booking**: <br>&emsp; + Xây dựng dialog xác nhận với các tùy chọn lý do hủy <br>&emsp; + Triển khai logic nghiệp vụ: chỉ booking ở trạng thái Pending/Confirmed mới có thể hủy <br>&emsp; + Thêm hiển thị chính sách hoàn tiền cho việc hủy booking đã xác nhận <br>&emsp; + Triển khai optimistic UI update với rollback khi thất bại <br>&emsp; + Kết nối đến API endpoint PATCH /bookings/:id/cancel | 22/06/2026 | 22/06/2026 | React Modal, Optimistic Updates |
| 6 | - **Vòng đời Trạng thái Booking**: <br>&emsp; + Triển khai state machine: Pending → Confirmed (bởi chủ doanh nghiệp), Pending → Cancelled (bởi người dùng), Confirmed → Completed (sau ngày booking), Confirmed → Cancelled (bởi người dùng) <br>&emsp; + Thêm Socket.io listener cho thay đổi trạng thái real-time <br>&emsp; + Xây dựng toast notification cho cập nhật trạng thái <br>&emsp; + Viết automated tests cho tất cả các chuyển đổi trạng thái <br> - Kiểm thử end-to-end toàn bộ luồng booking | 23/06/2026 | 23/06/2026 | XState (state machine), Socket.io, React Hot Toast |


### Kết quả đạt được tuần 10:

* ✅ **Trang Booking** hoàn chỉnh với date/time picker, kiểm tra tình trạng còn chỗ real-time, chọn số khách và luồng booking nhiều bước.
* ✅ **Trang My Bookings** hoàn thành với lọc theo tab (5 tab trạng thái), phân trang infinite scroll và bố cục thẻ responsive.
* ✅ **Trang Chi tiết Booking** cung cấp thông tin booking toàn diện, timeline trạng thái trực quan và mã QR để check-in dễ dàng.
* ✅ **Luồng Hủy Booking** triển khai với thu thập lý do, xác thực quy tắc nghiệp vụ (chỉ trạng thái Pending/Confirmed) và optimistic UI updates.
* ✅ **State Machine Vòng đời Trạng thái** xử lý chính xác tất cả 4 chuyển đổi với cập nhật WebSocket real-time và toast notification.
* ✅ Đã viết 40+ unit test cho logic booking và 15 integration test cho toàn bộ luồng booking từ tạo đến hoàn thành.
* ✅ Tất cả các màn hình Booking đã triển khai lên staging và vượt qua QA review với không lỗi nghiêm trọng.
