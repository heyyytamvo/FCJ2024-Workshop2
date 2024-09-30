---
title : "Triển khai Kubernetes Cluster"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---
{{% notice info %}}
Source code tại phần này sẽ được triển khai tại Ops Repo
{{% /notice %}}

Tại phần này, ta sẽ triển khai cụm Kubernetes Cluster, cũng chính là nơi mà application sẽ được deployed. Thêm vào đó, ta cũng sẽ tạo Elastic Container Registry, nơi đây sẽ chứa các built image của chúng ta.

Kết thúc phần này, ta sẽ có hoàn chỉnh phần Infrastructure, việc còn lại là triển khai CI/CD Pipeline và DevSecOps. Hình bên dưới sẽ là hạ tầng của chúng ta sau khi hoàn thành phần này.

![ConnectPrivate](/FCJ2024-Workshop2/images/3-EKS/Archi.png)  
### Nội dung

- [Tạo Role cho EKS Cluster](3.1-eks-role/) 
- [Tạo Role cho EKS Worker Node](3.2-eks-worker-role/) 
- [Tạo EKS Cluster](3.3-eks-create/)
- [Tạo EKS Worker Node](3.4-eks-worker-node-create/) 
- [Tạo Elastic Container Registry](3.5-ecr/) 
- [Chạy Terraform để triển khai hạ tầng](3.6-run-terraform/) 