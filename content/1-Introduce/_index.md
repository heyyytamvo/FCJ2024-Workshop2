---
title : "Problem Definition"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---

### Why Microservices?

Before diving into Microservices, we will get into the traditional software architecture in the deployment stage: Monolithic. Monolithic is a software architecture in which all modules (features/services) are containerized in a single *‘block’*. The most common containerization technology that you may have heard of is Docker. Supposedly your software has already been packaged into a ‘block’ and deployed to the Virtual Private Server (VPS). Now, your development team has released a new feature. Then, your application needs to be updated. With monolithic architecture, the software updating process is demonstrated below:


![ConnectPrivate](/FCJ2024-Workshop2/images/1.Intro/Mono.gif) 

As you can see, you need to shut down the application for a while. Then, a new version will be deployed. In the meantime, end users can not access the application. With business consideration, this is a huge issue: updating a feature affects the entire application. Of course, we can solve the problem by implementing the blue/green deployment strategy, but it is out of scope in this workshop.

There is another software architecture that can handle this problem: Microservices. Microservices apply the theory of divide and conquer: Every service (feature) of the application will be packaged as a single '*block*' (or Image) and they communicate to each other by some standards such as REST, v.v. Updating a feature has no impact on other features as described below:

![ConnectPrivate](/FCJ2024-Workshop2/images/1.Intro/Micro.gif) 

Kubernetes (K8s) is the most common tool for deploying a microservice application because of its utilization in allocating computing resources. In this workshop, we will use Kubernetes to deploy a simple microservices application. However, we will not set up the entire K8s Cluster. Instead, we will use Elastic Kubernetes Service (EKS) from AWS. The infrastructure deployment stage requires a smooth collaboration between the Operations Team (or Ops Team including System Engineer, System Administration, etc.). Hence, GitOps is the key point to guarantee that collaboration. 

### Why GitOps?

### Why DevSecOps?

DevOps practice enhances an organization’s ability to deliver applications by using automation tools. Hence, the amount of required time to release a new feature will be effectively reduced, then:
- End users receive the latest version of the application as soon as possible
- The development team will focus on their tasks since other manual work (building, testing, deploying, etc.) is automated

During the automation process, could we find out some security risks from the source code, built image, or even our production? DevSecOps is the answer to that question. In this workshop, we will integrate some simple DevSecOps techniques such as:
- **SAST (Static Application Security Testing)**: A type of security testing that analyzes our code base before executing the program.
- **Image Scan and Secure IaC**: Scan and detect the vulnerabilities in the built image before deploying it to the production environment. Scan our infrastructure based on the IaC code base.
- **DAST (Dynamic Application Security Testing)**: While SAST analyzes static code, DAST performs security testing while the application is operating.

![ConnectPrivate](/FCJ2024-Workshop2/images/1.Intro/DevSecOps.gif) 

### Monitoring

Suppose you are a developer and our application is deployed in a Kubernetes (K8s) Cluster. One day, the application crashed and you need to fix it as soon as possible. The first thing that comes to your mind is checking the logs. However, you have no idea how to access the K8s Cluster because it is too complicated. Hence, we need to centralize all the application logs in one place. In this workshop, we will deploy a EFK Stack to solve this problem. After the EFK is successfully deployed, developers will use their web browser to read all the application logs. Below is the final practice.

![ConnectPrivate](/FCJ2024-Workshop2/images/1.Intro/Monitor.gif)

In this workshop, we will use these services from Amazon Web Service to solve all the problems above:

- **Elastic Compute Service (EC2)**: Jenkins Server, and SonarQube Server will be hosted here. They played an essential part in our CI/CD Pipeline
- **Elastic Kubernetes Service (EKS)**: Instead of setting up a Kubernetes Cluster, we will use service from AWS
- **Elastic Container Registry (ECR)**: It serves as a “private Docker Registry” where we store our application image.

{{% notice note %}}
You need to install Terraform to finish this Workshop
{{% /notice %}}