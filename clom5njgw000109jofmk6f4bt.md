---
title: "DevOps 3.5: Let Validate our Work"
seoTitle: "DevOps 3.5: Let Validate our Work"
seoDescription: ""Validation of out Project""
datePublished: Mon Nov 06 2023 00:19:34 GMT+0000 (Coordinated Universal Time)
cuid: clom5njgw000109jofmk6f4bt
slug: devops-35-let-validate-our-work
tags: linux, automation, devops, wemakedevs

---

# Steps for Validation:

1. Login to web01 using `vagrant ssh web01` .
    
2. And type `ip addr show` for the IP address. Then copy the eth2 IP address and paste it into the browser. The IP is of nginx and web page from the Tomcat server. It means Nginx is a successful routing into Tomcat.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699228543321/86bd584a-a15c-49e4-bb0f-340b65e746ab.png align="center")
    
    The username and password are - admin\_vp
    
3. To check for rabbitMQ click on rabbitmq if the below page is showing then it is working-
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699228726161/c4e5fe12-b469-420c-9a35-85a03ae68b4a.png align="center")
    
4. To check memcache - Go to all users if you get something below then it is working -
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699229689280/ae3e6c68-0d99-412c-af65-07e22e4f0a65.png align="center")

### So this is how you set up various services manually !! Next Blog we are going to automate this using provisioning ...... So Do check it out !! ✌️