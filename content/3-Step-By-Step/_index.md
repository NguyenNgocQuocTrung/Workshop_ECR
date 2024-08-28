---
title : "Step-By-Step "
date : "`r Sys.Date()`"
weight : 2
chapter : false
pre : " <b> 3. </b> "
---


### Add Dockerfile
+ In your repository, create a new file named Dockerfile in the root directory.
+ You can copy my simple Dockerfile to build Nodejs image
  
 ![Dockerfile](/images/3-stepbystep/Dockerfile.png)

 ### Build Yaml

 ![yaml](/images/3-stepbystep/yaml.png)


#### 1. Pre-build Phase
 **aws ecr get-login-password --region ap-southeast-2 | docker login --username AWS --password-stdin 590183925097.dkr.ecr.ap-southeast-2.amazonaws.com:**

+ Retrieves the authentication token for logging into ECR and logs Docker into the ECR registry in the ap-southeast-2 region.
  
+ 590183925097.dkr.ecr.ap-southeast-2.amazonaws.com is the ECR repository URL. 

**REPOSITORY_URI=590183925097.dkr.ecr.ap-southeast-2.amazonaws.com/test:**
 Sets the repository URI in the ECR to the REPOSITORY_URI variable. **You can change your RepoURL here**

#### 2. Build Phase

**echo Build started on** date: Outputs a message indicating when the build started.

**docker build --platform linux/amd64 -t $REPOSITORY_URI .:**

+ Initiates the Docker build process using the Dockerfile in the current directory.
+ The --platform linux/amd64 option ensures the image is built for the x86_64 architecture.
+ Tags the image as latest.
  

**docker tag $REPOSITORY_URI $REPOSITORY_URI:$IMAGE_TAG:**

+ Tags the newly built Docker image with the IMAGE_TAG generated in the pre_build phase.

#### 3. Post-build Phase


**docker push $REPOSITORY_URI:**

Pushes the Docker image with the latest tag to Amazon ECR.

**docker push $REPOSITORY_URI:$IMAGE_TAG:**

Pushes the Docker image with the IMAGE_TAG to Amazon ECR.

**printf '[{"name":"simple-app","imageUri":"%s"}]' $REPOSITORY_URI:$IMAGE_TAG > imagedefinitions.json:**

Creates an imagedefinitions.json file containing information about the Docker image that was built. This file can be used by other services, such as ECS (Elastic Container Service), for deploying the container.

**cat imagedefinitions.json:**

Outputs the contents of the imagedefinitions.json file to verify that it has been created correctly.

#### 4. Artifacts
**files: imagedefinitions.json:**
Specifies that the imagedefinitions.json file will be stored as an artifact after the build completes. This artifact can be used in subsequent steps of a CI/CD pipeline.


### Run the Build

#### 1. Commit and Push

Commit the "buildspec.yml" file to your github repository

#### 2. Start the Build

+ Go back to your CodeBuild project in the AWS Management Console.
+ Click on Start build to trigger the build process.
  
  ![build](/images/3-stepbystep/build.png)

#### 3. Monitor the Build

+ Monitor the build progress in the AWS CodeBuild console.
+ Check the logs to ensure everything is running smoothly.
  ![monitor](/images/3-stepbystep/monitor.png)
  
#### 4. Verify Docker Image in ECR:
+ After the build completes, go to the Amazon ECR console.
+ Verify that the Docker image has been pushed to the repository.
  ![image](/images/3-stepbystep/iamge.png)

+ Now whenever you commit code, the pipeline process will run automatically

#### 5. Clean Up Resources

+ Remove ECR Repository:
If you no longer need the ECR repository, delete it to avoid incurring charges.

+ Delete CodeBuild Project:
Delete the CodeBuild project if it's no longer required.

+ Revoke IAM Permissions:
Adjust or remove IAM roles and permissions to follow the principle of least privilege.
