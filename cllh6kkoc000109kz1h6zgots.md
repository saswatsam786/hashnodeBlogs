---
title: "🔧🚀 DevOps 1.4: Unraveling Services and Processes"
seoTitle: "Understanding Linux Services and Processes: Basics and Management"
seoDescription: "Learn about managing services and processes in Linux. Understand how systemctl works, and master the art of keeping things running smoothly."
datePublished: Fri Aug 18 2023 22:47:17 GMT+0000 (Coordinated Universal Time)
cuid: cllh6kkoc000109kz1h6zgots
slug: devops-14-unraveling-services-and-processes
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692333474112/43fe5f0d-21aa-4ad8-98bd-f8afdf0e1130.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692398688902/d9638fb5-ca56-41cb-bbe6-44f9fdf1ac48.png
tags: linux, developer, devops, services, wemakedevs

---

# Services in Linux:

In Linux, services are background programs that run automatically when your system starts. They manage various tasks, like handling network connections or running applications. For example, the "SSH" service allows remote login to a computer, while the "Apache" service powers web servers. Services ensure essential functions are always available, making your system efficient and user-friendly.

Earlier we installed a package httpd: Let's check that -

So we had earlier installed a package name httpd which can be managed by the systemctl command -

`systemctl` is a command in Linux used to control and manage systemd services, which are background processes that handle various system tasks. It allows users to start, stop, enable, disable, and check the status of services, making system administration more efficient. For more understanding checkout the below

`systemctl status httpd` - Shows the status of the the service

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692334521215/4c524ccb-424d-4739-b63e-24d839c8ee4a.png align="center")

As you can see the status is inactive. Now if you want to start the service we can use `systemctl start httpd`.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692334676115/cebf0ecb-e2b0-4615-9afe-6966afb47462.png align="center")

`systemctl restart httpd` - This command will restart the httpd service.

`systemctl reload httpd` - Unlike the `restart` command, the `reload` command doesn't stop and start the service. Instead, it causes the web server to reload its configuration files and apply any changes without interrupting active connections.

NOTE: While booting up, this service will not come up.

## To get the service at the boot time:

`systemctl enable httpd` - After booting up service will come up. Use this command before booting up and then start the service.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692353995929/fc5980a8-324a-4a02-875f-e9d63a052718.png align="center")

## Few Other Commands:

`systemctl is-active httpd` : To check if the service is active.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692354216193/0b80d6a6-de59-4519-a8ce-3ecab387c27c.png align="center")

`sytemctl is-enabled httpd`: To check if the service is enabled for the boot time or not.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692354299143/4483b99d-a09a-4a37-9318-bc7264bd7a5f.png align="center")

The way `systemct` works is based on its configuration file.

In Linux, the `systemctl` command is used for controlling and managing systemd units, which can be services, sockets, devices, etc. Systemd units are defined using configuration files that are typically stored in the `/etc/systemd/system/` directory.

```bash
[root@bazinga ~] cat /etc/systemd/system/multi-user.target.wants/httpd.service 
# See httpd.service(8) for more information on using the httpd service.

# Modifying this file in-place is not recommended, because changes
# will be overwritten during package upgrades.  To customize the
# behaviour, run "systemctl edit httpd" to create an override unit.

# For example, to pass additional options (such as -D definitions) to
# the httpd binary at startup, create an override unit (as is done by
# systemctl edit) and enter the following:

#	[Service]
#	Environment=OPTIONS=-DMY_DEFINE

[Unit]
Description=The Apache HTTP Server
Wants=httpd-init.service
After=network.target remote-fs.target nss-lookup.target httpd-init.service
Documentation=man:httpd.service(8)

[Service]
Type=notify
Environment=LANG=C

ExecStart=/usr/sbin/httpd $OPTIONS -DFOREGROUND # This the binary which runs with some options when we start the service
ExecReload=/usr/sbin/httpd $OPTIONS -k graceful
# Send SIGWINCH for graceful stop
KillSignal=SIGWINCH
KillMode=mixed
PrivateTmp=true
OOMPolicy=continue

[Install]
WantedBy=multi-user.target
[root@bazinga ~]#
```

# Linux Processes:

In Linux, processes are like tasks that your computer runs to accomplish various things. Just like how you might have different apps open on your phone, each doing its own job, your computer runs processes to handle tasks such as running programs, managing files, or handling network connections. Every process has its own space to work in and interacts with the computer's resources, like memory and CPU. Linux is really good at managing these processes, making sure they run smoothly and efficiently, just like a conductor in an orchestra making sure all the instruments play in harmony.

`top` - It provides a real-time overview of the system's resource utilization and running processes.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692355565161/a6f453b7-ce1f-498a-bbc6-30751b248ec3.png align="center")

* **System Information**:
    
    * **Uptime**: Displays how long the system has been running.
        
    * **Load Average**: This shows the system's average workload over different time periods.
        
* **Tasks Information:**
    
    * **Total Tasks:** Number of running processes.
        
    * **Running Tasks:** Processes currently executing.
        
    * **Sleeping Tasks:** Processes in a waiting state.
        
    * **Stopped Tasks:** Processes paused or stopped.
        
    * **Zombie Tasks:** Processes that have finished but not been cleaned up.
        
* **CPU Usage:**
    
    * **CPU Usage:** Percentage of CPU being used.
        
    * **CPU States:** Breakdown of CPU activity (user, system, idle, etc.).
        
* **Memory Usage:**
    
    * **Total Memory:** The system's total available RAM.
        
    * **Used Memory:** How much RAM is currently in use?
        
    * **Free Memory:** Available, unused RAM.
        
    * **Buffers and Cache:** Memory used for temporary data storage.
        
* **Process List:**
    
    * **Process ID (PID):** Unique identification for each process.
        
    * **User:** Owner of the process.
        
    * **CPU %:** Percentage of CPU used by the process.
        
    * **Memory %:** Percentage of memory used by the process.
        
    * **Command:** Name of the command or program being executed.
        

`ps aux` - It just displays the information and quits.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692395467153/0822b8e5-33c9-444d-9e68-7d531d8bbea5.png align="center")

`ps -ef` - It shows the parent process id and some extra information. In the below image, you can see PID 1 has PPID 0 which is not present because it's dead or it has completed its execution.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692395675505/27fc5ca4-ab1f-45b5-b356-6f7c4b5ef924.png align="center")

`ps -ef | grep httpd` - Show the processes which have httpd word in it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692396203765/89fc94c5-8243-4b9c-a85e-947afaf9b366.png align="center")

`ps -ef | grep httpd | grep -v 'grep'` - Show the processes which have httpd in it excluding the word grep from it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692396265148/8935df4a-4c11-4af6-9308-29f3845f0017.png align="center")

`kill <process id>` - It will kill the process with that id and all the processes derived from it. E.g. `kill 764` It will kill all the process.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692396434460/794dba0e-2e84-42b6-a35f-61e2bac62afa.png align="center")

`kill -9 <process id>` - It will force kill that process, but it may or may not kill its child processes depending upon the system. The child processes become orphan and it gets adopted by the systems processes.

`ps -ef | grep httpd | grep -v 'grep' | awk '{print $2}'` - Prints column 2 of the table.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692397994560/70691a91-5054-4cde-ac80-b49bbf133184.png align="center")

`ps -ef | grep httpd | grep -v 'grep' | awk '{print $2}' | xargs kill -9` - It takes column 2 as an argument and deletes the processes.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692398111981/fcb90f77-29fc-41b4-b701-82d879e2819b.png align="center")

`NOTE` - You can identify the zombie process by seeing status Z. Best way to clear the zombie process is to reboot your machine.

# Conclusion:

🔧🔄 In the world of Linux and DevOps, understanding services and processes is like unraveling the heartbeat of your system. From systemctl commands to managing processes, you've gained insights into the core of system management. Now you're ready to orchestrate with confidence! 💻🚀 #DevOps #Linux #SystemManagement.

> "Managing services and processes in Linux is a piece of cake, said - no one ever! 🍰🔥 #LinuxChallenges"