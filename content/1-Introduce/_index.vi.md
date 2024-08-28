---
title : "Giới thiệu"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---

**AWS CodeBuild** là một dịch vụ tích hợp liên tục hoàn toàn quản lý, dùng để biên dịch mã nguồn, chạy các bài kiểm tra, và tạo ra các gói phần mềm sẵn sàng để triển khai. Với CodeBuild, bạn không cần phải quản lý, cấp phát, và mở rộng các máy chủ build của riêng mình. CodeBuild tự động mở rộng và xử lý nhiều bản build đồng thời, nên các bản build của bạn sẽ không bị chờ đợi trong hàng đợi.

Các Tính Năng Chính:

+ Quản Lý Hoàn Toàn: AWS CodeBuild được quản lý hoàn toàn, có nghĩa là AWS sẽ lo việc cấp phát và mở rộng cơ sở hạ tầng cần thiết để chạy các bản build của bạn.
+ Khả Năng Mở Rộng: CodeBuild tự động mở rộng dựa trên số lượng bản build, đảm bảo việc xử lý nhanh chóng và hiệu quả.
+ Tùy Biến: Bạn có thể sử dụng các môi trường build tùy chỉnh để chạy các dự án CodeBuild trong các môi trường container hóa của riêng bạn, bao gồm cả phần mềm và cấu hình tùy chỉnh.
 
**Docker** là một nền tảng mã nguồn mở được thiết kế để tự động hóa việc triển khai ứng dụng bên trong các container nhẹ và di động. Container bao gồm ứng dụng và tất cả các phụ thuộc của nó, đảm bảo rằng ứng dụng sẽ chạy giống nhau bất kể môi trường nào.

Các Khái Niệm Chính:

+ Container: Các đơn vị phần mềm tiêu chuẩn hóa đóng gói mã và tất cả các phụ thuộc của nó.
+ Image: Các mẫu chỉ đọc định nghĩa môi trường trong đó ứng dụng của bạn chạy.
+ Dockerfile: Một tệp văn bản chứa tất cả các lệnh để tạo thành một Docker image.
  
**Amazon Elastic Container Registry (ECR)** là một Docker container registry hoàn toàn quản lý, giúp các nhà phát triển dễ dàng lưu trữ, quản lý và triển khai các Docker container images. ECR tích hợp với Amazon ECS, đơn giản hóa quy trình từ phát triển đến sản xuất.

Các Lợi Ích Chính:

+ Quản Lý Hoàn Toàn: ECR quản lý việc vận hành và mở rộng cơ sở hạ tầng cần thiết cho việc lưu trữ container image.
+ Bảo Mật: Images được mã hóa khi lưu trữ, và IAM policies có thể kiểm soát quyền truy cập vào các images.
+ Tích Hợp: Tích hợp liền mạch với các dịch vụ AWS khác như ECS, Fargate, và CodeBuild.
  
**Trường Hợp Sử Dụng:**

ECR thường được sử dụng cùng với AWS CodeBuild để tự động hóa quy trình xây dựng Docker images từ mã nguồn lưu trữ trong hệ thống quản lý phiên bản như GitHub, sau đó đẩy các images đã xây dựng lên ECR để triển khai.