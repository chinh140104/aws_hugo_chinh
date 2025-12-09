---
title: "Blog 3"
date: "2025-09-09"
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# Mở khóa trí tuệ bán lẻ bằng cách chuyển đổi dữ liệu thành thông tin chi tiết có thể hành động bằng Generative AI với Amazon Q Business

**Bởi Suprakash Dutta, Abhijit Dutta, Girish Nazhiyath, Krishnan Hariharan, Alberto Alonso và Ramesh Venkataraman — ngày 09 THÁNG 7 NĂM 2025 — trong [Amazon Q Business](https://aws.amazon.com/blogs/machine-learning/category/amazon-q/amazon-q-business/), [Amazon QuickSight](https://aws.amazon.com/blogs/machine-learning/category/analytics/amazon-quicksight/), [Analytics](https://aws.amazon.com/blogs/machine-learning/category/analytics/), [Artificial Intelligence](https://aws.amazon.com/blogs/machine-learning/category/artificial-intelligence/), [Generative AI](https://aws.amazon.com/blogs/machine-learning/category/artificial-intelligence/generative-ai/), [Intermediate (200)](https://aws.amazon.com/blogs/machine-learning/category/learning-levels/intermediate-200/), [Retail](https://aws.amazon.com/blogs/machine-learning/category/industries/retail/), [Technical How-to](https://aws.amazon.com/blogs/machine-learning/category/post-types/technical-how-to/) [Permalink](https://aws.amazon.com/blogs/machine-learning/unlock-retail-intelligence-by-transforming-data-into-actionable-insights-using-generative-ai-with-amazon-q-business/) [Comments](https://aws.amazon.com/blogs/machine-learning/unlock-retail-intelligence-by-transforming-data-into-actionable-insights-using-generative-ai-with-amazon-q-business/#Comments) [Share](https://aws.amazon.com/vi/blogs/machine-learning/unlock-retail-intelligence-by-transforming-data-into-actionable-insights-using-generative-ai-with-amazon-q-business/#)**

Doanh nghiệp thường đối mặt với thách thức trong việc quản lý và khai thác giá trị từ dữ liệu của họ. Theo [McKinsey](https://www.mckinsey.com/capabilities/quantumblack/our-insights/the-state-of-ai), 78% tổ chức hiện đang sử dụng AI trong ít nhất một chức năng kinh doanh (tính đến năm 2024), cho thấy tầm quan trọng ngày càng tăng của các giải pháp AI trong kinh doanh. Ngoài ra, 21% tổ chức sử dụng generative AI đã tái thiết kế hoàn toàn quy trình làm việc của họ, cho thấy cách AI đang chuyển đổi các hoạt động kinh doanh.

[Gartner](https://www.gartner.com/en/information-technology/customer-success-stories/enabling-new-retail-and-business-innovation) xác định phân tích và báo cáo được hỗ trợ bởi AI là lĩnh vực đầu tư cốt lõi đối với các tổ chức bán lẻ, với hầu hết các nhà bán lẻ lớn dự kiến sẽ triển khai hoặc mở rộng quy mô các giải pháp như vậy trong vòng 12–18 tháng tới. Độ phức tạp của dữ liệu trong ngành bán lẻ đòi hỏi các giải pháp tinh vi có thể tích hợp liền mạch với các hệ thống hiện có. [Amazon Q Business](https://aws.amazon.com/q/business/) cung cấp các tính năng có thể được tùy chỉnh để đáp ứng nhu cầu cụ thể của doanh nghiệp, bao gồm khả năng tích hợp với các hệ thống quản lý bán lẻ phổ biến, hệ thống điểm bán hàng (POS), phần mềm quản lý hàng tồn kho và hệ thống thương mại điện tử. Thông qua các thuật toán AI tiên tiến, hệ thống phân tích dữ liệu lịch sử và xu hướng hiện tại, giúp doanh nghiệp chuẩn bị hiệu quả cho những biến động theo mùa trong nhu cầu và đưa ra quyết định dựa trên dữ liệu.

Amazon Q Business for Retail Intelligence là một trợ lý được hỗ trợ bởi AI được thiết kế để giúp các doanh nghiệp bán lẻ hợp lý hóa hoạt động, cải thiện dịch vụ khách hàng và nâng cao quy trình ra quyết định. Giải pháp này được thiết kế đặc biệt để có thể mở rộng và thích ứng với các doanh nghiệp ở nhiều quy mô khác nhau, giúp họ cạnh tranh hiệu quả hơn. Trong bài viết này, chúng tôi sẽ trình bày cách bạn có thể sử dụng Amazon Q Business for Retail Intelligence để chuyển đổi dữ liệu của mình thành thông tin chi tiết có thể hành động.

## **Tổng quan giải pháp**

Amazon Q Business for Retail Intelligence là một giải pháp toàn diện chuyển đổi cách các nhà bán lẻ tương tác với dữ liệu của họ bằng generative AI. Kiến trúc giải pháp kết hợp khả năng generative AI mạnh mẽ của [Amazon Q Business](https://aws.amazon.com/q/business/) và các trực quan hóa từ [Amazon QuickSight](https://aws.amazon.com/quicksight) để cung cấp thông tin chi tiết có thể hành động trên toàn bộ chuỗi giá trị bán lẻ. Giải pháp của chúng tôi cũng sử dụng [Amazon Q Apps](https://docs.aws.amazon.com/amazonq/latest/qbusiness-ug/purpose-built-qapps.html) để các vai trò và người dùng trong ngành bán lẻ có thể tạo các ứng dụng tùy chỉnh được hỗ trợ bởi AI nhằm hợp lý hóa các tác vụ hàng ngày và tự động hóa quy trình công việc và quy trình kinh doanh.

Sơ đồ sau minh họa kiến trúc giải pháp.


![anh1](/images/3-Blog/Blog3_image1.png)

Giải pháp sử dụng kiến trúc AWS ở trên để cung cấp một giải pháp an toàn, hiệu suất cao và đáng tin cậy cho trí tuệ bán lẻ. Amazon Q Business đóng vai trò là công cụ generative AI chính, cho phép tương tác bằng ngôn ngữ tự nhiên và cung cấp năng lực cho các ứng dụng tùy chỉnh dành riêng cho bán lẻ. Kiến trúc này bao gồm [AWS IAM Identity Center](https://aws.amazon.com/iam/identity-center/) để xác thực và kiểm soát truy cập mạnh mẽ, và [Amazon Simple Storage Service](http://aws.amazon.com/s3) (Amazon S3) cung cấp lưu trữ hồ dữ liệu an toàn cho các nguồn dữ liệu bán lẻ. Chúng tôi sử dụng QuickSight để tạo trực quan hóa tương tác, giúp nâng cao khả năng diễn giải dữ liệu. Tính linh hoạt của giải pháp được tăng cường thêm bởi [AWS Lambda](http://aws.amazon.com/lambda) cho xử lý serverless, [Amazon API Gateway](https://aws.amazon.com/api-gateway) cho quản lý endpoint hiệu quả, và [Amazon CloudFront](https://aws.amazon.com/cloudfront/) cho phân phối nội dung được tối ưu hóa. Giải pháp này sử dụng plugin tùy chỉnh Amazon Q Business để gọi các API endpoint nhằm bắt đầu quy trình tự động hóa trực tiếp từ giao diện ứng dụng web Amazon Q Business dựa trên các truy vấn và tương tác của khách hàng.

Cấu hình này triển khai kiến trúc ba tầng: Lớp tích hợp dữ liệu: thu nạp dữ liệu an toàn từ nhiều nguồn bán lẻ, lớp xử lý: nơi Amazon Q Business phân tích truy vấn và tạo thông tin chi tiết, lớp trình bày: cung cấp thông tin chi tiết được cá nhân hóa, dựa trên vai trò, thông qua một giao diện thống nhất.

Chúng tôi đã cung cấp một mẫu [AWS CloudFormation](http://aws.amazon.com/cloudformation), bộ dữ liệu mẫu và các script mà bạn có thể sử dụng để thiết lập môi trường cho bản demo này.

Trong các phần tiếp theo, chúng tôi sẽ đi sâu vào cách hoạt động của giải pháp này.

## **Triển khai**

Chúng tôi đã cung cấp giải pháp Amazon Q Business for Retail Intelligence dưới dạng mã nguồn mở — bạn có thể sử dụng nó làm điểm khởi đầu cho giải pháp của riêng mình và giúp chúng tôi cải thiện bằng cách đóng góp các bản sửa lỗi và tính năng thông qua pull request trên GitHub.

Truy cập [GitHub repository](https://github.com/aws-samples/sample-amazon-qbusiness-and-quicksight-for-retail-intelligence) để khám phá mã, chọn **Watch** để nhận thông báo về các bản phát hành mới, và kiểm tra tệp README để xem các cập nhật tài liệu mới nhất.

Sau khi bạn thiết lập môi trường, bạn có thể truy cập bảng điều khiển Amazon Q Business for Retail Intelligence, như minh họa trong ảnh chụp màn hình sau.


![anh2](/images/3-Blog/Blog3_image2.png)

Bạn có thể tương tác với các trực quan hóa QuickSight và giao diện trò chuyện Amazon Q Business để đặt câu hỏi bằng ngôn ngữ tự nhiên.

## **Các tính năng và năng lực chính**

Người dùng bán lẻ có thể tương tác với giải pháp này theo nhiều cách khác nhau. Trong phần này, chúng ta sẽ khám phá các tính năng chính.

Đối với các giám đốc điều hành cấp cao hoặc lãnh đạo doanh nghiệp muốn biết doanh nghiệp của bạn đang hoạt động như thế nào, giải pháp của chúng tôi cung cấp một giao diện thống nhất, giúp truy cập và tương tác với dữ liệu định tính và định lượng của doanh nghiệp một cách dễ dàng thông qua ngôn ngữ tự nhiên. Ví dụ: người dùng có thể phân tích dữ liệu định lượng như doanh số sản phẩm hoặc hiệu quả chiến dịch marketing bằng các trực quan hóa tương tác từ QuickSight, và dữ liệu định tính như phản hồi của khách hàng từ Amazon Q Business, tất cả chỉ trong một giao diện duy nhất.


![anh3](/images/3-Blog/Blog3_image3.png)

Giả sử bạn là một nhà phân tích marketing và bạn muốn đánh giá hiệu quả chiến dịch và mức độ tiếp cận trên các kênh, đồng thời tiến hành phân tích chi tiêu quảng cáo so với doanh thu. Với Amazon Q Business, bạn có thể chạy các truy vấn phức tạp bằng các câu hỏi ngôn ngữ tự nhiên và chia sẻ Q Apps với nhiều nhóm. Giải pháp này cung cấp thông tin chi tiết tự động về hành vi khách hàng và hiệu quả chiến dịch, giúp các nhóm marketing đưa ra quyết định nhanh hơn và điều chỉnh linh hoạt để tối đa hóa ROI.


![anh4](/images/3-Blog/Blog3_image4.png)

Tương tự, giả sử bạn là một nhà hoạch định hàng hóa hoặc quản lý nhà cung cấp, và bạn muốn hiểu tác động của các sự kiện có chi phí cao đối với hoạt động kinh doanh quốc tế của bạn — nơi bạn phải xử lý việc nhập khẩu và xuất khẩu hàng hóa và dịch vụ. Bạn có thể nhập thông tin đầu vào vào Amazon Q Apps và nhận phản hồi dựa trên sản phẩm hoặc nhóm sản phẩm cụ thể đó.


![anh5](/images/3-Blog/Blog3_image5.png)

Người dùng cũng có thể gửi yêu cầu thông qua API bằng các plugin tùy chỉnh của Amazon Q Business để tương tác thời gian thực với các ứng dụng phụ trợ. Ví dụ, một **quản lý cửa hàng** có thể muốn biết những mặt hàng nào trong kho hiện tại cần được bổ sung hoặc cân bằng lại cho tuần tới dựa trên dự báo thời tiết hoặc các sự kiện thể thao địa phương.


![anh6](/images/3-Blog/Blog3_image6.png)

Để tìm hiểu thêm, hãy tham khảo bản demo hoàn chỉnh dưới đây.

<video controls width="100%">
  <source src="https://d2908q01vomqb2.cloudfront.net/artifacts/DBSBlogs/ml-18557/Demo_video_best_quality.mp4?_=1" type="video/mp4">
  Your browser does not support the video tag.
</video>

Trong bài viết này, chúng tôi không sử dụng khả năng generative business intelligence (BI) của Amazon Q kết hợp với các trực quan hóa QuickSight. Để tìm hiểu thêm, hãy xem [Amazon Q in QuickSight.](https://aws.amazon.com/quicksight/q/)

## **Trao quyền cho các vai trò bán lẻ với trí tuệ do AI dẫn dắt**

Amazon Q Business for Retail Intelligence thay đổi cách các nhà bán lẻ xử lý thách thức dữ liệu của họ thông qua một trợ lý được hỗ trợ bởi generative AI. Giải pháp này tích hợp liền mạch với các hệ thống hiện có, sử dụng Retrieval Augmented Generation (RAG) để hợp nhất các nguồn dữ liệu rời rạc và cung cấp thông tin chi tiết có thể hành động theo thời gian thực. Dưới đây là một số lợi ích chính cho các vai trò khác nhau:

- **Các giám đốc điều hành cấp cao** — Truy cập các bảng điều khiển thời gian thực toàn diện cho các chỉ số và KPI trên toàn doanh nghiệp, đồng thời sử dụng các khuyến nghị được hỗ trợ bởi AI cho các quyết định chiến lược. Sử dụng phân tích dự đoán để dự đoán xu hướng tiêu dùng và cho phép điều chỉnh chiến lược chủ động cho sự tăng trưởng kinh doanh.

- **Các nhà quản lý hàng hóa** — Có được thông tin chi tiết ngay lập tức về xu hướng bán hàng, biên lợi nhuận và tỷ lệ luân chuyển hàng tồn kho thông qua các công cụ phân tích tự động và chiến lược định giá được hỗ trợ bởi AI. Xác định và tận dụng các xu hướng mới nổi thông qua phân tích dự đoán để tối ưu hóa danh mục và cơ cấu sản phẩm.

- **Các nhà quản lý hàng tồn kho** — Thực hiện tối ưu hóa mức tồn kho dựa trên dữ liệu trên nhiều địa điểm cửa hàng đồng thời hợp lý hóa hoạt động với các phép tính điểm đặt hàng tự động. Dự đoán và chuẩn bị chính xác cho các biến động theo mùa để duy trì mức tồn kho tối ưu trong thời gian cao điểm.

- **Các quản lý cửa hàng** — Tối đa hóa hiệu quả hoạt động thông qua tối ưu hóa nhân sự được AI dự đoán, đồng thời truy cập thông tin chi tiết về các điều kiện địa phương ảnh hưởng đến hiệu suất cửa hàng. So sánh các chỉ số cửa hàng với các địa điểm khác bằng các công cụ đo chuẩn tinh vi để xác định cơ hội cải thiện.

- **Các nhà phân tích marketing** — Giám sát và phân tích hiệu quả chiến dịch marketing trên các kênh theo thời gian thực trong khi phát triển các phân khúc khách hàng tinh vi bằng phân tích được hỗ trợ bởi AI. Tính toán và tối ưu hóa ROI marketing trên các kênh để phân bổ ngân sách hiệu quả và cải thiện hiệu suất chiến dịch.

Amazon Q Business for Retail Intelligence giúp việc phân tích dữ liệu phức tạp trở nên dễ tiếp cận hơn đối với nhiều loại người dùng khác nhau thông qua giao diện ngôn ngữ tự nhiên. Giải pháp này cho phép ra quyết định dựa trên dữ liệu trong toàn tổ chức bằng cách cung cấp thông tin chi tiết theo vai trò, phá vỡ các silo dữ liệu truyền thống. Bằng cách cung cấp cho mỗi vai trò trong bán lẻ các phân tích và khuyến nghị hành động phù hợp, các tổ chức có thể đạt được hiệu quả hoạt động cao hơn và duy trì lợi thế cạnh tranh trong bối cảnh bán lẻ năng động ngày nay.

## **Kết luận**

Amazon Q Business for Retail Intelligence kết hợp khả năng generative AI với các công cụ trực quan hóa mạnh mẽ để cách mạng hóa hoạt động bán lẻ. Bằng cách cho phép tương tác ngôn ngữ tự nhiên với các hệ thống dữ liệu phức tạp, giải pháp này dân chủ hóa việc truy cập dữ liệu trên mọi cấp độ tổ chức — từ các giám đốc điều hành cấp cao đến các quản lý cửa hàng. Khả năng của hệ thống trong việc cung cấp thông tin chi tiết theo vai trò, tự động hóa quy trình công việc và hỗ trợ ra quyết định thời gian thực khiến nó trở thành công cụ quan trọng cho các doanh nghiệp bán lẻ đang tìm cách duy trì khả năng cạnh tranh trong bối cảnh năng động hiện nay. Khi các nhà bán lẻ tiếp tục áp dụng các giải pháp được dẫn dắt bởi AI, Amazon Q Business for Retail Intelligence có thể giúp đáp ứng nhu cầu ngày càng tăng của ngành về phân tích dữ liệu tinh vi và hiệu quả hoạt động.

Để tìm hiểu thêm về các giải pháp và dịch vụ của chúng tôi, hãy tham khảo [Amazon Q Business](https://aws.amazon.com/q/business/) và [Generative AI on AWS](https://aws.amazon.com/ai/generative-ai/). Để nhận hỗ trợ chuyên môn, [AWS Professional Services](https://aws.amazon.com/professional-services/), [AWS Generative AI partner solutions](https://aws.amazon.com/ai/partners/?aws-marketplace-cards.sort-by=item.additionalFields.sortOrder&aws-marketplace-cards.sort-order=asc&awsf.aws-marketplace-aws-marketplace-aim=*all&awsf.aws-marketplace-aim=*all&awsf.aws-marketplace-asset-type=*all&awsf.aws-marketplace-category=*all), và [AWS Generative AI Competency Partners](https://aws.amazon.com/ai/generative-ai/partners/?aws-marketplace-cards.sort-by=item.additionalFields.sortOrder&aws-marketplace-cards.sort-order=asc&awsf.aws-marketplace-aws-marketplace-aim=*all&awsf.aws-marketplace-aim=aws-marketplace-aim%23gen-ai-software-competency-partner) luôn sẵn sàng giúp đỡ.

## **Về các tác giả**



![Suprakash Dutta](/images/3-Blog/Blog3_image7.png)

**[Suprakash Dutta](https://www.linkedin.com/in/suprakashdutta/)** là Senior Solutions Architect tại Amazon Web Services, dẫn dắt các chương trình chuyển đổi đám mây chiến lược cho các nhà bán lẻ Fortune 500 và các doanh nghiệp lớn. Ông chuyên thiết kế các giải pháp bán lẻ quan trọng dựa trên cloud, triển khai generative AI và các sáng kiến hiện đại hóa bán lẻ. Ông là một kiến trúc sư đa chứng chỉ cloud và đã cung cấp các giải pháp chuyển đổi giúp hiện đại hóa hoạt động trên hàng nghìn cửa hàng bán lẻ, đồng thời đạt được hiệu quả vượt trội thông qua các giải pháp trí tuệ bán lẻ được hỗ trợ bởi AI.


![Alberto Alonso](/images/3-Blog/Blog3_image8.png)

**Alberto Alonso** là Specialist Solutions Architect tại Amazon Web Services. Ông tập trung vào generative AI và cách nó có thể được áp dụng cho các thách thức kinh doanh.


![Abhijit Dutta](/images/3-Blog/Blog3_image9.png)

**Abhijit Dutta** là Sr. Solutions Architect trong mảng Retail/CPG tại AWS, tập trung vào các lĩnh vực chính như di chuyển và hiện đại hóa ứng dụng kế thừa, ra quyết định dựa trên dữ liệu và triển khai các khả năng AI/ML. Chuyên môn của ông nằm ở việc giúp các tổ chức tận dụng công nghệ cloud cho các sáng kiến chuyển đổi số, đặc biệt nhấn mạnh vào phân tích và giải pháp generative AI.


![Ramesh Venkataraman](/images/3-Blog/Blog3_image10.png)

**Ramesh Venkataraman** là Solutions Architect, người yêu thích làm việc với khách hàng để giải quyết các thách thức kỹ thuật bằng dịch vụ AWS. Ngoài công việc, Ramesh thích theo dõi các câu hỏi trên Stack Overflow và trả lời bất cứ khi nào có thể.


![Girish Nazhiyath](/images/3-Blog/Blog3_image11.png)

**Girish Nazhiyath** là Sr. Solutions Architect trong mảng Retail/CPG của Amazon Web Services. Ông thích làm việc với khách hàng bán lẻ/CPG để thúc đẩy đổi mới bán lẻ dựa trên công nghệ, với hơn 20 năm kinh nghiệm trong nhiều lĩnh vực và phân khúc bán lẻ trên toàn cầu.


![Krishnan Hariharan](/images/3-Blog/Blog3_image12.png)

**Krishnan Hariharan** là Sr. Manager, Solutions Architecture tại AWS, có trụ sở tại Chicago. Trong vai trò hiện tại, ông sử dụng sự kết hợp đa dạng giữa kỹ năng khách hàng, sản phẩm, công nghệ và vận hành để giúp khách hàng bán lẻ/CPG xây dựng các giải pháp tối ích bằng AWS. Trước khi gia nhập AWS, Krishnan từng là Chủ tịch/CEO tại Kespry và COO tại LightGuide. Ông có bằng MBA từ The Fuqua School of Business, Đại học Duke, và Cử nhân Khoa học ngành Điện tử từ Đại học Delhi.