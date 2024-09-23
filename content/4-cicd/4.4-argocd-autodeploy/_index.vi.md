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

Tại Ops Repository, tạo Folder `argocd` với các files tại [đây](). Sơ qua, với các File như hình dưới, Argo CD sẽ đựơc deployed trong namespace `argocd`:

![ConnectPrivate](/images/4-cicd/4.4-argocd-autodeploy/argo.png)