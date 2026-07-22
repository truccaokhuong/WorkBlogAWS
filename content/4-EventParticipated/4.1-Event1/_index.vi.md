---
title: "Event 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 4.1. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

# Bài thu hoạch: "FCAJ Community Day"

| Thông tin | Chi tiết |
|---|---|
| **Ngày** | 09/05/2026 |
| **Địa điểm** | Tầng 26, Tòa nhà Bitexco, Số 02 Đường Hải Triều, Phường Sài Gòn, TP. Hồ Chí Minh |
| **Vai trò** | Người tham dự |

### Mục Đích Của Sự Kiện

- Chia sẻ các kỹ thuật tâm lý để tăng động lực học tập và xây dựng thói quen học tập bền vững.
- Giới thiệu các kỹ thuật Prompt Engineering nâng cao để cải thiện chất lượng đầu ra của LLM.
- Trình bày kiến trúc AWS Serverless thực tế cho các ứng dụng AI.
- Định hướng nghề nghiệp, nhấn mạnh nền tảng kỹ thuật cốt lõi và tư duy chuyên nghiệp.
- Giới thiệu phương pháp BMAD để cấu trúc tương tác AI Agent trong Vòng đời Phát triển Phần mềm (SDLC).

### Danh Sách Diễn Giả

- **Mr. Huynh Hoang Long** - Chia sẻ kỹ thuật điều tiết dopamine và gamification trong học tập.
- **Mr. Thinh Nguyen** - Trình bày về Prompt Engineering và kiến trúc AWS Cloud.
- **Mr. Khang** - Solutions Architect tại Cloud Kinetics.
- **Ms. Thao** - Software Developer tại VIB.

### Nội Dung Nổi Bật

#### 1. Hacking Não Bộ để Tạo Động Lực Học Tập

- **Cơ chế Dopamine:** Dopamine được kích hoạt bởi sự mong đợi phần thưởng, không chỉ là sự hoàn thành. Đưa vào sự biến đổi và tò mò có thể duy trì sự gắn kết lâu dài.
- **Gamification:** Áp dụng các yếu tố trò chơi vào việc học, như duy trì chuỗi ngày liên tục và tận dụng nỗi sợ mất tiến độ để xây dựng tính nhất quán.
- **Chia nhỏ nhiệm vụ:** Chia các chủ đề lớn thành các phần nhỏ, dễ quản lý (ví dụ: học một dịch vụ AWS mỗi ngày) để tránh sự kháng cự tinh thần.
- **Quy tắc 2 Phút:** Thực hiện ngay các nhiệm vụ mất dưới hai phút để tránh trì hoãn.

#### 2. Prompt Engineering Đỉnh Cao & Kiến trúc AWS Serverless

- **Cấu trúc Prompt:** Prompt chất lượng cao phải xác định rõ Vai trò, Nhiệm vụ, Ngữ cảnh, Đầu vào, Ràng buộc Đầu ra và Ví dụ. Tránh các ràng buộc tiêu cực để giảm thiểu Ảo giác LLM.
- **Kỹ thuật Nâng cao:** Sử dụng các phương pháp như Chuỗi Suy nghĩ (Chain of Thought) và Cây Suy nghĩ (Tree of Thoughts) để hướng dẫn LLM qua quá trình suy luận phức tạp, từng bước.
- **Hệ sinh thái Serverless:** Trình diễn kiến trúc ứng dụng AI có khả năng mở rộng sử dụng:
    - **Frontend & CDN:** Amazon S3 và Amazon CloudFront.
    - **Xác thực:** Amazon Cognito.
    - **Backend Compute:** Amazon API Gateway và AWS Lambda.
    - **AI & Lưu trữ Dữ liệu:** Amazon Bedrock cho foundation models, Amazon DynamoDB cho lưu trữ NoSQL, và Amazon CloudWatch để giám sát liên tục.

#### 3. Tư Duy Nghề Nghiệp & Nền Tảng Cốt Lõi

- **Nền tảng quan trọng hơn Công cụ:** AI đóng vai trò là bộ khuếch đại cho các kỹ năng hiện có. Điều quan trọng là không giao phó tư duy phản biện cho AI; nền tảng kỹ thuật vững chắc vẫn không thể thay thế.
- **Tư duy "Tại sao":** Chuyên gia phải liên tục đặt câu hỏi về lý do đằng sau các quyết định kỹ thuật và thiết kế hệ thống, thay vì chỉ tập trung vào việc triển khai.
- **Tính chính trực nghề nghiệp:** Cố gắng dự đoán và xử lý triệt để các trường hợp ngoại lệ, duy trì tiêu chuẩn cao ngay cả khi không bị quản lý giám sát rõ ràng.
- **Tầm nhìn dài hạn:** Ưu tiên việc thu nhận kiến thức, kinh nghiệm thực tế và mạng lưới quan hệ hơn là lợi ích tài chính ngắn hạn trong giai đoạn đầu sự nghiệp.

#### 4. Phương Pháp BMAD cho SDLC có Hỗ Trợ AI

- **Hạn chế Cửa sổ Ngữ cảnh:** Việc prompting không có cấu trúc và liên tục dẫn đến tràn Cửa sổ Ngữ cảnh, gây ra Ảo giác và mã nguồn phân mảnh, không sử dụng được.
- **AI Agent theo Vai trò:** Phương pháp BMAD giảm thiểu điều này bằng cách gán các vai trò SDLC riêng biệt cho các AI Agent chuyên biệt:
    - **PM Agent:** Tạo PRD (Tài liệu Yêu cầu Sản phẩm).
    - **Architect Agent:** Xây dựng Kiến trúc Hệ thống.
    - **BA Agent:** Phân rã yêu cầu thành các Epic và Story chi tiết.
    - **Developer & QA Agents:** Tạo và kiểm thử lặp lại mã cho các story riêng biệt.
- **Lợi ích Kiến trúc:** Cô lập các nhiệm vụ đảm bảo đầu ra chính xác, giảm thiểu chồng chéo ngữ cảnh và tạo ra các thành phần phần mềm sẵn sàng sản xuất.

### Ứng Dụng Vào Công Việc

- **Tối ưu Tương tác LLM:** Triển khai Chuỗi Suy nghĩ và các mẫu prompt có cấu trúc cho tất cả các nhiệm vụ phát triển có hỗ trợ AI.
- **Áp dụng Kiến trúc Serverless:** Thử nghiệm kết hợp AWS Lambda, Amazon API Gateway và Amazon Bedrock cho các thành phần ứng dụng có khả năng mở rộng.
- **Củng cố Kiến thức Cốt lõi:** Dành các buổi học tập trung vào các nguyên lý hạ tầng cơ bản, chủ động tránh phụ thuộc vào AI cho logic nền tảng.
- **Triển khai BMAD trong Dự án:** Cấu trúc các bài tập lập trình tương lai bằng cách xác định vai trò và ranh giới ngữ cảnh rõ ràng trước khi tạo mã với AI Agents.

### Trải nghiệm trong event

Tham dự **"FCAJ Community Day"** là một trải nghiệm vô cùng truyền cảm hứng, mở rộng góc nhìn của tôi về cả khía cạnh kỹ thuật và tâm lý khi làm việc trong ngành công nghiệp đám mây. Những suy ngẫm chính bao gồm:

#### Tâm lý Học tập & Động lực
- Buổi chia sẻ của Mr. Huynh Hoang Long về điều tiết dopamine đã cho tôi hiểu biết khoa học về cách xây dựng thói quen học tập nhất quán. Quy tắc 2 Phút và chiến lược chia nhỏ nhiệm vụ có thể áp dụng ngay vào thói quen học tập hàng ngày của tôi.
- Các khái niệm gamification như duy trì chuỗi ngày đã thay đổi cách tôi tiếp cận việc học các dịch vụ AWS - những gì từng cảm thấy quá sức giờ đây giống như một trò chơi có cấu trúc.

#### Phát triển Kỹ thuật
- Buổi Prompt Engineering của Mr. Thinh Nguyen thực sự mở mang tầm mắt. Hiểu các kỹ thuật như Chuỗi Suy nghĩ và Cây Suy nghĩ đã thay đổi căn bản cách tôi tương tác với LLM để lập trình và giải quyết vấn đề.
- Nhìn thấy kiến trúc Serverless thực tế kết hợp S3, CloudFront, Cognito, API Gateway, Lambda, Bedrock và DynamoDB đã cho tôi một bản thiết kế cụ thể để thiết kế các ứng dụng hỗ trợ AI.

#### Góc nhìn Nghề nghiệp
- Sự nhấn mạnh vào "Nền tảng quan trọng hơn Công cụ" đã gây ấn tượng sâu sắc. AI có thể tăng tốc việc học, nhưng không thể thay thế sự hiểu biết sâu sắc về các nguyên lý kỹ thuật.
- Buổi thảo luận nghề nghiệp đã củng cố tầm quan trọng của việc đặt câu hỏi "tại sao" đằng sau mỗi quyết định kỹ thuật, duy trì tính chính trực nghề nghiệp và ưu tiên sự phát triển hơn lợi ích ngắn hạn trong giai đoạn đầu sự nghiệp.

#### Phương pháp BMAD
- Tìm hiểu về phương pháp BMAD đã cung cấp một khuôn khổ thực tế để tận dụng AI Agents trong phát triển phần mềm mà không mất kiểm soát về chất lượng mã và kiến trúc.
- Cách tiếp cận dựa trên vai trò (PM, Architect, BA, Developer, QA) phản ánh cấu trúc nhóm thực tế và làm cho việc phát triển có hỗ trợ AI trở nên có cấu trúc và đáng tin cậy hơn.

#### Một số hình ảnh khi tham gia sự kiện
*Thêm các hình ảnh của các bạn tại đây*

> Tổng thể, FCAJ Community Day không chỉ là một sự kiện kỹ thuật - đó là một trải nghiệm toàn diện kết hợp tâm lý học, sự xuất sắc về kỹ thuật, trí tuệ nghề nghiệp và các thực hành AI tiên tiến sẽ định hình cách tiếp cận của tôi đối với điện toán đám mây và phát triển chuyên môn trong tương lai.
