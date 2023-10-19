---
title: "DevOps 2.5: Effortless WordPress Automation"
seoTitle: ""Streamline Your Workflow: Automate WordPress Setup with DevOps 2.5""
seoDescription: ""DevOps 2.5: Automate WordPress Setup - Learn how to automate the setup of WordPress websites for efficiency and scalability.""
datePublished: Thu Oct 19 2023 21:48:05 GMT+0000 (Coordinated Universal Time)
cuid: clnxpr9ev000309l3c1nl7l4m
slug: devops-25-effortless-wordpress-automation
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697750396728/a97d8f9b-574a-43d6-ad37-130fb964cf1a.avif
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1697751981337/3bd8947d-c75a-4010-bba0-e6bc0545848c.avif
tags: linux, automation, devops, beginners, wemakedevs

---

# INTRODUCTION:

In "DevOps 2.5: Automate WordPress Setup," we'll dive into the world of automation to streamline the process of deploying and configuring WordPress websites efficiently. Whether you're a seasoned pro or just starting with DevOps, these automation techniques will save you time and effort while ensuring a smooth WordPress setup. Join us in simplifying your workflow and enhancing your website management capabilities. Before starting this go through my previous [DevOps 2.3 article](https://saswatblogs.hashnode.dev/devops-23-launch-wordpress-template-on-ubuntu) on how to launch a WordPress on Linux.

# STEPS:

1. Begin by duplicating a Vagrant file from your previous WordPress project and relocating it to a fresh directory. Then, open it using VSCode to proceed with your setup.
    
2. Second change the IP address of the VM so that it does not collide with other VM.
    
3. Next, through provisioning, we are going to enter all the commands through which we set up the website.
    
4. Copy the below provisioning code to the vagrant file.
    

```bash
config.vm.provision "shell", inline: <<-SHELL
  sudo apt update
     sudo apt install apache2 \
                      ghostscript \
                      libapache2-mod-php \
                      mysql-server \
                      php \
                      php-bcmath \
                      php-curl \
                      php-imagick \
                      php-intl \
                      php-json \
                      php-mbstring \
                      php-mysql \
                      php-xml \
                      php-zip -y
              
     sudo mkdir -p /srv/www
     sudo chown www-data: /srv/www
     curl https://wordpress.org/latest.tar.gz | sudo -u www-data tar zx -C /srv/www
     
     cat > /etc/apache2/sites-available/wordpress.conf <<EOF
<VirtualHost *:80>
         DocumentRoot /srv/www/wordpress
         <Directory /srv/www/wordpress>
             Options FollowSymLinks
             AllowOverride Limit Options FileInfo
             DirectoryIndex index.php
             Require all granted
         </Directory>
         <Directory /srv/www/wordpress/wp-content>
             Options FollowSymLinks
             Require all granted
         </Directory>
  </VirtualHost>
EOF
     
     sudo a2ensite wordpress
     sudo a2enmod rewrite
     sudo a2dissite 000-default
     
     
     mysql -u root -e 'CREATE DATABASE wordpress;'
     mysql -u root -e 'CREATE USER wordpress@localhost IDENTIFIED BY "admin123";'
     mysql -u root -e 'GRANT SELECT,INSERT,UPDATE,DELETE,CREATE,DROP,ALTER ON wordpress.* TO wordpress@localhost;'   
     mysql -u root -e 'FLUSH PRIVILEGES;'
     
     sudo -u www-data cp /srv/www/wordpress/wp-config-sample.php /srv/www/wordpress/wp-config.php
     sudo -u www-data sed -i 's/database_name_here/wordpress/' /srv/www/wordpress/wp-config.php
     sudo -u www-data sed -i 's/username_here/wordpress/' /srv/www/wordpress/wp-config.php
     sudo -u www-data sed -i 's/password_here/admin123/' /srv/www/wordpress/wp-config.php
     
     systemctl restart mysql
     systemctl restart apache2
  SHELL
```

Now let's run the VagrantFile by doing `vagrant up` and `vagrant ssh`.

Now if you paste the IP address in the browser you will get the web page.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1697751815378/ae64940c-ace6-4caf-af33-5a1bc2f1d5d0.png align="center")

# Conclusion:

In "DevOps 2.5: Automate WordPress Setup using Provisioning," you've gained valuable insights into automating WordPress deployment. By harnessing the power of provisioning, you can efficiently and consistently set up WordPress sites, saving time and reducing errors. This knowledge empowers you to take your DevOps skills to the next level, making website deployment a breeze. Happy automating! 🚀💻🌐