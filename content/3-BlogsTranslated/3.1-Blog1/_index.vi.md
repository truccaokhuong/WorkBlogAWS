---
title: "Blog 1 - Amazon Bedrock – Dịch vụ Generative AI trên AWS"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

Trong thời gian gần đây mình đang dành thời gian tìm hiểu các dịch vụ AI trên AWS, đặc biệt là Amazon Bedrock. Sau khi đọc tài liệu của AWS và xem qua một số ví dụ triển khai, mình thấy đây là một dịch vụ khá hay vì giúp việc xây dựng các ứng dụng AI trở nên đơn giản hơn rất nhiều.

Điểm mình ấn tượng đầu tiên là Amazon Bedrock không yêu cầu người phát triển phải tự cài đặt hay quản lý hạ tầng AI. Thay vì phải chuẩn bị máy chủ GPU, cài đặt framework và triển khai mô hình ngôn ngữ lớn (LLM), AWS đã cung cấp sẵn nhiều mô hình AI từ các hãng khác nhau trên cùng một nền tảng. Người dùng chỉ cần gửi prompt thông qua API là có thể nhận được kết quả từ mô hình AI.

Trong sơ đồ mình minh họa, luồng xử lý của một ứng dụng AI sử dụng Amazon Bedrock diễn ra như sau:

Người dùng gửi yêu cầu từ Website hoặc Mobile App.
Amazon API Gateway tiếp nhận request và chuyển đến AWS Lambda.
AWS Lambda đóng vai trò xử lý nghiệp vụ, kiểm tra dữ liệu đầu vào, xây dựng prompt phù hợp rồi gửi đến Amazon Bedrock.
Amazon Bedrock sẽ lựa chọn mô hình AI phù hợp để xử lý và tạo ra câu trả lời.
Nếu ứng dụng cần truy xuất dữ liệu, Lambda có thể đọc tài liệu từ Amazon S3 hoặc lấy dữ liệu từ Amazon DynamoDB trước khi gửi prompt hoặc sau khi nhận kết quả.
Kết quả cuối cùng sẽ được trả về cho người dùng thông qua API Gateway.

Một điểm mình thấy khá thú vị là Amazon Bedrock không chỉ hỗ trợ một mô hình AI duy nhất mà còn tích hợp nhiều Foundation Models của các nhà cung cấp khác nhau như Amazon Titan, Claude, Llama, Cohere hay Mistral AI. Điều này giúp nhà phát triển dễ dàng thử nghiệm nhiều mô hình mà không cần thay đổi quá nhiều kiến trúc hệ thống.

Ngoài ra, Bedrock còn hỗ trợ kết hợp với Amazon Knowledge Bases để xây dựng các ứng dụng theo mô hình RAG (Retrieval-Augmented Generation). Thay vì chỉ dựa vào kiến thức đã được huấn luyện sẵn, AI có thể truy xuất thêm tài liệu từ doanh nghiệp hoặc từ Amazon S3 trước khi tạo câu trả lời. Điều này giúp kết quả chính xác và cập nhật hơn, đặc biệt phù hợp với chatbot nội bộ, trợ lý tra cứu tài liệu hoặc hệ thống hỏi đáp.

Một dịch vụ khác xuất hiện trong sơ đồ là Amazon CloudWatch. Đây không phải là thành phần xử lý dữ liệu mà là dịch vụ dùng để giám sát toàn bộ hệ thống. CloudWatch sẽ thu thập log, metrics và cảnh báo từ API Gateway, Lambda, Bedrock, S3 hoặc DynamoDB để giúp quản trị viên theo dõi hiệu suất, phát hiện lỗi và xử lý sự cố nhanh hơn.

Qua quá trình tìm hiểu, mình nhận thấy kiến trúc của AWS được thiết kế theo hướng tách biệt từng thành phần. Mỗi dịch vụ đảm nhiệm một vai trò riêng nên hệ thống dễ mở rộng, dễ bảo trì và có thể thay đổi từng thành phần mà không ảnh hưởng đến toàn bộ ứng dụng. Đây cũng là một trong những lý do AWS được nhiều doanh nghiệp lựa chọn khi triển khai các ứng dụng AI.

Trong thời gian tới mình sẽ tiếp tục nghiên cứu sâu hơn về các chủ đề như:

Amazon Bedrock Agents.
Knowledge Bases và mô hình RAG.
Prompt Engineering trên AWS.
Tích hợp Bedrock với Lambda và API Gateway để xây dựng chatbot AI hoàn chỉnh.
So sánh hiệu quả giữa các Foundation Models như Claude, Titan và Llama trong từng bài toán thực tế.

Mình vẫn đang trong quá trình học nên bài viết chủ yếu là những gì mình tổng hợp và tìm hiểu được. Nếu anh/chị hoặc các bạn đã có kinh nghiệm triển khai Amazon Bedrock trong dự án thực tế thì rất mong nhận được thêm góp ý hoặc chia sẻ để mình có cơ hội học hỏi thêm.
