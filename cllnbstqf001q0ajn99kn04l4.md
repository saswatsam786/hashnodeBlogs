---
title: "🚀🛠️ DevOps 2.1: Provisioning in Vagrant"
seoTitle: ""Streamlining Provisioning in Vagrant for Efficient Development""
seoDescription: ""Explore Vagrant provisioning techniques in DevOps 1.2, enhancing your infrastructure setup. Learn efficient provisioning methods for seamless development.""
datePublished: Wed Aug 23 2023 06:00:17 GMT+0000 (Coordinated Universal Time)
cuid: cllnbstqf001q0ajn99kn04l4
slug: provisioning-in-vagrant
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692759256224/d942fa70-0ae4-446e-a0e8-3ee40b548a0f.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692770375238/172faca7-d2da-4350-a29f-b9c3fb17f976.jpeg
tags: programming-blogs, linux, devops, wemakedevs, provisioning

---

# What is Provisioning?

Provisioning in Vagrant is the process of setting up and configuring a virtual machine automatically. It involves tasks like installing software, configuring settings, and preparing the VM to be in a desired state. This automation simplifies the setup of development environments, ensuring consistency and reducing manual effort.

### Let's do some testing:

Add the below code to your vagrant file:

```bash
 config.vm.provision "shell", inline: <<-SHELL
    	yum install httpd wget unzip git -y
	mkdir /opt/devopsdir
	free -m
	uptime
  SHELL
```

This will install all the things necessary while booting up - And your vagrant file may look something like this:

```bash
Vagrant.configure("2") do |config| 
    config.vm.box = "jacobw/fedora35-arm64" 
    config.vm.network "private_network", ip: "192.168.56.12"
    config.vm.provider "vmware_desktop" do |vmware|
      vmware.gui = true
      vmware.allowlist_verified = true
    end
     config.vm.provision "shell", inline: <<-SHELL
    	yum install httpd wget unzip git -y
	mkdir /opt/devopsdir
	free -m
	uptime
  SHELL
  end
```

And do `vagrant up` in your terminal where the vagrant file is present.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692765376988/700f0598-0098-4865-b613-b0f8a031d6e6.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692769734088/817b845a-e63d-4abf-ad27-7924650231b4.png align="center")

As you can see all the services have been downloaded and the output for free and uptime is also shown.

NOTE: Provisioning only happens once. If we do `vagrant reload` again it will not happen again.

You can do `vagrant provision` or use the `--provision` flag to do the provision again.

# Conclusion:

In the world of Vagrant, provisioning emerges as the magician's wand. With a few lines of code, it brings software installations, configurations, and setups to life. As we bid farewell to this provisioning chapter, we embrace the power it holds in automating our environments, making development smoother and deployments more reliable. Let's keep provisioning our way to DevOps excellence! 🪄🚀