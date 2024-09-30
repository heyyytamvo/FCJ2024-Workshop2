---
title : "Đặt vấn đề"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 1. </b> "
---
### Tại sao là Microservices?

Trước khi tìm hiểu về Microservices, ta cần tìm hiểu về cách triển khai production truyền thống: Monolithic. Monolithic là cách ‘đóng gói’ (hay còn gọi là containerize) phần mềm thành một khối duy nhất và triển khai nó lên server. Công nghệ containerize phổ biến mà bạn đọc có thể nghe đến tiêu biểu là Docker. Tưởng tượng phần mềm của bạn được containerized thành một khối duy nhất (hay còn gọi là Image) và đã được triển khai lên server. Bây giờ, một tính năng mới đã được phát triển và sẵn sàng triển khai trên môi trường production. Quá trình update phần mềm sẽ được diễn ra như hình bên dưới.

![ConnectPrivate](/FCJ2024-Workshop2/images/1.Intro/mono.gif) 

Như bạn đọc có thể thấy, application bắt buộc phải bị tắt, sau đó, phiên bản mới nhất sẽ được khởi chạy. Lúc này đồng nghĩa với việc End User sẽ phải đối diện với downtime vì rõ ràng, phần mềm được ‘đóng gói’ thành một khối duy nhất và việc update một chức năng cũ lại ảnh hưởng cả tập thể. Tất nhiên, vấn đề này có thể giải quyết bằng các Deployment Strategy như Blue/Green Deployment, etc. 

Tuy nhiên, có một kiến trúc phần mềm có thể giải quyết bài toán này: Microservices. Nôm na, Microservices là chia các chức năng (Service) trong Application thành các khối khác nhau và chúng giao tiếp với nhau thông qua các chuẩn giao tiếp như REST, v.v. Việc cập nhật một service sẽ không ảnh hưởng đến các service khác như hình bên dưới. 

![ConnectPrivate](/FCJ2024-Workshop2/images/1.Intro/Micro.gif) 

Triển khai một ứng dụng Microservice trên Kubernetes (K8s) là một bài toán tiêu biểu. Lúc này ta cần triển khai hạ tầng, và cấu hình cho cụm K8s đòi hỏi sự hợp tác của Team Vận hành (hay Ops Team bao gồm các system engineer, system administrator, network engineer, etc). Và GitOps sẽ là câu trả lời để đảm bảo sự phối hợp đó.

### Tại sao là GitOps?

### Tại sao là DevSecOps?

DevOps đã tối ưu hoá quy trình phát triển phần mềm bằng việc ứng dụng các công cụ automation và làm giảm thiểu thời gian ‘release’ sản phẩm. Từ đó, end users và đội ngũ phát triển sẽ được lợi, khi đó:

- End user sẽ được cập nhật phiên bản mới nhất của sản phẩm một cách nhanh chóng
- Đội ngũ phát triển sẽ tập trung vào công việc phát triển phần mềm, khi những công đoạn thủ công như: kiểm thử, containerize, etc. đã được tự động hoá.

Tuy nhiên, trong quá trình automation đó, liệu ta có muốn kiểm thử những lỗ hổng bảo mật của source code, built image, hay chính production của chúng ta một cách tự động? Và thế là DevSecOps ra đời để giải quyết những bài toán đó. Trong khuôn khổ của bài Workshop này, chúng ta sẽ triển khai các phương pháp kiểm thử trong DevSecOps như:

- **SAST (Static Application Security Testing)**: thực hiện kiểm thử source code trước khi ‘release’. Ví dụ, nếu ứng dụng của bạn được viết bằng Python, ta sẽ kiểm thử các lỗ hổng bảo mật có thể xuất hiện trên Source Code Python của ta.

- **Image Scan và Secure IaC**: Tương tự như scan source code cho application, ta cũng sẽ thực hiện scan source code cho hạ tầng (Ví dụ: Liệu hạ tầng cloud của ta có cho phép public access không?) và built image (ví dụ: Image Base của ta có outdated không?).

- **DAST (Dynamic Application Security Testing)**: thực hiện kiểm thử production của chúng ta (Ví dụ: Khi end user gửi một request đến production, liệu có những response không mong muốn nào được trả về không?)

![ConnectPrivate](/FCJ2024-Workshop2/images/1.Intro/DevSecOps.gif) 

### Monitoring có cần thiết không?

Tưởng tượng bạn đọc là một thành viên trong team Dev và Application của chúng ta được triển khai trên cụm Kubernetes. Một khi có lỗi xảy ra ở Application, bạn phải biết cách truy cập vào cụm K8s để xem logs và debug. Nhưng rõ ràng, ta không muốn điều đó xảy ra tí nào vì K8s rất phức tạp, và thế ta cần centralized các logs tại một nơi và developer có thể dễ dàng truy cập cho việc debug. Với bài Workshop này, ta sẽ ứng dụng EFK Stack. Khi đó, Developers sẽ biết được logs thông qua Web Browser.

![ConnectPrivate](/FCJ2024-Workshop2/images/1.Intro/Monitor.gif)

Trong bài Workshop này, chúng ta sẽ tận dụng các dịch vụ từ AWS để giải quyết bài toán trên:

- **Elastic Compute Service (EC2)**: Nơi ta sẽ host Jenkins Server, SonarQube Server. Chúng là một phần quan trọng trong CI/CD Pipeline của ta
- **Elastic Kubernetes Service (EKS)**: Thay vì tự tay setup một Kubernetes Cluster, chúng ta sẽ sử dụng dịch vụ từ AWS.
- **Elastic Container Registry (ECR)**: Đóng vai trò như một "*Private Docker Hub*". Rõ ràng, ta không muốn các Application Image bị lộ. Vì vậy, ta cần một nơi đủ tin cậy để chứa chúng và ECR là giải pháp.

{{% notice note %}}
Bạn đọc cần cài đặt Terraform trước khi có thể hoàn thành bài Workshop này
{{% /notice %}}
