---
title: "Kiểm thử & Xác thực"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 5.5. </b> "
---

### Kiểm tra Chức năng

Sau mỗi lần triển khai, xác thực các luồng chính trong môi trường test:

| Luồng | Kết quả mong đợi |
| --- | --- |
| Health check | API trả về HTTP 200 và payload hợp lệ |
| Đăng ký và đăng nhập | API trả về session tokens hợp lệ |
| Duyệt/tìm kiếm địa điểm | Lọc và phân trang trả về dữ liệu chính xác |
| Tạo/cập nhật review | Review được lưu và rating tổng hợp được làm mới |
| Tạo trip | Ngày, thứ tự và ghi chú cho mỗi địa điểm được lưu |
| Chia sẻ trip công khai | URL công khai hoạt động không cần xác thực |
| Tạo booking | Booking tuân theo workflow trạng thái mong đợi |
| Tải ảnh địa điểm | Browser tải lên qua S3 presigned URL ngắn hạn |

Ví dụ health check:

```powershell
curl.exe -i https://API_ID.execute-api.REGION.amazonaws.com/health
```

### Xác thực API Gateway

Kiểm tra cấu hình route và stage deployment để đảm bảo API Gateway trỏ đến đúng Lambda integration.

![API Gateway routes](/images/5-Workshop/06-api-gateway-routes.png)

![API Gateway stage](/images/5-Workshop/07-api-stage.png)

### Logs và Chẩn đoán

Đối với request thất bại, điều tra theo thứ tự sau:

1. Mở Lambda CloudWatch log group.
2. Chọn log stream mới nhất cho timestamp của request.
3. Xác định lỗi xảy ra trong validation, authorization, database access, Redis access hay S3 signing.
4. Sửa đơn vị cấu hình hoặc code nhỏ nhất chịu trách nhiệm.
5. Triển khai lại và lặp lại test tương tự.

![CloudWatch log stream](/images/5-Workshop/21-cloudwatch-log.png)

### Tín hiệu cần Giám sát

* Lambda errors, duration, throttles và timeouts.
* API Gateway latency và phản hồi 4xx/5xx.
* RDS CPU, số lượng kết nối và lỗi kết nối.
* Redis hit rate và trạng thái kết nối.
* Lỗi tải lên S3.
* CloudWatch log retention để tránh chi phí không cần thiết.
