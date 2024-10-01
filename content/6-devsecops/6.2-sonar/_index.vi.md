---
title : "Cấu hình SonarQube Server"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 6.2. </b> "
---

### Đăng nhập vào SonarQube Server

Truy cập SonarQube Server thông qua EC2 DNS, bạn đọc đăng nhập vào SonarQube Server với tài khoản và mật khẩu là `admin` như hình bên dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/6-devsecops/6.2-sonar/sonar0.png)

### Tạo Local Project

Tạo Local Project như hình bên dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/6-devsecops/6.2-sonar/sonar1.png)

Đặt tên Local Project là `microservice` như bên dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/6-devsecops/6.2-sonar/sonar2.png)

### Thiết lập Sonar File ở Dev Repository

Tại `Dev Repository`, tạo file `sonar-project.properties` như bên dưới:

```properties
sonar.projectKey=microservice
```

### Tạo Token để truy cập SonarQube Server

Tại mục `Administration > Security > Users`, với user admin, tạo một Token cho Admin như hình bên dưới.

![ConnectPrivate](/FCJ2024-Workshop2/images/6-devsecops/6.2-sonar/sonar3.png)

{{% notice info %}}
Đây không phải là Best Practice vì chúng ta đang trao quyền admin cho Jenkins Server.
{{% /notice %}}