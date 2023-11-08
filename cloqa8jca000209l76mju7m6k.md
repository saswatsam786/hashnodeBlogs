---
title: "DevOps 5.1: Run the project on containers"
seoTitle: "DevOps 5.1: Run the project on containers"
seoDescription: "Seamless Transition: Running Your Project on Containers 🐳🚀 - Learn how to harness the power of containerization for efficient project deployment"
datePublished: Wed Nov 08 2023 21:38:57 GMT+0000 (Coordinated Universal Time)
cuid: cloqa8jca000209l76mju7m6k
slug: devops-51-run-the-project-on-containers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1699375290798/d8990ae0-721a-4e50-b7f8-f02790b5cdb5.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1699479087872/e8a9ed6d-eef2-4fc5-b3ed-25ff85cb004e.png
tags: docker, devops, containers, docker-compose, wemakedevs

---

Previously, we constructed our project using virtual machines (VMs), and now it's time to take our project to the next level by leveraging the power of Docker. We'll break down each service into its own container, achieving a more streamlined and efficient deployment.

# What is Docker Compose?

Docker Compose is a tool for defining and running multi-container Docker applications. It allows you to describe your application's services, networks, and volumes in a single file, typically named `docker-compose.yml`. With Docker Compose, you can define a multi-container environment in a declarative way, specifying how different containers should interact, which images to use, the network configurations, and more. This simplifies the process of managing complex applications with multiple interconnected containers.

Docker Compose is particularly useful for orchestrating the deployment of applications that require several components to work together, such as web servers, databases, message brokers, and more. It simplifies tasks like starting, stopping, and scaling services and ensures that your entire application stack is consistent and can be managed as a single unit.

## Steps for Running in Docker -

1. Do `vagrant up` and `vagrant ssh` and go to the root for below VM file
    
    ```bash
    # -- mode: ruby --
    # vi: set ft=ruby :
    
    # All Vagrant configuration is done below. The "2" in Vagrant.configure
    # configures the configuration version (we support older styles for
    # backwards compatibility). Please don't change it unless you know what
    # you're doing.
    Vagrant.configure("2") do |config|
      # The most common configuration options are documented and commented below.
      # For a complete reference, please see the online documentation at
      # https://docs.vagrantup.com.
    
      # Every Vagrant development environment requires a box. You can search for
      # boxes at https://vagrantcloud.com/search.
      config.vm.box = "spox/ubuntu-arm" 
      config.vm.box_version = "1.0.0"
      config.vm.network "private_network", ip: "192.168.56.82"
      config.vm.provider "vmware_desktop" do |vmware|
        vmware.gui = true
        vmware.allowlist_verified = true
        vmware.memory = "2048"
       end
    
      # Disable automatic box update checking. If you disable this, then
      # boxes will only be checked for updates when the user runs
      # `vagrant box outdated`. This is not recommended.
      # config.vm.box_check_update = false
    
      # Create a forwarded port mapping which allows access to a specific port
      # within the machine from a port on the host machine. In the example below,
      # accessing "localhost:8080" will access port 80 on the guest machine.
      # NOTE: This will enable public access to the opened port
      # config.vm.network "forwarded_port", guest: 80, host: 8080
    
      # Create a forwarded port mapping which allows access to a specific port
      # within the machine from a port on the host machine and only allow access
      # via 127.0.0.1 to disable public access
      # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
    
      # Create a private network, which allows host-only access to the machine
      # using a specific IP.
      # config.vm.network "private_network", ip: "192.168.33.10"
    
      # Create a public network, which generally matched to bridged network.
      # Bridged networks make the machine appear as another physical device on
      # your network.
       config.vm.network "public_network"
    
      # Share an additional folder to the guest VM. The first argument is
      # the path on the host to the actual folder. The second argument is
      # the path on the guest to mount the folder. And the optional third
      # argument is a set of non-required options.
      # config.vm.synced_folder "../data", "/vagrant_data"
    
      # Provider-specific configuration so you can fine-tune various
      # backing providers for Vagrant. These expose provider-specific options.
      # Example for VirtualBox:
      #
      # config.vm.provider "virtualbox" do |vb|
      #   # Display the VirtualBox GUI when booting the machine
      #   vb.gui = true
      #
      #   # Customize the amount of memory on the VM:
      #   vb.memory = "2048"
      # end
      #
      # View the documentation for the provider you are using for more
      # information on available options.
    
      # Enable provisioning with a shell script. Additional provisioners such as
      # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
      # documentation for more information about their specific syntax and use.
       config.vm.provision "shell", inline: <<-SHELL
       sudo apt-get update
    sudo apt-get install \
        ca-certificates \
        curl \
        gnupg -y
    
    sudo install -m 0755 -d /etc/apt/keyrings
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    sudo chmod a+r /etc/apt/keyrings/docker.gpg
    echo \
      "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
      "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
      sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    sudo apt-get update
    sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
    sudo curl -L "https://github.com/docker/compose/releases/download/v2.1.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    
    chmod +x /usr/local/bin/docker-compose
       SHELL
    end
    ```
    
2. Create a directory named compose using `mkdir compose` and cd into it.
    
3. And do `wget` [`https://raw.githubusercontent.com/devopshydclub/vprofile-project/docker/compose/docker-compose.yml`](https://raw.githubusercontent.com/devopshydclub/vprofile-project/docker/compose/docker-compose.yml) .
    
4. Do `docker compose up -d`
    
    1. `docker-compose`: This command is used to interact with Docker Compose, a tool for defining and running multi-container Docker applications.
        
    2. `up`: This subcommand is used to create and start containers based on the services defined in your Docker Compose file.
        
    3. `-d` or `--detach`: This flag tells Docker Compose to run the containers in the background (detached mode). This means that the containers will be started, and you'll get your command prompt back without being attached to the containers' output.
        
5. Copy the IP address of the VM and paste it into the browser.
    
6. Now you can type `docker compose down` - The `docker-compose down` command is used to stop and remove the containers defined in your Docker Compose file. It effectively reverses the process started by `docker-compose up`.
    
7. The `docker system prune -a` command is used to remove all stopped containers, all networks not used by at least one container, all dangling images, and all build cache. The `-a` flag means it will remove all containers and images, not just the dangling ones.
    

# Conclusion:

Running multiple services on containers offers several advantages over using virtual machines:

1. **Resource Efficiency**: Containers share the host operating system, making them more resource-efficient than VMs. They consume less memory and start quickly, allowing you to run more containers on the same hardware.
    
2. **Isolation**: Containers provide process and file system isolation, ensuring that one service does not interfere with another. This isolation is less resource-intensive than full virtualization.
    
3. **Portability**: Containers encapsulate the application and its dependencies, making it easy to move and run the same container on different hosts. This portability simplifies development, testing, and deployment.
    
4. **Scalability**: Containers can be easily scaled up or down to meet changing workloads. You can run multiple instances of a service without the overhead of managing multiple VMs.
    
5. **Rapid Deployment**: Containers can be spun up in seconds, allowing for rapid deployment and scaling in response to changing demand.
    
6. **Resource Utilization**: Containers efficiently use system resources, preventing overallocation of resources that can occur with VMs.
    
7. **Ecosystem and Tooling**: The container ecosystem has a rich set of tools for container management, orchestration, and monitoring, such as Docker and Kubernetes.
    
8. **Cost-Efficiency**: Running containers generally results in cost savings as you can use resources more efficiently, and you don't need to maintain and license multiple VMs.