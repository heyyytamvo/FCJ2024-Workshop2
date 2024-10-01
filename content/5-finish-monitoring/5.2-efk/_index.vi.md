---
title : "Set up EFK Stack"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 5.2. </b> "
---

### Truy cập vào Kibana thông qua DNS

Thông qua DNS ở phần `EC2 > Load Balancers`, bạn đọc truy cập Kibana và chọn `Explore on my own` như bên dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/5-finish-monitoring/5.2-efk/efk_0.png)

### Set up Index Pattern

Tại phần `Management > Index Patterns > Create Index Pattern`, tạo cấu hình như bên dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/5-finish-monitoring/5.2-efk/efk_1.png)

![ConnectPrivate](/FCJ2024-Workshop2/images/5-finish-monitoring/5.2-efk/efk_2.png)

### Kiểm tra Kibana

Quay lại trang chủ của Kibana, ta sẽ thu thập được toàn bộ Logs như hình bên dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/5-finish-monitoring/5.2-efk/efk_3.png)