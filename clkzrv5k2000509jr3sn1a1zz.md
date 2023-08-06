---
title: "🐧📦 DevOps 1.3: Package Management in Linux 🚀💻"
seoTitle: ""Ultimate Guide to Linux Package Management in DevOps 📦💻""
seoDescription: "Learn about package management in Linux! Explore RPM, YUM, dependencies, and more for efficient software installation. Master DevOps with ease. 📦🐧 #Linux"
datePublished: Sun Aug 06 2023 18:23:32 GMT+0000 (Coordinated Universal Time)
cuid: clkzrv5k2000509jr3sn1a1zz
slug: package-management-in-linux
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691022624632/26f06007-7f6b-45db-848d-852314b4e657.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1691345984839/2cfab422-97d8-40ce-b153-268f0662ca95.jpeg
tags: linux, developer, package, devops, wemakedevs

---

# INTRODUCTION -

Welcome to DevOps 1.3! In this edition, we delve into the fascinating world of package management in Linux. Discover how to efficiently install, update, and manage software packages on your Linux system, empowering you to streamline your development process and enhance system stability. Let's embark on this journey of efficient package management! 📦🐧

# "Mastering Package Installation: A Manual Approach 📦💻"

`tree /var/log` - It shows a directory in a tree structure. It will show all the directories and subdirectories in a tree structure.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691325472010/1f35d4b3-8767-437d-a973-010da24ccf49.png align="center")

Above you can see the tree package is not available. So let's install it from Google.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691325659453/96bd64a8-f459-4257-9f43-2edbfcc71f3d.png align="center")

Install the package according to your system's Linux configurations. Since mine is Fedora Arch 64, I'll proceed with installing the marked package.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691325968896/a80f2791-50e3-4a18-a12b-cfc406d63e92.png align="center")

Copy the link address of that link. And use the curl command to access the link and store the output (`-o`) in a file as shown below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691326259047/4490b914-adb1-4d3d-a87d-dc70ccb69b30.png align="center")

If you do `ls` now then you will find the rpm file in your current working directory. Now let's install the package using the below command - `rpm -ivh <filename>` - `-i` flag to install, `v` is for verbose which means printing, `h` is for printing in human-readable format. e.g - `rpm -ivh tree-2.1.0-2.fc38.aarch64.rpm`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691326598489/cdcdec37-36d9-439b-ba8a-a623764efb68.png align="center")

Now let's see if the tree command is working or not.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691326651497/e4cdaa86-6d74-4689-aff4-60ddbf3ee296.png align="center")

Now you can see the directory is in a tree structure.

## ⚠️ Challenges in Manual Installation ⚙️:

During the package installation process, you may encounter prompts to install all necessary dependencies before proceeding with the package installation which is a troublesome task. E.g. below

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691328104973/6099d4e5-8c62-4012-a682-6d4246b00297.png align="center")

As you can see it shows failed dependencies.

NOTE - You can see more options in rpm by using `rpm --help`

To overcome this we can use the **YUM** package manager.

# Discover the Power of YUM: 📦🐧

YUM (Yellowdog Updater, Modified) is a package manager for Linux operating systems, designed to automate the process of installing, updating, and removing software packages. It simplifies package management by resolving dependencies and providing an easy-to-use command-line interface. YUM is commonly used in RPM-based Linux distributions such as Fedora, CentOS, and Red Hat Enterprise Linux.

Yum does all this by using some configuration files in the below directory.

`cd /etc/yum.repos.d/`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691341505025/ee484d64-269d-472d-9fd4-cd58e7946c1e.png align="center")

During the installation of the Linux operating system, these files configure access to repositories on the internet. As a result, users gain access to a range of software and packages provided by the operating system.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691341802673/9683c687-88c5-4d24-b139-d55ec9848b87.png align="center")

You can search for the package using the yum search command as shown below `yum search httpd`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691341955936/31d9a537-794f-4ac0-9d7b-05bed147b06d.png align="center")

`yum install httpd` - To install a package.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691342286336/92910dee-aeb5-4c2d-98dc-68f90ae34669.png align="center")

`yum remove httpd` - To remove that particular package.

## Package Absence: What to Do When a Package is Not Present? 📦🔍

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691342557116/948ca245-593e-429a-a863-e44b99da3850.png align="center")

For that, you can search the **internet** where you can find the steps to install **Jenkins**. In the case of fedora you can find install the below -

```bash
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
sudo dnf upgrade
# Add required dependencies for the jenkins package
sudo dnf install java-17-openjdk
sudo dnf install jenkins
sudo systemctl daemon-reload
```

```bash
# Lets go line by line - 
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
# The above code is importing the output into /etc/yum.repos.d/jenkins.repo
# file from the link 
[root@bazinga ~] cat /etc/yum.repos.d/jenkins.repo 
[jenkins]
name=Jenkins-stable
baseurl=http://pkg.jenkins.io/redhat-stable
gpgcheck=1
[root@bazinga ~]# 
# It creates the repository detail as shown above in the file.
```

```bash
sudo rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
# This key will help access the above repository
sudo dnf install java-17-openjdk
# Java jdk is installed
sudo dnf install jenkins
# Jenkins is installed
```

# Conclusion:

In conclusion, package management is a crucial aspect of Linux administration in the DevOps world. Understanding package managers like RPM and YUM empower users to efficiently install, update, and remove software packages, simplifying the management of dependencies and ensuring system stability. By mastering package management, DevOps professionals can streamline their workflow and enhance the overall efficiency of their Linux-based systems. Embrace the power of package management to optimize your DevOps journey! 📦🐧🚀

"Package management in Linux is a piece of cake! Said no one ever." - hehe 🍰🚫