---
title: "Nhật ký Tuần 9"
date: 2026-06-12
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

### Mục tiêu tuần 9

* Triển khai các màn hình dành cho chủ doanh nghiệp.
* Xây dựng bảng điều khiển với số liệu thống kê và biểu đồ.
* Phát triển luồng xác minh quyền sở hữu địa điểm.
* Hoàn thiện quản lý danh sách doanh nghiệp và đánh giá của khách hàng.

### Các công việc cần triển khai trong tuần này

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | Xây dựng **Bảng điều khiển doanh nghiệp** với thẻ thống kê lượt xem, số đánh giá, điểm trung bình và biểu đồ Recharts; thêm trạng thái đang tải, xử lý lỗi và kết nối `GET /businesses/:id/stats`. | 12/06/2026 | 12/06/2026 | Tài liệu Recharts, Tailwind UI |
| 3 | Xây dựng **Trang xác minh địa điểm** với tìm kiếm, lọc, biểu mẫu gửi tài liệu, URL ký sẵn của S3, theo dõi trạng thái và kết nối `POST /businesses/:id/claim`. | 13/06/2026 | 13/06/2026 | AWS SDK for S3, React Hook Form |
| 4 | Xây dựng **Danh sách doanh nghiệp của tôi** dạng lưới; hiển thị trạng thái hoạt động, chờ duyệt hoặc bị khóa; thêm cửa sổ chi tiết, phân trang, tìm kiếm và kết nối `GET /places?owner_id=me`. | 14/06/2026 | 14/06/2026 | React Query, Tailwind CSS Grid |
| 5 | Xây dựng **Biểu mẫu cập nhật thông tin doanh nghiệp** với kiểm tra dữ liệu bằng Zod, tải ảnh lên S3, xem trước ảnh và cảnh báo khi có thay đổi chưa lưu; kết nối `PUT /businesses/:id`. | 15/06/2026 | 15/06/2026 | Zod, React Dropzone |
| 6 | Xây dựng **Trang quản lý đánh giá** với bộ lọc, thông tin người đánh giá, phản hồi trực tiếp và thông báo theo thời gian thực; kết nối `GET /places/:id/reviews` và `PUT /reviews/:id/reply`; kiểm tra trên nhiều trình duyệt và kích thước màn hình. | 16/06/2026 | 16/06/2026 | Socket.io, React Hook Form |

### Kết quả đạt được tuần 9

* ✅ Hoàn thành bảng điều khiển với bốn thẻ thống kê và biểu đồ tương tác.
* ✅ Hoàn thành luồng xác minh địa điểm, tải tài liệu lên S3 và theo dõi trạng thái.
* ✅ Hoàn thành danh sách doanh nghiệp, cửa sổ chi tiết, tìm kiếm và phân trang.
* ✅ Hoàn thành biểu mẫu cập nhật thông tin và xử lý ảnh.
* ✅ Hoàn thành trang quản lý đánh giá, phản hồi và thông báo theo thời gian thực.
* ✅ Tích hợp các màn hình với API, triển khai lên môi trường thử nghiệm và đạt hơn 95% độ phủ kiểm thử đơn vị.
