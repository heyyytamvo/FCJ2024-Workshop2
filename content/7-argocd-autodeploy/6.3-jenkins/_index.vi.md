---
title : "Cấu hình Jenkins Server"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 6.3. </b> "
---

Quay trở về Jenkins Server, tại phần **Credentials**, thêm vào một credential cho Sonar với Token mà ta lấy được ở phần trước. Tạo một credential như hình dưới:

![ConnectPrivate](/images/6-devsecops/6.2-sonar/sonar4.png)

Tại phần `Dashboard > Manage Jenkins > System`, ở mục **SonarQube servers**, thêm vào cấu hình bên dưới:

![ConnectPrivate](/images/6-devsecops/6.2-sonar/sonar5.png)