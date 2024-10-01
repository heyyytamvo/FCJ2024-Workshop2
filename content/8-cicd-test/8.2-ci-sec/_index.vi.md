---
title : "Kiểm tra DevSecOps Pipeline (CI)"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 8.2. </b> "
---

#### SAST (Static Application Security Testing)

Tại Jenkins Server, ta thấy trong Pipeline của ta có phần `SonarQube Analysis Source Code` như bên dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/8-cicd-test/8.2-ci-sec/CI_Pipeline_Sec0.png)

Kiểm tra tại Sonar Server, ta sẽ có được kết quả sau khi Scan Source Code. Vulnerabilities không nhiều vì Application của ta khá đơn giản:

![ConnectPrivate](/FCJ2024-Workshop2/images/8-cicd-test/8.2-ci-sec/CI_Pipeline_Sec1.png)

Bên dưới là các kết quả khác:

![ConnectPrivate](/FCJ2024-Workshop2/images/8-cicd-test/8.2-ci-sec/CI_Pipeline_Sec2.png)

#### Image Scan

Tại Jenkins Server, ta thấy trong Pipeline của ta có phần `Scan Image` như bên dưới:

![ConnectPrivate](/FCJ2024-Workshop2/images/8-cicd-test/8.2-ci-sec/CI_Pipeline_Sec3.png)

Bên dưới là kết quả sau khi scan Built Image:

![ConnectPrivate](/FCJ2024-Workshop2/images/8-cicd-test/8.2-ci-sec/CI_Pipeline_Sec4.png)

