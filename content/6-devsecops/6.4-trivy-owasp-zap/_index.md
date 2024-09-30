---
title : "Configure Trivy and OWASP ZAP"
date :  "`r Sys.Date()`" 
weight : 4 
chapter : false
pre : " <b> 6.4. </b> "
---

Trivy and OWASP ZAP are installed at Jenkins Server, using file `Terraform/jenkins_install.sh` at Ops Repository:

```sh

...
sudo apt-get install -y wget apt-transport-https gnupg
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | gpg --dearmor | sudo tee /usr/share/keyrings/trivy.gpg > /dev/null
echo "deb [signed-by=/usr/share/keyrings/trivy.gpg] https://aquasecurity.github.io/trivy-repo/deb generic main" | sudo tee -a /etc/apt/sources.list.d/trivy.list
sudo apt-get update
# Install trivy
sudo apt-get install -y trivy

# Install OWASP ZAP
docker pull zaproxy/zap-stable
```