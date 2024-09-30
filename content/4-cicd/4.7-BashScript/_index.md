---
title : "Automation Deployment with Bash Scripting"
date :  "`r Sys.Date()`" 
weight : 7 
chapter : false
pre : " <b> 4.7. </b> "
---

{{% notice info %}}
Working with Ops Repo in this section 
{{% /notice %}}

We will use Bash Script to deploy Argo CD, Prometheus and Grafana, and EFK Stack. At Ops Repository, create file `setup.sh` as below.

```sh
#!/bin/bash
#set up argo cd
kubectl apply -f argocd/namespace.yaml
kubectl apply -f argocd/default.yaml -n argocd

#set up efk stack
kubectl apply -f EFK/.

#set up Prometheus and Grafana
kubectl create namespace monitoring
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
helm install prometheus-operator prometheus-community/kube-prometheus-stack -n monitoring
kubectl apply -f monitoring/grafana.yaml -n monitoring
```
Below is the final Ops Repository
![ConnectPrivate](/images/4-cicd/4.7-BashScript/tree.png)

Now, push everything to Github Repository with `git push`.

{{% notice note %}}

Folder k8s will not be mentioned here because it depends on the application. Please refer to my [Ops Repository]() to see the k8s folder.
{{% /notice %}}