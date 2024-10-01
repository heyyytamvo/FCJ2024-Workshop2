---
title : "Auto Deployment with Argo CD"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 7.3. </b> "
---

In AWS Console Management, at `EC2 > Load Balancers`, using DNS of Argo CD to access the website of Argo CD. You will be required to login using the username of `admin` and Initial Password. To get the Initial Password, you will execute this command line at Jump Host (Make sure that AWS Credential is configured to access the K8s Cluster):

```sh
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

#### Connect to Ops Repository

After login, at `Settings > Repositories`, connect to the Ops Repository with setting below:


![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.3-argocd/ArgoCD_Deploy0.png)

#### Application Deployment

At `Applications`, create a new application with the configuration below:

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.3-argocd/ArgoCD_Deploy1.png)

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.3-argocd/ArgoCD_Deploy2.png)

#### Checking

After creating Application, Argo CD will automatically deploy our application to the K8s Cluster as below:

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.3-argocd/ArgoCD_Deploy3.png)

Going back to the AWS Console Management, at `EC2 > Load Balancers`, we will see a new load balancer (3 Load Balancer before). The new load balancer is our application.

![ConnectPrivate](/FCJ2024-Workshop2/images/7-argocd-autodeploy/7.3-argocd/ArgoCD_Deploy4.png)
