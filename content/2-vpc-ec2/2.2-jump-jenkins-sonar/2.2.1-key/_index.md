---
title : "Create Key Pair at Local Machine"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 2.2.1 </b> "
---


#### Create Public and Private Key at your local machine

Using **ssh-keygen** to create a key pair and name it *EC2*.

```
ssh-keygen -b 2048 -t rsa
```

{{% notice warning %}}
Please add it to .gitignore to avoid leaking credentials.{{% /notice %}}

Create `Terraform/04-keypair.tf` with the configuration below:

```tf
## Key pair
resource "aws_key_pair" "EC2key" {
  key_name   = var.ec2_key_name
  public_key = file("${path.module}/EC2.pub")
}
```