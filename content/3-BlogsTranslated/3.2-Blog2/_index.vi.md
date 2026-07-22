---
title: "AWS Well-Architected Framework trong Thiết kế Hệ thống Đám mây"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

Việc lựa chọn dịch vụ phù hợp chỉ là bước đầu tiên trong xây dựng hệ thống đám mây. Để hệ thống duy trì ổn định, bảo mật, phản hồi nhanh và có khả năng mở rộng theo thời gian, kiến trúc tổng thể phải tuân theo các nguyên tắc thiết kế rõ ràng.

**AWS Well-Architected Framework** là tập hợp hướng dẫn đánh giá và cải thiện kiến trúc đám mây theo các best practice do AWS phát triển. Đây không phải là một dịch vụ AWS riêng lẻ; đây là một cách tiếp cận có cấu trúc giúp tổ chức xác định rủi ro và đưa ra quyết định kiến trúc sáng suốt trong suốt vòng đời ứng dụng.

![Sáu trụ cột của AWS Well-Architected Framework](/images/blog2/aws-well-architected-six-pillars.png)

### Sáu Trụ cột

| Trụ cột | Mục tiêu chính | Thực hành ví dụ |
| --- | --- | --- |
| **Operational Excellence** | Vận hành workload nhất quán, quan sát hành vi, cải tiến liên tục. | Tự động hóa triển khai, thu thập log, giám sát hệ thống, phân tích dữ liệu vận hành. |
| **Security** | Bảo vệ dữ liệu, hệ thống và tài sản đám mây. | IAM, least privilege, MFA, mã hóa, giám sát truy cập. |
| **Reliability** | Thực hiện đúng chức năng và khôi phục khi có sự cố. | Triển khai đa AZ, backup, disaster recovery, auto scaling. |
| **Performance Efficiency** | Sử dụng tài nguyên hiệu quả khi nhu cầu và công nghệ thay đổi. | Chọn cấu hình phù hợp, dùng Lambda, CloudFront, Auto Scaling. |
| **Cost Optimization** | Đạt kết quả kinh doanh với chi phí phù hợp. | Giám sát tài nguyên, loại bỏ lãng phí, dùng Cost Explorer và Budgets. |
| **Sustainability** | Giảm thiểu tác động môi trường của workload đám mây. | Giảm công suất nhàn rỗi, dừng dịch vụ không dùng, tối ưu hóa sử dụng. |

### Operational Excellence

Trụ cột này tập trung vào vận hành và giám sát hệ thống đồng thời cải tiến quy trình liên tục. Các hoạt động lặp lại như triển khai hạ tầng, cấu hình tài nguyên và cập nhật ứng dụng nên được tự động hóa để giảm lỗi thủ công.

### Security

Bảo mật nên được triển khai nhiều lớp trong toàn hệ thống. AWS khuyến nghị quản lý danh tính với **IAM**, áp dụng **nguyên tắc đặc quyền tối thiểu**, bật **MFA** và mã hóa dữ liệu. Giám sát liên tục hoạt động truy cập giúp phát hiện hành vi bất thường và phản ứng kịp thời với mối đe dọa.

### Reliability

Hệ thống đáng tin cậy phải duy trì hoạt động và khôi phục khi thành phần gặp sự cố. Triển khai trên nhiều **Availability Zones**, tạo backup định kỳ và duy trì kế hoạch disaster recovery giúp giảm rủi ro gián đoạn dịch vụ.

### Performance Efficiency

Hiệu suất hệ thống phụ thuộc vào việc chọn đúng loại tài nguyên và dịch vụ. Công nghệ như **AWS Lambda**, **Amazon CloudFront** và **Auto Scaling** cung cấp khả năng mở rộng linh hoạt, giảm độ trễ và cải thiện hiệu quả tài nguyên.

### Cost Optimization

Mô hình pay-as-you-go chỉ mang lại giá trị khi tài nguyên được quản lý phù hợp. Tổ chức nên giám sát mức sử dụng, loại bỏ tài nguyên không cần thiết và điều chỉnh cấu hình theo nhu cầu workload.

### Sustainability

Trụ cột Sustainability nhằm giảm tác động môi trường của hệ thống đám mây. Tối ưu kiến trúc, tránh overprovisioning, tự động dừng tài nguyên không sử dụng và chọn giải pháp phù hợp với nhu cầu thực tế có thể giảm tiêu thụ năng lượng.

### Vai trò trong Thiết kế Hệ thống Đám mây

Điểm mạnh của Framework là cung cấp góc nhìn toàn hệ thống thay vì đánh giá dịch vụ riêng lẻ. Sáu trụ cột có mối liên kết chặt chẽ và thường có sự đánh đổi. Review kiến trúc định kỳ giúp xác định rủi ro thiết kế, hiểu hậu quả của quyết định, ưu tiên cải tiến và xây dựng hệ thống an toàn, đáng tin cậy, dễ mở rộng hơn.

### Kết luận

AWS Well-Architected Framework cung cấp nền tảng thiết kế quan trọng cho cloud engineer và solutions architect. Bằng cách cân bằng sáu trụ cột, tổ chức có thể xây dựng kiến trúc đám mây đáp ứng yêu cầu hiện tại và tiếp tục thích ứng trong tương lai.
