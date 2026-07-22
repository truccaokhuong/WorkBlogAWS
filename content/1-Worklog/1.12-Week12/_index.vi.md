---
title: "Worklog Tuần 12"
date: 2026-07-03
weight: 2
chapter: false
pre: " <b> 1.12. </b> "
---


### Mục tiêu tuần 12:

* Kiểm thử toàn diện trên cả ba phân hệ (Business, Booking, Admin).
* Sửa các lỗi nghiêm trọng và xử lý edge cases phát hiện trong quá trình kiểm thử.
* Hoàn thiện UI/UX với responsive design, animation và cải thiện accessibility.
* Viết tài liệu dự án bao gồm hướng dẫn sử dụng và tài liệu kỹ thuật.
* Tổng duyệt cuối cùng với nhóm và chuẩn bị nộp báo cáo.

### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu |
| --- | --------- | ------------ | --------------- | -------------- |
| 2 | - **Kiểm thử Tích hợp**: <br>&emsp; + Kiểm thử luồng xuyên suốt các phân hệ: User đặt booking → Business owner xác nhận → Admin giám sát <br>&emsp; + Xác minh tất cả 9 màn hình được phân công hoạt động end-to-end <br>&emsp; + Kiểm thử tích hợp API với backend services <br>&emsp; + Xác thực authentication và authorization trên tất cả các route <br>&emsp; + Kiểm thử tính năng real-time: WebSocket notifications cho thay đổi trạng thái booking, review mới, hành động admin | 03/07/2026 | 03/07/2026 | Jest, React Testing Library, Cypress |
| 3 | - **Sửa lỗi & Edge Cases**: <br>&emsp; + Sửa 15 lỗi UI: căn chỉnh nút, thông báo xác thực form, responsive breakpoints, trạng thái loading <br>&emsp; + Xử lý edge cases: trạng thái trống, lỗi mạng, session timeout, xung đột booking đồng thời <br>&emsp; + Sửa race conditions trong cập nhật trạng thái booking và phê duyệt claim <br>&emsp; + Giải quyết CORS và xử lý lỗi API không nhất quán <br>&emsp; + Tối ưu hiệu năng: lazy loading ảnh, code splitting, memoization | 04/07/2026 | 04/07/2026 | Chrome DevTools, React Profiler |
| 4 | - **Hoàn thiện UI/UX**: <br>&emsp; + Triển khai spacing, typography và color scheme nhất quán trên tất cả các màn hình <br>&emsp; + Thêm micro-animations: chuyển trang, hiệu ứng hover, skeleton loading <br>&emsp; + Đảm bảo responsive design hoạt động trên mobile (320px), tablet (768px) và desktop (1440px+) <br>&emsp; + Thêm tính năng accessibility: ARIA labels, keyboard navigation, focus management <br>&emsp; + Triển khai dark mode với theme toggle | 05/07/2026 | 05/07/2026 | Tailwind CSS, Framer Motion, WCAG 2.1 AA |
| 5 | - **Tài liệu**: <br>&emsp; + Viết Hướng dẫn Sử dụng bao gồm tất cả tính năng với ảnh chụp màn hình và hướng dẫn từng bước (30 trang) <br>&emsp; + Tạo Tài liệu Kỹ thuật: tổng quan kiến trúc, tham khảo API, sơ đồ database, hướng dẫn triển khai (40 trang) <br>&emsp; + Ghi chép các màn hình được phân công với cây component, quản lý state và sơ đồ luồng dữ liệu <br>&emsp; + Viết README.md với tổng quan dự án, hướng dẫn cài đặt và quy tắc đóng góp | 06/07/2026 | 06/07/2026 | Markdown, draw.io (sơ đồ) |
| 6 | - **Tổng duyệt & Nộp báo cáo**: <br>&emsp; + Tổng duyệt code lần cuối và merge tất cả các nhánh tính năng <br>&emsp; + Chạy toàn bộ test suite và xác minh tỷ lệ pass 100% <br>&emsp; + Triển khai phiên bản cuối lên production sử dụng AWS Amplify <br>&emsp; + Chuẩn bị gói nộp: mã nguồn, tài liệu, video demo <br>&emsp; + Viết báo cáo tổng kết thực tập: bài học kinh nghiệm, thách thức đã vượt qua và kỹ năng đã đạt được | 07/07/2026 | 07/07/2026 | AWS Amplify, Git |


### Kết quả đạt được tuần 12:

* ✅ Thực hiện thành công 80+ integration test trên tất cả các phân hệ với tỷ lệ pass 98% (2 lỗi nhỏ không chặn đã được ghi nhận).
* ✅ Đã sửa 23 lỗi bao gồm 5 lỗi nghiêm trọng trong booking state machine và luồng phê duyệt claim của admin.
* ✅ Triển khai responsive design với hỗ trợ đầy đủ cho mobile, tablet và desktop - đã kiểm thử trên Chrome, Firefox, Safari và Edge.
* ✅ Đạt chuẩn accessibility WCAG 2.1 AA với ARIA labels, keyboard navigation và screen reader support.
* ✅ Thêm dark mode, animation chuyển trang và skeleton loading states để cải thiện UX.
* ✅ Hoàn thành tài liệu toàn diện:
  * **Hướng dẫn Sử dụng**: 30 trang với 50+ ảnh chụp màn hình bao phủ tất cả tính năng
  * **Tài liệu Kỹ thuật**: 40 trang với sơ đồ kiến trúc, tham khảo API và hướng dẫn triển khai
* ✅ Dự án cuối đã triển khai lên môi trường production AWS Amplify với CI/CD pipeline.
* ✅ Toàn bộ code đã merge, review và gắn tag v1.0.0.

### Tổng kết Hành trình Thực tập (12 Tuần)

Nhìn lại hành trình thực tập 12 tuần với First Cloud Journey tại AWS Vietnam, tôi đã trưởng thành vượt bậc cả về mặt kỹ thuật và chuyên môn:

**Phát triển Kỹ thuật:**
- Thành thạo hệ sinh thái AWS bao gồm các dịch vụ cốt lõi (EC2, S3, RDS, Lambda, API Gateway, Cognito, CloudFront)
- Xây dựng ứng dụng full-stack từ đầu sử dụng React, TypeScript, Node.js, PostgreSQL và nhiều dịch vụ AWS
- Có kinh nghiệm thực tế với kiến trúc serverless, giao tiếp WebSocket real-time và triển khai đám mây
- Phát triển 9 màn hình sẵn sàng production trên ba phân hệ, xử lý logic nghiệp vụ phức tạp và quản lý state
- Viết 200+ unit test và integration test đảm bảo chất lượng và độ tin cậy của code

**Kỹ năng Chuyên môn:**
- Hợp tác hiệu quả trong nhóm 4 thành viên sử dụng phương pháp Agile với standup hàng ngày và sprint hai tuần
- Học cách phân rã yêu cầu phức tạp thành các nhiệm vụ khả thi và ước lượng effort chính xác
- Cải thiện kỹ năng giao tiếp qua các buổi demo định kỳ, code review và viết tài liệu
- Có kinh nghiệm với CI/CD pipeline và quy trình triển khai production
- Hiểu tầm quan trọng của accessibility, responsive design và phát triển lấy người dùng làm trung tâm

**Thách thức đã Vượt qua:**
- Logic booking state machine đòi hỏi hiểu sâu về quy tắc nghiệp vụ và xử lý cẩn thận các cập nhật đồng thời
- Tích hợp WebSocket real-time đặt ra thách thức với quản lý kết nối và chiến lược reconnect
- Cân bằng giữa phát triển tính năng với kiểm thử và tài liệu trong timeline chặt chẽ đã rèn luyện kỹ năng ưu tiên

**Định hướng Tương lai:**
Kỳ thực tập này đã củng cố niềm đam mê của tôi với điện toán đám mây và phát triển full-stack. Tôi dự định theo đuổi chứng chỉ AWS Solutions Architect và tiếp tục xây dựng các ứng dụng cloud-native. Kinh nghiệm làm việc trong một dự án nhóm thực tế với các công cụ và quy trình chuẩn công nghiệp đã chuẩn bị tốt cho tôi bước vào sự nghiệp kỹ sư phần mềm.
