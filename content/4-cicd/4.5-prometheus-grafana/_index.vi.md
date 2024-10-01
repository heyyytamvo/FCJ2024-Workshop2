---
title : "Cấu hình Prometheus và Grafana"
date :  "`r Sys.Date()`" 
weight : 5 
chapter : false
pre : " <b> 4.5. </b> "
---

{{% notice info %}}
Source code tại phần này sẽ được triển khai tại Ops Repo
{{% /notice %}}

Tại Ops Repository, tạo Folder `monitoring` với các files tại [đây](https://github.com/heyyytamvo/FCJ2024-WS2-OpsRepo/tree/main/monitoring). Sơ qua, với các File như hình dưới, Grafana sẽ được sẽ được deployed trong namespace `monitoring`:

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.5-prometheus-grafana/grafana.png)

{{% notice note %}}
Ta sẽ triển khai Prometheus ở phần Bash Scripting, hiện tại, đây chỉ là những file cấu hình và chúng chưa được deploy lên K8s.
{{% /notice %}}