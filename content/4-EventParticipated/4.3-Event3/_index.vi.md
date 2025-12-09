---
title: "Event 3"
date: "2025-11-16"
weight: 3
chapter: false
pre: " <b> 4.3. </b> "
---
# Bài Thu Hoạch Workshop "AWS Cloud Mastery Series #2: DevOps on AWS"

### Mục Đích Của Sự Kiện
- Cung cấp cái nhìn toàn diện về văn hóa, nguyên tắc và thực hành DevOps trên nền tảng AWS.
- Hướng dẫn xây dựng pipeline CI/CD hoàn chỉnh từ source control đến deployment tự động.
- Giới thiệu các công cụ Infrastructure as Code (IaC) chính trên AWS và cách áp dụng chúng.
- Trang bị kiến thức về containerization, observability và các best practices để vận hành hệ thống ổn định.

### Diễn Giả / Người Hướng Dẫn Chính (Dự kiến)
- **Anh Đỗ Huy Thắng** – DevOps Lead, VNG (Session chính về văn hóa & thực hành DevOps)
- **Chị Nguyễn Thị Thu Hà** – Sr. DevOps Engineer, AWS (Phần kỹ thuật CI/CD & IaC)
- **Anh Phạm Tuấn Anh** – Solutions Architect, AWS (Phần Container & Observability)

### Nội Dung Nổi Bật & Bài Học Chính

#### 1. Văn Hóa & Nguyên Tắc DevOps
- **DevOps Mindset**: Không phải chỉ là công cụ, mà là **văn hóa hợp tác** giữa Development và Operations để tối ưu hóa toàn bộ quy trình phát triển phần mềm.
- **Đo lường hiệu suất**: Các chỉ số DORA (Deployment Frequency, Lead Time, MTTR, Change Failure Rate) là **thước đo quan trọng** để đánh giá hiệu quả của DevOps.
- **Shift-Left Testing & Security**: Tích hợp kiểm thử và bảo mật sớm vào pipeline để **phát hiện lỗi nhanh hơn**, giảm chi phí sửa chữa.

#### 2. CI/CD Pipeline Trên AWS: Từ Code Đến Production
- **AWS Developer Tools Suite**: Bộ công cụ toàn diện (CodeCommit, CodeBuild, CodeDeploy, CodePipeline) cho phép **tự động hóa hoàn toàn** quy trình release.
- **Chiến lược Deployment**: Hiểu sâu về **Blue/Green** (zero-downtime), **Canary** (giảm thiểu rủi ro), và **Rolling Updates** để lựa chọn phù hợp.
- **Demo thực tế**: Xây dựng một pipeline đầy đủ từ commit code, chạy test tự động, đến deploy lên EC2/ECS, giúp hình dung rõ luồng công việc.

#### 3. Infrastructure as Code (IaC): Quản Lý Hạ Tầng Như Mã Nguồn
- **AWS CloudFormation**: Công cụ IaC "declarative" mạnh mẽ, sử dụng template YAML/JSON để định nghĩa và quản lý toàn bộ tài nguyên AWS.
- **AWS CDK (Cloud Development Kit)**: Cách tiếp cận "imperative" dùng ngôn ngữ lập trình quen thuộc (Python, TypeScript) để định nghĩa hạ tầng, **tăng tính tái sử dụng và dễ bảo trì**.
- **Drift Detection**: Cơ chế phát hiện sự khác biệt giữa cấu hình định nghĩa trong code và hạ tầng thực tế, đảm bảo **tính nhất quán và tuân thủ**.

#### 4. Container Services & Microservices Architecture
- **Containerization với Docker**: Cách đóng gói ứng dụng thành các container **nhẹ, độc lập và portable**, là nền tảng của kiến trúc microservices.
- **Amazon ECS vs Amazon EKS**: So sánh chi tiết hai dịch vụ container orchestration hàng đầu của AWS để **lựa chọn đúng công cụ** cho nhu cầu (fully-managed vs self-managed Kubernetes).
- **AWS App Runner**: Giải pháp "serverless" đơn giản hóa việc deploy container, **giảm thiểu công quản lý** hạ tầng.

#### 5. Giám Sát & Quan Sát Hệ Thống (Monitoring & Observability)
- **Amazon CloudWatch**: Trung tâm thu thập metrics, logs, thiết lập alarm và dashboard để **giám sát sức khỏe hệ thống** theo thời gian thực.
- **AWS X-Ray**: Công cụ phân tích hiệu năng và debug ứng dụng phân tán bằng cách **theo dõi request xuyên suốt các service**.
- **Best Practices**: Thiết lập alerting có ý nghĩa, dashboards tập trung vào SLOs (Service Level Objectives), và quy trình xử lý sự cố (on-call, postmortem).

### Những Gì Học Được (Key Takeaways)

#### Về Tư Duy Và Văn Hóa
- **DevOps là hành trình, không phải đích đến**: Cần cải tiến liên tục dựa trên dữ liệu và phản hồi.
- **Automation là cốt lõi**: Tự động hóa mọi thứ có thể để **giảm lỗi thủ công** và giải phóng thời gian cho công việc sáng tạo.
- **Failure is an option**: Xây dựng hệ thống có khả năng chịu lỗi và học hỏi từ sự cố thông qua blameless postmortems.

#### Về Kỹ Thuật & Công Cụ
- **CI/CD không chỉ là "chạy pipeline"**: Đó là việc tạo ra một **luồng công việc đáng tin cậy** để deliver giá trị cho người dùng một cách nhanh chóng và an toàn.
- **IaC thay đổi cách quản lý hạ tầng**: Mang lại tính **nhất quán, kiểm soát phiên bản, và khả năng tái tạo** môi trường.
- **Observability > Monitoring**: Không chỉ cảnh báo khi có lỗi, mà còn **hiểu được nguyên nhân gốc rễ** (root cause) thông qua logs, metrics và traces.

#### Về Kỹ Năng Nghề Nghiệp
- **Cần hiểu biết rộng**: Một DevOps Engineer cần kiến thức từ networking, security, coding đến system operations.
- **Kỹ năng giải quyết vấn đề**: Khả năng debug hệ thống phức tạp là vô giá.

### Kế Hoạch Hành Động Cá Nhân Sau Workshop
1.  **Thiết lập Pipeline CI/CD cá nhân**: Sử dụng AWS CodeCommit & CodePipeline để tự động hóa việc deploy một ứng dụng web tĩnh hoặc API nhỏ lên AWS.
2.  **Làm quen với AWS CDK**: Chọn một ngôn ngữ (Python) và thử viết CDK code để deploy một vài tài nguyên AWS cơ bản (VPC, EC2, S3).
3.  **Thực hành với Docker & ECS**: Đóng gói một ứng dụng đơn giản thành Docker image, push lên Amazon ECR và thử deploy lên ECS Fargate.
4.  **Xây dựng Dashboard CloudWatch cơ bản**: Cho ứng dụng demo của mình, thiết lập một vài metrics và alarms đơn giản.

### Trải Nghiệm Cá Nhân Trong Sự Kiện

Một ngày dài từ 8:30 sáng đến 5 giờ chiều tập trung vào DevOps đã mang lại một lượng kiến thức cực kỳ giá trị và thực tế. So với buổi về AI/ML, workshop này đi sâu hơn vào **quy trình và kỹ thuật vận hành**, thứ mà một developer như em thường ít được tiếp xúc trực tiếp.

**Phần demo về CI/CD pipeline và IaC là vô cùng ấn tượng.** Được chứng kiến cách một commit code kích hoạt cả một chuỗi hành động tự động: build, test, security scan, rồi deploy với chiến lược Blue/Green, đã cho em thấy sức mạnh thực sự của tự động hóa. Nó không chỉ nhanh mà còn **giảm thiểu rủi ro** một cách đáng kể.

Em cũng đặc biệt thích phần chia sẻ về **văn hóa DevOps và các case study**. Nghe anh Thắng từ VNG chia sẻ về cách họ áp dụng DevOps để giảm MTTR từ vài giờ xuống còn vài phút, hay câu chuyện về một startup thất bại vì thiếu quan tâm đến monitoring, đã cho em những bài học "đắt giá" ngoài sách vở.

Buổi học kết thúc với cảm giác **được trang bị một "bộ công cụ" tinh thần đầy đủ hơn**. Em nhận ra rằng để trở thành một kỹ sư phần mềm giỏi, ngoài việc viết code tốt, cần phải hiểu biết về toàn bộ vòng đời của phần mềm - từ ý tưởng, code, cho đến vận hành và học hỏi từ sự cố.

#### Một số hình ảnh khi tham gia sự kiện
![anh3 event](/images/4-Event/event-image3.png)
![anh4 event](/images/4-Event/event-image4.png)