---
title : "Các bước cụ thể "
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 3. </b> "
---


### Thêm Dockerfile
+ Trong repo của bạn, tạo một tệp mới có tên Dockerfile trong thư mục gốc.
+ Bạn có thể copy Dockerfile đơn giản của mình để build Nodejs image


![Dockerfile](/images/3-stepbystep/Dockerfile.png)

 ### Build Yaml

 ![yaml](/images/3-stepbystep/yaml.png)


#### 1. Giai đoạn Pre-build 

 **aws ecr get-login-password --region ap-southeast-2 | docker login --username AWS --password-stdin 590183925097.dkr.ecr.ap-southeast-2.amazonaws.com:**

+ Truy xuất mã thông báo xác thực để đăng nhập vào ECR và ghi Docker logs vào ECR registry ở vùng ap-southeast-2.
  
+ 590183925097.dkr.ecr.ap-southeast-2.amazonaws.com là đường dẫn ECR repository. 

**REPOSITORY_URI=590183925097.dkr.ecr.ap-southeast-2.amazonaws.com/test:**
  Đặt URI repository trong ECR thành biến REPOSITORY_URI. **Bạn có thể thay đổi đường dẫn Repo ở đây**


#### 2. Giai đoạn Build 

**echo Build started on** date: Xuất ra thông báo cho biết thời điểm quá trình build bắt đầu.

**docker build --platform linux/amd64 -t $REPOSITORY_URI .:**
  
+ Bắt đầu quá trình build Docker bằng Dockerfile trong thư mục hiện tại.
+ Tùy chọn --platform linux/amd64 đảm bảo image được xây dựng cho kiến ​​trúc x86_64.
+ Tag image là mới nhất.
  
**docker tag $REPOSITORY_URI $REPOSITORY_URI:$IMAGE_TAG:**

+ Gắn image Docker mới được build với IMAGE_TAG được tạo trong giai đoạn pre_build.



#### 3. Giai đoạn Post-build 


**docker push $REPOSITORY_URI:**

+ Đẩy Docker image có thẻ mới nhất lên Amazon ECR.

**docker push $REPOSITORY_URI:$IMAGE_TAG:**

+ Đẩy Docker image có IMAGE_TAG tới Amazon ECR.

**printf '[{"name":"simple-app","imageUri":"%s"}]' $REPOSITORY_URI:$IMAGE_TAG > imagedefinitions.json:**

Tạo tệp imagedef địnhs.json chứa thông tin về Docker image đã được tạo. Tệp này có thể được sử dụng bởi các dịch vụ khác, chẳng hạn như ECS (Dịch vụ vùng chứa đàn hồi), để triển khai vùng chứa.

**cat imagedefinitions.json:**

Xuất nội dung của tệp imagedef địnhs.json để xác minh rằng nó đã được tạo chính xác.

#### 4. Artifacts
**files: imagedefinitions.json:**
Chỉ định rằng tệp imagedef địnhs.json sẽ được lưu trữ dưới dạng atifact sau khi quá trình xây dựng hoàn tất. Artifact này có thể được sử dụng trong các bước tiếp theo của quy trình CI/CD.


### Run the Build

#### 1. Commit and Push

Commit "buildspec.yml" file len github repository

#### 2. Bắt đầu quá trình Build

+ Quay lại dự án CodeBuild của bạn trong Bảng điều khiển quản lý AWS.
+ Click vào Start build để kích hoạt quá trình build.
  
  ![build](/images/3-stepbystep/build.png)

#### 3. Giám sát quá trìnhBuild

+ Theo dõi tiến trình build trong bảng điều khiển AWS CodeBuild.
+ Kiểm tra nhật ký để đảm bảo mọi thứ đều hoạt động trơn tru.
  ![monitor](/images/3-stepbystep/monitor.png)
  
#### 4. Xác nhận Docker Image ở ECR:
+ Sau khi quá trình xây dựng hoàn tất, hãy chuyển đến bảng điều khiển Amazon ECR.
+ Xác minh Docker image đã được đẩy vào kho lưu trữ.
  ![image](/images/3-stepbystep/iamge.png)

+ Bây giờ bất cứ khi nào bạn commit code, quá trình pipeline sẽ tự động chạy

#### 5. Xóa tài nguyên (tùy ý )

+ Xóa ECR repository:
Nếu bạn không cần ECR repository nữa, hãy xóa nó để tránh phát sinh phí.

+ Xóa dự án CodeBuild:
Xóa dự án CodeBuild nếu nó không còn cần thiết nữa.

+ Thu hồi quyền IAM:
Điều chỉnh hoặc xóa vai trò và quyền IAM để tuân theo nguyên tắc đặc quyền tối thiểu.

