---
title: "Blog 3 - Khảo sát các lớp lưu trữ trong Amazon S3 và tiêu chí lựa chọn"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

Amazon S3 (Simple Storage Service) là một trong những dịch vụ lưu trữ dữ liệu phổ biến nhất của Amazon Web Services (AWS), được thiết kế với khả năng lưu trữ gần như không giới hạn, độ bền dữ liệu lên đến 99,999999999% (11 số 9) và khả năng mở rộng linh hoạt. Thay vì chỉ cung cấp một hình thức lưu trữ duy nhất, Amazon S3 được chia thành nhiều Storage Classes nhằm đáp ứng các nhu cầu khác nhau về tần suất truy cập, hiệu năng, thời gian lưu trữ và chi phí.

Việc lựa chọn đúng lớp lưu trữ không chỉ giúp đảm bảo hiệu quả trong quá trình sử dụng mà còn góp phần tối ưu đáng kể chi phí vận hành. Mỗi Storage Class đều được thiết kế cho một nhóm dữ liệu cụ thể, từ dữ liệu thường xuyên truy cập cho đến dữ liệu lưu trữ lâu dài phục vụ mục đích sao lưu hoặc lưu trữ hồ sơ.

## Tổng quan về các lớp lưu trữ trong Amazon S3

Amazon S3 hiện cung cấp nhiều lớp lưu trữ khác nhau, trong đó phổ biến nhất gồm:

- S3 Standard
- S3 Intelligent-Tiering
- S3 Standard-Infrequent Access (Standard-IA)
- S3 One Zone-Infrequent Access (One Zone-IA)
- S3 Glacier Instant Retrieval
- S3 Glacier Flexible Retrieval
- S3 Glacier Deep Archive

Các lớp lưu trữ này được phân chia theo mức độ truy cập dữ liệu, từ dữ liệu "nóng" (Hot Data) thường xuyên sử dụng đến dữ liệu "lạnh" (Cold Data) chỉ được truy xuất trong những trường hợp đặc biệt.

## S3 Standard

S3 Standard là lớp lưu trữ mặc định của Amazon S3 và phù hợp với các dữ liệu được truy cập thường xuyên. Đây là lựa chọn dành cho những ứng dụng yêu cầu hiệu năng cao, độ trễ thấp và khả năng sẵn sàng cao.

Một số trường hợp sử dụng bao gồm: Website tĩnh, ứng dụng web, ứng dụng di động, lưu trữ hình ảnh, video hoặc tài liệu được truy cập liên tục.

Ưu điểm của S3 Standard là thời gian truy cập chỉ tính bằng mili giây, khả năng sẵn sàng cao và dữ liệu được lưu trên nhiều Availability Zone nhằm tăng khả năng chịu lỗi. Tuy nhiên, chi phí lưu trữ của lớp này cũng cao hơn so với các lớp còn lại.

## S3 Intelligent-Tiering

S3 Intelligent-Tiering được thiết kế cho những dữ liệu có tần suất truy cập không ổn định hoặc khó dự đoán. Điểm nổi bật của lớp lưu trữ này là khả năng tự động chuyển dữ liệu giữa các tầng lưu trữ dựa trên mức độ sử dụng mà không cần người dùng can thiệp.

Nếu dữ liệu được truy cập thường xuyên, hệ thống sẽ duy trì ở tầng hiệu năng cao. Khi dữ liệu ít được sử dụng hơn, Amazon S3 sẽ tự động chuyển sang tầng có chi phí thấp hơn để tiết kiệm ngân sách.

Lớp lưu trữ này phù hợp với kho dữ liệu doanh nghiệp, tài liệu dự án, nội dung số có tần suất truy cập thay đổi theo thời gian. Mặc dù có thêm chi phí giám sát đối tượng (Monitoring Fee), Intelligent-Tiering giúp giảm đáng kể chi phí lưu trữ đối với các hệ thống có lượng dữ liệu lớn.

## S3 Standard-Infrequent Access (Standard-IA)

Standard-IA được thiết kế cho dữ liệu ít được truy cập nhưng vẫn cần khả năng truy xuất nhanh khi cần thiết. So với S3 Standard, chi phí lưu trữ của Standard-IA thấp hơn, tuy nhiên người dùng sẽ phải trả thêm phí mỗi lần truy xuất dữ liệu.

Một số trường hợp sử dụng gồm: sao lưu dữ liệu, hồ sơ lưu trữ, dữ liệu dự phòng, tài liệu chỉ sử dụng vài lần trong năm. Lớp lưu trữ này vẫn đảm bảo độ bền dữ liệu tương đương S3 Standard và dữ liệu được lưu trên nhiều Availability Zone.

## S3 One Zone-Infrequent Access

One Zone-IA có đặc điểm tương tự Standard-IA nhưng dữ liệu chỉ được lưu trong một Availability Zone duy nhất. Do không có cơ chế sao chép dữ liệu giữa nhiều Availability Zone nên chi phí lưu trữ thấp hơn. Tuy nhiên, nếu Availability Zone xảy ra sự cố nghiêm trọng, dữ liệu có nguy cơ không thể phục hồi.

One Zone-IA phù hợp với dữ liệu có thể tạo lại, file tạm, dữ liệu sao lưu thứ cấp, nội dung không yêu cầu mức độ sẵn sàng cao. Đây là lựa chọn hợp lý khi doanh nghiệp muốn tiết kiệm chi phí và có thể chấp nhận mức rủi ro cao hơn.

## S3 Glacier Instant Retrieval

Glacier Instant Retrieval dành cho dữ liệu lưu trữ dài hạn nhưng vẫn cần truy xuất ngay lập tức khi có nhu cầu. Khác với các lớp Glacier truyền thống, thời gian truy xuất của Glacier Instant Retrieval chỉ tính bằng mili giây, trong khi chi phí lưu trữ thấp hơn S3 Standard-IA.

Lớp lưu trữ này thường được sử dụng cho hồ sơ y tế, hình ảnh lưu trữ, nội dung đa phương tiện, dữ liệu pháp lý cần lưu giữ lâu dài.

## S3 Glacier Flexible Retrieval

Glacier Flexible Retrieval hướng đến dữ liệu lưu trữ lâu dài và không yêu cầu truy cập thường xuyên. Người dùng có thể lựa chọn nhiều mức thời gian truy xuất khác nhau, từ vài phút đến vài giờ, tùy thuộc vào nhu cầu và mức chi phí mong muốn.

Một số ứng dụng phổ biến: lưu trữ hồ sơ doanh nghiệp, sao lưu dữ liệu định kỳ, lưu trữ tài liệu lịch sử, dữ liệu phục vụ kiểm toán. Đây là lớp lưu trữ cân bằng giữa chi phí và khả năng truy xuất.

## S3 Glacier Deep Archive

Glacier Deep Archive là lớp lưu trữ có chi phí thấp nhất trong Amazon S3, được thiết kế cho dữ liệu cần lưu giữ trong thời gian rất dài và gần như không cần truy cập. Thời gian truy xuất có thể kéo dài nhiều giờ, vì vậy lớp lưu trữ này không phù hợp với dữ liệu cần sử dụng thường xuyên.

Một số trường hợp sử dụng gồm: lưu trữ hồ sơ pháp lý, dữ liệu lưu trữ nhiều năm, tài liệu lưu trữ theo quy định của doanh nghiệp hoặc cơ quan nhà nước, sao lưu dài hạn. Đây là giải pháp phù hợp khi mục tiêu chính là giảm tối đa chi phí lưu trữ.

## Tiêu chí lựa chọn lớp lưu trữ phù hợp

Việc lựa chọn Storage Class không nên chỉ dựa trên chi phí mà cần xem xét đồng thời nhiều yếu tố.

### Tần suất truy cập dữ liệu

Đây là yếu tố quan trọng nhất. Dữ liệu được truy cập thường xuyên nên sử dụng S3 Standard hoặc Intelligent-Tiering. Đối với dữ liệu chỉ truy cập vài lần mỗi tháng hoặc vài lần mỗi năm, Standard-IA hoặc Glacier sẽ là lựa chọn phù hợp hơn.

### Thời gian cần truy xuất dữ liệu

Nếu ứng dụng yêu cầu truy xuất ngay lập tức, nên lựa chọn các lớp có thời gian phản hồi tính bằng mili giây như Standard, Intelligent-Tiering hoặc Glacier Instant Retrieval. Đối với dữ liệu có thể chờ vài phút hoặc vài giờ, Glacier Flexible Retrieval hoặc Glacier Deep Archive sẽ giúp tiết kiệm chi phí đáng kể.

### Chi phí lưu trữ và chi phí truy xuất

Thông thường, lớp lưu trữ có chi phí lưu trữ càng thấp thì chi phí truy xuất sẽ càng cao. Vì vậy, cần cân nhắc giữa số lần truy cập dữ liệu và tổng chi phí trong suốt vòng đời của dữ liệu.

### Yêu cầu về tính sẵn sàng

Nếu dữ liệu quan trọng và cần khả năng sẵn sàng cao, nên ưu tiên các lớp lưu trữ được triển khai trên nhiều Availability Zone như Standard hoặc Standard-IA. Trong trường hợp dữ liệu có thể tái tạo hoặc không quá quan trọng, One Zone-IA sẽ giúp giảm chi phí.

### Thời gian lưu trữ dữ liệu

Dữ liệu sử dụng trong thời gian ngắn thường phù hợp với Standard hoặc Intelligent-Tiering. Ngược lại, dữ liệu cần lưu trữ trong nhiều năm nhưng rất ít khi truy cập nên sử dụng Glacier Flexible Retrieval hoặc Glacier Deep Archive để tối ưu ngân sách.

Việc Amazon S3 cung cấp nhiều lớp lưu trữ khác nhau cho thấy AWS không hướng đến một giải pháp chung cho mọi loại dữ liệu mà cho phép người dùng lựa chọn phương án phù hợp với từng nhu cầu cụ thể. Hiểu rõ đặc điểm của từng Storage Class sẽ giúp xây dựng chiến lược lưu trữ hiệu quả hơn, vừa đảm bảo khả năng truy cập dữ liệu khi cần thiết, vừa tối ưu chi phí vận hành hệ thống trên nền tảng AWS.
