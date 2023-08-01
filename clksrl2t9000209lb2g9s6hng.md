---
title: "🔑🚀 DevOps 1.2: All about Sudo! 💻🔐"
seoTitle: "Mastering Sudo: A Comprehensive Guide to DevOps 1.2 and Secure System"
seoDescription: "Master Sudo commands in DevOps 1.2! Learn how to wield powerful permissions securely. Get all the details in this comprehensive guide. 💻🔒 #DevOps #Sudo"
datePublished: Tue Aug 01 2023 20:41:18 GMT+0000 (Coordinated Universal Time)
cuid: clksrl2t9000209lb2g9s6hng
slug: devops-12-all-about-sudo
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689297994740/c793db0f-5550-487b-8ace-fc6de0813da6.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1690922276698/85443620-a726-4bb7-bff7-1c6d305e1d9c.jpeg
tags: software-development, linux, devops, linux-for-beginners, wemakedevs

---

# 🔑 Sudo: Superuser Do! 🔒

Sudo is a powerful command in Unix-based operating systems, that allows users to execute commands with elevated privileges or as the "superuser" (root). It stands for "superuser do" and enables authorized users to perform administrative tasks without having to log in directly as the root user.

The use of sudo is crucial for maintaining system security and preventing unauthorized access to sensitive resources. It helps enforce the principle of least privilege by granting temporary administrative access only when necessary, reducing the risk of accidental or malicious actions that could compromise system integrity. 🛡️🔒

So, next time you need to perform administrative tasks, remember to use sudo and wield your superuser powers responsibly! ✨🔑👨‍💻

# 💡 Use cases of Sudo: Unleashing Superuser Powers! 💪🔧

`sudo -i` - Change from normal user to the root user.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690912825557/e3ba2d39-8b09-40bf-8a71-6ed514e49707.png align="center")

## 🤖🔐 Empower Any User (e.g. Ansible) to Execute Sudo Commands: 👩‍💻💪

If you run sudo in any user which is not present in the sudoers file it will show the below error -

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690919201742/84cb397d-990e-45b2-9d3c-18423f8da9b8.png align="center")

`ls -l /etc/sudoers` - To know the details about the sudoers file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690919356610/d29d8cd1-5504-4491-8cf5-f14847cf5560.png align="left")

As you can see there is **no write permission** even for the root user.

Do `visudo` to open the sudoers file in Vim and add the **101st** line to the file.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690919864389/5f44e2c7-edb6-42ac-8444-220c09a70044.png align="center")

As you can see below we are not getting the error anymore:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690920195929/3e3e11bb-9277-4d58-b13c-21d1523b0ae9.png align="center")

If you want to **remove the asking for a password** which is not required when we are executing scripts in the background then add this to the **101** line. This below line will ensure to not ask ansible for its own password when executing sudo -

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690920530171/94553fc5-c328-4721-9a30-409dcf0f1699.png align="center")

**NOTE** \- If there is a syntax error or human error in the sudoers file then it will detect it and ask for an edit.  
If you don't have a root user password (generally it is not there due to security reasons) then it will be difficult to fix the error.

## 🛡️👩‍💻 Forge Your Own Sudoers File -

So a better solution is to go to `/etc/sudoers. d/` directory and create your **own file** -

```bash
[root@bazinga ~] cd /etc/sudoers.d/
[root@bazinga sudoers.d] ls
vagrant
[root@bazinga sudoers.d] cat vagrant
Defaults:vagrant !fqdn
Defaults:vagrant !requiretty
vagrant ALL=(ALL) NOPASSWD: ALL
[root@bazinga sudoers.d] cp vagrant devops
[root@bazinga sudoers.d] vim devops

[No write since last change]
/bin/bash: line 1: wq: command not found

shell returned 127

Press ENTER or type command to continue
[root@bazinga sudoers.d] cat devops. # percentile to denote it for groups
%devops ALL=(ALL) NOPASSWD: ALL
[root@bazinga sudoers.d] cat *
%devops ALL=(ALL) NOPASSWD: ALL
Defaults:vagrant !fqdn
Defaults:vagrant !requiretty
vagrant ALL=(ALL) NOPASSWD: ALL
[root@bazinga sudoers.d] 
```

So now any **user** who belongs to group devops can do **sudo.** It is a safer option than editing the file.

There is more to sudoers file like you can also give special commands to execute in the sudoers file too.

# Conclusion:

🔚🎉 In a world filled with code and commands, you've reached the end of this epic journey! 🌟🌈 The tale of Sudo, the magical command that grants power, has unfolded before your eyes. 🛡️👀 From understanding its purpose to exploring its use cases, you've delved into the depths of system administration. 💻🔍

🧙‍♂️ With the knowledge of Sudo, you can now wield the mighty power to execute commands as a superuser. 👩‍💻🔮 Your path to becoming a tech wizard has been illuminated, and you hold the key to unlocking the full potential of your system. 🌠💡

> Remember with great power comes great responsibility - "a sudo user"