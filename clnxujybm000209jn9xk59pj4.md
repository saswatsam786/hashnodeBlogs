---
title: "🚀🌐 DevOps 2.6: Multi-VM Vagrant Setup 🖥️🌐"
seoTitle: ""Mastering Multi-VM Vagrant Files: A DevOps Guide""
seoDescription: ""Master the Art of Multi-VM Vagrant Files: Learn How to Create and Manage Multiple Virtual Machines for Your DevOps Projects. Unlock Efficiency Today!""
datePublished: Fri Oct 20 2023 00:02:22 GMT+0000 (Coordinated Universal Time)
cuid: clnxujybm000209jn9xk59pj4
slug: devops-26-multi-vm-vagrant-setup
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697753290892/79e86191-6e6a-4d0e-a874-938790398c61.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1697760045706/35c98518-e003-4fbf-946a-3a57125d77d8.png
tags: vagrant, linux, developer, devops, wemakedevs

---

# INTRODUCTION:

In "DevOps 2.6: Multiple VM Vagrant File," we will delve into the powerful world of multi-VM Vagrant configurations. Discover how to manage and provision multiple virtual machines efficiently, unlocking new possibilities for your development and testing environments. This guide will equip you with the skills to orchestrate complex setups and network them seamlessly, all within the realm of Vagrant. Let's embark on this journey into the advanced territory of DevOps.

# STEPS:

1. Lets first create MultiVM vagrant file using chatGPT. And then we will make necessary changes to it. You can use the below prompt.
    
    * `Multivm Vagrantfile with web01 ubuntu20, web02 with ubuntu20 and db01 on fedora. Private IP for all the VMs.Provisioning for db01. Set hostname also.`
        
    * You can modify the output code as below -
        
    * ```bash
        Vagrant.configure("2") do |config|
            # Configuration for web01 (Ubuntu 20.04)
            config.vm.define "web01" do |web01|
              web01.vm.box = "spox/ubuntu-arm" 
              web01.vm.network "private_network", ip: "192.168.56.41"
              web01.vm.hostname = "web01"
            end
          
            # Configuration for web02 (Ubuntu 20.04)
            config.vm.define "web02" do |web02|
              web02.vm.box = "spox/ubuntu-arm"
              web02.vm.network "private_network", ip: "192.168.56.42"
              web02.vm.hostname = "web02"
            end
          
            # Configuration for db01 (Fedora 33) with provisioning
            config.vm.define "db01" do |db01|
              db01.vm.box = "jacobw/fedora35-arm64"
              db01.vm.network "private_network", ip: "192.168.56.43"
              db01.vm.hostname = "db01"
          
              # Provisioning script for db01
              db01.vm.provision "shell", inline: <<-SHELL
                # Add your provisioning commands here
                yum install -y wget unzip mariadb-server -y
                stystemctl start mariadb
                systemctl enable mariadb
              SHELL
            end
          end    
                        
        ```
        
2. Then do `vagrant up`.
    
3. You can authenticate to vms using `vagrant ssh <VM name>` e.g. vagrant ssh web01.
    
4. You can manage this vms using name. E.g. vagrant halt web02.
    

# Conclusion:

In the realm of DevOps and system administration, the power of multi-VM Vagrant files cannot be underestimated. They grant us the capability to create complex, interconnected environments for development, testing, and more. By mastering the art of multi-VM Vagrant setups, you're poised to unlock the full potential of your infrastructure. Whether it's replicating intricate production systems or experimenting with cutting-edge configurations, Vagrant multi-VM setups pave the way for innovation and efficiency.