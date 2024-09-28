---
title : "Create Elastic Container Registry"
date :  "`r Sys.Date()`" 
weight : 5 
chapter : false
pre : " <b> 3.5. </b> "
---

Create file `Terraform/10-ecr` as below:

```tf
resource "aws_ecr_repository" "ECR" {
  name                 = "fcjws2"
  image_tag_mutability = "IMMUTABLE"

  image_scanning_configuration {
    scan_on_push = false
  }
}
```