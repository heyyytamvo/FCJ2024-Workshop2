---
title : "Chạy CI Pipeline"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 7.1. </b> "
---

### Trigger CI Pipeline

Ở Dev Repository, đẩy code lên Github Repository để trigger Jenkins Pipeline:

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.1-ci-pipeline/CI_Pipeline0.png)

Quay trở về Jenkins Server, bạn đọc có thể thấy tổng cộng có 3 pipeline đang chạy.

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.1-ci-pipeline/CI_Pipeline1.png)

Sau một lúc, CI Pipeline đã chạy hoàn thành như bên dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.1-ci-pipeline/CI_Pipeline2.png)

### Kiểm tra Image ở Private Registry

Ở remote Dev Repository, ta thấy lần cuối một commit được đẩy lên có ID `d966430` như bên dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.1-ci-pipeline/CI_Pipeline3.png)

Kiểm tra ở AWS Elastic Container Registry, bạn đọc sẽ thấy ta có tổng cộng 3 Image được tagged theo commit ID:

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.1-ci-pipeline/CI_Pipeline4.png)

Bây giờ, ta đã sẵn sàng dùng Argo CD để triển khai Automation Deployment.