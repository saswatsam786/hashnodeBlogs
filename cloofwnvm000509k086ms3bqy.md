---
title: "🚀🐋 DevOps 5.0: Embracing Containers - A Journey Into the Future 💼💡"
seoTitle: "DevOps 5.0: Embracing Containers - A Journey Into the Future"
seoDescription: "🚀🔍 DevOps 5.0: Unveiling the Container Revolution 📦💡"
datePublished: Tue Nov 07 2023 14:42:08 GMT+0000 (Coordinated Universal Time)
cuid: cloofwnvm000509k086ms3bqy
slug: devops-50-embracing-containers-a-journey-into-the-future
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1699353205711/6c2b36ba-8e7e-40aa-af57-f92f165ab103.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1699368102560/2924e31b-0c0b-4d6e-9d15-df1df7018947.jpeg
tags: docker, devops, containers, devops-articles, wemakedevs

---

# What are Containers?

Containers are a lightweight form of virtualization that allows you to package and run applications and their dependencies in isolated environments. Unlike traditional virtual machines, which emulate entire operating systems, containers share the host OS kernel but provide a consistent and isolated runtime environment for applications. This makes them highly efficient and portable, ideal for DevOps, microservices, and cloud-native application deployments. Popular containerization technologies include Docker and container orchestration platforms like Kubernetes.

***Let's take an example of a web application, say a simple website, and see how containers work:***

**Application:**  
Imagine you have a web application that includes a front-end written in JavaScript and a back-end written in Python. This application needs a specific version of Python, certain libraries, and a web server to run successfully.

**Containers:**

1. You create a container image that includes the required version of Python, the necessary libraries, and the web server.
    
2. This container image is like a standalone package containing the application code and all its dependencies. It's created from a configuration file called a Dockerfile.
    
3. You store this image in a container registry, like Docker Hub.
    
4. When you need to run your web application, you can use the container image to create and run a container instance. This instance is a lightweight, isolated environment.
    

**Advantages of Containers:**

* **Consistency:** The application runs consistently across different environments because it's packaged with all its dependencies.
    
* **Isolation:** Containers ensure that the application doesn't interfere with other applications on the same host.
    
* **Portability:** You can easily move and run containers on different systems, like a developer's laptop, a test server, or a production server.
    

So, containers, in this context, are like self-sufficient units for deploying and running applications. They simplify the process of packaging, distributing, and running software.

### Do we require VMs if we have containers ?

The need for virtual machines (VMs) alongside containers depends on your specific use case and requirements. Here are some scenarios where you might consider using VMs alongside containers:

1. **Isolation Requirements:** If your application has stringent security or isolation requirements, you might choose to run containers within VMs. This provides an additional layer of separation between your containers and the underlying host system.
    
2. **Legacy Applications:** In some cases, you might need to run legacy applications that are not containerized. VMs allow you to run these applications in an isolated environment.
    
3. **Multi-Tenancy:** When hosting applications from different users or tenants, VMs can provide strong isolation and ensure that one tenant's containers don't affect another's.
    
4. **Testing and Development:** Developers often use VMs to set up development and testing environments. While containers are lightweight and efficient for development, VMs can replicate production environments more accurately.
    
5. **Operating System Compatibility:** If your containers require a specific version of the operating system that doesn't match the host's OS, VMs can be used to run containers with the desired OS version.
    
6. **Hybrid Environments:** Some organizations have a mix of VMs and containers in their infrastructure, especially during a transition from traditional VM-based architectures to container-based ones.
    

In many cases, especially in modern cloud-native and microservices architectures, organizations are moving towards containerization and leveraging container orchestration platforms like Kubernetes. Containers provide better resource utilization, scalability, and portability.

However, the decision to use VMs alongside containers should be based on your specific requirements, including security, isolation, compatibility, and legacy application support. Both VMs and containers have their strengths, and the choice depends on your use case.

# Hands-on Docker:

1. Copy the below code and paste in the Vagrantfile and do vagrant up -
    
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
       SHELL
    end
    ```
    
2. Then do `vagrant ssh`
    
3. Check status of docker using `systemctl status docker`
    
4. Let's get an image using `docker run hellow-world` . It will just show something.
    
5. `docker images` command is used to list the container images that are currently stored on your system.
    
6. The `docker ps` command is used to list the currently running Docker containers on your system. It provides information about the containers that are active and running, along with details such as container IDs, names, status, ports, and more.
    
7. The `docker ps -a` command is used to list all containers, including both running and stopped containers, on your system.
    
8. `docker run --name web01 -d -p 9080:80 nginx` -
    
    1. Here's a breakdown of the command:
        
        * `docker run`: This is the standard command to create and run a Docker container.
            
        * `--name web01`: This option specifies the name of the container, in this case, "web01." Giving your container a name makes it easier to manage and reference it later.
            
        * `-d`: This option runs the container in "detached" mode, which means it runs in the background. The container's output won't be displayed in the current terminal session.
            
        * `-p 9080:80`: This option maps a port from the host machine to a port in the container. In this case, it maps port 9080 on your host to port 80 in the container. This means you can access the NGINX web server running in the container by navigating to [`http://localhost:9080`](http://localhost:9080) in your web browser.
            
        * `nginx`: This is the name of the Docker image you want to use to create the container. In this case, it's the official NGINX image from Docker Hub.
            
9. `docker inspect web01` - The `docker inspect` command is used to retrieve detailed information about a Docker container or image.
    
10. From docker inspect you can get the ip address of the container and see the web page using `curl http://172.17.0.2:80` .
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699357570996/ecb6d485-a63c-45f8-96db-34d32e274211.png align="center")
    
11. To access it from your web browser you can use your machines IP address with port number.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699357646309/672ef16b-7673-4a6d-be99-a854f3b35f80.png align="center")
    
12. The `docker build` command is used to build a Docker image from a set of instructions defined in a Dockerfile. When you run:
    
    1. Here's what happens:
        
        * `docker build`: This is the command used to build a Docker image.
            
        * `-t testimg`: This part of the command specifies the name and optionally a tag for the image. In this case, you're naming the image "testimg" with no specific tag. The `-t` flag is used to set the name and optional tag.
            
        * `.`: The dot (.) at the end of the command tells Docker to look for a Dockerfile in the current directory (the directory where you're running the command). The Dockerfile contains the instructions for building the image.
            
13. `docker run -d -P testimg` -
    
    1. Here's what each part of the command does:
        
        * `docker run`: This is the command to create and start a new Docker container.
            
        * `-d`: This is a flag that runs the container in detached mode, meaning it runs in the background, and the container's output is not shown in the terminal.
            
        * `-P`: This is another flag that tells Docker to publish all exposed ports to random ports on the host. It is useful when you want to access the container's services from the host machine.
            
        * `testimg`: This is the name of the Docker image that you want to use for creating the container. In this case, it's using the image named "testimg" that you presumably built previously using `docker build`.
            
14. `docker rm <Container_Name>` - To remove the containers
    
15. `docker rmi <IMAGE ID>` - To remove the images
    

### So, This is Intro to Docker and Containers!!! Do Check for more !!!