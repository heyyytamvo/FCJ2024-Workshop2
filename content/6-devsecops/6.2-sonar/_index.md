---
title : "Configure SonarQube Server"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 6.2. </b> "
---

### Login SonarQube Server

Access the SonarQube Server via EC2 DNS, you will be required to login to SonarQube Server with username (`admin`) and password (`admin`)

![ConnectPrivate](/images/6-devsecops/6.2-sonar/sonar0.png)

### Create Local Project

Create Local Project as the picture below:

![ConnectPrivate](/images/6-devsecops/6.2-sonar/sonar1.png)

Naming Local Project `microservice` as below:

![ConnectPrivate](/images/6-devsecops/6.2-sonar/sonar2.png)

### Create Sonar File at Dev Repository

At `Dev Repository`, create file `sonar-project.properties` as below:

```properties
sonar.projectKey=microservice
```

### Create Token to access SonarQube Server

At `Administration > Security > Users`, with user admin, create a Token for Admin as below.

![ConnectPrivate](/images/6-devsecops/6.2-sonar/sonar3.png)

{{% notice info %}}
This is not best practice because we gave the Admin Rights to Jenkins Server.
{{% /notice %}}