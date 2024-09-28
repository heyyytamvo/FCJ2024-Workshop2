---
title : "Create SonarQube Server"
date :  "`r Sys.Date()`" 
weight : 4 
chapter : false
pre : " <b> 2.2.4 </b> "
---

Our code base will be analyzed by the SonarQube Server. You can deploy Jenkins and SonarQube Server on a single EC2 for saving budget. In this Workshop, I will use two EC2 Instances. Create file `Terraform/sonarqube_install.sh` as below:

```sh
#!/bin/bash
sudo apt update -y
sudo apt install -y fontconfig openjdk-17-jre

# Sonarqube
sudo apt install curl ca-certificates
sudo install -d /usr/share/postgresql-common/pgdg
sudo curl -o /usr/share/postgresql-common/pgdg/apt.postgresql.org.asc --fail https://www.postgresql.org/media/keys/ACCC4CF8.asc
sudo sh -c 'echo "deb [signed-by=/usr/share/postgresql-common/pgdg/apt.postgresql.org.asc] https://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
sudo apt update
sudo apt install postgresql-15 -y
sudo -i -u postgres bash << EOF
# Create the user and database, and set the password
createuser sonar
createdb sonar -O sonar
psql -c "ALTER USER sonar WITH ENCRYPTED PASSWORD 'your_password';"
EOF
wget https://binaries.sonarsource.com/Distribution/sonarqube/sonarqube-10.5.1.90531.zip
sudo apt install -y unzip
sudo unzip sonarqube-10.5.1.90531.zip
sudo mv sonarqube-10.5.1.90531 /opt/sonarqube
sudo adduser --system --no-create-home --group --disabled-login sonarqube
sudo chown -R sonarqube:sonarqube /opt/sonarqube

sudo bash -c 'cat << EOF > /opt/sonarqube/conf/sonar.properties
sonar.jdbc.username=sonar
sonar.jdbc.password=your_password
sonar.jdbc.url=jdbc:postgresql://localhost/sonar
EOF'

sudo bash -c 'cat << EOF > /etc/systemd/system/sonarqube.service
[Unit]
Description=SonarQube service
After=syslog.target network.target

[Service]
Type=forking

ExecStart=/opt/sonarqube/bin/linux-x86-64/sonar.sh start
ExecStop=/opt/sonarqube/bin/linux-x86-64/sonar.sh stop

User=sonarqube
Group=sonarqube
Restart=always

LimitNOFILE=65536
LimitNPROC=4096

[Install]
WantedBy=multi-user.target
EOF'

sudo systemctl daemon-reload
sudo systemctl start sonarqube
sudo systemctl enable sonarqube

# Update limits.conf
sudo bash -c 'cat << EOF >> /etc/security/limits.conf
sonarqube   -   nofile   65536
sonarqube   -   nproc    4096
EOF'

# Update sysctl.conf
sudo bash -c 'cat << EOF >> /etc/sysctl.conf
vm.max_map_count=262144
EOF'
sudo sysctl -p

# install nginx
sudo apt install -y nginx
sudo systemctl start nginx

sudo rm /etc/nginx/sites-enabled/default
sudo tee /etc/nginx/sites-enabled/default > /dev/null << 'EOF'
server {
        listen 80;
        server_name _;
 
        location / {
                proxy_pass http://localhost:9000; 
                proxy_set_header X-Real-IP $remote_addr;
                proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
                proxy_set_header Host $http_host;
                proxy_redirect off;
        }
}
EOF
sudo systemctl reload nginx
```
Next, we will configure our Sonar Server. Creating file `Terraform/05-sonar_server.tf` as below:

```tf
# Security Group for EC2
resource "aws_security_group" "SONAR_HOST_SG" {
  name        = "SONAR_HOST_SG"
  description = "Allow SSH, HTTP inbound and all outbound traffic"
  vpc_id      = aws_vpc.main.id

  ingress = [
    {
      from_port        = 80
      to_port          = 80
      protocol         = "tcp"
      cidr_blocks      = ["0.0.0.0/0"]
      description      = "Allow inbound traffic on port 80"
      ipv6_cidr_blocks = []
      prefix_list_ids  = []
      security_groups  = []
      self             = false
    },

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
    Name = "SONAR_HOST SG"
  }
}

resource "aws_instance" "Sonar_host" {

  ami                         = var.ec2_ami
  instance_type               = var.ec2_instance_type
  key_name                    = aws_key_pair.EC2key.key_name
  monitoring                  = true
  subnet_id                   = values(aws_subnet.public_subnets)[1].id
  vpc_security_group_ids      = [aws_security_group.SONAR_HOST_SG.id]
  associate_public_ip_address = true

  user_data = file("${path.module}/sonarqube_install.sh")
  tags = {
    Terraform   = "true"
    Environment = "dev"
    Name        = "Sonar Host"
  }

  root_block_device {
    volume_size = 30
  }
}
```