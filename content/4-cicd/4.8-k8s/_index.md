---
title : "Deploy K8s Cluster"
date :  "`r Sys.Date()`" 
weight : 8 
chapter : false
pre : " <b> 4.8. </b> "
---

### Connect to Jump Host

Using Console Management, at `EC2 > Security Group`, modify the Security Group of the EKS Control Plane such that it accepts traffic from Jump Host on port 443.

![ConnectPrivate](/images/4-cicd/4.8-k8s/des.png)

![ConnectPrivate](/images/4-cicd/4.8-k8s/sg.png)


Now, use the private key to connect to **Jump Host** via SSH Protocol. Next, at **Jump Host**, we need to configure AWS Credentials to access the cluster.

{{% notice warning %}}

Using Environment Variables so that when you end the SSH Session, AWS Credentials will be gone.
{{% /notice %}}

```sh
export AWS_ACCESS_KEY_ID=<your-access-id> \
export AWS_SECRET_ACCESS_KEY=<your-secret> \
export AWS_DEFAULT_REGION=<your-deployed-region>
```

Next, using AWS CLI to configure EKS Cluster. In this Workshop, the name of EKS Cluster is *WS2Cluster* and it is deployed in region *us-east-1*. Below is how we configure.

```sh
aws eks update-kubeconfig --region us-east-1 --name WS2Cluster
```

### Deploy K8s Cluster


Using Git to clone the Ops Repository to the Jump Host as below (You can use my Ops Repository):

```sh
git clone https://github.com/heyyytamvo/FCJ2024-WS2-OpsRepo.git
```

Now, we will deploy Argo CD, Prometheus and Grafana, and EFK Stack by executing file `setup.sh` as below:

```
cd FCJ2024-WS2-OpsRepo
chmod +x setup.sh
source setup.sh
```

In the AWS Console Management, at `EC2 > Load Balancers`, we can see there are 3 Load Balancers. Every DNS will lead us to:

- Argo CD Web 
- Grafana Web
- Kibana Web

![ConnectPrivate](/images/4-cicd/4.8-k8s/3ELB.png)