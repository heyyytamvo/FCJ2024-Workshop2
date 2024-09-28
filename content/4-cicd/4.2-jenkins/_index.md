---
title : "Configure Jenkins Server"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 4.2. </b> "
---

### Install Plugins and Tools on Jenkins Server

Access Jenkins Server via the DNS of the Jenkins Server EC2, you will be required to type Initial Password. Connect to Jenkins Server via SSH Protocol and execute this command line to get the Initial Password:

```sh
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

![ConnectPrivate](/images/4-cicd/4.2-jenkins/0_Jenkins.png)

Installing all Suggested Plugins as below:

![ConnectPrivate](/images/4-cicd/4.2-jenkins/1_Jenkins.png)

Create admin user as below:

![ConnectPrivate](/images/4-cicd/4.2-jenkins/2_Jenkins.png)

At `Dashboard > Manage Jenkins > Plugins`, installing these Plugins:

- Docker Pipeline
- Amazon ECR
- SonarQube Scanner 

At `Dashboard > Manage Jenkins > Tools`, installing **SonarQube Scanner** as below:

![ConnectPrivate](/images/4-cicd/4.2-jenkins/3_Jenkins.png)

### Create Credentials

At `Dashboard > Manage Jenkins > Credentials > System > Global credentials (unrestricted)`, create these credentials as below:

- áocd
- ácdc
- ácd
- cálc

![ConnectPrivate](/images/4-cicd/4.2-jenkins/4_Jenkins.png)

### Create CI Pipelines

Create Pipeline for `Service API Gateway` as below:

![ConnectPrivate](/images/4-cicd/4.2-jenkins/5_Jenkins.png)

At Build Triggers, choose **GitHub hook trigger for GITScm polling** as below:

![ConnectPrivate](/images/4-cicd/4.2-jenkins/6_Jenkins.png)

At Pipeline section, configure as below to connect to the Dev Repository. Currently, our repository is publicly visible, so we will skip the Credentials.

![ConnectPrivate](/images/4-cicd/4.2-jenkins/7_Jenkins.png)

Configure Branch **main** as below. Pipeline only run when there is a change in branch **main**.

![ConnectPrivate](/images/4-cicd/4.2-jenkins/8_Jenkins.png)

At **Script Path** section, modify to `api-gateway/Jenkinsfile` as below. Whenever there is a change in the folder `api-gateway`, Jenkins Server will run the Pipeline based on the configuration in the file `api-gateway/Jenkinsfile`.

![ConnectPrivate](/images/4-cicd/4.2-jenkins/9_Jenkins.png)

Creating Pipeline for `Info Service` and `Order Service` will be the same. However, at **Script Path** section, we modify to `info/Jenkinsfile` and `order/Jenkinsfile`, respectively.
