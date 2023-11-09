---
title: "DevOps 6.0: Bash Scripting 🚀✨"
seoTitle: "DevOps 6.0: Bash Scripting 🚀✨"
seoDescription: ""DevOps 6.0: Bash Scripting - Unleashing the Power of Automation 🚀💻""
datePublished: Thu Nov 09 2023 18:59:49 GMT+0000 (Coordinated Universal Time)
cuid: clorjzre5000008l6bx354svp
slug: devops-60-bash-scripting
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1699552754344/74d23407-425a-402e-a288-97082582392c.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1699556361652/bc835351-7722-47ad-b901-39c21c2a3123.png
tags: linux, bash, devops, bash-script, wemakedevs

---

# What is bash scripting?

Bash scripting is a method of automating tasks on Unix-like operating systems using the Bash shell. It involves writing sequences of commands in a script to streamline and automate repetitive tasks, making system administration and other routine processes more efficient.

# Let's create a Script:

## Steps:

1. Create directory bashscripts.
    
2. Copy the below Vagrantfile to it
    
    ```bash
    Vagrant.configure("2") do |config|
        config.vm.define "scriptbox" do |scriptbox|    
        scriptbox.vm.box = "jacobw/fedora35-arm64"
        scriptbox.vm.network "private_network", ip: "192.168.56.26"
        scriptbox.vm.hostname = "scriptbox"
        scriptbox.vm.provider "vmware_desktop" do |v|
          v.allowlist_verified = true
          v.ssh_info_public = true
            v.gui = true
        end
        scriptbox.vm.provision "shell", inline: <<-SHELL
         mv /etc/yum.repos.d/fedora-updates.repo /tmp/
         mv /etc/yum.repos.d/fedora-updates-modular.repo /tmp/
         yum clean all
         yum update
         systemctl stop firewalld
        SHELL
      end
        config.vm.define "web01" do |web01|    
        web01.vm.box = "jacobw/fedora35-arm64"
        web01.vm.network "private_network", ip: "192.168.56.27"
        web01.vm.hostname = "web01"
        web01.vm.provider "vmware_desktop" do |v|
          v.allowlist_verified = true
          v.ssh_info_public = true
            v.gui = true
        end
        web01.vm.provision "shell", inline: <<-SHELL
         mv /etc/yum.repos.d/fedora-updates.repo /tmp/
         mv /etc/yum.repos.d/fedora-updates-modular.repo /tmp/
         yum clean all
         yum update
         systemctl stop firewalld
        SHELL
      end
        config.vm.define "web02" do |web02|    
        web02.vm.box = "jacobw/fedora35-arm64"
        web02.vm.network "private_network", ip: "192.168.56.28"
        web02.vm.hostname = "web02"
        web02.vm.provider "vmware_desktop" do |v|
          v.allowlist_verified = true
          v.ssh_info_public = true
            v.gui = true
        end
        web02.vm.provision "shell", inline: <<-SHELL
         mv /etc/yum.repos.d/fedora-updates.repo /tmp/
         mv /etc/yum.repos.d/fedora-updates-modular.repo /tmp/
         yum clean all
         yum update
         systemctl stop firewalld
        SHELL
      end
        config.vm.define "web03" do |web03|    
        web03.vm.box = "spox/ubuntu-arm" 
        web03.vm.box_version = "1.0.0"
        web03.vm.network "private_network", ip: "192.168.56.29"
        web03.vm.hostname = "web03"
        web03.vm.provider "vmware_desktop" do |v|
          v.allowlist_verified = true
          v.ssh_info_public = true
            v.gui = true
        end
      end
    end
    ```
    
3. Do `vagrant up scriptbox` and `vagrant ssh` to login.
    
4. Do `sudo -i` to go to root user.
    
5. Create a directory using `mkdir /opt/scripts` .
    
6. cd into it using `cd /opt/scripts` .
    
7. Do `vim firstscript.sh` . sh is the extension for shell script but it is not necessary.
    
8. Enter the below script into it -
    
    ```bash
    #! /bin/bash
    # The above line is called a shebang, indicating that the script should be interpreted using the Bash shell.
    
    echo "Welcome to bash script"
    # Print a welcome message to the console.
    
    echo
    # Print an empty line for better readability in the console.
    
    echo "The uptime of the system is: "
    uptime
    # Display the system uptime using the 'uptime' command.
    
    echo "Memory Utilization"
    free -m
    # Display memory utilization using the 'free' command with the '-m' option to show results in megabytes.
    
    echo "Disk Utilization"
    df -h
    # Display disk utilization using the 'df' command with the '-h' option to show results in a human-readable format.
    ```
    
9. Do `./firstscript.sh` you will get permission denied because it does not have execute permission
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699554566993/4b46ecf5-5d72-4c6c-ba0b-fd9aba7bfd9f.png align="center")
    
10. So give permission using `chmod +x firstscript.sh` .
    
11. Run `./firstscript.sh` to see the output.
    

## Setup a website using script:

### Steps:

1. Create the script using `vim /opt/scripts/websetup.sh` .
    
2. Copy the below contents in the script -
    
    ```bash
    #! /bin/bash
    
    ######## Install required packages ########
    sudo yum install wget unzip httpd -y
    
    ######## Start and enable Apache HTTP server ########
    sudo systemctl start httpd
    sudo systemctl enable httpd
    
    ######## Create a temporary directory for web files ########
    mkdir -p /tmp/webfiles
    cd /tmp/webfiles
    
    ######## Download and extract a web template ########
    wget https://www.tooplate.com/zip-templates/2136_kool_form_pack.zip
    unzip 2136_kool_form_pack
    
    ######## Copy the extracted files to the web server's directory ########
    sudo cp -r 2136_kool_form_pack/* /var/www/html/
    
    ######## Restart the Apache HTTP server to apply changes ########
    sudo systemctl restart httpd
    
    ######## Clean up: Remove the temporary directory ########
    rm -rf /tmp/webfiles
    ```
    
3. Execute using `/opt/scripts/websetup.sh` .
    
4. Get the IP address of the VM and paste it on the browser to see the website live.
    

### This is how script makes the process is !!!