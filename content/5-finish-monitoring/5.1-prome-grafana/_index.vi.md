---
title : "Set up Prometheus và Grafana"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 5.1. </b> "
---

### Đăng nhập vào Grafana

Truy cập DNS của Grafana, bạn đọc đăng nhập với tài khoản và mật khẩu như bên dưới:

![ConnectPrivate](/images/5-finish-monitoring/5.1-prome-grafana/pro_gra_0.png)

Kế đến, bạn đọc thay đổi mật khẩu theo yêu cầu của Grafana

### Tạo Data Source

Chọn phần `Connections > Data Sources` như bên dưới để tạo data source:

![ConnectPrivate](/images/5-finish-monitoring/5.1-prome-grafana/pro_gra_1.png)

Lựa chọn Prometheus làm Data Source như bên dưới:

![ConnectPrivate](/images/5-finish-monitoring/5.1-prome-grafana/pro_gra_2.png)

{{% notice info %}}
Prometheus Server URL sẽ là: `http://prometheus-operator-kube-p-prometheus.monitoring.svc.cluster.local:9090`
{{% /notice %}}

### Tạo Dashboard

Tại phần `Home > Dashboards > Import Dashboard`, tạo Dashboard với cấu hình như bên dưới:

![ConnectPrivate](/images/5-finish-monitoring/5.1-prome-grafana/pro_gra_3.png)

Chọn Data Source là *Prometheus* như bên dưới:

![ConnectPrivate](/images/5-finish-monitoring/5.1-prome-grafana/pro_gra_4.png)

### Kiểm tra Metrics của các Worker Nodes

Sau khi hoàn tất tạo Dashboard, ta sẽ thu thập được system metrics của các Worker Node như hình bên dưới. Worker Nodes trong K8s Cluster của chúng ta là 3 EC2 Instance nằm ở private subnet với địa chỉ IP như bên dưới:

#### EC2 (1) với private IP là `10.0.4.56`

![ConnectPrivate](/images/5-finish-monitoring/5.1-prome-grafana/pro_gra_5.png)
#### EC2 (2) với private IP là `10.0.5.114`

![ConnectPrivate](/images/5-finish-monitoring/5.1-prome-grafana/pro_gra_6.png)
#### EC2 (3) với private IP là `10.0.6.202`
![ConnectPrivate](/images/5-finish-monitoring/5.1-prome-grafana/pro_gra_7.png)