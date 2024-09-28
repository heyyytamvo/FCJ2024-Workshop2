---
title : "Create EKS Cluster"
date :  "`r Sys.Date()`" 
weight : 3 
chapter : false
pre : " <b> 3.3. </b> "
---

Create file `Terraform/08-eks.tf` as below:

```tf
module "eks" {
  source          = "terraform-aws-modules/eks/aws"
  cluster_name    = var.cluster_name
  cluster_version = var.cluster_version
  vpc_id          = aws_vpc.main.id
  subnet_ids                               = [for subnet in aws_subnet.private_subnets : subnet.id]
  cluster_endpoint_public_access           = true
  iam_role_arn                             = aws_iam_role.ekse_role.arn
  enable_cluster_creator_admin_permissions = true

  cluster_addons = {
    kube-proxy = {
      most_recent = true
    }
    vpc-cni = {
      most_recent = true
    }
  }

  control_plane_subnet_ids = [for subnet in aws_subnet.private_subnets : subnet.id]

  tags = {
    Environment = "Development"
  }
  depends_on = [aws_iam_role_policy_attachment.AmazonEKSClusterPolicy]
}
```