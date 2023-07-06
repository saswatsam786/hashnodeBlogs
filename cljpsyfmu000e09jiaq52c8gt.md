---
title: "🚀 DevOps 1.0: Linux Users & Groups Simplified! 💻👥"
seoTitle: ""Master Linux User and Group Management: DevOps 1.0 Simplified!""
seoDescription: "Simplify Linux user and group management with DevOps 1.0! Learn to streamline operations and enhance collaboration. 💻👥 #Linux #DevOps"
datePublished: Wed Jul 05 2023 14:16:40 GMT+0000 (Coordinated Universal Time)
cuid: cljpsyfmu000e09jiaq52c8gt
slug: linux-users-groups-simplified
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688566293314/93f3e033-da69-4a3b-b9d5-39d559ffd099.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1688566445431/b94febbb-6a91-4132-bccc-ebb68d297fc0.jpeg
tags: linux, devops, devops-articles, linux-commands, wemakedevs

---

# Prerequisites:

1. Basic familiarity with the Linux operating system.
    
2. Understanding of command-line interface (CLI) and basic shell commands.
    

# 👥🔑 User and Group in Linux: A Brief Overview -

In Linux, users and groups play essential roles in system administration and security.

**👤 User:** A user represents an individual or entity interacting with the system. Each user has a unique username and associated attributes, such as a user ID (UID) and a home directory. Users are granted specific permissions and can execute various operations on the system.

**👥 Group:** A group is a collection of users with common permissions or administrative purposes. Group membership allows users to share files, directories, and permissions, simplifying access management. Each group has a group ID (GID) and is associated with certain privileges and ownership settings.

🔒 Effective user and group management ensures proper security, resource allocation, and collaboration within a Linux environment. Understanding these concepts empowers administrators to control access, maintain system integrity, and streamline workflows efficiently.

Remember, mastering user and group management is crucial for maintaining a secure and well-organized Linux system. 🚀🐧

## 🔑 Key Insights on User Management: Linux Edition! 💡👥

### Here are some crucial points to know about managing users in Linux: 📌

* Users and groups are used to control access to files and resources.
    
* Users log in to the system by supplying their username and password.
    
* Every file on the system is owned by a user and associated with a group.
    
* Every process has an owner and group affiliation, and can only access the resources its owner or group can access.
    
* Every user of the system is assigned a unique user ID number ( the UID).
    
* Users name and UID are stored in `/etc/passwd`.
    
* The user's password is stored in `/etc/shadow` in encrypted form.
    
* Users are assigned a home directory and a program that is run when they log in **(Usually a Shell).**
    
* Users cannot read, write or execute each other's files without permission.
    

##   
🔢👤 Types of Users: Exploring User Roles in Linux! 🚀👥

* **Regular User:** 🙎‍♂️🙎‍♀️ Regular users, also known as standard users, are the most common type of users. They have limited system privileges and typically interact with the system to perform day-to-day tasks and run applications.
    
* **Root User (Superuser):** 🧑‍💻🔑 The root user, also called the superuser, holds the highest level of administrative privileges. This user has unrestricted access to all system resources and can make critical changes to the system. However, it is important to use the root account cautiously to avoid accidental damage.
    
* **Service Account:** 🤖👥 Service accounts are used to run background services, daemons, or automated processes. They are created specifically for running specific services or applications and often have limited shell access or no login capabilities.
    

| *TYPE* | *EXAMPLE* | *USER ID (UID)* | *GROUP ID (GID)* | *HOME DddIR* | *SHELL* |
| --- | --- | --- | --- | --- | --- |
| ROOT | root | 0 | 0 | /root | /bin/bash |
| REGULAR | saswat, vagrant | 1000 to 60000 | 1000 to 60000 | /home/username | /bin/bash |
| SERVICE | ftp, ssh, apache | 1 to 999 | 1 to 999 | /var/ftp etc | /sbin/nologin |

#   
💻🔧 Linux User & Group Management: Essential Commands! 🛠️👥

* `cat /etc/passwd` \- the contents of the <mark>/etc/passwd</mark> file. This file is a system database that stores essential information about user accounts on the system. Below are all the system users -
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688498885775/bc4bb2ca-87ca-4ffe-ab7f-55644e16183a.png align="center")
    
* `head -1 /etc/passwd` - Displays the top user.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688499235203/6ccf5a03-6329-4223-b5e1-1de8143e7fbc.png align="center")
    
    The above line has 7 columns separated by `:`
    
    1) Username
    
    2) Link to the shadow file. (Shadow file will hold the password encrypted)
    
    3) Root ID - It is user ID. 0 for root.
    
    4) Group ID - It is group ID. 0 for root.
    
    5) Comment
    
    6) Home dir of the root user.
    
    7) Login Shell
    
* `grep vagrant /etc/passwd` - Command to search for any user ID in <mark>/etc/passwd</mark> file. E.g. Search command for vagrant user.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688503227764/f7e50211-7073-4386-a7cf-dbeb7d3e2be6.png align="center")

* `cat /etc/group` - Command to get all the groups.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688503441719/122a270e-e2db-4c3c-95ed-6a52b7e707b2.png align="center")
    

**NOTE** - The is similarity in group and user naming and display.

Search for vargrant in user and group using the grep command given below to see the similarity.

```bash
grep vagrant /etc/passwd
grep vargrant /etc/group
```

* `id vagrant`\- It gives information about the user.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688503845362/a95bba25-e043-4962-b35d-25fc8c60189a.png align="center")
    
* `useradd aws`\- Command to add user. E.g aws user gets add.
    
    ```bash
    useradd ansible
    useradd jenkins
    useradd aws
    ```
    
    To check if users is been added just check the /etc/passwd file.
    
    `tail -3 /etc/passwd`
    
    **NOTE** \- When a user gets created then a group is also created.
    
* `groupadd devops` - Creates a group named devops.
    
* `usermod -aG devops ansible` - It adds ansible user to devops group.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688561467034/75aaee03-b39b-47f6-90ac-b27f71cb246d.png align="center")
    
    Above picture you can see ansible is present in devops group.
    
* `grep devops /etc/group` - It search for the devops group from <mark>/etc/group</mark> file.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688563728178/2366bca4-af1f-47f5-a0e0-1b1d26dbb0bf.png align="center")
    
    Above you can see ansible is present in the devops group.
    
    **Another way adding of adding user into the group** is by directly editing the <mark>/etc/passwd</mark> file using the command `vim /etc/group`.
    

## 🔒💻 Setting User Password: Securing User Accounts in Linux! 💡🔐

### Execute the below command in root user -

`passwd ansible` - It will set the passwd for the user ansible.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688564503291/81e03cf0-9695-4252-8de5-aa0fb4d6dc9c.png align="center")

**NOTE** - To reset the passwd it can all be done in root user

### 🚀👥 Switching Users💻🔄:

`su - ansible` - To switch to ansible user. It will ask for password depending upon the user.

NOTE - If your switching from root user then the password is not required. Password is required if your switching from one regular user to another regular user.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688565206595/94b81c1b-2b7d-4654-b50c-efc3c376e209.png align="center")

Type `exit` to logout from the current user.

## 🛠️🔧 Some More Handy Linux Commands:

* `last` - It shows the users who logged into the system.
    
* `who` and `whoami` - It will show current login user.
    
* `lsof -u username` - It will list all the files opened by the user.
    
* `userdel -r aws` - It will delete the user with its home directory.
    
* `groupdel devops` - To delete group.
    

## 📚🌟 Hope you found this article insightful and enjoyed exploring new concepts! Happy Learning and Upskilling! 🎉📖💡

**"DevOps is not a goal, but a never-ending process of continual improvement." - Jez Humble, Co-author of "Continuous Delivery" 🌟🔧**