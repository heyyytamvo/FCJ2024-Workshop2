---
title : "Create Subnet and Subnet Association"
date :  "`r Sys.Date()`" 
weight : 2
chapter : false
pre : " <b> 2.1.2 </b> "
---

#### Create Subnet

Create file `Terraform/02-subnet.tf` to create subnets as below:

```tf
// Public Subnet
resource "aws_subnet" "public_subnets" {
  for_each                = toset(var.vpc_public_subnets)
  vpc_id                  = aws_vpc.main.id
  cidr_block              = each.value
  availability_zone       = var.vpc_azs[index(var.vpc_public_subnets, each.value)]
  map_public_ip_on_launch = true

  tags = {
    Name = "Public Subnet ${index(var.vpc_public_subnets, each.value) + 1}"
  }
}

// Private Subnet
resource "aws_subnet" "private_subnets" {
  for_each          = toset(var.vpc_private_subnets)
  vpc_id            = aws_vpc.main.id
  cidr_block        = each.value
  availability_zone = var.vpc_azs[index(var.vpc_private_subnets, each.value)]

  tags = {
    Name = "Private Subnet ${index(var.vpc_private_subnets, each.value) + 1}"
  }
}
```
#### Route Table and Subnet Association

Next, we will create Route Tables, then, we will associate Internet Gateway, NAT Gateway, and Subnets. Create file `Terraform/03-route_table.tf` as below:

```tf
// create public route table
resource "aws_route_table" "public_route_table" {
  vpc_id = aws_vpc.main.id

  route {
    cidr_block = var.vpc_cidr
    gateway_id = "local"
  }

  route {
    cidr_block = "0.0.0.0/0"
    gateway_id = aws_internet_gateway.defaultIGW.id
  }

  tags = {
    Name = "Public Route Table"
  }
}

// create private route table
resource "aws_route_table" "private_route_table" {
  vpc_id = aws_vpc.main.id

  tags = {
    Name = "Private Route Table"
  }
}

## public subnet Association
resource "aws_route_table_association" "public_subnets_associations" {
  for_each       = aws_subnet.public_subnets
  subnet_id      = each.value.id
  route_table_id = aws_route_table.public_route_table.id
}

## private subnet Association
resource "aws_route_table_association" "private_subnets_associations" {
  for_each       = aws_subnet.private_subnets
  subnet_id      = each.value.id
  route_table_id = aws_route_table.private_route_table.id
}

resource "aws_route" "route_nat_gw" {
  route_table_id         = aws_route_table.private_route_table.id
  destination_cidr_block = "0.0.0.0/0"
  nat_gateway_id         = aws_nat_gateway.my_nat_gtw.id

  timeouts {
    create = "5m"
  }
}
```
