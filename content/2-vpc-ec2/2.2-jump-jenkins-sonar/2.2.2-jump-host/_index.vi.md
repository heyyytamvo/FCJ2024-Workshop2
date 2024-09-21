---
title : "Tạo Jump Host"
date :  "`r Sys.Date()`" 
weight : 2 
chapter : false
pre : " <b> 2.2.2 </b> "
---

Thông qua Jump Host, ta sẽ tương tác với cụm K8s, điều này sẽ giảm nguy cơ cụm K8s của ta có thể được public accessed. Dùng private key mà ta đã tạo ở phần trước để truy cập Jump Host thông qua giao thức SSH. Nhưng trước hết, ta cần cài đặt các package cần thiết thông qua file Bash Script. Tạo file `Terraform/jump_host_install.sh` như bên dưới:

```sh
#!/bin/bash
sudo apt update -y
# Install eksctl
ARCH=amd64
PLATFORM=$(uname -s)_$ARCH

curl -sLO "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_$PLATFORM.tar.gz"

# (Optional) Verify checksum
curl -sL "https://github.com/eksctl-io/eksctl/releases/latest/download/eksctl_checksums.txt" | grep $PLATFORM | sha256sum --check

sudo tar -xzf eksctl_$PLATFORM.tar.gz -C /tmp && rm eksctl_$PLATFORM.tar.gz

sudo mv /tmp/eksctl /usr/local/bin

# Install kubectl
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"

sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

# install aws-cli
sudo apt install -y unzip
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install --bin-dir /usr/local/bin --install-dir /usr/local/aws-cli --update

# install docker 
sudo apt-get install -y ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
echo \
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin


sudo curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
sudo chmod 700 get_helm.sh
sudo bash get_helm.sh
```

Vì phiên bản Jump Host hiện tại là **Ubuntu 22.04**, nếu bạn đọc có nhu cầu dùng khác bản 0S (Amazon Linux, etc.), bạn đọc cần cấu hình lại file Bash Script ở trên.

Kế tiếp, ta sẽ thiết lập cấu hình cho Jump Host. Tạo file `Terraform/05-jump_host.tf` như bên dưới:

```tf
# Security Group for EC2
resource "aws_security_group" "JUMP_HOST_SG" {
  name        = "JUMP_HOST_SG"
  description = "Allow SSH inbound and all outbound traffic"
  vpc_id      = aws_vpc.main.id

  ingress = [
    {
      from_port        = -1
      to_port          = -1
      protocol         = "icmp"
      cidr_blocks      = ["0.0.0.0/0"],
      description      = "Allow inbound ICMP Traffic"
      ipv6_cidr_blocks = []
      prefix_list_ids  = []
      security_groups  = []
      self             = false
    },

    {
      from_port        = 22
      to_port          = 22
      protocol         = "tcp"
      cidr_blocks      = ["0.0.0.0/0"]
      description      = "Allow inbound traffic on port 22"
      ipv6_cidr_blocks = []
      prefix_list_ids  = []
      security_groups  = []
      self             = false
    }
  ]

  egress {
    from_port   = 0
    to_port     = 0
    protocol    = "-1"
    cidr_blocks = ["0.0.0.0/0"]
  }

  tags = {
    Name = "JUMP_HOST SG"
  }
}

resource "aws_instance" "Jump_host" {

  ami                         = var.ec2_ami
  instance_type               = var.ec2_instance_type
  key_name                    = aws_key_pair.EC2key.key_name
  monitoring                  = true
  subnet_id                   = values(aws_subnet.public_subnets)[0].id
  vpc_security_group_ids      = [aws_security_group.JUMP_HOST_SG.id]
  associate_public_ip_address = true

  user_data = file("${path.module}/jump_host_install.sh")
  tags = {
    Terraform   = "true"
    Environment = "dev"
    Name        = "Jump Host"
  }

  root_block_device {
    volume_size = 30
  }
}
```