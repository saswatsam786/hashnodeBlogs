---
title: "🚀💻 DevOps 3.1: VM Setup 💼🔧"
seoTitle: ""Mastering Virtual Machine Setup: DevOps 3.1 Guide""
seoDescription: ""Master VM Setup in DevOps 3.1: Streamline Your Virtual Environment for Ultimate Productivity. Get Ready to Optimize Your Workflow.""
datePublished: Sat Oct 21 2023 03:18:06 GMT+0000 (Coordinated Universal Time)
cuid: clnzgzie1000008mk7wlleqzx
slug: devops-31-vm-setup
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697855481885/21ef955c-9a0d-4be6-b966-ff5138221047.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1697858208787/26a91062-30ab-4459-95bb-9139cf4bd321.png
tags: vagrant, virtual-machine, linux, devops, wemakedevs

---

# Important Note:

Clone and go through this repository and read the PDF for the steps and better understanding - [<mark>Repo Link.</mark>](https://github.com/saswatsam786/DevOps-Java-Deployment)

# Steps:

1. First, Destroy all the previously running VMs if present.
    
2. Install this Plugin `vagrant plugin install vagrant-hostmanager` - This plugin helps manage the /etc/hosts file on your host machine and guest VMs, making it easier to access your VMs by hostname instead of IP addresses. It automatically updates the host file with entries for your Vagrant VMs, allowing you to use custom hostnames for your virtual machines. This can be especially useful when you have multiple VMs and want to access them using user-friendly names instead of remembering IP addresses.
    
3. Install this plugin too - `vagrant plugin install vagrant-vbguest` -  
    The command "vagrant plugin install vagrant-vbguest" is used to install the "vagrant-vbguest" plugin for Vagrant. This plugin is designed to help keep VirtualBox Guest Additions up to date in your Vagrant virtual machines.
    
4. Then do `vagrant up` to start the VMs. If any error occurs fix the error by googling. You can also verify by going through the entries of host file in one of the VMs.
    

### Next, we will set up DB, CACHE, and Queue Setup.