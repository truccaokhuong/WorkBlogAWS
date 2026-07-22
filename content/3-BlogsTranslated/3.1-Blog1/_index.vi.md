---
title: "Amazon S3 Storage Classes và Tiêu chí Lựa chọn"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---
Amazon Simple Storage Service (Amazon S3) là dịch vụ lưu trữ đối tượng có khả năng mở rộng cao, cung cấp dung lượng gần như không giới hạn và độ bền dữ liệu lên đến **99.999999999% (11 số 9)**. Thay vì cung cấp một mô hình lưu trữ duy nhất, Amazon S3 cung cấp nhiều storage class cho các tần suất truy cập, tốc độ truy xuất, yêu cầu tính sẵn sàng, thời gian lưu trữ và mục tiêu chi phí khác nhau.

Việc chọn storage class phù hợp giúp hệ thống đáp ứng yêu cầu truy cập dữ liệu đồng thời tối ưu chi phí vận hành tổng thể.

![Tổng quan các storage class của Amazon S3](/images/blog1/amazon-s3-storage-classes.png)

### Tổng quan Storage Class

| Storage class | Đặc điểm chính | Trường hợp sử dụng phù hợp |
| --- | --- | --- |
| **S3 Standard** | Truy cập millisecond, tính sẵn sàng cao, dữ liệu lưu trên nhiều AZ. Chi phí lưu trữ cao hơn. | Website, web/mobile app, ảnh, video, tài liệu truy cập thường xuyên. |
| **S3 Intelligent-Tiering** | Tự động chuyển đối tượng giữa các tier theo mức sử dụng. Có phí giám sát. | Dữ liệu doanh nghiệp, tài liệu dự án, nội dung có pattern truy cập thay đổi. |
| **S3 Standard-IA** | Chi phí lưu trữ thấp hơn, truy xuất nhanh, có phí truy xuất. Multi-AZ. | Backup, archive, dữ liệu dự phòng, tài liệu truy cập ít lần/năm. |
| **S3 One Zone-IA** | Tương tự Standard-IA nhưng chỉ một AZ. Chi phí thấp hơn, độ bền thấp hơn. | Dữ liệu có thể tạo lại, file tạm, backup thứ cấp. |
| **S3 Glacier Instant Retrieval** | Lưu trữ dài hạn, truy xuất millisecond. | Hồ sơ y tế, dữ liệu pháp lý, ảnh lưu trữ, media dài hạn. |
| **S3 Glacier Flexible Retrieval** | Truy xuất từ vài phút đến vài giờ. Cân bằng chi phí và khả năng truy cập. | Backup định kỳ, hồ sơ kinh doanh, tài liệu lịch sử, dữ liệu kiểm toán. |
| **S3 Glacier Deep Archive** | Storage class chi phí thấp nhất. Truy xuất mất vài giờ. | Hồ sơ pháp lý, lưu trữ nhiều năm, archive tuân thủ quy định. |

### Tiêu chí Lựa chọn

**1. Tần suất truy cập** – Dữ liệu dùng thường xuyên phù hợp với **S3 Standard**. Pattern không thể đoán trước dùng **S3 Intelligent-Tiering**. Dữ liệu ít truy cập phù hợp với **Standard-IA** hoặc Glacier.

**2. Thời gian truy xuất yêu cầu** – Truy cập ngay cần class độ trễ millisecond (Standard, Intelligent-Tiering, Glacier Instant Retrieval). Chấp nhận đợi vài phút đến vài giờ có thể dùng Glacier Flexible Retrieval hoặc Deep Archive.

**3. Tổng chi phí lưu trữ và truy xuất** – Chi phí lưu trữ thấp thường đi kèm phí truy xuất cao. Cần đánh giá tổng thể số lần đọc, khối lượng truy xuất và vòng đời đối tượng.

**4. Yêu cầu tính sẵn sàng** – Dữ liệu quan trọng nên dùng class multi-AZ (S3 Standard, Standard-IA). One Zone-IA chỉ phù hợp khi dữ liệu có thể tạo lại hoặc chấp nhận rủi ro.

**5. Thời gian lưu trữ** – Dữ liệu ngắn hạn phù hợp S3 Standard hoặc Intelligent-Tiering. Lưu trữ nhiều năm phù hợp Glacier Flexible Retrieval hoặc Deep Archive.

### Kết luận

Không có storage class S3 nào tối ưu cho mọi loại dữ liệu. Lựa chọn đúng cân bằng giữa tần suất truy cập, tốc độ khôi phục, tính sẵn sàng, thời gian lưu trữ và tổng chi phí. S3 Lifecycle policies có thể tự động chuyển đối tượng từ storage class truy cập thường xuyên sang các tier lạnh hơn theo thời gian.
