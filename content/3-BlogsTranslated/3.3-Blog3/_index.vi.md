---
title: "Amazon Bedrock – AI tạo sinh trên AWS"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---

**Amazon Bedrock** là dịch vụ được quản lý hoàn toàn để xây dựng ứng dụng AI tạo sinh trên AWS. Thay vì cấp phát máy chủ GPU, cài đặt khung phát triển và triển khai mô hình ngôn ngữ lớn, nhà phát triển có thể truy cập các **mô hình nền tảng** thông qua API. Cách tiếp cận này rút ngắn thời gian phát triển và giúp nhóm tập trung vào logic nghiệp vụ.

Bedrock cung cấp quyền truy cập đến các nhóm mô hình từ nhiều nhà cung cấp, gồm Amazon Titan, Anthropic Claude, Meta Llama, Cohere và Mistral AI. Ứng dụng có thể đánh giá, chọn mô hình phù hợp cho từng trường hợp sử dụng mà không phải xây dựng lại toàn bộ hạ tầng AI.

![Kiến trúc ứng dụng AI sử dụng Amazon Bedrock trên AWS](/images/blog3/amazon-bedrock-ai-architecture.png)

### Các thành phần chính

| Thành phần | Vai trò |
| --- | --- |
| **Ứng dụng web hoặc di động** | Cung cấp giao diện để người dùng gửi yêu cầu và nhận kết quả. |
| **Amazon API Gateway** | Nhận yêu cầu từ ứng dụng, chuyển đến tầng xử lý và trả phản hồi. |
| **AWS Lambda** | Kiểm tra dữ liệu đầu vào, áp dụng logic nghiệp vụ, xây dựng câu lệnh và gọi mô hình qua Amazon Bedrock. |
| **Amazon Bedrock** | Cung cấp API truy cập mô hình nền tảng và tạo nội dung từ câu lệnh. |
| **Amazon S3** | Lưu tài liệu hoặc dữ liệu phi cấu trúc cần thiết cho ứng dụng. |
| **Amazon DynamoDB** | Lưu dữ liệu ứng dụng, trạng thái phiên hoặc lịch sử tương tác. |
| **Knowledge Bases for Amazon Bedrock** | Truy xuất thông tin từ nguồn dữ liệu để bổ sung ngữ cảnh cho mô hình. |
| **Amazon CloudWatch** | Thu thập nhật ký, số liệu, cảnh báo và hỗ trợ khắc phục sự cố. |

### Luồng yêu cầu của ứng dụng

Một yêu cầu AI tạo sinh đi qua hệ thống như sau:

1. Người dùng nhập câu hỏi hoặc hướng dẫn trong trang web hay ứng dụng di động.
2. Amazon API Gateway nhận yêu cầu và chuyển đến AWS Lambda.
3. Lambda kiểm tra dữ liệu đầu vào, thực thi logic nghiệp vụ và xây dựng câu lệnh.
4. Nếu cần thêm ngữ cảnh, Lambda hoặc quy trình Bedrock truy xuất tài liệu từ Amazon S3, dữ liệu từ DynamoDB hoặc kiến thức liên quan qua Knowledge Bases.
5. Lambda gọi mô hình nền tảng đã chọn qua Amazon Bedrock.
6. Mô hình xử lý câu lệnh và trả kết quả cho Lambda.
7. Lambda định dạng, kiểm tra hoặc lưu kết quả trước khi phản hồi.
8. API Gateway gửi câu trả lời cuối cùng về giao diện người dùng.

### Lựa chọn mô hình nền tảng

Amazon Bedrock không giới hạn ứng dụng vào một mô hình duy nhất. Nhà phát triển có thể so sánh các mô hình theo chất lượng phản hồi, khả năng suy luận, ngôn ngữ, loại nội dung hỗ trợ, độ trễ, kích thước cửa sổ ngữ cảnh, chi phí và yêu cầu của tác vụ như trả lời câu hỏi, tóm tắt, tạo nội dung hoặc lập trình.

### Cơ sở tri thức và RAG

**Phương pháp tạo sinh tăng cường truy xuất (Retrieval-Augmented Generation – RAG)** kết hợp khả năng tạo nội dung của mô hình nền tảng với thông tin được truy xuất từ nguồn dữ liệu riêng. Knowledge Bases for Amazon Bedrock hỗ trợ quy trình này, cho phép ứng dụng sử dụng tài liệu của tổ chức thay vì chỉ dựa vào kiến thức có sẵn trong mô hình.

### Giám sát với Amazon CloudWatch

Amazon CloudWatch cung cấp khả năng quan sát cho hệ thống. Nhật ký, số liệu và cảnh báo từ API Gateway, Lambda cùng các thành phần liên quan giúp quản trị viên theo dõi lưu lượng, độ trễ và lỗi; phát hiện hoạt động bất thường; điều tra nguyên nhân và xử lý sự cố nhanh hơn.

### Kết luận

Amazon Bedrock giảm đáng kể lượng hạ tầng mà nhóm phải quản lý khi phát triển ứng dụng AI tạo sinh. Kết hợp với API Gateway, Lambda, S3, DynamoDB, Knowledge Bases và CloudWatch, dịch vụ này có thể đóng vai trò trung tâm của một kiến trúc AI theo mô-đun, dễ bảo trì và mở rộng.
