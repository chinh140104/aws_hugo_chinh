---
title: "Blog 1"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

# Cách Uniphore đạt được 30% tiết kiệm chi phí bằng cách hiện đại hóa các máy chủ Windows trên AWS


**Bởi Sornavel Perumal và Ismail Baig vào ngày 19 tháng 6 năm 2025 trong các mục: [Amazon EC2](https://aws.amazon.com/blogs/storage/category/compute/amazon-ec2/), [Amazon Elastic File System (EFS)](https://aws.amazon.com/blogs/storage/category/storage/amazon-elastic-file-system-efs/), [Amazon Elastic Kubernetes Service](https://aws.amazon.com/blogs/storage/category/compute/amazon-kubernetes-service/), [Amazon Simple Storage Service (S3)](https://aws.amazon.com/blogs/storage/category/storage/amazon-simple-storage-services-s3/), [AWS Backup](https://aws.amazon.com/blogs/storage/category/storage/aws-backup/), [Customer](https://aws.amazon.com/blogs/storage/category/post-types/customer-solutions/)**

Uniphore là công ty đầu tiên được xây dựng theo định hướng mở rộng, AI-native, đưa AI vào mọi phần của trải nghiệm doanh nghiệp. Nền tảng AI và dữ liệu đa phương thức cấp doanh nghiệp của Uniphore thống nhất tất cả các yếu tố của giọng nói, video, văn bản và dữ liệu bằng cách sử dụng Generative AI, Knowledge AI, Emotion AI và tự động hóa quy trình làm việc cùng nhau như một trợ lý đồng hành đáng tin cậy. Uniphore vận hành một trong những ứng dụng cốt lõi của doanh nghiệp trên hạ tầng Windows Server kế thừa, vốn gặp phải các thách thức về khả năng mở rộng và hiệu suất khi doanh nghiệp phát triển. Chi phí bảo trì tăng và các lo ngại bảo mật liên quan đến hệ điều hành hết hạn hỗ trợ có nghĩa là Uniphore cần hiện đại hóa cơ sở hạ tầng của họ đồng thời đảm bảo tính liên tục của hoạt động kinh doanh.

[Uniphore](https://www.uniphore.com/) đã thành công trong việc sử dụng các dịch vụ của Amazon Web Services (AWS) để hiện đại hóa các khối lượng công việc Windows của họ thông qua containerization và các giải pháp cloud-native. Bằng cách sử dụng [Amazon Elastic Kubernetes Service (Amazon EKS)](https://aws.amazon.com/eks/) cho containerization và [Amazon Elastic Compute Cloud (Amazon EC2)](https://aws.amazon.com/ec2/) cho tài nguyên tính toán, kết hợp với [Amazon Elastic File System (Amazon EFS)](https://aws.amazon.com/efs/) và [Amazon S3](https://aws.amazon.com/S3/) cho lưu trữ, Uniphore đã đạt được mức tiết kiệm chi phí 30% trong khi cải thiện đáng kể khả năng vận hành của họ. Họ đã di chuyển từ cơ sở hạ tầng Windows on-premises sang Linux trên AWS để tối ưu hóa các khối lượng công việc phân tích trung tâm cuộc gọi. Họ nhận thấy rằng các yêu cầu kinh doanh cốt lõi của họ đối với việc huấn luyện và tinh chỉnh các mô hình ngôn ngữ lớn (LLMs) hoạt động tốt hơn đáng kể trên các hệ thống dựa trên Linux, cho phép họ xây dựng một hệ sinh thái thống nhất, hiệu suất cao được thiết kế riêng cho hoạt động AI/ML.

Trong bài viết này, chúng tôi khám phá cách Uniphore tiếp cận hành trình hiện đại hóa của họ và chia sẻ những hiểu biết thực tế cho các tổ chức đang xem xét các chuyển đổi tương tự. Chúng tôi trình bày một phương pháp thực tế để hiện đại hóa các khối lượng công việc Windows kế thừa thông qua containerization, di chuyển dữ liệu hiệu quả và các dịch vụ cloud-native. Dù bạn đang lên kế hoạch cho một chuyển đổi tương tự hay đánh giá các lựa chọn hiện đại hóa, ví dụ thực tế này cho thấy cách vượt qua các thách thức di chuyển phổ biến đồng thời đạt được các lợi ích kinh doanh hữu hình như cải thiện khả năng mở rộng, tăng cường bảo mật và giảm chi phí vận hành.

## **Thách thức kinh doanh**

Nền tảng U-Assist của Uniphore ban đầu được lưu trữ on-premises trên 50 máy chủ vật lý Windows Server 2008 R2. Khi doanh nghiệp mở rộng nhanh chóng, các máy chủ này bắt đầu chịu tải nặng đáng kể. Các tình trạng thiếu dung lượng lưu trữ thường xuyên dẫn đến lỗi bộ nhớ cache của ứng dụng và gián đoạn hoạt động. Dữ liệu vượt quá 60 TB cùng phần cứng cũ đạt đến giới hạn của nó khiến chi phí bảo trì tăng cao trong khi hiệu suất hệ thống giảm sút.

Các ứng dụng này không được thiết kế để có khả năng mở rộng và thiếu sự hỗ trợ từ nhà cung cấp, khiến việc đáp ứng nhu cầu kinh doanh ngày càng tăng trở nên khó khăn hơn. Bảo mật là một mối lo ngại đáng kể khác, vì tình trạng hết hỗ trợ của Windows Server 2008 R2 đồng nghĩa với việc không còn các bản vá bảo mật hoặc hỗ trợ tuân thủ. Những thách thức này, kết hợp với chi phí vận hành đáng kể từ việc can thiệp thủ công thường xuyên, cho thấy rõ ràng rằng việc hiện đại hóa là cần thiết.

## **Giải pháp được triển khai**

### Uniphore đã triển khai một chiến lược hiện đại hóa toàn diện bằng cách sử dụng các dịch vụ AWS trong ba lĩnh vực chính:

#### **1. Hiện đại hóa ứng dụng**

Nhóm đã hiện đại hóa ngăn xếp ứng dụng bằng cách viết lại các dịch vụ dựa trên Java để trở nên độc lập với hệ điều hành (OS-agnostic) và triển khai containerization bằng Docker. Điều này bao gồm việc tái cấu trúc các phụ thuộc cụ thể của Windows, chẳng hạn như đường dẫn hệ thống tệp, đồng thời tách biệt cấu hình để tương thích với container. Sau đó, ứng dụng được container hóa được triển khai lên Amazon EKS bằng Kubernetes, giúp đạt được khả năng di động và tính chịu lỗi thực sự của ứng dụng trên các môi trường đám mây thông qua khả năng tự động mở rộng, tự phục hồi và cập nhật cuốn chiếu (rolling updates).

#### **2. Giải pháp di chuyển dữ liệu tùy chỉnh**

Uniphore đã phát triển một giải pháp di chuyển tùy chỉnh bằng cách sử dụng công nghệ hypervisor Type 2. Cách tiếp cận sáng tạo này cho phép lưu trữ tác nhân [AWS DataSync](https://aws.amazon.com/datasync/) và tích hợp liền mạch với lưu trữ dựa trên Windows. Bằng cách sử dụng kết nối internet chuyên dụng tốc độ cao, dữ liệu được truyền hiệu quả đến Amazon EFS, đảm bảo độ tin cậy và tính sẵn sàng được cải thiện.

#### **3. Thiết lập cơ sở hạ tầng đám mây**

Cơ sở hạ tầng hiện đại sử dụng Amazon EC2 và Amazon EKS cho tính toán và điều phối container, với [Amazon Virtual Private Cloud (Amazon VPC)](https://aws.amazon.com/vpc/) cung cấp sự cô lập mạng an toàn. Nhu cầu lưu trữ được đáp ứng thông qua Amazon EFS và Amazon S3, trong khi DataSync được sử dụng để truyền dữ liệu từ các máy chủ kế thừa sang Amazon EFS, như minh họa trong Hình 1.

Ứng dụng chạy trên Amazon EKS sẽ xử lý dữ liệu được lấy từ EFS, và kết quả đầu ra được lưu trữ trong Amazon S3. Dữ liệu đã xử lý được sao lưu bằng [AWS Backup](https://aws.amazon.com/backup/).


![anh1 blog](/images/Blog1_image1.png)

*Hình 1: Kiến trúc di chuyển dữ liệu của Uniphore với DataSync và các dịch vụ AWS*

## **Triển khai kỹ thuật**

Để đảm bảo quá trình chuyển đổi liền mạch và không gián đoạn từ hạ tầng kế thừa sang môi trường cloud-native hiện đại, Uniphore đã thực hiện việc di chuyển theo ba giai đoạn có cấu trúc. Mỗi giai đoạn tập trung vào việc giảm thiểu rủi ro, đảm bảo tính toàn vẹn dữ liệu và duy trì tính liên tục kinh doanh.

#### **Giai đoạn 1: Triển khai Hypervisor và DataSync agent**

Nhóm bắt đầu bằng cách thiết lập hypervisor Type 2 (ví dụ: VMware Workstation hoặc Hyper-V) trên phần cứng hiện có để lưu trữ DataSync agent. Thiết lập này cho phép kết nối an toàn giữa các máy chủ Windows Server on-premises và môi trường AWS.

Các hành động chính trong giai đoạn này bao gồm:

- Cung cấp và cấu hình hypervisor để chạy DataSync agent trong một môi trường cô lập, ổn định.
- Tối ưu hóa lớp mạng với internet tốc độ cao chuyên dụng và VPN tunnels để tối đa hóa băng thông và giảm độ trễ.
- Xác thực kết nối giữa lưu trữ on-premises và các đích Amazon EFS để đảm bảo sẵn sàng truyền dữ liệu.

#### **Giai đoạn 2: Di chuyển dữ liệu an toàn và xác thực**

Khi cơ sở hạ tầng đã sẵn sàng, nhóm bắt đầu di chuyển hơn 60 TB dữ liệu có cấu trúc và phi cấu trúc. DataSync được sử dụng để điều phối việc truyền dữ liệu một cách đáng tin cậy và được giám sát chặt chẽ.

Để đảm bảo tính toàn vẹn và đầy đủ của dữ liệu:

- Các lần truyền được thực hiện theo từng phần, với xác thực checksum ở cả hai đầu.
- Các tác vụ truyền được giám sát theo thời gian thực thông qua [Amazon CloudWatch](https://aws.amazon.com/cloudwatch/) và các chỉ số DataSync.
- Hiệu suất truyền được tinh chỉnh nhiều lần để tối ưu hóa thông lượng, đặc biệt đối với các tệp lớn và cấu trúc thư mục sâu.
- Một môi trường thử nghiệm riêng biệt trên AWS được sử dụng để xác thực dữ liệu đã di chuyển và hành vi của ứng dụng trước khi chuyển đổi cuối cùng.

#### **Giai đoạn 3: Chuyển sang môi trường sản xuất và triển khai ứng dụng**

Giai đoạn cuối cùng liên quan đến việc chuyển đổi sang các khối lượng công việc sản xuất được lưu trữ trên AWS. Ngăn xếp ứng dụng dựa trên Windows kế thừa đã được container hóa bằng Docker và triển khai lên Amazon EKS, cho phép nền tảng mở rộng linh hoạt và chạy độc lập với hệ điều hành bên dưới.

Các bước chính trong giai đoạn này:

- Cụm EKS được cấu hình với các nhóm node có khả năng tự động mở rộng bằng Amazon EC2, giúp tối ưu hóa chi phí và hiệu suất.
- Amazon VPC được thiết lập với định tuyến tùy chỉnh, Security Groups và NACLs để đảm bảo luồng lưu lượng an toàn giữa các dịch vụ nội bộ (east-west) và bên ngoài (north-south).
- Cấu hình ứng dụng và thông tin bí mật được quản lý bằng [AWS Systems Manager Parameter Store](https://docs.aws.amazon.com/systems-manager/latest/userguide/systems-manager-parameter-store.html) và AWS Secrets Manager.
- A/B testing và chuyển đổi lưu lượng dần dần đảm bảo triển khai không thời gian chết
- Các hệ thống kế thừa chỉ được ngừng hoạt động sau khi đã xác thực đầy đủ trong môi trường đám mây.

## **Thực hành tốt nhất**

Các thực hành tốt nhất sau đây đã được áp dụng:

- Infrastructure as Code (IaC) với Terraform: Hạ tầng được cung cấp bằng Terraform, cho phép triển khai có kiểm soát phiên bản, có thể lặp lại và có khả năng kiểm toán.
- CI/CD pipelines: Các pipeline GitLab được thiết lập cho continuous integration và deployment (CI/CD), đảm bảo cập nhật nhanh chóng và an toàn cho các dịch vụ được container hóa.
- Quan sát: [DATADOG](https://aws.amazon.com/codedeploy/product-integrations/datadog/) và CloudWatch được tích hợp để giám sát và cảnh báo toàn bộ ngăn xếp, bao gồm compute, storage và network.
- Sao lưu và khôi phục thảm họa: Chính sách AWS Backup được áp dụng cho Amazon EFS và các bản snapshot Amazon EC2, với khả năng sao chép cross-[Region](https://aws.amazon.com/about-aws/global-infrastructure/regions_az/) cho các khối lượng công việc quan trọng.

## **Lợi ích chính**

Sau đây là sáu lợi ích chính đạt được với giải pháp này:

#### **1. Khả năng mở rộng và hiệu suất**

Trước khi hiện đại hóa, các máy chủ vật lý của Uniphore bị cố định tài nguyên, thường dẫn đến tắc nghẽn hiệu suất trong thời gian cao điểm.

Sau khi di chuyển:

- Auto Scaling với Amazon EC2 và Amazon EKS cho phép cơ sở hạ tầng tự động mở rộng hoặc thu hẹp dựa trên khối lượng công việc thực tế.
- Tính mở rộng linh hoạt này đảm bảo tính sẵn sàng cao và hiệu suất ổn định, ngay cả trong thời gian tải cao hoặc xử lý hàng loạt.
- Độ trễ của ứng dụng giảm đáng kể nhờ điều phối container được tối ưu hóa và cung cấp compute phù hợp (right-sized).

#### **2. Tính linh hoạt và khả năng di chuyển**

Các ứng dụng kế thừa trước đây được gắn chặt với một phiên bản Windows OS cụ thể (2008 R2), khiến việc nâng cấp hoặc di chuyển trở nên khó khăn.

Sau khi tái cấu trúc và container hóa:

- Ứng dụng trở nên OS-agnostic và không phụ thuộc vào môi trường cụ thể.
- Các dịch vụ được container hóa hiện có thể chạy trên bất kỳ nền tảng tương thích Kubernetes nào, như Amazon EKS, cụm tự quản lý hoặc thậm chí các nhà cung cấp đám mây khác, đảm bảo tính độc lập với nhà cung cấp (vendor neutrality) và khả năng di chuyển.
- Các nhà phát triển có được sự linh hoạt để kiểm thử và triển khai trong các môi trường cô lập mà không gặp xung đột phụ thuộc.

#### **3. Tăng cường bảo mật và tuân thủ**

Vận hành các hệ thống không còn được hỗ trợ như Windows Server 2008 R2 tiềm ẩn rủi ro nghiêm trọng về bảo mật và tuân thủ, chẳng hạn như:

- Thiếu bản vá bảo mật.
- Không tương thích với các khung tuân thủ hiện đại như SOC 2, HIPAA hoặc ISO 27001.

Sau khi di chuyển:

- Việc sử dụng Amazon VPC, [AWS Identity and Access Management (IAM)](https://aws.amazon.com/iam/) roles, Security Groups và Kubernetes RBAC cải thiện kiểm soát truy cập và phân đoạn mạng.
- Tất cả các khối lượng công việc chạy trên các phiên bản hệ điều hành được hỗ trợ tích cực và được bảo vệ bằng các công cụ bảo mật gốc AWS như [Amazon Inspector](https://aws.amazon.com/inspector/), [AWS Config](https://aws.amazon.com/config/) và [AWS GuardDuty](https://aws.amazon.com/guardduty/).
- AWS Backup và kiến trúc multi-Availability Zone (AZ) cung cấp khả năng khôi phục thảm họa và tính liên tục kinh doanh được tích hợp sẵn.

#### **4. Quản lý dữ liệu hiệu quả**

Tốc độ tăng trưởng dữ liệu đã vượt quá khả năng của cơ sở hạ tầng on-premises, dẫn đến các vấn đề về dung lượng lưu trữ và lỗi sao lưu.

- Amazon EFS cung cấp hệ thống tệp NFS được quản lý hoàn toàn, có khả năng mở rộng tự động cùng với sự tăng trưởng của dữ liệu.
- Amazon S3 được sử dụng để lưu trữ dữ liệu đã xử lý, hưởng lợi từ độ bền cao và các chính sách vòng đời (lifecycle policies) để di chuyển dữ liệu cũ sang các lớp lưu trữ tiết kiệm chi phí như S3 Glacier.
- DataSync cho phép truyền nhanh và an toàn hơn 60 TB dữ liệu, đồng thời đảm bảo tính toàn vẹn với checksum và cơ chế retry.

#### **5. Giảm chi phí vận hành**

Quản lý hạ tầng on-premises kéo theo chi phí vận hành cao, từ việc vá lỗi thủ công, giám sát cho đến lập kế hoạch dung lượng

Sau khi di chuyển:

- Nhóm không còn phải lo về bảo trì phần cứng, nâng cấp hệ điều hành hoặc viết script sao lưu.
- IaC bằng Terraform và pipeline CI/CD tự động cho phép quản lý hạ tầng và triển khai nhất quán, đáng tin cậy hơn.
- Đội kỹ sư hiện có thể tập trung vào đổi mới sản phẩm thay vì xử lý sự cố hạ tầng.

#### **6. Tiết kiệm chi phí đáng kể**

Một trong những kết quả có tác động lớn nhất của sáng kiến này là giảm 30% tổng chi phí vận hành.

Tiết kiệm chi phí đạt được thông qua:

- Tắt các tài nguyên trung tâm dữ liệu kế thừa.
- Tối ưu hóa việc sử dụng instance với EC2 Auto Scaling và Spot Instances.
- Điều chỉnh phù hợp quy mô lưu trữ và compute.
- Containerization giảm chi phí tài nguyên, cho phép nhiều ứng dụng chạy hiệu quả trên ít node hơn.
- Khả năng giảm quy mô tài nguyên không sử dụng trong giờ thấp điểm giúp giảm trực tiếp hóa đơn đám mây hàng tháng.

## **Kết luận**

Bài viết này minh họa cách các doanh nghiệp có thể thành công trong việc hiện đại hóa khối lượng công việc Windows Server kế thừa bằng các dịch vụ AWS, thông qua hành trình của Uniphore --- từ máy chủ vật lý sang kiến trúc container hóa, cloud-native.

Thông qua việc lập kế hoạch cẩn thận và triển khai containerization, các giải pháp di chuyển dữ liệu tùy chỉnh và hạ tầng đám mây hiện đại, các tổ chức có thể đạt được lợi ích đáng kể về vận hành và chi phí trong khi vẫn duy trì tính liên tục kinh doanh.

Các điểm chính rút ra từ hành trình hiện đại hóa này bao gồm:

- Tầm quan trọng của cách tiếp cận di chuyển theo từng giai đoạn để giảm rủi ro và đảm bảo tính toàn vẹn dữ liệu.
- Cách containerization có thể biến đổi các ứng dụng Windows kế thừa thành các khối lượng công việc linh hoạt và có khả năng mở rộng.
- Chiến lược di chuyển dữ liệu hiệu quả bằng cách sử dụng AWS DataSync và các giải pháp tùy chỉnh.
- Thực hành tốt nhất để triển khai bảo mật, giám sát và khôi phục thảm họa trong môi trường đám mây.

## **Tìm hiểu thêm**

Để bắt đầu hành trình hiện đại hóa của riêng bạn, vui lòng xem các tài nguyên sau:

- [https://aws.amazon.com/enterprise/modernization/](https://aws.amazon.com/enterprise/modernization/)
- [https://www.youtube.com/watch?v=iL5FJ_1vKik](https://www.youtube.com/watch?v=iL5FJ_1vKik)
- [https://www.youtube.com/watch?v=4rquMWa3qp0](https://www.youtube.com/watch?v=4rquMWa3qp0)

TAGS: [Amazon EKS](https://aws.amazon.com/blogs/storage/tag/amazon-eks/), [Amazon Elastic Compute Cloud (Amazon EC2)](https://aws.amazon.com/blogs/storage/tag/amazon-elastic-compute-cloud-amazon-ec2/), [Amazon Simple Storage Service (Amazon S3)](https://aws.amazon.com/blogs/storage/tag/amazon-simple-storage-service-amazon-s3/), [AWS Cloud Storage](https://aws.amazon.com/blogs/storage/tag/aws-cloud-storage/), [AWS DataSync](https://aws.amazon.com/blogs/storage/tag/aws-datasync/)

### **Sornavel Perumal**

![Sornavel Perumal](/images/Blog1_image2.png)

 **Sornavel Perumal** là Senior Technical Account Manager tại AWS với hơn 20 năm kinh nghiệm. Ông giúp khách hàng xây dựng các giải pháp có khả năng mở rộng và tối ưu chi phí với AWS. Ông đam mê về Analytics, Machine Learning và GenAI, và luôn thích học hỏi những điều mới mỗi ngày.

### **Ismail Baig**

![Ismail Baig](/images/Blog1_image3.png)

**Ismail Baig** là Manager of DevOps and Cloud tại Uniphore và là chuyên gia AWS Certified Solutions Architect. Với hơn 12 năm kinh nghiệm, ông chuyên giải quyết các thách thức hạ tầng phức tạp cho các startup thế hệ mới trong các lĩnh vực Analytics, AI, ML, Big Data và Digital Solutions.