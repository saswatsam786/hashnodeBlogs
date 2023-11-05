---
title: "DevOps 3.4: Nginx Setup"
seoTitle: "DevOps 3.4: Optimizing Web Traffic with Nginx Configuration"
seoDescription: "Optimizing Web Service with Nginx Configuration and Deployment."
datePublished: Sun Nov 05 2023 22:20:56 GMT+0000 (Coordinated Universal Time)
cuid: clom1eyyj000309l56ygn2p5b
slug: devops-34-nginx-setup
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1699204546810/62fb1f31-9da4-4885-b67d-d34a633d7210.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1699222772671/b2400678-4aa8-4022-a9ec-31046546d2a0.jpeg
tags: linux, nginx, devops, reverse-proxy, wemakedevs

---

# Nginx Setup:

1. Login to nginx vm:
    
    ```bash
    vagrant ssh web01
    ```
    
2. `sudo -i` go to the root user.
    
3. Update OS with the latest patches.
    
    ```bash
    apt update && apt upgrade -y
    ```
    
4. Then install the nginx
    
    ```bash
    apt install nginx -y
    ```
    
5. Create a nginx file:
    
    ```bash
    vi /etc/nginx/sites-available/vproapp
    ```
    
6. Below you can see the initial configuration file which is enabled now -
    
7. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699221978595/010c6add-0bda-4519-a354-d80e810e3539.png align="center")
    
    Now remove that link using `rm -rf /etc/nginx/sites-enabled/default` .
    
8. Create a link to activate the website
    
    ```bash
    ln -s /etc/nginx/sites-available/vproapp /etc/nginx/sites-enabled/vproapp
    ```
    
9. Then restart the nginx -
    
    ```bash
    systemctl restart nginx
    ```
    

### In the next blog, we will see this project in action !!! Do check it out !!