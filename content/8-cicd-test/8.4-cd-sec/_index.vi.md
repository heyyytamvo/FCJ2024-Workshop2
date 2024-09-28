---
title : "Kiểm tra DevSecOps Pipeline (CD)"
date :  "`r Sys.Date()`" 
weight : 4 
chapter : false
pre : " <b> 8.4. </b> "
---

Tại Jenkins Server, `Ops Pipeline` sẽ được trigger để tiến hành scan Source Code Terraform và dùng OWASP ZAP để kiểm tra bảo mật cho Website của chúng ta.

### Secure IaC

![ConnectPrivate](/images/8-cicd-test/8.4-cd-sec/terraform_0.png)

![ConnectPrivate](/images/8-cicd-test/8.4-cd-sec/terraform_1.png)

### DAST (Dynamic Application Security Testing)

![ConnectPrivate](/images/8-cicd-test/8.4-cd-sec/OWASP_1.png)

![ConnectPrivate](/images/8-cicd-test/8.4-cd-sec/OWASP_2.png)
