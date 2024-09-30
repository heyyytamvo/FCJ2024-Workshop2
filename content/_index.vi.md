---
title : "Triển khai DevSecOps và ứng dụng GitOps trong CI/CD Pipeline cho ứng dụng Microservices trên AWS EKS"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
---
# Triển khai DevSecOps và ứng dụng GitOps trong CI/CD Pipeline cho ứng dụng Microservices trên AWS EKS


### Tổng quan

Trong bài Workshop này, bạn đọc sẽ tìm hiểu cách thức tích hợp DevSecOps và ứng dụng GitOps vào CI/CD Pipeline cho một ứng dụng Microservice được triển khai trên Amazon Elastic Kubernetes (EKS). Bạn đọc sẽ bắt đầu việc triển khai hạ tầng trên AWS bằng Terraform, triển khai CI/CD Pipeline, và cuối cùng tích hợp các phương pháp bảo mật trong DevOps, hay còn gọi là DevSecOps.

<!-- ![ConnectPrivate](/images/graph.mov)  -->
![ConnectPrivate](/FCJ2024-Workshop2/images/Workshop2.gif)

### Kỳ vọng

#### Kiến trúc hạ tầng Cloud
Bên dưới là toàn bộ kiến trúc cho hạ tầng của chúng ta và các luồng traffic sau khi hoàn thành bài Workshop này

![ConnectPrivate](/FCJ2024-Workshop2/images/Archi.gif)


#### CI Pipeline
CI Pipeline được mô tả như hình bên dưới

![ConnectPrivate](/FCJ2024-Workshop2/images/CI_Pipeline.gif)


#### CD Pipeline
CD Pipeline được mô tả như hình bên dưới

![ConnectPrivate](/FCJ2024-Workshop2/images/CD_Pipeline.gif)


Toàn bộ Source Code cho Workshop này, bạn đọc có thể tham khảo:

+ Dev Repo (Nơi Dev Team sẽ làm việc): [Link](https://github.com/heyyytamvo/FCJ2024-WS2-DevRepo)
+ Ops Repo (Nơi Ops Team sẽ làm việc): [Link](https://github.com/heyyytamvo/FCJ2024-WS2-OpsRepo)

### Nội dung

 1. [Đặt vấn đề](1-Introduce)
 2. [Triển khai VPC, Jenkins, và SonarQube Server](2-vpc-ec2/)
 3. [Triển khai Kubernetes Cluster](3-EKS/)
 4. [Chuẩn bị CI/CD Pipeline](4-cicd/)
 5. [Hoàn thiện Monitoring](5-finish-monitoring/)
 6. [Triển khai DevSecOps](6-devsecops/)
 7. [Application Deployment](7-argocd-autodeploy/)
 8. [Kiểm thử CI/CD Pipeline](8-cicd-test/)

{{% notice info %}}
Tại mỗi phần, bạn đọc sẽ được hướng dẫn nên để Source Code ở Dev Repo hoặc Ops Repo
{{% /notice %}}