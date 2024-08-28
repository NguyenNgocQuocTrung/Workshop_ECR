---
title : "Overview"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---

**AWS CodeBuild** is a fully managed continuous integration service that compiles source code, runs tests, and produces software packages ready for deployment. With CodeBuild, there’s no need to provision, manage, and scale your own build servers. CodeBuild scales automatically and processes multiple builds concurrently, so your builds are not left waiting in a queue.

Key Features:

+ Fully Managed: AWS CodeBuild is fully managed, which means AWS takes care of provisioning and scaling the infrastructure needed to run your builds.
+ Scalable: CodeBuild scales up and down automatically based on the number of builds, ensuring quick and efficient processing.
+ Customizable: You can use custom build environments to run CodeBuild projects in your own containerized environments, which can include custom software and configuration.


**Docker** is an open-source platform designed to automate the deployment of applications inside lightweight, portable containers. Containers include the application and all its dependencies, ensuring that the application will run the same regardless of the environment.

Key Concepts:

+ Containers: Standardized units of software that package up code and all its dependencies.
+ Images: Read-only templates that define the environment within which your application runs.
+ Dockerfile: A text file that contains all the commands to assemble a Docker image.


**Amazon Elastic Container Registry (ECR)** is a fully managed Docker container registry that makes it easy for developers to store, manage, and deploy Docker container images. ECR integrates with Amazon ECS, simplifying the development to production workflow.

Key Benefits:

+ Fully Managed: ECR takes care of operating and scaling the infrastructure required for container image storage.
+ Secure: Images are encrypted at rest, and IAM policies can control access to the images.
+ Integrated: Seamless integration with other AWS services like ECS, Fargate, and CodeBuild.
  
**Use Case:**

ECR is often used in conjunction with AWS CodeBuild to automate the process of building Docker images from source code stored in a version control system like GitHub, and then pushing the built images to ECR for deployment.


