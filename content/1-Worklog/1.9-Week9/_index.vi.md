---
title: "Worklog Tuần 9"
date: 2026-06-12
weight: 1
chapter: false
pre: " <b> 1.9. </b> "
---


### Mục tiêu tuần 9:

* Triển khai các màn hình phân hệ Business Owner: Dashboard, Claim Listing và My Business Listings.
* Xây dựng chức năng cập nhật thông tin doanh nghiệp.
* Phát triển tính năng quản lý review (xem review mới, phản hồi review).
* Tạo dashboard thống kê với biểu đồ cho chủ doanh nghiệp.
* Tích hợp AWS S3 để tải lên logo doanh nghiệp và hình ảnh.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | - **Giao diện Business Dashboard**: <br>&emsp; + Thiết kế bố cục dashboard với các thẻ thống kê (lượt xem, số review, rating trung bình) <br>&emsp; + Tích hợp API: GET /businesses/:id/stats <br>&emsp; + Xây dựng component biểu đồ sử dụng Recharts (biểu đồ cột cho lượt xem theo tháng, biểu đồ tròn cho phân bố review) <br>&emsp; + Thêm skeleton loading và xử lý trạng thái lỗi | 12/06/2026 | 12/06/2026 | Recharts Documentation, Tailwind UI |
| 3 | - **Trang Claim Listing**: <br>&emsp; + Xây dựng giao diện tìm kiếm địa điểm với bộ lọc danh mục và tự động hoàn thành vị trí <br>&emsp; + Triển khai form claim với tài liệu xác minh doanh nghiệp <br>&emsp; + Tích hợp AWS S3 presigned URLs để tải lên tài liệu <br>&emsp; + Thêm theo dõi trạng thái claim (pending → approved/rejected) <br>&emsp; + Kết nối đến API endpoint POST /businesses/:id/claim | 13/06/2026 | 13/06/2026 | AWS S3 SDK, React Hook Form |
| 4 | - **Trang My Business Listings**: <br>&emsp; + Tạo bố cục lưới thẻ hiển thị tất cả địa điểm đang quản lý <br>&emsp; + Triển khai huy hiệu trạng thái (active, pending, locked) với mã màu <br>&emsp; + Xây dựng modal chi tiết địa điểm với khả năng chỉnh sửa <br>&emsp; + Thêm phân trang và lọc tìm kiếm cho danh sách lớn <br>&emsp; + Kết nối đến API endpoint GET /places?owner_id=me | 14/06/2026 | 14/06/2026 | React Query, Tailwind CSS Grid |
| 5 | - **Form Cập nhật Thông tin Doanh nghiệp**: <br>&emsp; + Thiết kế form với các trường: tên doanh nghiệp, mô tả, logo, thông tin liên hệ, giờ hoạt động <br>&emsp; + Triển khai schema xác thực Zod cho tất cả các trường <br>&emsp; + Xây dựng chức năng tải ảnh lên với xem trước sử dụng AWS S3 <br>&emsp; + Thêm phát hiện trạng thái form đã thay đổi và cảnh báo chưa lưu <br>&emsp; + Kết nối đến API endpoint PUT /businesses/:id | 15/06/2026 | 15/06/2026 | Zod Validation, React Dropzone |
| 6 | - **Trang Quản lý Review**: <br>&emsp; + Xây dựng danh sách review với lọc theo rating, ngày và trạng thái (mới/đã phản hồi) <br>&emsp; + Tạo thẻ chi tiết review hiển thị thông tin người dùng, sao đánh giá và bình luận <br>&emsp; + Triển khai form phản hồi trực tiếp để chủ doanh nghiệp trả lời review <br>&emsp; + Thêm huy hiệu thông báo real-time cho review mới chưa đọc <br>&emsp; + Kết nối đến API endpoints GET /places/:id/reviews và PUT /reviews/:id/reply <br> - Kiểm tra cross-browser và điều chỉnh responsive design | 16/06/2026 | 16/06/2026 | Socket.io (thông báo), React Hook Form |


### Kết quả đạt được tuần 9:

* ✅ **Business Dashboard** hoàn chỉnh với 4 thẻ thống kê (Tổng lượt xem, Tổng review, Rating trung bình, Booking đang hoạt động) và biểu đồ tương tác sử dụng Recharts.
* ✅ **Claim Listing** hoàn thành với tìm kiếm, lọc, form claim kèm tải tài liệu lên S3 và theo dõi trạng thái real-time.
* ✅ **My Business Listings** triển khai với lưới thẻ responsive, huy hiệu trạng thái, chỉnh sửa trực tiếp và phân trang cho 100+ địa điểm.
* ✅ **Form Cập nhật Thông tin Doanh nghiệp** xây dựng với xác thực toàn diện (50+ quy tắc), tải ảnh lên với cắt/xem trước và phát hiện thay đổi chưa lưu.
* ✅ **Trang Quản lý Review** cung cấp lọc review, hiển thị sao đánh giá và chức năng phản hồi trực tiếp với thông báo WebSocket.
* ✅ Tất cả 5 màn hình Business Owner đã tích hợp với backend APIs và triển khai lên môi trường staging để nhóm đánh giá.
* ✅ Đạt 95%+ độ phủ unit test trên tất cả các component Business Owner sử dụng Jest và React Testing Library.
