---
title : "Triển khai Kubernetes Cluster"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---

Tại phần này, ta sẽ triển khai cụm Kubernetes Cluster, cũng chính là nơi mà application sẽ được deployed. Thêm vào đó, ta cũng sẽ tạo Elastic Container Registry, nơi đây sẽ chứa các built image của chúng ta.

Kết thúc phần này, ta sẽ có hoàn chỉnh phần Infrastructure, việc còn lại là triển khai CI/CD Pipeline và DevSecOps. Hình bên dưới sẽ là hạ tầng của chúng ta sau khi hoàn thành phần này.

### Nội dung

- [Tạo Role cho EKS Cluster](3.1-connect-bastion/) 
- [Tạo Role cho EKS Worker Node](3.2-scaling-check/) 
- [Tạo EKS Cluster](3.2-scaling-check/) 
- [Tạo EKS Worker Node](3.2-scaling-check/) 
- [Tạo Elastic Container Registry](3.2-scaling-check/) 
- [Chạy Terraform để triển khai hạ tầng](3.2-scaling-check/) 