---
title : "Create IAM role"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 2.1.1 </b> "
---


### Create IAM role 

+ You need to have an IAM user with sufficient permissions to create and manage IAM roles, especially the service role for AWS CodeBuild.
  
+ Ensure the IAM user or role you are using has permissions to access and manage Amazon ECR, such as **ecr:GetAuthorizationToken**, **ecr:BatchCheckLayerAvailability**
  
+ If you are using a specific IAM role for **CodeBuild**, verify that the role has the necessary policies attached to interact with both **CodeBuild** and **ECR**.

![IAMrole](/images/2-prerequisites/IAMrole2.png) 
