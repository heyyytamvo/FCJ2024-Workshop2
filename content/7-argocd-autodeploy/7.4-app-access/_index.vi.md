---
title : "Truy cập Application"
date :  "`r Sys.Date()`" 
weight : 4
chapter : false
pre : " <b> 7.4. </b> "
---

### Truy cập Application

Thông qua Load Balancer, truy cập Application của ta như hình bên dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.4-app-access/ArgoCD_Deploy5.png)

Thực hiện request đến Info Service, ta sẽ nhận được kết quả như bên dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.4-app-access/ArgoCD_Deploy6.png)

### Dev Team Debug với EFK Stack


Tại đường dẫn `domain.com/get-orders`, nếu thực hiện load nhiều lần, ta sẽ có lỗi như hình bên dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.4-app-access/ArgoCD_Deploy7.png)

Vấn đề đã xảy ra, chúng ta có bugs và cần fix sớm nhất có thể. Rất may là ta đã dùng EFK Stack để centralized các logs tại một nơi. Thông qua Kibana, Dev Team có thể biết được logs của các pods như bên dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.4-app-access/ArgoCD_Deploy8.png)

Đây chính là do ta chưa implement các Queue để các Service giao tiếp với nhau khi chúng đang giao tiếp với cơ chế bất đồng bộ (asynchronous). Quả thật, triển khai một ứng dụng Microservices không hề dễ dàng.