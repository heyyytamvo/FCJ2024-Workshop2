---
title : "Cấu hình Argo CD"
date :  "`r Sys.Date()`" 
weight : 4 
chapter : false
pre : " <b> 4.4. </b> "
---
{{% notice info %}}
Source code tại phần này sẽ được triển khai tại Ops Repo
{{% /notice %}}

Tại Ops Repository, tạo Folder `argocd` với các files tại [đây](https://github.com/heyyytamvo/FCJ2024-WS2-OpsRepo/tree/main/argocd). Sơ qua, với các File như hình dưới, Argo CD sẽ đựơc deployed trong namespace `argocd`:

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.4-argocd-autodeploy/argo.png)