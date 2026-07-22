---
title: "Amazon Bedrock – Generative AI trên AWS"
date: 2024-01-01
weight: 3
chapter: false
pre: " <b> 3.3. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

**Amazon Bedrock** là dịch vụ được quản lý hoàn toàn để xây dựng ứng dụng generative AI trên AWS. Thay vì cấp phát GPU server, cài đặt framework và triển khai large language model, nhà phát triển có thể truy cập **foundation models (FMs)** thông qua API. Cách tiếp cận này rút ngắn thời gian phát triển và cho phép nhóm tập trung vào business logic của ứng dụng.

Bedrock cung cấp quyền truy cập đến các model family từ nhiều nhà cung cấp, bao gồm Amazon Titan, Anthropic Claude, Meta Llama, Cohere và Mistral AI. Ứng dụng có thể đánh giá và chọn model phù hợp cho từng use case mà không cần xây dựng lại toàn bộ hạ tầng AI.

![Kiến trúc ứng dụng AI sử dụng Amazon Bedrock trên AWS](/images/blog3/amazon-bedrock-ai-architecture.png)

### Các Thành phần Chính

| Thành phần | Vai trò |
| --- | --- |
| **Web/Mobile App** | Cung cấp giao diện để người dùng gửi yêu cầu và nhận kết quả. |
| **Amazon API Gateway** | Nhận yêu cầu từ ứng dụng, chuyển tiếp đến tầng xử lý và trả về phản hồi. |
| **AWS Lambda** | Xác thực đầu vào, áp dụng business logic, xây dựng prompt và gọi model đã chọn qua Amazon Bedrock. |
| **Amazon Bedrock** | Cung cấp API để truy cập foundation models và tạo nội dung từ prompt. |
| **Amazon S3** | Lưu trữ tài liệu hoặc dữ liệu phi cấu trúc cần thiết cho ứng dụng. |
| **Amazon DynamoDB** | Lưu trữ dữ liệu ứng dụng, trạng thái phiên hoặc lịch sử tương tác khi cần. |
| **Knowledge Bases for Amazon Bedrock** | Truy xuất thông tin liên quan từ nguồn dữ liệu để bổ sung ngữ cảnh cho model. |
| **Amazon CloudWatch** | Thu thập log và metric, hỗ trợ cảnh báo, giám sát hiệu suất và khắc phục sự cố. |

### Luồng Yêu cầu Ứng dụng

Một yêu cầu generative AI di chuyển qua hệ thống như sau:

1. Người dùng nhập câu hỏi hoặc hướng dẫn trong website hoặc ứng dụng di động.
2. Amazon API Gateway nhận yêu cầu và chuyển tiếp đến AWS Lambda.
3. Lambda xác thực đầu vào, thực thi business logic và xây dựng prompt.
4. Nếu cần thêm ngữ cảnh, Lambda hoặc Bedrock workflow truy xuất tài liệu từ Amazon S3, dữ liệu từ DynamoDB hoặc kiến thức liên quan qua Knowledge Base.
5. Lambda gọi foundation model đã chọn qua Amazon Bedrock.
6. Model xử lý prompt và trả về output cho Lambda.
7. Lambda có thể định dạng, xác thực hoặc lưu trữ output trước khi phản hồi.
8. API Gateway gửi câu trả lời cuối cùng trở lại giao diện người dùng.

### Lựa chọn Foundation Model

Amazon Bedrock không giới hạn ứng dụng vào một model duy nhất. Nhà phát triển có thể so sánh foundation models theo chất lượng phản hồi và khả năng suy luận, ngôn ngữ và loại nội dung hỗ trợ, độ trễ yêu cầu, kích thước context-window, chi phí sử dụng và yêu cầu tác vụ như trả lời câu hỏi, tóm tắt, tạo nội dung hoặc lập trình.

### Knowledge Bases và RAG

**Retrieval-Augmented Generation (RAG)** kết hợp khả năng sinh của foundation model với thông tin truy xuất từ nguồn dữ liệu riêng. Knowledge Bases for Amazon Bedrock hỗ trợ workflow này, cho phép ứng dụng AI sử dụng tài liệu tổ chức thay vì chỉ dựa vào kiến thức có sẵn trong model.

### Giám sát với Amazon CloudWatch

Amazon CloudWatch cung cấp khả năng quan sát cho hệ thống. Log, metric và cảnh báo từ API Gateway, Lambda và các thành phần liên quan giúp quản trị viên giám sát lưu lượng, độ trễ và lỗi, phát hiện yêu cầu thất bại hoặc hoạt động bất thường, và điều tra nguyên nhân và giải quyết sự cố nhanh hơn.

### Kết luận

Amazon Bedrock giảm đáng kể hạ tầng mà nhóm phải quản lý khi phát triển ứng dụng generative AI. Kết hợp với API Gateway, Lambda, S3, DynamoDB, Knowledge Bases và CloudWatch, nó có thể đóng vai trò trung tâm của kiến trúc AI module có thể bảo trì và mở rộng.
