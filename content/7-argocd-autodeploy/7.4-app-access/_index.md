---
title : "Access the Application"
date :  "`r Sys.Date()`" 
weight : 4 
chapter : false
pre : " <b> 7.4. </b> "
---

### Access the Application

Via Load Balancer, access the application as below:

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.4-app-access/ArgoCD_Deploy5.png)

Makine a request to Info Service, we will receive the response as below:

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.4-app-access/ArgoCD_Deploy6.png)

### EFK Stack for debugging

At the URL `domain.com/get-orders`, sometimes, we will receive the error as below:

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.4-app-access/ArgoCD_Deploy7.png)

There is an error and we need to fix it as soon as possible. Fortunately, we used EFK Stack to centralize all logs at one place. Via Kibana, Development Team can know the logs of all K8s Pods. 


![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.4-app-access/ArgoCD_Deploy8.png)

The issue comes from queue implementation. All the services communicate asynchronously, so we need to implement the queue. Obviously, it is quite complicated to deploy a microservices application.