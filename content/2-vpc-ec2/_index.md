---
title : "Deploy VPC, Jenkins, and SonarQube Server"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---

{{% notice info %}}
We use Ops Repo in this section
{{% /notice %}}


Trong phần này, chúng ta sẽ triển khai một VPC với:

- 3 Availability Zones
- 3 Public Subnets
- 3 Private Subnets
- 1 Internet Gateway
- 1 NAT Gateway
- 3 EC2, where:
   - 1 Jump Host for interacting with the Kubernetes Cluster
   - 1 Jenkins Server for CI pipeline
   - 1 SonarQube Server for DevSecOps Pipeline



### Content
  - [Create VPC](2.1-basic/)
  - [Create Jump Host, Jenkins Server, and SonarQube Server](2.2-createalb-asg-ecs/)