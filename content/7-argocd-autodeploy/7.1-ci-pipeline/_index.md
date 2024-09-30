---
title : "Run CI Pipeline"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 7.1. </b> "
---

### Trigger CI Pipeline

At Dev Repository, push code into Github Repository to trigger Jenkins Pipeline:

![ConnectPrivate](/images/7-argocd-autodeploy/7.1-ci-pipeline/CI_Pipeline0.png)

At Jenkins Server, we can see that there are 3 running Pipeline

![ConnectPrivate](/images/7-argocd-autodeploy/7.1-ci-pipeline/CI_Pipeline1.png)

After a while, CI Pipeline is completed as below:

![ConnectPrivate](/images/7-argocd-autodeploy/7.1-ci-pipeline/CI_Pipeline2.png)

### Check Image at Private Registry

At remote Dev Repository, the latest commit is tagged with the ID of `d966430` as below:

![ConnectPrivate](/images/7-argocd-autodeploy/7.1-ci-pipeline/CI_Pipeline3.png)

Check your AWS Elastic Container Registry, we will see there are 3 Images with the tag of `d966430`:

![ConnectPrivate](/images/7-argocd-autodeploy/7.1-ci-pipeline/CI_Pipeline4.png)

Now, we will use Argo CD for Automation Deployment
