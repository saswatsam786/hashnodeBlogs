---
title: "🚀💻 DevOps 2.4: Automate Website Setup 🌐🤖"
seoTitle: "Automate Website Setup: DevOps 2.4 Simplifies Your Workflow"
seoDescription: "DevOps 2.4: Automate Website Setup - Streamline and simplify your website deployment process with automation techniques."
datePublished: Mon Oct 02 2023 17:32:42 GMT+0000 (Coordinated Universal Time)
cuid: cln965cvd000008mn7gee6isl
slug: devops-24-automate-website-setup
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696247930594/d69fd830-6e07-4c7a-8e83-1a58475cc0ae.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1696267856526/437a9bb1-c373-44ef-a61c-7fc0915f8440.jpeg
tags: vagrant, linux, automation, devops, wemakedevs

---

# Introduction:

In "DevOps 2.4: Automate Website Setup," we delve into the world of automation to streamline website deployment and management.

# STEPS:

1. Begin by duplicating a Vagrant file from your previous project and relocating it to a fresh directory. Then, open it using VSCode to proceed with your setup.
    
2. Second change the IP address of the VM so that it does not collide with other VM.
    
3. Next, through provisioning, we are going to enter all the commands through which we set up the website.
    
4. Copy the below provisioning code to the vagrant file.
    

```bash
 config.vm.provision "shell", inline: <<-SHELL
    yum install httpd wget unzip vim -y
    systemctl start httpd
    systemctl enabled httpd
    firewall-cmd --permanent --add-port=80/tcp
    firewall-cmd --permanent --zone=public --add-port=2888/tcp
    firewall-cmd --reload
    mkdir -p /tmp/finance
    cd /tmp/finance
    wget https://www.tooplate.com/zip-templates/2136_kool_form_pack.zip
    unzip -o 2136_kool_form_pack.zip
    cp -r 2136_kool_form_pack/* /var/www/html/
    cd /tmp/
    rm -rf /tmp/finance
  SHELL
```

Now let's run the VagrantFile by doing `vagrant up` and `vagrant ssh`.  
Now if you paste the ip address in the browser you will get the web page.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696267643916/f1b86d25-5c5b-4a94-b65a-a4359121990c.png align="center")

# Conclusion:

In conclusion, DevOps 2.4 delves into the world of automated website setup, streamlining processes, and boosting efficiency in website deployment. Embrace automation for a smoother web development journey.