---
title : "Tạo VPC, Internet Gateway, và NAT Gateway"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 2.1.1 </b> "
---

Tạo Folder `Terraform`, tạo các file `Terraform/terraform.tfvars` và `Terraform/variables.tf`. Các file này sẽ định nghĩa các cấu hình hạ tầng của ta.

Bạn đọc tham khảo tại đây [`Terraform/terraform.tfvars`](https://github.com/heyyytamvo/FCJ2024-WS2-OpsRepo/blob/main/Terraform/terraform.tfvars) và [`Terraform/variables.tf`](https://github.com/heyyytamvo/FCJ2024-WS2-OpsRepo/blob/main/Terraform/variables.tf)


Tạo file `Terraform/00-main.tf` để định nghĩa AWS Provider.

```tf
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }

  required_version = ">= 1.2.0"
}

provider "aws" {
  region = "us-east-1"
}
```


#### Tạo VPC, Internet Gateway, và NAT Gateway
Tạo file `Terraform/01-vpc.tf` để tạo VPC, Internet Gateway, và NAT Gateway.

```tf
resource "aws_vpc" "main" {
  cidr_block           = var.vpc_cidr
  enable_dns_hostnames = true
  enable_dns_support   = true
  tags = {
    Name = var.vpc_name
  }
}

resource "aws_internet_gateway" "defaultIGW" {
  vpc_id = aws_vpc.main.id
  tags = {
    Name = "Internet Gateway"
  }
}

resource "aws_eip" "my_elastic_ip" {
  domain = "vpc"
}

# NAT Gateway
resource "aws_nat_gateway" "my_nat_gtw" {
  allocation_id = aws_eip.my_elastic_ip.id
  subnet_id     = values(aws_subnet.public_subnets)[0].id

  tags = {
    Name = "NAT Gateway"
  }
}
```
Như trên, ta cần tạo một Elastic IP Address và gán nó vào NAT Gateway của ta.
