---
title : "Tạo Elastic Container Registry"
date :  "`r Sys.Date()`" 
weight : 5 
chapter : false
pre : " <b> 3.4. </b> "
---

Tạo File `Terraform/10-ecr` như bên dưới:

```tf
resource "aws_ecr_repository" "ECR" {
  name                 = var.ecr_repo_name
  image_tag_mutability = "IMMUTABLE"

  image_scanning_configuration {
    scan_on_push = false
  }
}
```