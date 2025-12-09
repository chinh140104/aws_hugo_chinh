---
title: "Worklog Tuần 12"
date: "2025-11-28"
weight: 12
chapter: false
pre: " <b> 1.12 </b> "
---

### Mục tiêu tuần 12:

* Kiểm tra và đánh giá hiệu suất hệ thống sau khi triển khai lên AWS.
* Tối ưu mã nguồn, tối ưu Lambda và cơ sở dữ liệu DynamoDB.
* Rà soát luồng xác thực – ủy quyền ở mức cơ bản để tránh lỗi (không đi sâu bảo mật).
* Hoàn thiện báo cáo tổng hợp đồ án và chuẩn bị tài liệu trình bày.
### Các công việc cần triển khai trong tuần này:
| Thứ | Công việc                                                                                                                                                                                   | Ngày bắt đầu | Ngày hoàn thành | Nguồn tài liệu                            |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ | --------------- | ----------------------------------------- |
| 2   | - Phân tích log CloudWatch <br> - Sử dụng X-Ray để tìm bottleneck và lỗi runtime                                                                                             | 24/11/2025 | 24/11/2025      |
| 3   | - Kiểm tra hiệu suất Backend (thời gian phản hồi API / Cold Start) <br> - Thử load nhẹ để đánh giá khả năng mở rộng         | 25/11/2025 | 25/11/2025      |  |
| 4   | - Tối ưu code .NET: giảm kích thước package, tối ưu hàm Lambda <br> - Rà soát truy vấn DynamoDB và tối ưu GSI nếu cần | 26/11/2025 | 26/11/2025      |  |
| 5   | - Rà soát cơ bản việc xác thực/ủy quyền (không đi sâu, chỉ test hoạt động ổn định) <br> - Hoàn thiện sơ đồ kiến trúc & mô tả luồng dữ liệu                  | 27/11/2025 | 27/11/2025      | |
| 6   | - Tổng hợp worklog tuần 10–12 vào báo cáo cuối <br> - Viết đánh giá, kết luận, ưu nhược điểm kiến trúc <br> - Chuẩn bị tài liệu thuyết trình                                                                                       | 28/11/2025 | 28/11/2025      | |


### Kết quả đạt được tuần 12:

* Tổng quát:
  * Trong tuần này tôi tập trung kiểm tra lại toàn bộ hệ thống đã triển khai trên AWS, đánh giá hiệu suất thực tế và tối ưu các thành phần chính. Sau đó tôi hoàn thiện tài liệu và báo cáo tổng hợp đồ án.

* Lý thuyết đã học:
  * Cách truy vấn và phân tích log runtime trong CloudWatch.
  * Theo dõi luồng request bằng X-Ray để tìm bottleneck.
  * Kiến thức về tối ưu hiệu suất Lambda (cold start, initialization).
  * Cách tối ưu DynamoDB bằng GSI/LSI và phân tích pattern truy vấn.
  * Tổng hợp kiến trúc Serverless và đánh giá ưu/nhược điểm.

* Thực hành / Sản phẩm:
  * Phân tích lỗi runtime và hiệu suất trên CloudWatch & X-Ray.
  * Kiểm tra thời gian phản hồi API và đề xuất giải pháp cold start (nếu cần).
  * Tối ưu kích thước package Lambda và cải thiện thời gian thực thi.
  * Tối ưu mô hình DynamoDB để giảm độ trễ truy vấn.
  * Hoàn thiện sơ đồ kiến trúc AWS cuối cùng.
  * Viết xong báo cáo tổng hợp đồ án, bao gồm đánh giá cuối và chuẩn bị slide thuyết trình.