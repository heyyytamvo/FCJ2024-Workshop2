---
title : "Set up EFK Stack"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 5.2. </b> "
---

### Access Kibana 

Access the DNS of Kibana, choose `Explore on my own` as the picture below:

![ConnectPrivate](/FCJ2024-Workshop2/images/5-finish-monitoring/5.2-efk/efk_0.png)

### Set up Index Pattern

At `Management > Index Patterns > Create Index Pattern`, create the configuration as below:

![ConnectPrivate](/FCJ2024-Workshop2/images/5-finish-monitoring/5.2-efk/efk_1.png)

![ConnectPrivate](/FCJ2024-Workshop2/images/5-finish-monitoring/5.2-efk/efk_2.png)

### Check Kibana


Go to the homepage of Kibana, we will collect all logs from the K8s Pods as the picture below:

![ConnectPrivate](/FCJ2024-Workshop2/images/5-finish-monitoring/5.2-efk/efk_3.png)