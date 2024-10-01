---
title : "Cấu hình EFK Stack"
date :  "`r Sys.Date()`" 
weight : 6 
chapter : false
pre : " <b> 4.6. </b> "
---

{{% notice info %}}
Source code tại phần này sẽ được triển khai tại Ops Repo
{{% /notice %}}

Tại Ops Repository, tạo Folder `EFK` với các files tại [đây](https://github.com/heyyytamvo/FCJ2024-WS2-OpsRepo/tree/main/EFK). Sơ qua, với các File như hình dưới,  EFK Stack sẽ được sẽ được deployed trong namespace `efklog`:

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.6-EFK/EFK.png)