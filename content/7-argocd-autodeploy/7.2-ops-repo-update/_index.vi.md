---
title : "Cập nhật Ops Repository"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 7.2. </b> "
---


Ở file `k8s/deployment.yaml` ở Ops Repository, với các Image mà ta có ở Registry, cập nhật image cho từng Service và đẩy lên Remote Ops Repository như bên dưới:

#### Service API Gateway

![ConnectPrivate](/images/7-argocd-autodeploy/7.2-ops-repo-update/updateOps_0.png)

#### Info Service

![ConnectPrivate](/images/7-argocd-autodeploy/7.2-ops-repo-update/updateOps_1.png)

#### Order Service

![ConnectPrivate](/images/7-argocd-autodeploy/7.2-ops-repo-update/updateOps_2.png)
