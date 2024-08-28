---
title : "Tạo vai trò IAM"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.1.1 </b> "
---

### Tạo vai trò IAM 

+ Bạn cần có người dùng IAM có đủ quyền để tạo và quản lý các vai trò IAM, đặc biệt là vai trò dịch vụ cho AWS CodeBuild.
  
+ Đảm bảo người dùng hoặc vai trò IAM bạn đang sử dụng có quyền truy cập và quản lý Amazon ECR, chẳng hạn như **ecr:GetAuthorizationToken**, **ecr:BatchCheckLayerAvailability**
  
+ Nếu bạn đang sử dụng một vai trò IAM cụ thể cho **CodeBuild**, hãy xác minh rằng vai trò đó có đính kèm các chính sách cần thiết để tương tác với cả **CodeBuild** và **ECR**.

![IAMrole](/images/2-prerequisites/IAMrole2.png) 
