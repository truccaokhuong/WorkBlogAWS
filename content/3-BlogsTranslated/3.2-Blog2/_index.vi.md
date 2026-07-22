---
title: "Blog 2 - AWS Well-Architected Framework trong thiết kế hệ thống Cloud"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

Khi triển khai một hệ thống trên nền tảng điện toán đám mây, việc lựa chọn các dịch vụ phù hợp mới chỉ là bước khởi đầu. Để hệ thống có thể vận hành ổn định, đáp ứng tốt nhu cầu của người dùng và dễ dàng mở rộng trong tương lai, kiến trúc tổng thể cần được thiết kế theo những nguyên tắc rõ ràng. Nhằm hỗ trợ các doanh nghiệp và nhà phát triển xây dựng những hệ thống Cloud hiệu quả, Amazon Web Services (AWS) đã xây dựng AWS Well-Architected Framework – bộ khung hướng dẫn thiết kế kiến trúc dựa trên các thực tiễn tốt nhất được đúc kết từ quá trình triển khai và vận hành hạ tầng Cloud trên quy mô toàn cầu.

AWS Well-Architected Framework không phải là một dịch vụ của AWS mà là một tài liệu hướng dẫn giúp đánh giá và cải thiện chất lượng kiến trúc hệ thống. Bộ khung này được xây dựng dựa trên kinh nghiệm thực tế của AWS cùng phản hồi từ hàng triệu khách hàng đang sử dụng nền tảng Cloud. Mục tiêu của Framework là giúp các tổ chức thiết kế hệ thống có khả năng vận hành ổn định, an toàn, tối ưu chi phí và đáp ứng tốt khi quy mô sử dụng ngày càng mở rộng.

Nền tảng của AWS Well-Architected Framework được xây dựng dựa trên sáu trụ cột, đại diện cho sáu yếu tố quan trọng cần được cân nhắc trong quá trình thiết kế và vận hành hệ thống.

## Operational Excellence (Vận hành hiệu quả)

Operational Excellence tập trung vào việc xây dựng quy trình vận hành có tính nhất quán và khả năng cải tiến liên tục. AWS khuyến khích tự động hóa các công việc lặp lại như triển khai hạ tầng, cấu hình tài nguyên hay cập nhật ứng dụng nhằm giảm thiểu sai sót do thao tác thủ công.

Bên cạnh đó, việc theo dõi nhật ký hoạt động, giám sát hiệu năng và phân tích dữ liệu vận hành giúp nhóm quản trị nhanh chóng phát hiện những bất thường, từ đó đưa ra phương án xử lý phù hợp trước khi ảnh hưởng đến người dùng.

## Security (Bảo mật)

Bảo mật luôn là một trong những ưu tiên hàng đầu khi triển khai hệ thống trên nền tảng Cloud. AWS khuyến nghị áp dụng nhiều lớp bảo vệ nhằm đảm bảo dữ liệu và tài nguyên luôn được kiểm soát chặt chẽ.

Một số nguyên tắc quan trọng bao gồm quản lý quyền truy cập thông qua AWS Identity and Access Management (IAM), áp dụng nguyên tắc Least Privilege để chỉ cấp đúng quyền cần thiết cho từng người dùng hoặc ứng dụng, sử dụng xác thực đa yếu tố (MFA), mã hóa dữ liệu trong quá trình lưu trữ và truyền tải, đồng thời giám sát các hoạt động truy cập để kịp thời phát hiện các dấu hiệu bất thường.

Những biện pháp này góp phần giảm thiểu rủi ro về bảo mật và nâng cao khả năng bảo vệ hệ thống trước các mối đe dọa.

## Reliability (Độ tin cậy)

Reliability hướng đến mục tiêu giúp hệ thống duy trì hoạt động ổn định ngay cả khi xảy ra sự cố. AWS khuyến nghị triển khai tài nguyên trên nhiều Availability Zone (AZ) trong cùng một Region để tăng khả năng dự phòng và hạn chế gián đoạn dịch vụ.

Ngoài việc xây dựng kiến trúc dự phòng, hệ thống cũng cần có cơ chế sao lưu dữ liệu định kỳ, khôi phục sau thảm họa và tự động mở rộng tài nguyên khi lưu lượng truy cập tăng cao. Những giải pháp này giúp đảm bảo ứng dụng vẫn có thể phục vụ người dùng trong nhiều tình huống khác nhau.

## Performance Efficiency (Hiệu năng)

Hiệu năng của hệ thống phụ thuộc vào việc lựa chọn đúng tài nguyên và dịch vụ phù hợp với từng nhu cầu sử dụng. AWS cung cấp nhiều loại dịch vụ với các mức cấu hình khác nhau, cho phép doanh nghiệp lựa chọn giải pháp tối ưu về cả hiệu suất và chi phí.

Các dịch vụ như AWS Lambda, Amazon CloudFront hay Auto Scaling giúp hệ thống có khả năng mở rộng linh hoạt, giảm độ trễ và cải thiện tốc độ phản hồi khi số lượng người dùng tăng lên. Việc thường xuyên đánh giá hiệu năng cũng giúp doanh nghiệp điều chỉnh tài nguyên phù hợp với từng giai đoạn phát triển.

## Cost Optimization (Tối ưu chi phí)

Một trong những ưu điểm nổi bật của Cloud Computing là mô hình thanh toán theo mức sử dụng. Tuy nhiên, việc sử dụng tài nguyên không hợp lý có thể làm chi phí vận hành tăng đáng kể.

AWS khuyến nghị theo dõi mức sử dụng tài nguyên thường xuyên, loại bỏ các dịch vụ không còn cần thiết, lựa chọn cấu hình phù hợp với khối lượng công việc và sử dụng các công cụ như AWS Cost Explorer hoặc AWS Budgets để kiểm soát ngân sách.

Tối ưu chi phí không chỉ là cắt giảm chi tiêu mà còn là sử dụng tài nguyên đúng mục đích để đạt hiệu quả cao nhất.

## Sustainability (Phát triển bền vững)

Sustainability là trụ cột mới được AWS bổ sung nhằm hướng tới việc sử dụng tài nguyên công nghệ thông tin một cách hiệu quả và thân thiện với môi trường.

Việc tối ưu kiến trúc, hạn chế tài nguyên dư thừa, tự động tắt các dịch vụ không sử dụng và lựa chọn giải pháp phù hợp với nhu cầu thực tế sẽ giúp giảm mức tiêu thụ năng lượng cũng như lượng phát thải từ các trung tâm dữ liệu.

Đây là xu hướng ngày càng được nhiều doanh nghiệp quan tâm trong quá trình chuyển đổi số và phát triển hạ tầng Cloud.

## Vai trò của AWS Well-Architected Framework trong thiết kế hệ thống Cloud

Điểm nổi bật của AWS Well-Architected Framework là cung cấp một góc nhìn tổng thể về kiến trúc hệ thống thay vì chỉ tập trung vào từng dịch vụ riêng lẻ. Sáu trụ cột của Framework có mối liên hệ chặt chẽ với nhau và cần được cân bằng trong suốt vòng đời của ứng dụng.

Ví dụ, một hệ thống có hiệu năng cao nhưng thiếu các biện pháp bảo mật sẽ tiềm ẩn nhiều rủi ro. Ngược lại, một hệ thống được đầu tư quá nhiều tài nguyên để đảm bảo hiệu năng nhưng không được tối ưu chi phí sẽ làm giảm hiệu quả khai thác Cloud. Việc đánh giá kiến trúc dựa trên Framework giúp các tổ chức nhận diện những điểm cần cải thiện và xây dựng hệ thống theo các tiêu chuẩn mà AWS khuyến nghị.

AWS Well-Architected Framework hiện được xem là một trong những tài liệu quan trọng dành cho các kỹ sư Cloud, kiến trúc sư giải pháp và những người đang tìm hiểu về AWS. Việc nghiên cứu bộ khung này không chỉ giúp hiểu rõ hơn về tư duy thiết kế hệ thống trên nền tảng Cloud mà còn tạo nền tảng để áp dụng hiệu quả các dịch vụ AWS trong những dự án thực tế.
