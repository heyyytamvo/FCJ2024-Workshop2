---
title : "Changing Source Code at Ops Repository"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 8.3. </b> "
---
Please refer to this [Ops Repository](https://github.com/heyyytamvo/FCJ2024-WS2-OpsRepo/tree/main). At Jenkinsfile, modify the `PRODUCTION_LINK` as below. The OWASP ZAP will scan the website at `PRODUCTION_LINK` to check the security risks.

![ConnectPrivate](/images/8-cicd-test/8.3-change-code-ops/OWASP_0.png)

At file `k8s/deployment.yaml`, modify image of API Gateway as the picture below:

![ConnectPrivate](/images/8-cicd-test/8.3-change-code-ops/UpdateK8s.png)


Push everything to Remote Github Repository to trigger DevSecOps Pipeline and Argo CD Auto Application Update.