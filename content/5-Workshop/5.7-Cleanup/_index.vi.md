---
title: "Dọn dẹp"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

### Nguyên tắc Dọn dẹp

Trước khi xóa tài nguyên, tạo backup cho bất kỳ dữ liệu nào cần được giữ lại. Không bao giờ xóa shared VPC, production database hoặc shared S3 bucket chỉ vì nó xuất hiện trong workshop này.

### Thứ tự Xóa Khuyến nghị

1. Vô hiệu hóa frontend hosting và custom domain mappings nếu có.
2. Xóa API Gateway sau khi xác nhận không còn clients nào sử dụng endpoint.
3. Xóa Lambda functions, unused layers và log groups theo chính sách retention.
4. Dọn sạch S3 buckets artifact/test-upload cụ thể cho workshop, sau đó xóa nếu không còn cần thiết.
5. Tạo snapshot cuối cùng trước khi xóa database RDS test.
6. Xóa tài nguyên ElastiCache Redis.
7. Xóa Security Groups, IAM roles/policies và VPC resources chỉ sau khi xác nhận chúng không được chia sẻ.

### Kiểm tra Sau Dọn dẹp

* Kiểm tra AWS Billing/Cost Explorer sau 24 giờ để đảm bảo không có chi phí bất thường.
* Kiểm tra các CloudWatch log groups còn sót lại.
* Kiểm tra S3 buckets, RDS snapshots và Elastic IPs không sử dụng.
* Ghi lại danh sách tài nguyên đã xóa trong báo cáo bàn giao.
