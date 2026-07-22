---
title: "Nhật ký Tuần 12"
date: 2026-07-03
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

### Mục tiêu tuần 12

* Kiểm thử toàn diện trên ba phân hệ doanh nghiệp, đặt chỗ và quản trị.
* Sửa lỗi nghiêm trọng và xử lý các trường hợp biên.
* Hoàn thiện trải nghiệm giao diện, khả năng thích ứng và khả năng tiếp cận.
* Viết tài liệu dự án, tổng duyệt và chuẩn bị nộp báo cáo.

### Các công việc cần triển khai trong tuần này

| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --- | --- | --- | --- |
| 2 | **Kiểm thử tích hợp:** kiểm tra luồng người dùng đặt chỗ, chủ doanh nghiệp xác nhận và quản trị viên giám sát; xác minh chín màn hình hoạt động xuyên suốt; kiểm tra API, xác thực, phân quyền và thông báo WebSocket. | 03/07/2026 | 03/07/2026 | Jest, React Testing Library, Cypress |
| 3 | **Sửa lỗi và trường hợp biên:** sửa lỗi căn chỉnh, biểu mẫu, điểm ngắt màn hình và trạng thái đang tải; xử lý lỗi mạng, phiên hết hạn, xung đột đặt chỗ; khắc phục điều kiện tranh chấp, CORS và xử lý lỗi API; tối ưu tải ảnh, tách mã và ghi nhớ kết quả. | 04/07/2026 | 04/07/2026 | Chrome DevTools, React Profiler |
| 4 | **Hoàn thiện giao diện và trải nghiệm:** thống nhất khoảng cách, kiểu chữ, màu sắc; thêm hiệu ứng nhỏ; kiểm tra trên điện thoại, máy tính bảng và máy tính; bổ sung nhãn ARIA, điều hướng bàn phím, quản lý tiêu điểm và chế độ tối. | 05/07/2026 | 05/07/2026 | Tailwind CSS, Framer Motion, WCAG 2.1 AA |
| 5 | **Tài liệu:** viết hướng dẫn sử dụng, tài liệu kỹ thuật, tổng quan kiến trúc, tham khảo API, sơ đồ cơ sở dữ liệu, hướng dẫn triển khai và ghi chú về cây thành phần, trạng thái, luồng dữ liệu. | 06/07/2026 | 06/07/2026 | Markdown, draw.io |
| 6 | **Tổng duyệt và nộp báo cáo:** rà soát mã, hợp nhất các nhánh, chạy toàn bộ bộ kiểm thử, triển khai bản cuối lên AWS Amplify, chuẩn bị mã nguồn, tài liệu, video trình diễn và báo cáo tổng kết thực tập. | 07/07/2026 | 07/07/2026 | AWS Amplify, Git |

### Kết quả đạt được tuần 12

* ✅ Thực hiện hơn 80 kiểm thử tích hợp với tỷ lệ đạt 98%; hai lỗi nhỏ không ảnh hưởng luồng chính đã được ghi nhận.
* ✅ Sửa 23 lỗi, gồm năm lỗi nghiêm trọng trong vòng đời đặt chỗ và luồng xác minh của quản trị viên.
* ✅ Hoàn thiện thiết kế thích ứng trên điện thoại, máy tính bảng và máy tính; kiểm tra trên Chrome, Firefox, Safari và Edge.
* ✅ Đạt tiêu chuẩn tiếp cận WCAG 2.1 AA với nhãn ARIA, điều hướng bàn phím và hỗ trợ trình đọc màn hình.
* ✅ Hoàn thành hướng dẫn sử dụng 30 trang và tài liệu kỹ thuật 40 trang.
* ✅ Triển khai bản cuối lên AWS Amplify với quy trình CI/CD; hợp nhất, rà soát toàn bộ mã và gắn nhãn phiên bản `v1.0.0`.

### Tổng kết hành trình thực tập 12 tuần

**Phát triển kỹ thuật:**

- Nắm vững các dịch vụ AWS cốt lõi như EC2, S3, RDS, Lambda, API Gateway, Cognito và CloudFront.
- Xây dựng ứng dụng đầy đủ từ giao diện đến hệ thống phía máy chủ bằng React, TypeScript, Node.js và PostgreSQL.
- Có kinh nghiệm thực tế với kiến trúc phi máy chủ, WebSocket theo thời gian thực và triển khai trên đám mây.
- Phát triển chín màn hình cho ba phân hệ, xử lý logic nghiệp vụ phức tạp và quản lý trạng thái.
- Viết hơn 200 kiểm thử đơn vị và kiểm thử tích hợp để đảm bảo chất lượng mã.

**Kỹ năng chuyên môn:**

- Hợp tác trong nhóm bốn thành viên theo phương pháp Agile, họp nhanh hằng ngày và làm việc theo chu kỳ hai tuần.
- Phân rã yêu cầu phức tạp thành nhiệm vụ khả thi và ước lượng khối lượng công việc.
- Cải thiện kỹ năng giao tiếp qua các buổi trình diễn, rà soát mã và viết tài liệu.
- Có kinh nghiệm với quy trình CI/CD và triển khai vào môi trường vận hành thực tế.
- Hiểu tầm quan trọng của khả năng tiếp cận, thiết kế thích ứng và phát triển lấy người dùng làm trung tâm.

**Thách thức đã vượt qua:**

- Vòng đời trạng thái đặt chỗ đòi hỏi hiểu sâu quy tắc nghiệp vụ và xử lý cập nhật đồng thời.
- Tích hợp WebSocket đặt ra thách thức về quản lý kết nối và kết nối lại.
- Việc cân bằng phát triển tính năng, kiểm thử và tài liệu trong thời gian giới hạn giúp tôi rèn luyện kỹ năng ưu tiên.

**Định hướng tương lai:**

Kỳ thực tập củng cố niềm đam mê của tôi với điện toán đám mây và phát triển ứng dụng toàn diện. Tôi dự định theo đuổi chứng chỉ AWS Solutions Architect và tiếp tục xây dựng các ứng dụng hướng đám mây. Kinh nghiệm làm việc trong dự án nhóm thực tế với công cụ và quy trình chuẩn đã giúp tôi chuẩn bị tốt hơn cho sự nghiệp kỹ sư phần mềm.
