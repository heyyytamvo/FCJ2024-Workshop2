---
title : "Application Auto Update"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 8.5. </b> "
---

### Old Version

Before making a commit at Ops Repository, below is our application:

![ConnectPrivate](/images/8-cicd-test/8.5-app/update_0.png)

### New Version

At Argo CD, we can see that **API Gateway Pods** is being updated:

![ConnectPrivate](/images/8-cicd-test/8.5-app/update_1.png)

Finally, our application is automatically updated as below:

![ConnectPrivate](/images/8-cicd-test/8.5-app/update_2.png)