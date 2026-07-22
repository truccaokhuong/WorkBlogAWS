---
title: "Bản đề xuất"
date: 2026-04-17
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

# Travel Platform
## Nền tảng khám phá địa điểm và lập kế hoạch du lịch trên AWS

### 1. Tóm tắt điều hành

Travel Platform là ứng dụng web trên nền tảng đám mây, hợp nhất các chức năng khám phá địa điểm, lưu địa điểm yêu thích, lập kế hoạch chuyến đi, quản lý lịch trình, đánh giá và đặt chỗ trong cùng một hệ thống. Nền tảng cũng cung cấp chức năng riêng cho chủ doanh nghiệp và quản trị viên. Phạm vi dự án được thiết kế phù hợp để nhóm thực tập gồm năm thành viên có thể triển khai, trình diễn và vận hành trong thời gian thực tập.

Giao diện người dùng được phân phối qua Amazon CloudFront và Amazon S3. Amazon Cognito quản lý việc xác thực người dùng, còn Amazon API Gateway tiếp nhận các yêu cầu gửi đến hệ thống phía máy chủ. AWS Lambda thực thi logic ứng dụng và các tác vụ nền. Amazon RDS for PostgreSQL lưu dữ liệu quan hệ, Amazon ElastiCache for Redis tăng tốc các truy vấn thường xuyên, còn một vùng lưu trữ S3 riêng dùng cho hình ảnh được tải lên. Amazon EventBridge, Amazon SQS và Amazon SNS hỗ trợ xử lý bất đồng bộ; Amazon CloudWatch tập trung nhật ký và giám sát hệ thống.

Giải pháp sử dụng kiến trúc phi máy chủ theo mô-đun. Các trách nhiệm được tách thành những phân hệ rõ ràng nhưng vẫn hoạt động trên một nền tảng thống nhất phía sau lớp API chung. Thiết kế này giảm độ phức tạp vận hành, đồng thời giúp nhóm thực hành về mạng, điện toán phi máy chủ, cơ sở dữ liệu được quản lý, bộ nhớ đệm, truyền thông điệp, bảo mật và khả năng quan sát trên AWS.

### 2. Vấn đề và giải pháp đề xuất

#### Thách thức hiện tại

Quá trình lập kế hoạch du lịch thường bị phân tán giữa công cụ tìm kiếm, nền tảng đánh giá, bản đồ, bảng tính và ứng dụng nhắn tin. Người dùng phải chuyển dữ liệu thủ công giữa nhiều công cụ, dẫn đến khó đồng bộ địa điểm đã lưu, lịch trình theo ngày, thông tin đặt chỗ và ghi chú chuyến đi.

Nền tảng cần giải quyết các thách thức kỹ thuật sau:

- Lưu trữ và truy xuất hiệu quả dữ liệu địa điểm, đánh giá, đặt chỗ, chuyến đi và lịch trình.
- Bảo vệ thông tin người dùng và doanh nghiệp bằng xác thực và phân quyền theo vai trò.
- Không để việc tải hình ảnh hoặc tác vụ nền làm chậm yêu cầu tương tác.
- Hỗ trợ thống nhất các luồng của khách hàng, chủ doanh nghiệp và quản trị viên.
- Kiểm soát chi phí hạ tầng trong quá trình phát triển và trình diễn.

#### Giải pháp đề xuất

Travel Platform cung cấp trải nghiệm thống nhất để người dùng khám phá địa điểm, lưu địa điểm yêu thích, tạo chuyến đi, sắp xếp lịch trình theo ngày, gửi đánh giá và quản lý đặt chỗ. Chủ doanh nghiệp có thể quản lý địa điểm và phản hồi hoạt động của khách hàng; quản trị viên có thể quản lý người dùng, địa điểm, yêu cầu xác minh và báo cáo.

Nền tảng sử dụng các dịch vụ AWS được quản lý để giảm công việc vận hành hạ tầng. CloudFront và S3 phân phối giao diện; Cognito và API Gateway bảo vệ API; Lambda xử lý logic nghiệp vụ. PostgreSQL lưu dữ liệu giao dịch, Redis lưu dữ liệu truy cập thường xuyên trong bộ nhớ đệm, còn S3 lưu hình ảnh người dùng. SQS, SNS và EventBridge chuyển các tác vụ chậm hoặc theo sự kiện sang tiến trình xử lý bất đồng bộ.

#### Lợi ích kỳ vọng

- **Trải nghiệm lập kế hoạch thống nhất:** Địa điểm đã lưu, chuyến đi, lịch trình, đánh giá và đặt chỗ được quản lý trong một nền tảng.
- **Phản hồi nhanh:** Bộ nhớ đệm và tiến trình xử lý bất đồng bộ giúp giảm độ trễ cho thao tác của người dùng.
- **Kiến trúc an toàn:** Xác thực, đặc quyền tối thiểu, mạng con riêng tư và thông tin bí mật được mã hóa giúp bảo vệ tài nguyên nhạy cảm.
- **Khả năng mở rộng:** Các dịch vụ được quản lý có thể đáp ứng lưu lượng tăng mà không cần duy trì máy chủ ứng dụng liên tục.
- **Giá trị học tập thực tế:** Nhóm áp dụng kiến trúc AWS, hạ tầng dưới dạng mã, giám sát và bảo mật đám mây trong một dự án thực tế.

### 3. Kiến trúc giải pháp

![Kiến trúc giải pháp Travel Platform](/images/5-Workshop/target-architecture.jpg)

Kiến trúc được tổ chức theo các lớp, mỗi lớp chịu trách nhiệm cho một phần cụ thể của nền tảng.

#### Lớp phân phối nội dung và giao diện

Người dùng truy cập ứng dụng qua Amazon CloudFront. Các tệp giao diện tĩnh được lưu trên Amazon S3 và phân phối qua CloudFront để tăng tốc độ tải, đồng thời kiểm soát truy cập đến nguồn nội dung.

#### Lớp xác thực và API

Amazon Cognito quản lý đăng ký, đăng nhập và xác thực bằng mã thông báo. Amazon API Gateway kiểm tra và định tuyến yêu cầu hợp lệ đến hàm Lambda xử lý API.

#### Lớp xử lý

Hàm Lambda xử lý API thực hiện các thao tác đồng bộ như lấy danh sách địa điểm, lưu địa điểm, tạo chuyến đi, cập nhật lịch trình, gửi đánh giá và quản lý đặt chỗ. Một tiến trình Lambda riêng xử lý công việc từ hàng đợi hoặc sự kiện mà không làm chậm phản hồi API.

#### Lớp dữ liệu

Amazon RDS for PostgreSQL lưu người dùng, địa điểm, đánh giá, địa điểm đã lưu, chuyến đi, mục lịch trình, đặt chỗ, yêu cầu xác minh và dữ liệu quản trị. Redis lưu dữ liệu được đọc nhiều và các giá trị tạm thời trong bộ nhớ đệm. Hình ảnh người dùng được lưu trong một vùng lưu trữ S3 riêng.

#### Lớp truyền thông điệp và giám sát

Amazon SQS cung cấp hàng đợi đáng tin cậy cho công việc nền, Amazon SNS phát sự kiện đến nhiều thành phần nhận, còn Amazon EventBridge điều phối quy trình theo lịch hoặc theo sự kiện. Amazon CloudWatch thu thập nhật ký, số liệu và cảnh báo. IAM, KMS, Secrets Manager và X-Ray tăng cường kiểm soát truy cập, mã hóa, lưu thông tin bí mật và theo dõi luồng yêu cầu.

### 4. Dịch vụ AWS sử dụng

| Dịch vụ AWS | Vai trò trong nền tảng |
| --- | --- |
| Amazon CloudFront | Phân phối giao diện và cải thiện hiệu năng truy cập nội dung. |
| Amazon S3 | Lưu tệp giao diện tĩnh và hình ảnh du lịch do người dùng tải lên. |
| Amazon Cognito | Xác thực người dùng và kiểm soát truy cập bằng mã thông báo. |
| Amazon API Gateway | Cung cấp API bảo mật và định tuyến yêu cầu đến Lambda. |
| AWS Lambda | Chạy bộ xử lý API và các tiến trình bất đồng bộ. |
| Amazon RDS for PostgreSQL | Lưu dữ liệu quan hệ và dữ liệu giao dịch của ứng dụng. |
| Amazon ElastiCache for Redis | Lưu dữ liệu thường xuyên truy cập trong bộ nhớ đệm để giảm tải cơ sở dữ liệu. |
| Amazon SQS | Xếp hàng tác vụ nền để xử lý đáng tin cậy. |
| Amazon SNS | Phát thông báo hoặc sự kiện đến nhiều thành phần nhận. |
| Amazon EventBridge | Điều phối tác vụ theo lịch và quy trình theo sự kiện. |
| Amazon CloudWatch | Tập trung nhật ký, số liệu, bảng điều khiển và cảnh báo. |
| AWS IAM | Áp dụng đặc quyền tối thiểu giữa các dịch vụ. |
| AWS KMS | Hỗ trợ mã hóa tài nguyên nhạy cảm. |
| AWS Secrets Manager | Lưu thông tin kết nối cơ sở dữ liệu và thông tin bí mật của ứng dụng. |
| AWS X-Ray | Theo dõi yêu cầu qua API và các dịch vụ phụ thuộc. |

### 5. Thiết kế thành phần

#### Ứng dụng giao diện người dùng

Giao diện web tương thích nhiều kích thước màn hình cung cấp chức năng tìm kiếm, xem chi tiết địa điểm, quản lý Địa điểm đã lưu (Saved Places), tạo Chuyến đi (Trips), lập Lịch trình (Itinerary), đánh giá, đặt chỗ, quản lý doanh nghiệp và quản trị hệ thống. Các tệp tĩnh được lưu trên S3 và phân phối qua CloudFront.

#### Dịch vụ lập kế hoạch chuyến đi

Dịch vụ lập kế hoạch chuyến đi (Trip Planner Service) quản lý dữ liệu về địa điểm đã lưu, chuyến đi và lịch trình. Dịch vụ kiểm tra quyền sở hữu của người dùng, lưu thông tin chuyến đi, sắp xếp hoạt động theo ngày và thứ tự, đồng thời cung cấp API cho các màn hình tương ứng.

#### Bộ xử lý API nền tảng

Hàm Lambda chính chứa logic dùng chung cho người dùng, địa điểm, đánh giá, đặt chỗ, yêu cầu xác minh doanh nghiệp và quản trị. Thành phần này kiểm tra danh tính và quyền từ Cognito trước khi truy cập PostgreSQL hoặc Redis.

#### Tiến trình xử lý bất đồng bộ

Tiến trình này xử lý thông báo, tác vụ liên quan đến hình ảnh, đồng bộ dữ liệu và công việc nhận từ SQS, SNS hoặc EventBridge. Thông điệp lỗi có thể được thử lại hoặc chuyển vào hàng đợi thư lỗi để điều tra.

#### Lưu trữ dữ liệu và hình ảnh

PostgreSQL lưu dữ liệu chuẩn hóa cùng các quan hệ nghiệp vụ. Redis lưu dữ liệu đệm và giá trị tạm thời có thể tái tạo. S3 lưu tệp hình ảnh, còn siêu dữ liệu và thông tin sở hữu được lưu trong PostgreSQL.

### 6. Triển khai kỹ thuật

#### Các giai đoạn triển khai

1. **Phân tích và thiết kế:** Xác định vai trò người dùng, luồng nghiệp vụ, mô hình dữ liệu, đặc tả API và kiến trúc AWS.
2. **Xây dựng hạ tầng nền:** Tạo mạng, nhóm bảo mật, Cognito, S3, CloudFront, API Gateway, Lambda, PostgreSQL, Redis và tài nguyên giám sát bằng AWS CDK.
3. **Phát triển hệ thống phía máy chủ:** Xây dựng API cho địa điểm, địa điểm đã lưu, chuyến đi, lịch trình, đánh giá, đặt chỗ, chức năng doanh nghiệp và quản trị.
4. **Phát triển giao diện người dùng:** Xây dựng giao diện cho người dùng, chủ doanh nghiệp và quản trị viên, sau đó kết nối với API.
5. **Tích hợp xử lý bất đồng bộ:** Thêm SQS, SNS và EventBridge cho xử lý nền và thông báo.
6. **Kiểm thử và triển khai:** Kiểm thử tích hợp và xuyên suốt, rà soát IAM và mạng, tối ưu chi phí, sửa lỗi và triển khai môi trường trình diễn cuối cùng.

#### Yêu cầu kỹ thuật

- **Giao diện:** React, TypeScript, Tailwind CSS, thiết kế tương thích nhiều kích thước màn hình và lời gọi API có xác thực.
- **Hệ thống phía máy chủ:** TypeScript, AWS Lambda, AWS SDK, kiểm tra dữ liệu đầu vào và các phân hệ hướng dịch vụ.
- **Dữ liệu:** PostgreSQL; mô hình DynamoDB Single Table khi phù hợp với dữ liệu lập kế hoạch chuyến đi; Redis làm bộ nhớ đệm và S3 lưu trữ đối tượng.
- **Hạ tầng:** AWS CDK để tạo môi trường có thể triển khai lặp lại.
- **Bảo mật:** Amazon Cognito, đặc quyền IAM tối thiểu, thông tin bí mật được mã hóa, mạng con riêng tư cho dịch vụ dữ liệu và kiểm soát truy cập S3.
- **Chất lượng:** Kiểm thử tự động, ghi nhật ký có cấu trúc, cảnh báo CloudWatch và quy trình dọn dẹp được tài liệu hóa.

### 7. Lộ trình và mốc triển khai

| Thời gian | Hoạt động chính |
| --- | --- |
| Tuần 1–2 | Học AWS căn bản, IAM, mạng và các dịch vụ điện toán cốt lõi. |
| Tuần 3–4 | Thực hành lưu trữ, Lambda, DynamoDB, API Gateway và thiết kế phi máy chủ. |
| Tuần 5–6 | Tìm hiểu cơ sở dữ liệu được quản lý, bộ nhớ đệm, giám sát, DNS và dịch vụ hỗ trợ. |
| Tuần 7 | Hoàn thiện phạm vi nhóm, vai trò người dùng, yêu cầu và phân công nhiệm vụ. |
| Tuần 8 | Thiết kế kiến trúc hệ thống, mô hình dữ liệu và đặc tả API. |
| Tuần 9 | Triển khai chức năng chủ doanh nghiệp và quản lý địa điểm. |
| Tuần 10 | Triển khai chức năng đặt chỗ và luồng khách hàng. |
| Tuần 11 | Triển khai bảng điều khiển quản trị và các chức năng quản lý. |
| Tuần 12 | Kiểm thử tích hợp, sửa lỗi, hoàn thiện tài liệu và chuẩn bị trình diễn cuối kỳ. |

### 8. Ước tính ngân sách

Dự án phục vụ học tập và trình diễn, vì vậy cần giảm chi phí bằng cấu hình tài nguyên nhỏ, thời gian kiểm thử ngắn, tận dụng Bậc miễn phí của AWS khi phù hợp và dọn dẹp ngay sau khi hoàn tất.

| Nhóm tài nguyên | Biện pháp kiểm soát chi phí |
| --- | --- |
| S3 và CloudFront | Chỉ lưu tài nguyên tĩnh cần thiết và cấu hình bộ nhớ đệm phù hợp. |
| Lambda và API Gateway | Giới hạn lưu lượng kiểm thử, thời gian chạy và mức ghi nhật ký. |
| PostgreSQL | Dùng cấu hình nhỏ cho môi trường học tập và xóa khi không còn sử dụng. |
| Redis | Dùng nút bộ nhớ đệm nhỏ nhất phù hợp và kết thúc kiểm thử đúng thời gian. |
| SQS, SNS và EventBridge | Giữ lưu lượng truyền thông điệp ở mức thấp. |
| CloudWatch | Cấu hình thời gian lưu nhật ký và tránh ghi quá chi tiết khi không cần thiết. |

AWS Budgets cần được cấu hình trước khi triển khai. Cơ sở dữ liệu, nút bộ nhớ đệm, tài nguyên liên quan đến NAT và dữ liệu kiểm thử không còn sử dụng phải được xóa sau khi hoàn tất dự án.

### 9. Đánh giá rủi ro

| Rủi ro | Mức độ | Biện pháp giảm thiểu |
| --- | --- | --- |
| Cấu hình VPC hoặc nhóm bảo mật không chính xác | Cao | Rà soát mạng con, bảng định tuyến và quy tắc vào/ra trước khi tích hợp. |
| Quyền IAM quá rộng | Cao | Áp dụng đặc quyền tối thiểu và rà soát chính sách theo từng dịch vụ. |
| Lỗi kết nối PostgreSQL hoặc Redis | Cao | Dùng kiểm tra tình trạng, cảnh báo CloudWatch và cơ chế thử lại có giới hạn. |
| Tác vụ nền bị thất bại | Trung bình | Cấu hình thử lại, hàng đợi thư lỗi và cảnh báo cho SQS/Lambda. |
| Chi phí vượt ngân sách trình diễn | Trung bình | Dùng AWS Budgets, cấu hình nhỏ, giới hạn thời gian kiểm thử và tự động hóa dọn dẹp. |
| Dữ liệu hình ảnh không được bảo vệ | Cao | Dùng URL ký sẵn, chặn truy cập công khai và mã hóa vùng lưu trữ S3. |

### 10. Kết quả kỳ vọng

Kết quả cuối cùng là một Travel Platform hoạt động trên AWS, cho phép người dùng khám phá và lưu địa điểm, tạo chuyến đi, xây dựng lịch trình, gửi đánh giá và đặt chỗ; đồng thời hỗ trợ chủ doanh nghiệp và quản trị viên quản lý nội dung liên quan.

Dự án thể hiện khả năng của nhóm trong thiết kế kiến trúc AWS, triển khai hạ tầng dưới dạng mã, bảo vệ API, kết nối điện toán phi máy chủ với dịch vụ dữ liệu được quản lý, sử dụng truyền thông điệp bất đồng bộ, giám sát khối lượng công việc và phối hợp phát triển dự án trên nền tảng đám mây.
