---
title : "A Secured CI/CD Pipeline by implementing DevSecOps practice and GitOps principal for a Microservices Application on AWS EKS"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
---
# A Secured CI/CD Pipeline by implementing DevSecOps practice and GitOps principal for a Microservices Application on AWS EKS

### Overview

In this workshop, we will integrate DevSecOps Practice to a CI/CD for an application running on Amazon Elastic Kubernetes Service (EKS). To leverage our DevOps practice, we will apply the GitOps Principle during this workshop. You will begin with provisioning the AWS Infrastructure by Terraform, building a CI/CD Pipeline, and finally, you will integrate the DevSecOps practice to secure our software development life cycle.

![ConnectPrivate](/FCJ2024-Workshop2/images/Workshop2.gif) 

### Expectation

#### Cloud Infrastructure

Below is the final AWS Infrastructure and all the traffic after finishing this workshop.

![ConnectPrivate](/FCJ2024-Workshop2/images/Archi.gif)

#### CI Pipeline
CI Pipeline is described below.

![ConnectPrivate](/FCJ2024-Workshop2/images/CI_Pipeline.gif)


#### CD Pipeline
CD Pipeline is described below

![ConnectPrivate](/FCJ2024-Workshop2/images/CD_Pipeline.gif)

For your preference, below are the repositories.

 1. [Problem Definition](1-Introduce)
 2. [Deploy VPC, Jenkins, and SonarQube Server](2-vpc-ec2/)
 3. [Deploy Kubernetes Cluster](3-EKS/)
 4. [Prepare CI/CD Pipeline](4-cicd/)
 5. [Set up Monitoring](5-finish-monitoring/)
 6. [Integrate DevSecOps](6-devsecops/)
 7. [Application Deployment](7-argocd-autodeploy/)
 8. [Testing CI/CD Pipeline](8-cicd-test/)


### Content

 1. [Problem Definition](1-introduce/)
 2. [Preparation](2-Prerequiste/)
 3. [Scaling Testing](3-Scaling-Check/)
 4. [Cleanup](4-cleanup/)
