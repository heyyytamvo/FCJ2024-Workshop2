---
title : "Tạo cặp Public và Private Key ở Local Machine"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 2.2.1 </b> "
---

#### Tạo Public và Private Key ở local machine

Sử dụng **ssh-keygen** để tạo một cặp public và private key. Đặt tên chúng là EC2.

```
ssh-keygen -b 2048 -t rsa
```

{{% notice warning %}}
Bạn đọc cần thêm cặp key pair này vào file **.gitignore**
{{% /notice %}}

Tạo file `Terraform/04-keypair.tf` với cấu hình bên dưới:

```tf
## Key pair
resource "aws_key_pair" "EC2key" {
  key_name   = var.ec2_key_name
  public_key = file("${path.module}/EC2.pub")
}
```