---
title : "Configure Prometheus and Grafana"
date :  "`r Sys.Date()`" 
weight : 5 
chapter : false
pre : " <b> 4.5. </b> "
---

{{% notice info %}}
Working with Ops Repo in this section 
{{% /notice %}}



At Ops Repository, create folder `monitoring` with these [files](https://github.com/heyyytamvo/FCJ2024-WS2-OpsRepo/tree/main/monitoring). With all files as below, grafana will be deployed into namespace `monitoring`.

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.5-prometheus-grafana/grafana.png)

{{% notice note %}}
We will deploy Prometheus using Bash Scripting in the next section.
{{% /notice %}}