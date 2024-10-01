---
title : "Application Overall"
date :  "`r Sys.Date()`" 
weight : 1
chapter : false
pre : " <b> 4.1. </b> "
---

Our Application follows microservices architecture with 3 services: 

- **Service API Gateway**: Receiving traffic that comes from customer and forwarding traffic
- **Order Service**: Reponsible for Writing Database
- **Info Service**: Responsible for Reading Database

We will have 3 API Endpoints:

- domain.com/
- domain.com/create-order
- domain.com/get-orders

Traffic coming from customers will always reach the  **Customer API Gateway** first (a Load Balancer or a Reverse Proxy). Below are the demonstration for all traffic in our application.


![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.1-application/Application.gif)

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.1-application/Order.gif)

![ConnectPrivate](/FCJ2024-Workshop2/images/4-cicd/4.1-application/Info.gif)