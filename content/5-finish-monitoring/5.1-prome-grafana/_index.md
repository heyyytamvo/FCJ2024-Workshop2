---
title : "Set up Prometheus and Grafana"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 5.1. </b> "
---

### Login Grafana

Access the DNS of Grafana, you will be required to login with username and password as below:


![ConnectPrivate](/FCJ2024-Workshop2/images/5-finish-monitoring/5.1-prome-grafana/pro_gra_0.png)

Next, you need to change the password of Grafana

### Create Data Source

Choosing `Connections > Data Sources` as below to create Data Source:

![ConnectPrivate](/FCJ2024-Workshop2/images/5-finish-monitoring/5.1-prome-grafana/pro_gra_1.png)

Choosing Prometheus as Data Source:

![ConnectPrivate](/FCJ2024-Workshop2/images/5-finish-monitoring/5.1-prome-grafana/pro_gra_2.png)

{{% notice info %}}
Prometheus Server URL is: `http://prometheus-operator-kube-p-prometheus.monitoring.svc.cluster.local:9090`
{{% /notice %}}

### Create Dashboard

At `Home > Dashboards > Import Dashboard`, create Dashboard with settings as below:

![ConnectPrivate](/FCJ2024-Workshop2/images/5-finish-monitoring/5.1-prome-grafana/pro_gra_3.png)

Choosing Data Source *Prometheus* as below:

![ConnectPrivate](/FCJ2024-Workshop2/images/5-finish-monitoring/5.1-prome-grafana/pro_gra_4.png)

### Check Metrics of Worker Nodes

After creating Dashboard, we will collect all system metrics of Worker Node as the picture below. In our K8s Cluster, Worker Nodes are 3 EC2 Instances with private IP as below:

#### EC2 (1) with private IP `10.0.4.56`

![ConnectPrivate](/FCJ2024-Workshop2/images/5-finish-monitoring/5.1-prome-grafana/pro_gra_5.png)
#### EC2 (2) with private IP `10.0.5.114`

![ConnectPrivate](/FCJ2024-Workshop2/images/5-finish-monitoring/5.1-prome-grafana/pro_gra_6.png)
#### EC2 (3) with private IP `10.0.6.202`
![ConnectPrivate](/FCJ2024-Workshop2/images/5-finish-monitoring/5.1-prome-grafana/pro_gra_7.png)