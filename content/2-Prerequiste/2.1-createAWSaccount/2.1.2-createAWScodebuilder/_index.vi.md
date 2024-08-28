---
title : "Tạo AWS CodeBuild"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.1.2 </b> "
---


### Quyền của AWS CodeBuild

+ Bạn cần có người dùng IAM có đủ quyền để tạo và quản lý các vai trò IAM, đặc biệt là vai trò dịch vụ cho AWS CodeBuild.

![ContainerFullAccess](/images/2-prerequisites/IAMrole1.png) 

+ Nếu bạn không có quyền đó, hãy nhấp vào **Thêm quyền** -> tìm kiếm **Container** và chọn **AmazonEC2ContainerRegistryFullAccess**


### Tạo AWS CodeBuild 

+ Tìm kiếm **CodeBuild** và vào **Buildprojects** -> **tạo dự án xây dựng**

+ Tại **Source** các bạn có thể chọn nhiều Repositories cho mình lựa chọn, ở workshop này mình sẽ hướng dẫn các bạn Github
+ Bạn có thể đánh dấu vào kho lưu trữ trong tài khoản GitHub của tôi nếu bạn đã kết nối với Github của mình, ở đây tôi chọn Kho lưu trữ công khai và dán Liên kết Github của mình vào **URL kho lưu trữ**

![Source](/images/2-prerequisites/Source.png)

+ Chọn **Amazon Linux**
![Nguồn](/images/2-prerequisites/AL.png)


+ Ở bước này, hãy lưu ý rằng chức năng chính của **buildspec.yml** là chỉ định các lệnh sẽ chạy ở mỗi giai đoạn của quá trình xây dựng, chẳng hạn như cài đặt các phần phụ thuộc, xây dựng ứng dụng, chạy thử nghiệm và đóng gói đầu ra.

![BuildSpec](/images/2-prerequisites/BuildSpec.png)


+ Bạn cũng có thể tạo tên nhóm nhật ký để xem nhật ký

![Nhật ký](/images/2-prerequisites/CloudWatch.png)