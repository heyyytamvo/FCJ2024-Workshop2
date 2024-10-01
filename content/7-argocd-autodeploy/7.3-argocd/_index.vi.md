---
title : "Auto Deployment với Argo CD"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 7.3. </b> "
---

Tại mục `EC2 > Load Balancers`, dùng DNS của Argo CD để truy cập đến trang web của Argo CD. Bạn đọc sẽ được yêu cầu đăng nhập với tài khoản là `admin` và Initial Password. Để lấy được Initial Password của Argo CD, bạn đọc thực hiện câu lệnh sau tại Jump Host (hãy chắc chắn rằng Jump Host có credentials để tương tác với K8s Cluster):

```sh
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

#### Kết nối đến Ops Repository

Sau khi đăng nhập, tại phần `Settings > Repositories`, kết nối đến Ops Repository với cấu hình bên dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.3-argocd/ArgoCD_Deploy0.png)

#### Application Deployment

Tại phần `Applications`, tạo một application mới với cấu hình bên dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.3-argocd/ArgoCD_Deploy1.png)

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.3-argocd/ArgoCD_Deploy2.png)

#### Kiểm tra

Sau khi **Create Application**, Argo CD sẽ tự động deploy các application pods vào K8s Cluster của ta như hình bên dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.3-argocd/ArgoCD_Deploy3.png)

Trở lại AWS Console Management, tại phần `EC2 > Load Balancers`, ta sẽ thấy có một Load Balancer mới được deployed (trước đó chỉ có 3 Load Balancers), đó chính là đường dẫn đến Production của ta.

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.3-argocd/ArgoCD_Deploy4.png)
