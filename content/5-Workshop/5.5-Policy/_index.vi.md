---
title: "Kiểm thử và xác thực"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5.5. </b> "
---

### Kiểm tra chức năng

Sau mỗi lần triển khai, xác thực các luồng chính trong môi trường kiểm thử:

| Luồng | Kết quả mong đợi |
| --- | --- |
| Kiểm tra tình trạng hệ thống | API trả về HTTP 200 và dữ liệu hợp lệ |
| Đăng ký và đăng nhập | API trả về mã thông báo phiên hợp lệ |
| Duyệt và tìm kiếm địa điểm | Bộ lọc và phân trang trả về dữ liệu chính xác |
| Tạo hoặc cập nhật đánh giá | Đánh giá được lưu và điểm tổng hợp được làm mới |
| Tạo chuyến đi | Ngày, thứ tự và ghi chú cho từng địa điểm được lưu |
| Chia sẻ chuyến đi công khai | URL công khai hoạt động mà không cần xác thực |
| Tạo lượt đặt chỗ | Trạng thái thay đổi theo đúng quy trình |
| Tải ảnh địa điểm | Trình duyệt tải trực tiếp lên S3 qua URL ký sẵn có thời hạn ngắn |

Ví dụ kiểm tra tình trạng hệ thống:

```powershell
curl.exe -i https://API_ID.execute-api.REGION.amazonaws.com/health
```

### Xác thực API Gateway

Kiểm tra cấu hình tuyến và giai đoạn triển khai để đảm bảo API Gateway trỏ đến đúng hàm Lambda.

![Các tuyến API Gateway](/images/5-Workshop/06-api-gateway-routes.png)

![Giai đoạn triển khai API Gateway](/images/5-Workshop/07-api-stage.png)

### Nhật ký và chẩn đoán

Khi một yêu cầu thất bại, hãy điều tra theo thứ tự sau:

1. Mở nhóm nhật ký Lambda trong CloudWatch.
2. Chọn luồng nhật ký mới nhất tương ứng với thời điểm xảy ra lỗi.
3. Xác định lỗi nằm ở kiểm tra dữ liệu, phân quyền, truy cập PostgreSQL, Redis hay ký URL S3.
4. Sửa phần cấu hình hoặc mã nhỏ nhất gây ra lỗi.
5. Triển khai lại và lặp lại cùng phép kiểm thử.

![Luồng nhật ký CloudWatch](/images/5-Workshop/21-cloudwatch-log.png)

### Tín hiệu cần giám sát

* Số lỗi, thời gian chạy, lượt bị giới hạn và lượt hết thời gian của Lambda.
* Độ trễ API Gateway và phản hồi 4xx/5xx.
* CPU, số kết nối và lỗi kết nối RDS.
* Tỷ lệ dữ liệu tìm thấy trong Redis và trạng thái kết nối.
* Lỗi tải tệp lên S3.
* Thời gian lưu nhật ký CloudWatch để tránh chi phí không cần thiết.
