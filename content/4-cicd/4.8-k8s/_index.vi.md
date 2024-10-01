---
title : "Triển khai K8s Cluster"
date :  "`r Sys.Date()`" 
weight : 8 
chapter : false
pre : " <b> 4.8. </b> "
---

### Kết nối đến Jump Host
Dùng Console Management, tại phần `EC2 > Security Group`, ta cần sửa Security Group cho EKS Control Plane sao cho EKS Control Plane sẽ chấp nhận traffic đến từ Jump Host ở Port 443.

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.8-k8s/des.png)

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.8-k8s/sg.png)

Bây giờ, dùng private key để kết nối đến **Jump Host** thông qua giao thức SSH. Sau đó, tại **Jump Host**, ta cần thiết lập AWS Credentials để có thể truy cập Cluster. 

{{% notice warning %}}
Dùng Environment Variables để đảm bảo rằng khi kết thúc phiên làm việc, AWS Credentials sẽ không còn lưu tại Jump Host
{{% /notice %}}

```sh
export AWS_ACCESS_KEY_ID=<your-access-id> \
export AWS_SECRET_ACCESS_KEY=<your-secret> \
export AWS_DEFAULT_REGION=<your-deployed-region>
```

Sau đó, dùng AWS CLI để config EKS Cluster. Với bài Workshop này, EKS Cluster có tên là *WS2Cluster* và được deployed ở region *us-east-1*, thế nên, ta sẽ config như bên dưới:

```sh
aws eks update-kubeconfig --region us-east-1 --name WS2Cluster
```

### Triển khai K8s Cluster

Dùng Git để clone Ops Repository về Jump Host như bên dưới (Bạn đọc tham khảo Ops Repository của tôi như bên dưới):

```sh
git clone https://github.com/heyyytamvo/FCJ2024-WS2-OpsRepo.git
```

Bây giờ, ta sẽ triển khai Argo CD, Prometheus, Grafana, và EFK Stack với việc chạy file `setup.sh` như bên dưới:

```
cd FCJ2024-WS2-OpsRepo
chmod +x setup.sh
source setup.sh
```

Nếu bạn đọc truy cập phần `EC2 > Load Balancers`, ta sẽ có tổng cộng 3 Load Balancers, mỗi DNS sẽ đưa ta đến:

- Argo CD Web 
- Grafana Web
- Kibana Web

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.8-k8s/3ELB.png)