---
title: "DevOps 7.2 : Getting Started with EC2"
seoTitle: "DevOps 7.2: Getting Started with EC2"
seoDescription: "🚀✨ "Embark on Your Cloud Journey: Navigating the Basics of EC2" 💻🌐"
datePublished: Wed Feb 07 2024 16:05:06 GMT+0000 (Coordinated Universal Time)
cuid: clsbzdq1b000009jx9fdjhwd5
slug: devops-72-getting-started-with-ec2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1707321829860/5010b312-82f8-4118-b9a3-4aa7e673876a.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1707321876879/a469e488-43f7-4d28-bfea-8573cfe4740c.webp
tags: ec2, linux, aws, cloud-computing, devops

---

# What is EC2 ?

Amazon Elastic Compute Cloud (Amazon EC2) is a web service provided by Amazon Web Services (AWS) that offers resizable compute capacity in the cloud. It allows users to run virtual servers, known as instances, on-demand. EC2 instances provide a scalable and flexible computing solution, enabling users to easily scale their applications as computing requirements change. EC2 is a fundamental building block of AWS, providing the compute capacity needed to host applications ranging from simple web servers to complex machine learning workloads.

## What are the components in EC2 ?

**Amazon Machine Images (AMIs):** An AMI is a pre-configured virtual machine image, including an operating system and often additional software. Users can use existing AMIs or create custom ones.

**Instances:** These are the virtual servers in the cloud. Users can launch instances with different configurations, such as varying CPU, memory, storage, and network performance.

**Elastic Block Store (EBS):** EBS provides block-level storage volumes that can be attached to EC2 instances. It allows users to create persistent storage volumes that persist independently of the life of the instance.

**Key Pairs:** EC2 instances can be accessed securely using key pairs. A user stores one part of the key pair (the private key) securely and provides the other part (the public key) when launching an instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707306170214/aa0d6752-9a00-4ddc-ae52-b609d661017a.png align="center")

# QuickStart EC2 -

### Steps are as follows:

1. Log In to aws account.
    
2. Search for EC2 in the search bar.
    
3. Click on instances in the sidebar. And Click Launch Instances.
    
4. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707309410755/fe95d384-2533-410e-be18-7c8ecb28f1c5.png align="center")
    
    Give the project name as web01 and you can addition key-value tags for filtering.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707310041610/9ebbd936-5aaa-4983-9349-e0f50cffe275.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707309932742/d84bb336-bdf7-4add-859d-f238a45bff9d.png align="center")
    
5. Then click on Browser AMIs and search for centos in AWS Marketplace AMIs and go for Centos Stream 9 which is an free AMI.
    
6. In instance type select t2.micro which is free tier eligible.
    
7. Then click on Create new key pair and match below
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707310478072/3f369fb0-9222-4864-8427-52237b71ac2f.png align="center")
    
8. In network settings you can edit or keep the default settings if you want to.
    
9. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707310683738/eb8c6518-8ee3-4c81-bd5d-2c5ca4c2434a.png align="center")
    
    In advance detail you can scroll till the bottom and copy the below detail. This is like vagrant provisioning. It will run the commands when the instance starts running.
    
10. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707313098924/e149ba48-a4d7-43f8-92c4-4a536aea046e.png align="center")
    
    Then launch the instance. As you can see the instance is launched.
    
11. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707313207578/3f5d27ec-16ef-485c-8580-9d6a2a93ee57.png align="center")
    

### Lets connect to the instance -

1. Click on the instance and click on the connect option.
    
2. Select the option ssh client
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707313521231/92fd39f5-7ac7-41b3-8de3-d9bbcd762bd1.png align="center")
    
3. Copy the example and paste it in your local terminal and replace web-dev-key.pem with the location of the key you have downloaded.
    
    e.g. - **ssh -i /Downloads/web-dev-key.pem** [**ec2-user@ec2-35-171-28-205.compute-1.amazonaws.com**](mailto:ec2-user@ec2-35-171-28-205.compute-1.amazonaws.com)
    
4. As you can see the the httpd service is up and running.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707320789542/25288291-4371-4dcb-89a5-9664084200e1.png align="center")
    
5. For accessing the apache test webpage, you can access it using the public IP.  
    But first we have to add port 80 into our security group i.e. by editing the inbound rules.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707321607818/2ad38d54-3503-4dd8-b131-7c6fd28c50ae.png align="center")
    

# Conclusion:

In this concise guide, we delved into the swift deployment of EC2 instances, mastering the essentials like security groups and tags. Connecting seamlessly through SSH, we've laid the foundation. Stay tuned for deeper dives into EC2's rich capabilities in our upcoming blogs