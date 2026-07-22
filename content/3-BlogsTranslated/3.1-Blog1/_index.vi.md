---
title: "Các lớp lưu trữ Amazon S3 và tiêu chí lựa chọn"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

Amazon Simple Storage Service (Amazon S3) là dịch vụ lưu trữ đối tượng có khả năng mở rộng cao, cung cấp dung lượng gần như không giới hạn và độ bền dữ liệu lên đến **99,999999999% (11 số 9)**. Thay vì chỉ cung cấp một mô hình, Amazon S3 có nhiều lớp lưu trữ phù hợp với tần suất truy cập, tốc độ truy xuất, yêu cầu về tính sẵn sàng, thời gian lưu và mục tiêu chi phí khác nhau.

Chọn đúng lớp lưu trữ giúp hệ thống đáp ứng yêu cầu truy cập dữ liệu, đồng thời tối ưu tổng chi phí vận hành.

![Tổng quan các lớp lưu trữ Amazon S3](/images/blog1/amazon-s3-storage-classes.png)

### Tổng quan các lớp lưu trữ

| Lớp lưu trữ | Đặc điểm chính | Trường hợp sử dụng phù hợp |
| --- | --- | --- |
| **S3 Standard** | Truy cập trong vài mili giây, tính sẵn sàng cao, dữ liệu được lưu trên nhiều Vùng sẵn sàng. Chi phí lưu trữ cao hơn. | Trang web, ứng dụng web hoặc di động, ảnh, video và tài liệu được truy cập thường xuyên. |
| **S3 Intelligent-Tiering** | Tự động chuyển đối tượng giữa các tầng theo mức sử dụng; có phí giám sát. | Dữ liệu doanh nghiệp, tài liệu dự án và nội dung có tần suất truy cập thay đổi. |
| **S3 Standard-IA** | Chi phí lưu trữ thấp hơn, truy xuất nhanh nhưng có phí truy xuất; dữ liệu nằm trên nhiều Vùng sẵn sàng. | Bản sao lưu, dữ liệu dự phòng và tài liệu ít được truy cập. |
| **S3 One Zone-IA** | Tương tự Standard-IA nhưng chỉ lưu tại một Vùng sẵn sàng; chi phí thấp hơn và mức dự phòng thấp hơn. | Dữ liệu có thể tạo lại, tệp tạm và bản sao lưu thứ cấp. |
| **S3 Glacier Instant Retrieval** | Lưu trữ dài hạn, truy xuất trong vài mili giây. | Hồ sơ y tế, dữ liệu pháp lý, ảnh và nội dung cần lưu lâu dài. |
| **S3 Glacier Flexible Retrieval** | Truy xuất từ vài phút đến vài giờ, cân bằng chi phí và khả năng truy cập. | Bản sao lưu định kỳ, hồ sơ kinh doanh, tài liệu lịch sử và dữ liệu kiểm toán. |
| **S3 Glacier Deep Archive** | Lớp có chi phí lưu trữ thấp nhất; truy xuất mất vài giờ. | Hồ sơ pháp lý, dữ liệu lưu nhiều năm và tài liệu tuân thủ quy định. |

### Tiêu chí lựa chọn

**1. Tần suất truy cập:** Dữ liệu dùng thường xuyên phù hợp với **S3 Standard**. Dữ liệu có tần suất khó dự đoán phù hợp với **S3 Intelligent-Tiering**. Dữ liệu ít truy cập có thể dùng **S3 Standard-IA** hoặc các lớp Glacier.

**2. Thời gian truy xuất:** Dữ liệu cần truy cập ngay nên dùng lớp có độ trễ vài mili giây. Nếu chấp nhận chờ từ vài phút đến vài giờ, có thể dùng Glacier Flexible Retrieval hoặc Glacier Deep Archive.

**3. Tổng chi phí lưu trữ và truy xuất:** Chi phí lưu trữ thấp thường đi kèm phí truy xuất cao hơn. Cần đánh giá số lần đọc, khối lượng truy xuất và vòng đời đối tượng.

**4. Yêu cầu về tính sẵn sàng:** Dữ liệu quan trọng nên dùng lớp lưu trên nhiều Vùng sẵn sàng. S3 One Zone-IA chỉ phù hợp khi dữ liệu có thể tạo lại hoặc chấp nhận rủi ro mất một vùng.

**5. Thời gian lưu:** Dữ liệu ngắn hạn phù hợp với S3 Standard hoặc S3 Intelligent-Tiering; dữ liệu lưu nhiều năm phù hợp với Glacier Flexible Retrieval hoặc Glacier Deep Archive.

### Kết luận

Không có một lớp lưu trữ S3 tối ưu cho mọi loại dữ liệu. Lựa chọn phù hợp cần cân bằng tần suất truy cập, tốc độ khôi phục, tính sẵn sàng, thời gian lưu và tổng chi phí. Chính sách vòng đời S3 có thể tự động chuyển đối tượng từ lớp truy cập thường xuyên sang các tầng lưu trữ lạnh hơn theo thời gian.
