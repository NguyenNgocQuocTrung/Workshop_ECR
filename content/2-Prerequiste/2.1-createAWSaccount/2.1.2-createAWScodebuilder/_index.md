---
title : "Create AWS Code Builder"
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 2.1.2 </b> "
---


###  AWS CodeBuild Permissions

+ You need to have an IAM user with sufficient permissions to create and manage IAM roles, especially the service role for AWS CodeBuild.

![ContainerFullAccess](/images/2-prerequisites/IAMrole1.png) 

+ If you don't have that permissions, click **Add permissions** -> search **Container** and choose **AmazonEC2ContainerRegistryFullAccess**


### Create AWS CodeBuild 

+ Search **CodeBuild** and go to **Build projects** -> **create build project**

+ In **Source** you can choose many Repositories for your options, in this workshop i will guide you Github
+ You can tick repository in my GitHub account if you connected to your Github, here I choose Public repository and paste my Github Link on **Repository URL**

![Source](/images/2-prerequisites/Source.png)

+ Choose **Amazon Linux**
![Source](/images/2-prerequisites/AL.png)


+ In this step, note that the primary function of **buildspec.yml** is to specify the commands that should be run at each phase of the build process, such as installing dependencies, building the application, running tests, and packaging the output.

![BuildSpec](/images/2-prerequisites/BuildSpec.png)


+ You can also create group name of the logs to see logs

![Logs](/images/2-prerequisites/CloudWatch.png)
