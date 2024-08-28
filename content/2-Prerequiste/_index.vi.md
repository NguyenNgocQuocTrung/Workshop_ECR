---
title : "Các bước chuẩn bị"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---


{{% notice info %}}
Trước khi bắt đầu, hãy đảm bảo bạn cần có những điều sau:
{{% /notice %}}

**Tài khoản AWS:**
Tài khoản AWS có đủ quyền để truy cập và sử dụng các dịch vụ sau
  
**GitHub Repository:**
Kho lưu trữ GitHub chứa Dockerfile và mọi tệp cần thiết khác để xây dựng image Docker của bạn. Dockerfile xác định môi trường và các bước cần thiết để tạo hình ảnh Docker cho ứng dụng của bạn.

**AWS CLI:**
Giao diện dòng lệnh AWS (CLI) phải được cài đặt và định cấu hình trên máy cục bộ của bạn. Điều này rất cần thiết để tương tác với các dịch vụ AWS từ thiết bị đầu cuối của bạn.

**Docker:**
Docker phải được cài đặt và chạy trên máy cục bộ của bạn. Docker được sử dụng để xây dựng, chạy và quản lý các container.
  
### Nội dung
+ [Tạo tài khoản AWS](2.1-createAWSaccount/ )
+ [Tạo kho lưu trữ Github](2.2-createGithubRepo/ )
+ [Cài đặt AWS CLI](2.3-createAWSCLI/ )
+ [Cài đặt Docker](2.4-createDocker/)