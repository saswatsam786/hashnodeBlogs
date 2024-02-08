---
title: "🚀 DevOps 7.3: Rapid Website Deployment on EC2 🌐✨"
seoTitle: "🚀 DevOps 7.3: Rapid Website Deployment on EC2 🌐✨"
seoDescription: "🔧 Streamlining Your Web Presence: A Swift Guide to EC2 Deployment 🚀💻"
datePublished: Thu Feb 08 2024 07:16:56 GMT+0000 (Coordinated Universal Time)
cuid: clscvyctv000608jwbmy71o73
slug: devops-73-rapid-website-deployment-on-ec2
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1707376428936/d3364c0a-51e5-48f6-9104-910c2a827e3e.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1707376565805/d0d149dc-4ee4-42ef-9665-6301e701c8b2.png
tags: ec2, aws, deployment, devops, wemakedevs

---

# Introduction:

In **DevOps 7.3: Rapid Website Deployment on EC2** 🚀🌐, we delve into swift methods for deploying your website on Amazon EC2 instances. Learn the art of seamless website launch and enhance your AWS journey! 🌟💻

## Setup a website on EC2:

### Steps are as follows:

1. First lets go to key-pairs in EC2 instance.
    
2. Click on Create Key-Pair button.
    
3. You can take any project from tooplate.com and use it to deploy.
    
4. Name your key-pair.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707371394275/45c99c70-bec3-4431-b775-e360c270f8f9.png align="center")
    
5. So public key will be injected into instance and private key is the key which matches the instance and we get the access.
    
6. Now go to security group present in Network and Security in the sidebar. And click on Create Security Group button.
    
7. Now you can enter the inbound rules, i.e ssh port from your ip address only.
    
    <mark>NOTE: Do not change any outbound rules, which may lead to malfunction.</mark>
    
8. Now, lets launch the instance. You can add following key-value tags.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707372285100/300e5ada-e3d8-4a9f-9e13-74f2aba7fd6e.png align="center")
    
9. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707373893753/39f24712-a76a-4189-9ad8-0fb1e294ced3.png align="center")
    
    You can select the Ubuntu as AMI which is free tier eligible.
    
10. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707373971701/5209a1e5-e73f-45c0-a64a-8e71aa61446a.png align="center")
    
    You select the key-pair which you created earlier. This way you can use the same key-pair for multiple instances.
    
11. In network settings you can select the existing security group which you had created earlier.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707374178805/56b24d71-2ea1-4027-94c8-558b435f067c.png align="center")
    
12. Then you can launch the instance.
    
13. Lets connect to the instance using SSH as shown in my previous blog.
    
14. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707375366071/46baa1b5-39be-4f49-aa8b-aab107be5f6e.png align="center")
    
    You will see something like above when you connect with the instance.
    
15. We can follow the same process which we did while setting our website locally in my previous blogs. Link - [https://saswatblogs.hashnode.dev/launch-your-website-on-linux](https://saswatblogs.hashnode.dev/launch-your-website-on-linux)
    
    ```bash
    sudo -i
    sudo apt install apache2 wget unzip -y
    wget https://www.tooplate.com/zip-templates/2136_kool_form_pack.zip
    unzip 2136_kool_form_pack.zip 
    cp -r 2136_kool_form_pack/* /var/www/html/
    sudo systemctl restart apache2
    ```
    
16. We can access the website from the public ip on instance but for that we have to allow port 80 in security group.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707376254335/b7e92874-3dc1-4f83-bedc-54dc05d93b44.png align="center")
    

# Conclusion:

In conclusion, we've navigated the swift process of deploying a website on EC2, streamlining the path from setup to launch. Stay tuned for more insights in our DevOps journey! 🚀🌐 #AWS #DevOps #WebDeployment