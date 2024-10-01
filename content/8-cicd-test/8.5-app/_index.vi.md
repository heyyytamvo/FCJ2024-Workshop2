---
title : "Kiểm tra Application Auto Update"
date :  "`r Sys.Date()`" 
weight : 5 
chapter : false
pre : " <b> 8.5. </b> "
---

### Old Version

Trước khi commit ở Ops Repository, bên dưới là application của ta:

![ConnectPrivate](/FCJ2024-Workshop2/images/8-cicd-test/8.5-app/update_0.png)

### New Version

Tại Argo CD, ta có thể thấy **API Gateway Pods** đang được cập nhật như hình bên dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/8-cicd-test/8.5-app/update_1.png)

Cuối cùng, tại trang Production của ta đã được cập nhật với phiên bản mới nhất:

![ConnectPrivate](/FCJ2024-Workshop2/images/8-cicd-test/8.5-app/update_2.png)