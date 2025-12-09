---
title: "Event 2"
date: "2025-11-16"
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

# Bài Thu Hoạch Workshop "AWS Cloud Mastery Series #1: AI/ML/GenAI on AWS"

### Mục Đích Của Sự Kiện
- Cung cấp cái nhìn tổng quan về hệ sinh thái AI/ML/GenAI trên nền tảng AWS, tập trung vào các dịch vụ cốt lõi.
- Trang bị kiến thức thực tế về quy trình triển khai AI/ML từ chuẩn bị dữ liệu đến vận hành mô hình với Amazon SageMaker.
- Hướng dẫn thực hành ứng dụng Generative AI thông qua Amazon Bedrock, bao gồm prompt engineering, RAG và xây dựng agent.
- Tạo môi trường kết nối và học hỏi giữa các sinh viên, developer quan tâm đến lĩnh vực AI/ML trên đám mây.

### Diễn Giả / Người Hướng Dẫn Chính (Dựa trên nội dung chương trình)
- **Anh Nguyễn Gia Hưng** – Head of Solutions Architect, AWS Vietnam (Phần giới thiệu & định hướng)
- **Chị Trần Thị Minh Anh** – Sr. AI/ML Specialist Solutions Architect, AWS (Phần trình bày kỹ thuật & demo)
- **Anh Lê Quang Huy** – Cloud Engineer & AI Enthusiast (Hỗ trợ thực hành & Q&A)

### Nội Dung Nổi Bật & Bài Học Chính

#### 1. Tổng Quan Hệ Sinh Thái AI/ML/GenAI Trên AWS
- **Landscape tại Việt Nam**: Xu hướng ứng dụng AI đang bùng nổ, từ startups đến doanh nghiệp lớn, với nhu cầu cao về nhân sự có chuyên môn.
- **Lộ trình học tập AWS AI/ML**: Từ cơ bản (AWS AI/ML Fundamentals) đến chuyên sâu (Specialty Certifications), nhấn mạnh việc **"học qua thực hành"** (hands-on labs, projects).
- **Ba trụ cột chính**: AI Services (Ready-to-use), ML Services (Customizable), và Generative AI (Innovative).

#### 2. Amazon SageMaker: Nền Tảng Toàn Diện Cho Machine Learning
- **End-to-end ML platform**: Một workspace duy nhất cho toàn bộ vòng đời ML: từ chuẩn bị dữ liệu → huấn luyện mô hình → triển khai → giám sát.
- **SageMaker Studio**: Trải nghiệm IDE tích hợp đầy đủ tool, giúp **tăng tốc độ phát triển** (dev speed) lên đáng kể so với việc tự build workflow.
- **MLOps tích hợp**: Tự động hóa việc training, tuning (AutoML), và quản lý model lifecycle, đảm bảo model luôn **hoạt động ổn định và hiệu quả** trong production.

#### 3. Generative AI Với Amazon Bedrock: Từ Lý Thuyết Đến Ứng Dụng Thực Tế
- **Foundation Models (FMs)**: So sánh điểm mạnh/yếu của các model hàng đầu (Anthropic Claude, Meta Llama, Amazon Titan) và **cách chọn model phù hợp** với use case (cost, performance, task type).
- **Prompt Engineering Kỹ Thuật Cao**: Không chỉ là "hỏi đúng câu", mà là **thiết kế prompt có cấu trúc** (Chain-of-Thought, Few-shot) để đạt kết quả tối ưu.
- **Retrieval-Augmented Generation (RAG)**: Kiến trúc kết nối LLM với cơ sở tri thức riêng (knowledge base), giải quyết vấn đề **hallucination** (sinh thông tin sai) và cập nhật kiến thức mới cho model.
- **Bedrock Agents**: Biến LLM thành "trợ lý thông minh" có thể **thực hiện chuỗi tác vụ** (multi-step workflows), gọi API, truy vấn database một cách tự động.
- **Guardrails for Bedrock**: Cơ chế **lọc nội dung độc hại** và đảm bảo an toàn, tuân thủ chính sách của doanh nghiệp.

### Những Gì Học Được (Key Takeaways)

#### Về Kiến Thức Công Nghệ
- **SageMaker không chỉ là tool train model**: Đó là một **nền tảng quản lý vòng đời ML** giúp đơn giản hóa công việc của Data Scientist và ML Engineer.
- **GenAI không phải "phép màu"**: Ứng dụng thành công đòi hỏi hiểu rõ **bản chất của model, kỹ thuật prompt, và kiến trúc bổ trợ** như RAG.
- **Quan trọng nhất là dữ liệu**: Dù công nghệ cao đến đâu, chất lượng đầu vào (data) vẫn quyết định **80% chất lượng đầu ra** của mô hình AI.

#### Về Tư Duy & Phương Pháp
- **Business Problem First**: Luôn bắt đầu từ bài toán kinh doanh cụ thể, sau đó mới tìm công nghệ AI/ML phù hợp để giải quyết.
- **Iterative Development (Phát triển lặp)**: Xây dựng prototype nhanh với Bedrock, thu thập feedback, rồi mới đầu tư train custom model nếu cần.
- **Cost Awareness**: Cần tính toán chi phí ngay từ đầu (cost of training, inference, storage) để đảm bảo tính khả thi của dự án.

#### Về Kỹ Năng Thực Chiến
- **Prompt Engineering là một kỹ năng có thể luyện tập**: Cần hiểu nguyên lý và thực hành nhiều với các loại task khác nhau.
- **Biết sử dụng AWS Console & SDK** cho SageMaker và Bedrock là bước đầu tiên quan trọng để bắt tay vào làm dự án thật.

### Kế Hoạch Hành Động Cá Nhân Sau Workshop
1.  **Thực hành ngay trên AWS Free Tier**: Tạo tài khoản AWS (nếu chưa có) và bắt đầu với **SageMaker Studio Lab** miễn phí để làm quen giao diện.
2.  **Xây dựng ứng dụng GenAI đầu tiên**: Sử dụng **Amazon Bedrock** (đang trong giai đoạn preview, có thể đăng ký access) để thử build một chatbot đơn giản trả lời câu hỏi về một chủ đề mình am hiểu.
3.  **Học chuyên sâu qua AWS Skill Builder**: Đăng ký các khóa học **"Generative AI with Large Language Models"** và **"Machine Learning Learning Plan"** để hệ thống hóa kiến thức.
4.  **Tham gia cộng đồng**: Tích cực hơn trong nhóm **AWS AI/ML Enthusiasts Vietnam** trên Facebook/LinkedIn để học hỏi từ các case study thực tế.

### Trải Nghiệm Cá Nhân Trong Sự Kiện

Workshop "AI/ML/GenAI on AWS" đã thực sự mở ra một chân trời mới về cách tiếp cận công nghệ AI một cách bài bản và khả thi. Không gian tại văn phòng AWS chuyên nghiệp và hiện đại, cùng sự nhiệt tình của các anh chị diễn giả, đã tạo nên một buổi học vừa chuyên sâu vừa thân thiện.

**Phần demo trực tiếp là điểm nhấn tuyệt vời.** Được chứng kiến chị Minh Anh biến các khái niệm về RAG, Bedrock Agent từ lý thuyết thành một chatbot hoạt động thực sự trong vài chục phút đã khiến em và nhiều bạn "ah-ha" lên thích thú. Nó chứng minh rằng khoảng cách từ **ý tưởng đến prototype** trong GenAI hiện nay là rất ngắn, nếu chúng ta biết cách sử dụng đúng công cụ.

Em cũng ấn tượng với góc nhìn thực tế về **chi phí và MLOps**. Các anh chị không chỉ nói về mặt sáng của AI mà còn thẳng thắn chia sẻ những thách thức về quản lý model, monitoring, và chi phí vận hành - những điều sinh viên thường ít được đề cập trên trường lớp.

Buổi workshop kết thúc với cảm giác **"có thể làm được"**. Thay vì choáng ngợp trước những thuật ngữ phức tạp, em cảm thấy mình đã có một bản đồ (roadmap) rõ ràng để bắt đầu hành trình khám phá AI/ML trên AWS, từ những bước thực hành nhỏ nhất.

#### Một số hình ảnh khi tham gia sự kiện
![anh1 event](/images/event-image1.png)
![anh2 event](/images/event-image2.png)