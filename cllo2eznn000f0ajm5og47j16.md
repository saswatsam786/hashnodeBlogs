---
title: "🚀🌐 DevOps 2.3: Launch Your Website on Linux 🖥️🔥"
seoTitle: "Launch Your Website on Linux: A Step-by-Step Guide"
seoDescription: ""Learn how to launch your website on Linux with step-by-step instructions. Get your website up and running efficiently on a Linux server. 🚀🖥️""
datePublished: Wed Aug 23 2023 18:25:21 GMT+0000 (Coordinated Universal Time)
cuid: cllo2eznn000f0ajm5og47j16
slug: launch-your-website-on-linux
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692775762819/338ef169-8aa9-4f82-ab29-8df738ae7cd0.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692815022930/e1160c50-3a3a-4bb3-9c8c-f83a4066d508.webp
tags: linux, web-development, devops, services, wemakedevs

---

# Get Started:

Create a finance directory in your vms folder and run any of the vms from the vagrant box list by doing init.

```bash
mkdir finance
cd finance
```

`vagrant box list` - It will list all the vms.

And do `vagrant init <vm-name>`.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692784383173/e0d063bb-5ffb-4add-9c56-6b5282d2b811.png align="center")

Do vim Vagrantfile and do the following changes

```bash
# -*- mode: ruby -*-
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
  config.vm.box = "jacobw/fedora35-arm64"

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
   config.vm.network "private_network", ip: "192.168.56.22"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
   config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Disable the default share of the current code directory. Doing this
  # provides improved isolation between the vagrant box and your host
  # by making sure your Vagrantfile isn't accessable to the vagrant box.
  # If you use this you may want to enable additional shared subfolders as
  # shown above.
  # config.vm.synced_folder ".", "/vagrant", disabled: true

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
   config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
     vb.memory = "1024"
   end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
end
```

and start the vm by doing `vagrant up` and `vagrant ssh`.

### STEPS:

`yum install httpd wget vim unzip zip -y` - Install these services.

Do `systemctl start httpd` and `systemctl enable httpd`.

Then do `ip addr show`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692804179422/c575e4be-ddc9-415d-8e8a-1c7579729303.png align="center")

Use the IP address and open it in the host's local browser.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692804245855/b74f2111-7304-481b-b9ed-bdcbcc6e9d5e.png align="center")

If the IP does not work because you started the firewall service but did not have the correct firewall rules set up, it denies the request. With the commands below you will enable the firewall rule for port 80

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692809234662/35d71f52-ab80-4aae-b0b0-d5ce273498c6.png align="center")

If all is fine then cd into /var/www/html which you can also find on the HTTP webserver test page.

Write any content on `vim index.html` and restart the service using `systemctl restart httpd` and go to your webpage to see the change.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692809745203/efa13de9-1f6f-4fbc-ad09-61e0acb21e94.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692809933577/6d0eb218-8c87-4ea0-b332-919588badebf.png align="center")

Now let's deploy a full index.html page. You can download any HTML template from Google or from tooplate.com where you can get a zip download URL as shown below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692810155335/2d4b016b-f5d4-40d1-ba2b-92fab3a90eb8.png align="center")

Go to `/tmp` directory and do `wget` [`https://www.tooplate.com/zip-templates/2136_kool_form_pack.zip`](https://www.tooplate.com/zip-templates/2136_kool_form_pack.zip) . And unzip the content using unzip command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692814314225/a5aa3436-f38d-480c-a8ce-e0f072ce4c9d.png align="center")

Do `cp -r * /var/www/html` and do `systemctl restart httpd.`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692814436902/5755d161-cf7b-42f1-bb7e-8cf540be15e1.png align="center")

# Conclusion:

In conclusion, launching a website on Linux using the httpd service provides a straightforward and reliable method to make your web content accessible to users. The httpd service, also known as the Apache HTTP Server, acts as a powerful and flexible web server that delivers your website's content to visitors' browsers. By configuring the httpd service, setting up virtual hosts, and managing website files, you can establish a robust online presence and ensure that your web pages are efficiently served to users across the internet. Whether it's a personal blog, an e-commerce platform, or a company website, utilizing the httpd service allows you to navigate the digital landscape with ease and accessibility.

"Your thoughts and feedback are invaluable! Don't hesitate to like, share, and provide your insights to enhance this blog."