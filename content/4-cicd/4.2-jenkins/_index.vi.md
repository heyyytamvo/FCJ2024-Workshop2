---
title : "Cấu hình Jenkins Server"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 4.2. </b> "
---

### Cài đặt các Plugins và Tools cần thiết 

Truy cập Jenkins Server thông qua Domain Name của Jenkins Server EC2, ta sẽ được yêu cầu nhập Initial Password. Kết nối đến Jenkins Server thông qua giao thức SSH và thực hiện câu lệnh sau để lấy Initial Password:

```sh
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.2-jenkins/0_Jenkins.png)

Thực hiện cài đặt các Suggested Plugins như hình dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.2-jenkins/1_Jenkins.png)

Tạo admin user như hình dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.2-jenkins/2_Jenkins.png)

Tại phần `Dashboard > Manage Jenkins > Plugins`, cài đặt các Plugins ở bên dưới:

- Docker Pipeline
- Amazon ECR
- SonarQube Scanner 

Tại phần `Dashboard > Manage Jenkins > Tools`, cài đặt **SonarQube Scanner** như hình bên dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.2-jenkins/3_Jenkins.png)

### Thiết Lập Credentials

Tại phần: `Dashboard > Manage Jenkins > Credentials > System > Global credentials (unrestricted)`, tạo các credentials như hình bên dưới, trong đó:

- aws-cre: Gồm Access Key và Secret của AWS Account
- DB_HOST: Endpoint của Database Server
- DB_PORT: Port để connect với Database (3306 hoặc 5432)
- DB_USERNAME: Username để login vào Database
- DB_PASSWORD: Password để login vào Database
- DB_DATABASE: Tên của Database


![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.2-jenkins/4_Jenkins.png)

### Thiết lập các CI Pipelines

Thiết lập Pipeline cho `Service API Gateway` như hình bên dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.2-jenkins/5_Jenkins.png)

Tại phần Build Triggers, chọn **GitHub hook trigger for GITScm polling** như hình dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.2-jenkins/6_Jenkins.png)

Tại phần Pipeline, sửa như cấu hình bên dưới để kết nối đến GitHub Repository. Vì hiện tại Repository đang ở public, nên ta sẽ bỏ qua phần Credentials.

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.2-jenkins/7_Jenkins.png)

Thiết lập Branch **main** như hình bên dưới. Pipeline chỉ chạy khi có bất kỳ sự thay đổi nào ở branch **main**.

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.2-jenkins/8_Jenkins.png)

Ở phần **Script Path**, sửa thành `api-gateway/Jenkinsfile` như hình dưới. Mỗi lần folder `api-gateway` thay đổi, Jenkins Server sẽ dựa vào file `api-gateway/Jenkinsfile` để bắt đầu chạy Pipeline.

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.2-jenkins/9_Jenkins.png)

Thiết lập Pipeline cho `Info Service` và `Order Service` cũng sẽ tương tự như trên. Tuy nhiên, tại phần **Script Path** ta sẽ thay đổi lần lượt thành `info/Jenkinsfile` và `order/Jenkinsfile`.
