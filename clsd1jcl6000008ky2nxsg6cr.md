---
title: "🚀💻 DevOps 7.4: Advanced EC2 Explorations 🌐🛠️"
seoTitle: "🚀💻 DevOps 7.4: Advanced EC2 Explorations 🌐🛠️"
seoDescription: "Explore more on EC2 "
datePublished: Thu Feb 08 2024 09:53:14 GMT+0000 (Coordinated Universal Time)
cuid: clsd1jcl6000008ky2nxsg6cr
slug: devops-74-advanced-ec2-explorations
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1707379052232/ee675863-bd1b-49b0-aeb1-2ac816dea6ea.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1707385955951/5f21c5f0-7573-4848-9a57-5d2959510944.png
tags: ec2, aws, developer, cloud-computing, devops, wemakedevs, aws-elastic-ip

---

# More on AWS:

### Elastic IPs:

When you stop and restart the instance, the public IP changes, but the private IP remains constant.

To address this, Elastic IPs are employed, providing a consistent public IP throughout the instance lifecycle.

Here we get only 5 Elastic IPs but you can purchase more if you want.

## Steps for setting up Elastic IPs:

1. Navigate to "Elastic IPs" under "Network and Security" in the sidebar.
    
2. Click on "Allocate Elastic IP address" and then click Allocate.
    
3. Then select the IP and click action to click on Associate Elastic IP address.
    
4. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707383954560/66dc76c6-b0af-4636-aac3-a9f982b1716f.png align="center")
    
    Select the instance and click "Associate".
    
5. Now you stop and restart the instance the Public IP remains same.
    
6. **To terminate,** select the instance and click on "terminate" in actions.
    
7. Then go to Elastic IPs, select the Elastic IP and in action click "Release Elastic IP Address".
    
    <mark>Note: You should do this to avoid charges.</mark>
    

## About Network Interfaces:

In Amazon EC2, a network interface (ENI) is a virtual network card that you can attach to an instance in order to enable communication with your VPC (Virtual Private Cloud) and the internet. Each instance in a VPC can have one or more network interfaces. Network interfaces provide additional networking features beyond what is available with the primary network interface.

Key points about network interfaces in Amazon EC2:

1. **Primary Network Interface (eth0):** Every EC2 instance comes with a primary network interface, which is assigned a private IP address from the VPC CIDR block. This is typically named `eth0`.
    
2. **Additional Network Interfaces:** You can attach additional network interfaces to an instance, each with its own private IP address, security groups, and Elastic Network Interfaces (ENI). These can be used for various purposes like creating a multi-homed instance or providing additional network connectivity.
    
3. **Elastic Network Interfaces (ENIs):** ENIs provide a way to create a more modular and scalable network architecture. They can be moved between instances, allowing for flexibility in network design.
    
4. **Security Groups and IP Addresses:** Each network interface is associated with one or more security groups, and it is assigned one private IP address from each subnet to which it is connected.
    
5. **MAC Addresses:** Each network interface has a MAC address, and you can also assign one or more private IP addresses and Elastic IP addresses to a network interface.
    
6. **Lifecycle:** Network interfaces can be attached and detached from instances. When an instance is terminated, all its network interfaces are also terminated.
    
7. **Limitations:** The number of network interfaces you can use is limited by the instance type. For example, t2.micro allows only 2 network interfaces, whereas larger instances may allow more.
    

In summary, network interfaces in Amazon EC2 provide a way to customize and extend the networking capabilities of your instances within the AWS cloud environment.

<mark>NOTE: The security groups and IPs we create are for the network interface not for the instance.</mark>