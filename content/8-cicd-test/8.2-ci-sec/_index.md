---
title : "DevSecOps Pipeline (CI)"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 8.2. </b> "
---

#### SAST (Static Application Security Testing)

At Jenkins Server, we can see there is a stage `SonarQube Analysis Source Code` in our pipeline as below:

![ConnectPrivate](/FCJ2024-Workshop2/images/8-cicd-test/8.2-ci-sec/CI_Pipeline_Sec0.png)

At the Sonar Server, we have the scanning result. Because the codebase is still simple, we do not have much vulnerabilities:

![ConnectPrivate](/FCJ2024-Workshop2/images/8-cicd-test/8.2-ci-sec/CI_Pipeline_Sec1.png)

Below are other results:

![ConnectPrivate](/FCJ2024-Workshop2/images/8-cicd-test/8.2-ci-sec/CI_Pipeline_Sec2.png)

#### Image Scan

At Jenkins Server, we can see there is a stage `Scan Image` in our pipeline as below:

![ConnectPrivate](/FCJ2024-Workshop2/images/8-cicd-test/8.2-ci-sec/CI_Pipeline_Sec3.png)

Below is the result after scanning our built image:

![ConnectPrivate](/FCJ2024-Workshop2/images/8-cicd-test/8.2-ci-sec/CI_Pipeline_Sec4.png)