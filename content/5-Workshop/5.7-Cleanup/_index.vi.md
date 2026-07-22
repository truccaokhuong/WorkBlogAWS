---
title: "Dọn dẹp"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

### Nguyên tắc dọn dẹp

Trước khi xóa tài nguyên, hãy tạo bản sao lưu cho dữ liệu cần giữ lại. Không xóa VPC dùng chung, cơ sở dữ liệu đang vận hành hoặc vùng lưu trữ S3 dùng chung chỉ vì chúng xuất hiện trong hướng dẫn này.

### Thứ tự xóa khuyến nghị

1. Vô hiệu hóa dịch vụ lưu trữ giao diện và ánh xạ tên miền tùy chỉnh nếu có.
2. Xóa API Gateway sau khi xác nhận không còn ứng dụng nào sử dụng các điểm cuối.
3. Xóa các hàm Lambda, lớp không còn dùng và nhóm nhật ký theo chính sách lưu giữ.
4. Làm trống các vùng lưu trữ S3 dùng riêng cho gói triển khai hoặc tệp kiểm thử, sau đó xóa nếu không còn cần thiết.
5. Tạo ảnh chụp dữ liệu cuối cùng trước khi xóa cơ sở dữ liệu RDS dùng cho kiểm thử.
6. Xóa tài nguyên ElastiCache for Redis.
7. Chỉ xóa nhóm bảo mật, vai trò và chính sách IAM cùng tài nguyên VPC sau khi xác nhận chúng không được dùng chung.

### Kiểm tra sau khi dọn dẹp

* Kiểm tra AWS Billing hoặc Cost Explorer sau 24 giờ để đảm bảo không có chi phí bất thường.
* Kiểm tra các nhóm nhật ký CloudWatch còn sót lại.
* Kiểm tra vùng lưu trữ S3, ảnh chụp RDS và địa chỉ Elastic IP không sử dụng.
* Ghi lại danh sách tài nguyên đã xóa trong báo cáo bàn giao.
