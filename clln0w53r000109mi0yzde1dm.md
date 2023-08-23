---
title: "🚀🔧 DevOps 2.0: Vagrant Sync Directories🖥️💾"
seoTitle: ""Vagrant Sync Directories: Easy File Sharing with Virtual Machines""
seoDescription: "Learn how to efficiently sync directories using Vagrant. Explore seamless file sharing between host and guest systems. Boost your DevOps skills! 🚀🖥️💾"
datePublished: Wed Aug 23 2023 00:54:56 GMT+0000 (Coordinated Universal Time)
cuid: clln0w53r000109mi0yzde1dm
slug: vagrant-sync-directories
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692746734559/e3fcd528-0674-4885-9964-536bf129eafa.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692751555517/09519e89-22d9-44e1-a60c-12ea37fb0254.png
tags: vagrant, linux, developer, devops, wemakedevs

---

# What is Vagrant?

Vagrant is like a magic box for your computer. It helps you create and manage virtual machines with specific settings, making it easy to set up the perfect environment for your software development or testing needs. It saves you from the hassle of manual setup and lets you share these setups with your team, ensuring everyone works in the same environment.

First, bring up the VM using `vagrant up` command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692748060858/9233c802-f18a-431f-b5b4-3c7ce483fce8.png align="center")

Take a look at the highlighted lines looking that you can understand that the **yellow circle** basically is the **path of the VM** and the **red one** is basically the **host machine path**.  
Create a `test1.txt` file in the `vagrantfile` directory. And login in to your VM.  
Go the `/vagrant` directory and do ls. You will find the `test1.txt` file over there. This is known as the sync file directory. This path sync with the host machine VM.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692750098282/20b2d8c6-4de9-4ede-b506-9a13a30e21da.png align="center")

## Create a Custom Sync Folder:

Add this line `config.vm.synced_folder "/Users/bugsbunny/Desktop/scripts", "/opt/scripts"` depending upon your path to your own vagrant file as shown below.

```bash
Vagrant.configure("2") do |config|
  # Specify the base box and its version
  config.vm.box = "spox/ubuntu-arm"
  config.vm.box_version = "1.0.0"
  
  # Configure a private network with a specific IP address
  config.vm.network "private_network", ip: "192.168.56.11"
  
  # Configure the provider (VMware Desktop in this case)
  config.vm.provider "vmware_desktop" do |vmware|
    vmware.gui = true
    vmware.allowlist_verified = true
  end
  
  # Synced folder configuration to share files between host and VM
  config.vm.synced_folder "/Users/bugsbunny/Desktop/scripts", "/opt/scripts"
end
```

exit from the VM. And do `vagrant reload` to load the settings.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692750997105/6cce0f27-2737-4ecd-aa9a-e44ee09fc814.png align="center")

Above you can see there is new sync directory created. You can have as many as sync directories in your vagrant file.

## Use of Synced Directories:

1. **Code Sharing**: One of the primary uses of synced directories is to share code and files between the host and guest machines. This is especially useful for web development, where you can write and edit code on your local machine and immediately see the changes reflected in the web server running on the guest machine.
    
2. **Development Workflow**: Synced directories streamline the development workflow by allowing developers to use their preferred tools and editors on their host machine while having the application run and be tested on the guest machine. This eliminates the need to constantly transfer files back and forth.
    
3. **Data Transfer**: Synced directories can be used to transfer data, configuration files, and other resources between the host and guest machines. This is particularly helpful for setting up environments, deploying configurations, and managing data dependencies.
    
4. **Automation and Provisioning**: When using Vagrant for provisioning and configuration management, synced directories ensure that files generated or managed by provisioning scripts are accessible to both the host and guest machines.
    
5. **Running Scripts**: You can write scripts or utilities on your host machine and execute them within the guest machine. This is valuable for automating tasks or setting up specific configurations in the guest machine.
    
6. **Collaboration**: When working on a project with multiple developers, synced directories allow each developer to work on their local machine while sharing the same codebase and resources with the team.
    
7. **Debugging and Troubleshooting**: With synced directories, you can use debugging tools and analyze logs on your local machine, even if the application is running on the guest machine. This simplifies the debugging and troubleshooting process.
    
8. **Backup and Restore**: Important project files and data can be backed up on the host machine while the application runs on the guest machine. This provides a safety net in case of any unexpected issues.
    

Overall, synced directories enhance the efficiency and flexibility of development and deployment processes, as they bridge the gap between the host and guest environments and enable seamless interaction between the two.

# Conclusion:

In the world of DevOps, synced directories in Vagrant are the bridges that connect our local creativity with the virtual realms. 🌐🔗 Seamless file sharing, coding freedom, and streamlined workflows make development a breeze. With synced directories, coding and collaborating become a synchronized symphony. 🚀📂 #DevOps #Vagrant #SyncedDirectories

> Synced directories in Vagrant: because manually copying files between your local machine and virtual environments was just too convenient." - by someone