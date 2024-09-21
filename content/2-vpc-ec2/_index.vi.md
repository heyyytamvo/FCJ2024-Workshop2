---
title : "Triển khai VPC, Jenkins, và SonarQube Server"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---

{{% notice note %}}
Bạn đọc cần cài đặt Terraform trước khi có thể hoàn thành bài Workshop này
{{% /notice %}}
{{% notice info %}}
Source code tại phần này sẽ được triển khai tại Ops Repo
{{% /notice %}}


Trong phần này, chúng ta sẽ triển khai một VPC với:
- 3 Availability Zones
- 3 Public Subnets
- 3 Private Subnets
- 1 Internet Gateway
- 1 NAT Gateway
- 3 EC2, trong đó:
   - 1 Jump Host để tương tác với cụm K8s ở private subnet 
   - 1 Jenkins Server để triển khai CI pipeline
   - 1 SonarQube Server trong quy trình DevSecOps



### Nội dung
  - [Triển khai VPC](2.1-basic/)
  - [Tạo Jump Host, Jenkins Server, và SonarQube Server](2.2-createalb-asg-ecs/)