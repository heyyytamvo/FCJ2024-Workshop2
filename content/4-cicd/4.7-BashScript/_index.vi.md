---
title : "Bash Script cho Automation Deployment"
date :  "`r Sys.Date()`" 
weight : 7 
chapter : false
pre : " <b> 4.7. </b> "
---

{{% notice info %}}
Source code tại phần này sẽ được triển khai tại Ops Repo
{{% /notice %}}

Chúng ta sẽ dùng bash script để tạo các stack Argo CD, Prometheus, Grafana, và EFK Stack. Tại Ops Repo, tạo file `setup.sh` như bên dưới.

```sh
#!/bin/bash
#set up argo cd
kubectl apply -f argocd/namespace.yaml
kubectl apply -f argocd/default.yaml -n argocd

#set up efk stack
kubectl apply -f EFK/.

#set up Prometheus and Grafana
kubectl create namespace monitoring
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install prometheus-operator prometheus-community/kube-prometheus-stack -n monitoring
kubectl apply -f monitoring/grafana.yaml -n monitoring
```
Bây giờ, Ops Repository của ta đã có hoàn chỉnh như hình:

![ConnectPrivate](/images/4-cicd/4.7-BashScript/tree.png)

Bây giờ, đẩy tất cả mọi thứ lên GitHub Repository với `git push`.

{{% notice note %}}
Folder k8s sẽ không được đề cập ở đây, bạn đọc có thể tham khảo Source Code tại [Ops Repository]() của tôi.
{{% /notice %}}