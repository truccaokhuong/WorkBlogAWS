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

Travel Platform là ứng dụng web trên nền tảng đám mây, hợp nhất các chức năng khám phá địa điểm, lưu địa điểm yêu thích, lập kế hoạch chuyến đi, quản lý lịch trình, đánh giá và đặt chỗ trong cùng một hệ thống. Nền tảng cũng cung cấp các chức năng riêng cho chủ doanh nghiệp và quản trị viên. Phạm vi dự án được thiết kế phù hợp để nhóm thực tập gồm năm thành viên có thể triển khai, trình diễn và vận hành trong thời gian thực tập.

Frontend được phân phối thông qua Amazon CloudFront và Amazon S3. Amazon Cognito quản lý xác thực người dùng, còn Amazon API Gateway là điểm tiếp nhận các request backend. AWS Lambda thực thi logic ứng dụng và các worker nền. Amazon RDS for PostgreSQL lưu trữ dữ liệu quan hệ, Amazon ElastiCache for Redis tăng tốc các truy vấn thường xuyên, và một S3 bucket riêng lưu hình ảnh được tải lên. Amazon EventBridge, Amazon SQS và Amazon SNS hỗ trợ xử lý bất đồng bộ; Amazon CloudWatch tập trung log và hoạt động giám sát.

Giải pháp sử dụng kiến trúc serverless dạng modular. Các trách nhiệm được tách thành những module ứng dụng rõ ràng, nhưng backend vẫn là một nền tảng thống nhất phía sau lớp API chung. Thiết kế này giảm độ phức tạp vận hành, đồng thời giúp nhóm thực hành networking, serverless compute, managed database, caching, messaging, security và observability trên AWS.

### 2. Tuyên bố vấn đề

#### Thách thức hiện tại

Quá trình lập kế hoạch du lịch thường bị phân tán giữa công cụ tìm kiếm, nền tảng đánh giá, bản đồ, bảng tính và ứng dụng nhắn tin. Người dùng phải chuyển dữ liệu thủ công giữa nhiều công cụ, dẫn đến khó đồng bộ địa điểm đã lưu, lịch trình theo ngày, thông tin đặt chỗ và ghi chú chuyến đi.

Nền tảng cũng cần giải quyết các thách thức kỹ thuật sau:

- Lưu trữ và truy xuất hiệu quả dữ liệu địa điểm, đánh giá, booking, chuyến đi và lịch trình.
- Bảo vệ thông tin người dùng và doanh nghiệp bằng xác thực và phân quyền theo vai trò.
- Không để việc upload hình ảnh hoặc tác vụ nền làm chậm request tương tác.
- Hỗ trợ thống nhất các luồng của khách hàng, chủ doanh nghiệp và quản trị viên.
- Kiểm soát chi phí hạ tầng trong quá trình phát triển và demo.

#### Giải pháp đề xuất

Travel Platform cung cấp trải nghiệm thống nhất để người dùng khám phá địa điểm, lưu địa điểm yêu thích, tạo chuyến đi, sắp xếp lịch trình theo ngày, gửi đánh giá và quản lý booking. Chủ doanh nghiệp có thể quản lý địa điểm và phản hồi hoạt động của khách hàng; quản trị viên có thể quản lý người dùng, địa điểm, yêu cầu xác minh và báo cáo.

Nền tảng sử dụng các dịch vụ AWS được quản lý để giảm công việc vận hành hạ tầng. CloudFront và S3 phân phối frontend, Cognito và API Gateway bảo vệ API, còn Lambda xử lý logic nghiệp vụ. PostgreSQL lưu dữ liệu giao dịch, Redis cache thông tin được truy cập thường xuyên, và S3 lưu hình ảnh người dùng. SQS, SNS và EventBridge chuyển các tác vụ chậm hoặc theo sự kiện sang worker bất đồng bộ.

#### Lợi ích kỳ vọng

- **Trải nghiệm lập kế hoạch thống nhất:** Địa điểm đã lưu, chuyến đi, lịch trình, đánh giá và booking được quản lý trong một nền tảng.
- **Ứng dụng phản hồi nhanh:** Cache và worker bất đồng bộ giúp giảm độ trễ cho thao tác của người dùng.
- **Kiến trúc an toàn:** Xác thực, quyền tối thiểu, private subnet và secret được mã hóa giúp bảo vệ tài nguyên nhạy cảm.
- **Nền tảng có khả năng mở rộng:** Dịch vụ managed có thể đáp ứng lưu lượng tăng mà không cần vận hành application server liên tục.
- **Giá trị học tập thực tế:** Nhóm áp dụng kiến trúc AWS, infrastructure as code, monitoring và cloud security trong dự án thực tế.

### 3. Kiến trúc giải pháp

![Kiến trúc giải pháp Travel Platform](/images/5-Workshop/target-architecture.jpg)

Kiến trúc được tổ chức theo các lớp, mỗi lớp chịu trách nhiệm cho một phần cụ thể của nền tảng.

#### Lớp Edge và Frontend

Người dùng truy cập ứng dụng thông qua Amazon CloudFront. Frontend tĩnh được lưu trên Amazon S3 và phân phối qua CloudFront để tăng tốc độ tải cũng như kiểm soát truy cập vào origin.

#### Lớp xác thực và API

Amazon Cognito quản lý đăng ký, đăng nhập và xác thực bằng token. Amazon API Gateway kiểm tra và định tuyến request hợp lệ đến Lambda API Handler.

#### Lớp xử lý

Lambda API Handler xử lý các thao tác đồng bộ như lấy danh sách địa điểm, lưu địa điểm, tạo chuyến đi, cập nhật lịch trình, gửi đánh giá và quản lý booking. Một Async Worker riêng xử lý các tác vụ từ queue hoặc event mà không làm chậm phản hồi API.

#### Lớp dữ liệu

Amazon RDS for PostgreSQL lưu người dùng, địa điểm, đánh giá, địa điểm đã lưu, chuyến đi, mục lịch trình, booking, yêu cầu xác minh và dữ liệu quản trị. Redis cache dữ liệu đọc nhiều và giá trị tạm thời. Hình ảnh người dùng được lưu trong một S3 bucket riêng.

#### Lớp messaging và monitoring

Amazon SQS cung cấp hàng đợi đáng tin cậy cho công việc nền, Amazon SNS hỗ trợ phát sự kiện đến nhiều consumer, và Amazon EventBridge điều phối workflow theo lịch hoặc theo sự kiện. Amazon CloudWatch thu thập log, metric và alarm. IAM, KMS, Secrets Manager và X-Ray tăng cường kiểm soát truy cập, mã hóa, lưu secret và tracing.

### 4. Dịch vụ AWS sử dụng

| Dịch vụ AWS | Vai trò trong nền tảng |
| --- | --- |
| Amazon CloudFront | Phân phối frontend và cải thiện hiệu năng truy cập nội dung. |
| Amazon S3 | Lưu frontend tĩnh và hình ảnh du lịch do người dùng upload. |
| Amazon Cognito | Xác thực người dùng và kiểm soát truy cập bằng token. |
| Amazon API Gateway | Cung cấp API bảo mật và định tuyến request đến Lambda. |
| AWS Lambda | Chạy API Handler và worker bất đồng bộ. |
| Amazon RDS for PostgreSQL | Lưu dữ liệu quan hệ và dữ liệu giao dịch của ứng dụng. |
| Amazon ElastiCache for Redis | Cache dữ liệu thường xuyên truy cập để giảm tải database. |
| Amazon SQS | Xếp hàng tác vụ nền để xử lý đáng tin cậy. |
| Amazon SNS | Phát thông báo hoặc sự kiện đến nhiều consumer. |
| Amazon EventBridge | Điều phối tác vụ theo lịch và workflow theo sự kiện. |
| Amazon CloudWatch | Tập trung log, metric, dashboard và alarm. |
| AWS IAM | Áp dụng quyền tối thiểu giữa các dịch vụ. |
| AWS KMS | Hỗ trợ mã hóa tài nguyên nhạy cảm. |
| AWS Secrets Manager | Lưu thông tin kết nối database và secret ứng dụng. |
| AWS X-Ray | Theo dõi request qua API và các dịch vụ phụ thuộc. |

### 5. Thiết kế thành phần

#### Ứng dụng Frontend

Giao diện web responsive cung cấp tìm kiếm địa điểm, chi tiết địa điểm, Saved Places, tạo chuyến đi, lập lịch trình, đánh giá, booking, trang chủ doanh nghiệp và màn hình quản trị. File tĩnh được lưu trên S3 và phân phối qua CloudFront.

#### Trip Planner Service

Trip Planner Service quản lý dữ liệu Saved Places, Trips và Itinerary. Service kiểm tra quyền sở hữu của người dùng, lưu thông tin chuyến đi, sắp xếp hoạt động theo ngày và thứ tự, đồng thời cung cấp API cho các màn hình frontend tương ứng.

#### Platform API Handler

Lambda handler chính chứa logic dùng chung cho người dùng, địa điểm, đánh giá, booking, business claim và quản trị. Thành phần này kiểm tra danh tính và quyền từ Cognito trước khi truy cập PostgreSQL hoặc Redis.

#### Worker bất đồng bộ

Worker xử lý thông báo, tác vụ liên quan đến hình ảnh, đồng bộ dữ liệu và các công việc nhận từ SQS, SNS hoặc EventBridge. Message lỗi có thể được retry hoặc chuyển vào dead-letter queue để điều tra.

#### Lưu trữ dữ liệu và hình ảnh

PostgreSQL lưu dữ liệu chuẩn hóa cùng các quan hệ nghiệp vụ. Redis lưu cache và giá trị tạm thời có thể tái tạo. S3 lưu file hình ảnh, trong khi metadata và thông tin sở hữu được lưu trong PostgreSQL.

### 6. Triển khai kỹ thuật

#### Các giai đoạn triển khai

1. **Phân tích và thiết kế:** Xác định vai trò người dùng, luồng nghiệp vụ, data model, API contract và kiến trúc AWS.
2. **Xây dựng hạ tầng nền:** Tạo networking, security group, Cognito, S3, CloudFront, API Gateway, Lambda, PostgreSQL, Redis và tài nguyên monitoring bằng AWS CDK.
3. **Phát triển backend:** Xây dựng API cho địa điểm, Saved Places, Trips, Itinerary, đánh giá, booking, chức năng doanh nghiệp và quản trị.
4. **Phát triển frontend:** Xây dựng giao diện người dùng, chủ doanh nghiệp và quản trị viên, sau đó kết nối với API.
5. **Tích hợp bất đồng bộ:** Thêm SQS, SNS và EventBridge cho xử lý nền và thông báo.
6. **Kiểm thử và triển khai:** Kiểm thử integration và end-to-end, rà soát IAM/networking, tối ưu chi phí, sửa lỗi và triển khai môi trường demo cuối cùng.

#### Yêu cầu kỹ thuật

- **Frontend:** React, TypeScript, Tailwind CSS, responsive design và API call có xác thực.
- **Backend:** TypeScript, AWS Lambda, AWS SDK, validation và các module ứng dụng hướng dịch vụ.
- **Dữ liệu:** PostgreSQL, DynamoDB Single Table khi phù hợp cho dữ liệu Trip Planner, Redis cache và S3 object storage.
- **Hạ tầng:** AWS CDK để triển khai lặp lại được.
- **Bảo mật:** Amazon Cognito, IAM least privilege, secret được mã hóa, private subnet cho data service và kiểm soát truy cập S3.
- **Chất lượng:** Automated test, structured logging, CloudWatch alarm và quy trình cleanup được tài liệu hóa.

### 7. Lộ trình và mốc triển khai

| Thời gian | Hoạt động chính |
| --- | --- |
| Tuần 1–2 | Học AWS căn bản, IAM, networking và các dịch vụ compute cốt lõi. |
| Tuần 3–4 | Thực hành storage, Lambda, DynamoDB, API Gateway và thiết kế serverless. |
| Tuần 5–6 | Tìm hiểu managed database, caching, monitoring, DNS và dịch vụ hỗ trợ. |
| Tuần 7 | Hoàn thiện phạm vi nhóm, vai trò người dùng, yêu cầu và phân công nhiệm vụ. |
| Tuần 8 | Thiết kế kiến trúc hệ thống, data model và API contract. |
| Tuần 9 | Triển khai chức năng chủ doanh nghiệp và quản lý địa điểm. |
| Tuần 10 | Triển khai chức năng booking và luồng khách hàng. |
| Tuần 11 | Triển khai dashboard quản trị và các chức năng quản lý. |
| Tuần 12 | Kiểm thử tích hợp, sửa lỗi, hoàn thiện tài liệu và chuẩn bị demo cuối kỳ. |

### 8. Ước tính ngân sách

Dự án hướng đến môi trường học tập và demo, do đó cần giảm chi phí bằng resource size nhỏ, thời gian test ngắn, tận dụng Free Tier khi phù hợp và cleanup ngay sau khi trình diễn.

| Nhóm chi phí | Phương án kiểm soát |
| --- | --- |
| Lambda và API Gateway | Chạy theo nhu cầu và lưu lượng demo thấp. |
| S3 và CloudFront | Chỉ lưu asset cần thiết và cấu hình cache phù hợp. |
| RDS PostgreSQL | Dùng instance Single-AZ nhỏ trong giai đoạn phát triển. |
| Redis | Dùng cache node nhỏ nhất phù hợp và kết thúc test đúng thời gian. |
| Messaging | Giữ lưu lượng SQS, SNS và EventBridge ở mức thấp. |
| CloudWatch | Cấu hình thời gian lưu log và tránh logging quá chi tiết không cần thiết. |
| Secret và mã hóa | Chỉ tạo secret và key thực sự cần cho ứng dụng. |

AWS Budgets cần được cấu hình trước khi triển khai. Database, cache node, tài nguyên liên quan đến NAT và dữ liệu test không còn sử dụng phải được xóa sau khi hoàn tất dự án.

### 9. Đánh giá rủi ro

| Rủi ro | Ảnh hưởng | Biện pháp giảm thiểu |
| --- | --- | --- |
| Cấu hình VPC hoặc security group không chính xác | Cao | Rà soát subnet, route và rule inbound/outbound trước khi tích hợp. |
| Lambda không kết nối được PostgreSQL hoặc Redis | Cao | Kiểm tra private connectivity sớm và theo dõi lỗi kết nối trên CloudWatch. |
| Truy cập trái phép vào dữ liệu hoặc hình ảnh | Cao | Dùng Cognito authorization, IAM least privilege, mã hóa và URL upload có kiểm soát. |
| Message nền lỗi lặp lại | Trung bình | Cấu hình retry, dead-letter queue, handler idempotent và alarm. |
| Chi phí vượt ngân sách demo | Trung bình | Dùng AWS Budgets, resource nhỏ, thời gian test giới hạn và cleanup script. |
| Phạm vi dự án quá lớn | Trung bình | Ưu tiên khám phá địa điểm, Saved Places, Trips, Itinerary, đánh giá và booking. |

### 10. Kết quả kỳ vọng

Travel Platform sau khi hoàn thành sẽ cung cấp bản demo chạy trên cloud, cho phép người dùng khám phá và lưu địa điểm, tạo chuyến đi, sắp xếp lịch trình, gửi đánh giá và quản lý booking. Chủ doanh nghiệp và quản trị viên có thể thực hiện các luồng quản lý được phân công thông qua giao diện riêng.

Dự án cũng thể hiện khả năng của nhóm trong việc thiết kế kiến trúc AWS, triển khai infrastructure as code, bảo vệ API, kết nối serverless compute với managed data services, sử dụng messaging bất đồng bộ, giám sát workload và phối hợp phát triển dự án trên cloud.
