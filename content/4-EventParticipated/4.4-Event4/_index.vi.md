---
title: "Event 4"
date: "2025-11-30"
weight: 4
chapter: false
pre: " <b> 4.4. </b> "
---

# Bài Thu Hoạch Workshop "AWS Cloud Mastery Series #3: Theo AWS Well-Architected Security Pillar"

### Mục Đích Của Sự Kiện
- Giới thiệu khung kiến trúc Well-Architected Framework, tập trung vào trụ cột Bảo Mật (Security Pillar) - nền tảng cho mọi hệ thống trên AWS.
- Cung cấp kiến thức thực tiễn về 5 lĩnh vực trọng yếu của bảo mật trên cloud: Quản lý truy cập (IAM), Phát hiện sự cố, Bảo vệ hạ tầng, Bảo vệ dữ liệu và Ứng phó sự cố.
- Trang bị tư duy "Security by Design" và các mô hình bảo mật cốt lõi (Least Privilege, Zero Trust, Defense in Depth).
- Chia sẻ các thực tiễn phổ biến và bài học từ thực tế triển khai tại doanh nghiệp Việt Nam.

### Diễn Giả / Người Hướng Dẫn (Dự kiến)
- **Anh Nguyễn Văn Tú** – Sr. Security Specialist Solutions Architect, AWS
- **Chị Lê Thị Thanh Mai** – Cloud Security Engineer, Đối tác AWS
- **Anh Đặng Quốc Bảo** – Security Lead, Công ty Fintech (Khách mời chia sẻ case study)

### Nội Dung Nổi Bật & Bài Học Chính

#### 1. Nền Tảng Tư Duy Bảo Mật Trên Cloud
- **Security là "Pillar" đầu tiên**: Mọi kiến trúc trên AWS đều phải bắt đầu từ bảo mật, không phải là tính năng bổ sung.
- **Nguyên tắc cốt lõi**:
    - **Least Privilege**: Chỉ cấp quyền tối thiểu cần thiết để thực hiện nhiệm vụ.
    - **Zero Trust**: "Không tin tưởng, luôn xác minh" mọi yêu cầu truy cập, bất kể từ trong hay ngoài mạng.
    - **Defense in Depth**: Xây dựng nhiều lớp phòng thủ chồng lấn để khi một lớp thất bại, lớp khác vẫn bảo vệ được.
- **Shared Responsibility Model**: AWS chịu trách nhiệm bảo mật "của" đám mây, khách hàng chịu trách nhiệm bảo mật "trên" đám mây. **Hiểu rõ ranh giới này là sống còn**.

#### 2. Pillar 1 - Quản Lý Danh Tính & Truy Cập (Identity & Access Management)
- **Tránh dùng long-term credentials**: Ưu tiên sử dụng IAM Roles cho EC2, Lambda, ECS thay vì lưu key cố định.
- **IAM Identity Center & SSO**: Quản lý truy cập tập trung cho nhiều tài khoản AWS và ứng dụng SaaS, gắn Permission Sets theo nhóm.
- **Kiểm soát tài khoản tổ chức**: Sử dụng **Service Control Policies (SCPs)** và **Permission Boundaries** để thiết lập "guardrails" và giới hạn quyền tối đa trong toàn tổ chức.
- **Công cụ hỗ trợ**: IAM Access Analyzer để phát hiện tài nguyên chia sẻ công khai ngoài ý muốn.

#### 3. Pillar 2 - Phát Hiện (Detection) & Giám Sát Liên Tục
- **Ghi log toàn diện**: Bật **CloudTrail** ở cấp tổ chức (Organization Trail), kết hợp với VPC Flow Logs, Load Balancer logs.
- **Dịch vụ phát hiện đe dọa**: **GuardDuty** sử dụng AI/ML để phát hiện hành vi bất thường; **Security Hub** tổng hợp findings từ nhiều nguồn.
- **Detection-as-Code**: Định nghĩa quy tắc phát hiện bằng code (vd: AWS Config Rules) để đảm bảo tính nhất quán và khả năng tái tạo.
- **Tự động hóa cảnh báo**: Dùng **Amazon EventBridge** để định tuyến sự kiện bảo mật và kích hoạt phản hồi tự động.

#### 4. Pillar 3 - Bảo Vệ Hạ Tầng (Infrastructure Protection)
- **Thiết kế mạng an toàn**: Áp dụng **VPC segmentation** (Public, Private, Data subnets), đặt tài nguyên nhạy cảm trong private subnets.
- **Phân biệt Security Groups (Stateful) vs NACLs (Stateless)**: Security Groups dùng để kiểm soát lưu lượng ở cấp instance, NACLs cho cấp subnet với rules đơn giản hơn.
- **Bảo vệ lớp ứng dụng/web**: Sử dụng **WAF, Shield** để chống lại các tấn công DDoS và lọc lưu lượng HTTP/HTTPS độc hại.
- **Bảo mật workload cơ bản**: Áp dụng hardening OS, sử dụng IMDSv2 cho EC2, và tính năng bảo mật tích hợp trong ECS/EKS.

#### 5. Pillar 4 - Bảo Vệ Dữ Liệu (Data Protection)
- **Mã hóa là mặc định**: Bật encryption-at-rest (sử dụng **AWS KMS**) cho S3, EBS, RDS và encryption-in-transit (TLS) mọi nơi.
- **Quản lý khóa và bí mật**: Hiểu **KMS Key Policies** và dùng **Secrets Manager** để xoay vòng secret tự động (như database password).
- **Phân loại dữ liệu**: Áp dụng tagging và guardrails để kiểm soát truy cập dựa trên mức độ nhạy cảm của dữ liệu.

#### 6. Pillar 5 - Ứng Phó Sự Cố (Incident Response)
- **Có sẵn playbook**: Chuẩn bị các kịch bản ứng phó cho các tình huống phổ biến như: key bị rò rỉ, S3 public ngoài ý muốn, EC2 bị nhiễm malware.
- **Quy trình IR chuẩn**: Ngăn chặn → Loại trừ → Phục hồi, kèm theo việc thu thập bằng chứng (snapshot, logs) để phân tích sau.
- **Tự động hóa phản hồi**: Dùng **AWS Lambda và Step Functions** để tự động cách ly instance, thu hồi IAM key, hoặc gửi cảnh báo.

### Những Gì Học Được (Key Takeaways)

#### Về Tư Duy & Chiến Lược
- **"Security is job zero"**: Bảo mật không thể đắp vá sau khi hệ thống đã chạy. Phải được thiết kế từ đầu.
- **Ưu tiên dựa trên rủi ro**: Tập trung nguồn lực bảo mật vào các tài sản quan trọng nhất và các mối đe dọa có khả năng xảy ra cao nhất.
- **Đo lường và cải thiện**: Sử dụng Security Hub score và các chỉ số (metrics) để đánh giá và liên tục nâng cao tư thế bảo mật.

#### Về Kỹ Thuật
- **Giảm bề mặt tấn công**: Càng ít tài nguyên public, càng ít điểm cho kẻ tấn công khai thác.
- **Mã hóa mọi thứ**: Coi mã hóa là tiêu chuẩn bắt buộc, không phải tùy chọn.
- **Tự động hóa bảo mật**: Càng nhiều công việc bảo mật được tự động (quét cấu hình, xoay secret, phản hồi sự cố) càng tốt.

### Kế Hoạch Hành Động Cá Nhân Sau Workshop
1.  **Áp dụng Least Privilege ngay**: Review các IAM policies trong tài khoản AWS cá nhân/demo, xóa các quyền không cần thiết.
2.  **Bật các dịch vụ detection**: Kích hoạt **AWS GuardDuty** và **Security Hub** trong tài khoản free tier để làm quen với findings.
3.  **Thực hành mã hóa**: Tạo một KMS key và thử mã hóa một S3 bucket hoặc EBS volume mới.
4.  **Đọc hiểu Shared Responsibility Model**: Tìm hiểu sâu hơn về trách nhiệm của mình trên từng dịch vụ AWS mình sử dụng.

### Trải Nghiệm Cá Nhân Trong Sự Kiện

Workshop về Security Pillar đã thay đổi hoàn toàn cách nhìn của em về việc xây dựng hệ thống trên cloud. Nếu trước đây em nghĩ bảo mật là thứ phức tạp, xa vời và dành cho các chuyên gia, thì buổi học này đã **"demystify"** nó, biến thành một khung làm việc logic, có hệ thống với 5 trụ cột rõ ràng.

**Phần demo về IAM Policy Simulator và các kịch bản Incident Response thực tế là vô cùng giá trị.** Được thấy cách một policy được validate trước khi gán, hay các bước tự động hóa để cách ly một EC2 bị nhiễm độc, khiến em nhận ra bảo mật hiện đại là sự kết hợp giữa **chính sách chặt chẽ và tự động hóa thông minh**.

Em cũng ấn tượng với việc các diễn giả liên tục nhấn mạnh **"Security is everyone's job"**. Một developer viết code không an toàn, một SysOps cấu hình Security Group sai, đều có thể tạo ra lỗ hổng. Bài học lớn nhất là **tư duy bảo mật phải được thấm nhuần trong toàn bộ vòng đời phát triển phần mềm**, từ lúc viết dòng code đầu tiên đến khi vận hành.

Buổi học kết thúc với cảm giác **có trách nhiệm hơn**. Em nhận ra mình cần phải chủ động học hỏi và áp dụng các nguyên tắc bảo mật ngay từ những dự án nhỏ nhất, vì một cấu hình sai trên cloud có thể dẫn đến hậu quả lớn chỉ trong vài phút.

#### Một số hình ảnh khi tham gia sự kiện
![anh5 event](/images/4-Event/event-image5.png)
![anh6 event](/images/4-Event/event-image6.png)