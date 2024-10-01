---
title : "Configure Jenkins Server"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 6.3. </b> "
---

### Configure SonarQube Server

Back to Jenkins Server, at **Credentials**, adding a new credential for Sonar Server with the created Token in the previous section. Creating a new credential as the picture below:

![ConnectPrivate](/FCJ2024-Workshop2/images/6-devsecops/6.2-sonar/sonar4.png)

Go to `Dashboard > Manage Jenkins > System`, at the **SonarQube servers**, adding a new setting as below:

![ConnectPrivate](/FCJ2024-Workshop2/images/6-devsecops/6.2-sonar/sonar5.png)

### Create Ops Pipeline

Create `Ops Pipeline` as what we did for `Service API Gateway Pipeline`, however, GitHub Repository is the URL directing us to our remote Ops Repository.