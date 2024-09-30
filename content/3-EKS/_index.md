---
title : "Deploy Kubernetes Cluster"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 3. </b> "
---

{{% notice info %}}
Working with Ops Repo in this section
{{% /notice %}}

In this section, we will deploy the Kubernetes Cluster, where our microservices application operating. Next, we will create Elastic Container Registry, which serves as a *private Docker hub*.


After finishing this section, we will have the completed infrastructure as below:

![ConnectPrivate](/images/1.Intro/00problem.png) 

### Content

- [Role for EKS Cluster](3.1-eks-role/) 
- [Role for EKS Worker Node](3.2-eks-worker-role/) 
- [Create EKS Cluster](3.3-eks-create/) 
- [Create EKS Worker Node](3.4-eks-worker-node-create/) 
- [Create Elastic Container Registry](3.5-ecr/) 
- [Run Terraform](3.6-run-terraform/) 
