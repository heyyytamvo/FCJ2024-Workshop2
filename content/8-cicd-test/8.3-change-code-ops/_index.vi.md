---
title : "Thay đổi Source Code ở Ops Repo"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 8.3. </b> "
---

Bạn đọc tham khảo Ops Repository tại [đây](https://github.com/heyyytamvo/FCJ2024-WS2-OpsRepo/tree/main). Tại Jenkinsfile, chỉnh sửa `PRODUCTION_LINK` như bên dưới. Đây sẽ là đường liên kết để OWASP ZAP tiến hành kiểm tra lỗ hổng bảo mật.

![ConnectPrivate](/images/8-cicd-test/8.3-change-code-ops/OWASP_0.png)

Tại file `k8s/deployment.yaml`, sửa image của API Gateway như hình bên dưới:

![ConnectPrivate](/images/8-cicd-test/8.3-change-code-ops/UpdateK8s.png)

Đẩy source code lên Remote Github Repository để chạy DevSecOps Pipeline và Argo CD Auto Application Update.