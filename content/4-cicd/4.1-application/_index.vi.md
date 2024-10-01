---
title : "Tổng quan Application"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
pre : " <b> 4.1. </b> "
---

Application của chúng ta là được triển khai theo kiến trúc Microservices với 3 Services chính:

- **Service API Gateway**: Sẽ là nguồn nhận traffic (đến từ user) và chịu trách nhiệm điều hướng
- **Order Service**: Chịu trách nhiệm Write Database
- **Info Service**: Chịu trách nhiệm Read Database

Tổng cộng ta sẽ có 3 API Endpoints:

- domain.com/
- domain.com/create-order
- domain.com/get-orders

Traffic từ User sẽ luôn đi đến **Customer API Gateway** (là Load Balancer hoặc một Reverse Proxy) và được điều hướng đến **Service API Gateway**. Bên dưới là minh hoạ các luồng traffic cho 3 API Endpoints.

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.1-application/Application.gif)

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.1-application/Order.gif)

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.1-application/Info.gif)