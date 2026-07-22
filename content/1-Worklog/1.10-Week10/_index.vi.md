---
title: "Nhật ký Tuần 10"
date: 2026-06-19
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu tuần 10

* Triển khai các màn hình thuộc phân hệ đặt chỗ.
* Xây dựng luồng tạo và quản lý lượt đặt chỗ.
* Phát triển trang chi tiết, luồng hủy và vòng đời trạng thái.
* Đồng bộ thay đổi trạng thái theo thời gian thực.

### Các công việc cần triển khai trong tuần này

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | Xây dựng **Trang đặt chỗ** với bộ chọn ngày giờ, số lượng khách, yêu cầu đặc biệt, kiểm tra chỗ trống theo thời gian thực, tóm tắt giá và xác nhận trước khi gửi; kết nối `POST /bookings`. | 19/06/2026 | 19/06/2026 | React DatePicker, Zod |
| 3 | Xây dựng **Các lượt đặt chỗ của tôi** với các thẻ Tất cả, Chờ xử lý, Đã xác nhận, Đã hủy và Hoàn thành; thêm sắp xếp, phân trang và kết nối `GET /bookings?user_id=me`. | 20/06/2026 | 20/06/2026 | React Query, Tailwind CSS |
| 4 | Xây dựng **Trang chi tiết đặt chỗ** với thông tin địa điểm, dòng thời gian trạng thái, tùy chọn chỉnh sửa và mã QR xác nhận; kết nối `GET /bookings/:id`. | 21/06/2026 | 21/06/2026 | Thư viện mã QR, thành phần dòng thời gian |
| 5 | Xây dựng **Luồng hủy đặt chỗ** với hộp thoại xác nhận, lý do hủy, quy tắc nghiệp vụ, chính sách hoàn tiền và cơ chế khôi phục giao diện khi cập nhật thất bại; kết nối `PATCH /bookings/:id/cancel`. | 22/06/2026 | 22/06/2026 | React Modal, cập nhật lạc quan |
| 6 | Triển khai **vòng đời trạng thái đặt chỗ** từ chờ xử lý đến xác nhận, hoàn thành hoặc hủy; lắng nghe thay đổi bằng Socket.io, hiển thị thông báo và viết kiểm thử tự động, kiểm thử xuyên suốt toàn bộ luồng. | 23/06/2026 | 23/06/2026 | XState, Socket.io, React Hot Toast |

### Kết quả đạt được tuần 10

* ✅ Hoàn thành trang đặt chỗ nhiều bước và kiểm tra chỗ trống theo thời gian thực.
* ✅ Hoàn thành danh sách đặt chỗ với năm trạng thái, phân trang và bố cục thích ứng.
* ✅ Hoàn thành trang chi tiết, dòng thời gian trạng thái và mã QR.
* ✅ Hoàn thành luồng hủy với xác thực quy tắc nghiệp vụ và xử lý khi cập nhật thất bại.
* ✅ Đồng bộ trạng thái theo thời gian thực và hiển thị thông báo cho người dùng.
* ✅ Viết hơn 40 kiểm thử đơn vị, 15 kiểm thử tích hợp và triển khai các màn hình lên môi trường thử nghiệm để đánh giá chất lượng.
