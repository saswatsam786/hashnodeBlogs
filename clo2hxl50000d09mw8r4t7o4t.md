---
title: "DevOps 3.3: App Setup"
seoTitle: ""DevOps 3.3: Streamline Your Application Setup for Success""
seoDescription: ""DevOps 3.3: Streamlining Application Setup for Efficient Deployment and Management.""
datePublished: Mon Oct 23 2023 06:07:54 GMT+0000 (Coordinated Universal Time)
cuid: clo2hxl50000d09mw8r4t7o4t
slug: devops-33-app-setup
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698036856158/58b1ea0b-0255-4867-8195-507b7607abf8.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1698041184652/6a09f31d-85d6-4c57-a446-ce2baa704ebb.png
tags: vagrant, linux, devops, tomcat, wemakedevs

---

# TOMCAT SETUP:

## Login to the Tomcat VM:

1. Login to the Tomcat vm
    
    ```bash
    vagrant ssh app01
    ```
    
2. Verify Hosts entry, if entries missing update them with IP and hostnames using `cat /etc/hosts` .
    
3. Update the OS to the latest patches using `yum update -y` .
    
4. Set Repository
    
    using `yum install epel-release -y` .
    
5. Install dependencies `dnf -y install java-11-openjdk java-11-openjdk-devel` .
    
    `dnf install git maven wget -y`
    
6. Change dir to /tmp
    
    `cd /tmp/`
    
7. Download the Tomcat package `wget` [`https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.75/bin/apache-tomcat-9.0.75.tar.gz`](https://archive.apache.org/dist/tomcat/tomcat-9/v9.0.75/bin/apache-tomcat-9.0.75.tar.gz)
    
8. Now extract it using `tar xzvf apache-tomcat-9.0.75.tar.gz` .
    
9. Add tomcat user `useradd --home-dir /usr/local/tomcat --shell /sbin/nologin tomcat` .
    
10. Copy data to tomcat home dir using `cp -r /tmp/apache-tomcat-9.0.75/* /usr/local/tomcat/` .
    
11. Create Tomcat service file
    
    `vi /etc/systemd/system/tomcat.service` .
    
12. Update the file with the below content
    
    ```bash
    [Unit]
    Description=Tomcat
    After=network.target
    [Service]
    User=tomcat
    WorkingDirectory=/usr/local/tomcat
    Environment=JRE_HOME=/usr/lib/jvm/jre
    Environment=JAVA_HOME=/usr/lib/jvm/jre
    Environment=CATALINA_HOME=/usr/local/tomcat
    Environment=CATALINE_BASE=/usr/local/tomcat
    ExecStart=/usr/local/tomcat/bin/catalina.sh run
    ExecStop=/usr/local/tomcat/bin/shutdown.sh
    SyslogIdentifier=tomcat-%i
    [Install]
    WantedBy=multi-user.target
    ```
    
13. Reload the files `systemctl daemon-reload` .
    
14. Start and enable the service
    
    ```bash
    # systemctl start tomcat
    # systemctl enable tomcat
    ```
    
15. Enabling the firewall and allowing port 8080 to access the tomcat.
    
    ```bash
    # systemctl start firewalld
    # systemctl enable firewalld
    # firewall-cmd --get-active-zones
    # firewall-cmd --zone=public --add-port=8080/tcp --permanent
    # firewall-cmd --reload
    ```
    

**CODE BUILD & DEPLOY (app01)**

1. Download Source code
    
    `git clone -b main` [https://github.com/saswatsam786/devops-project-local](https://github.com/saswatsam786/devops-project-local)
    
2. Update configuration
    
    ```bash
    # cd vprofile-project
    # vim src/main/resources/application.properties
    # Update file with backend server details
    ```
    
3. **Build code**
    

1. `mvn install` *run it.*
    
2. Deploy artifact
    
    ```bash
    systemctl stop tomcat
    ```
    
3. Deploy artifact
    
    ```bash
    # systemctl stop tomcat
    ```
    
    ```bash
    # rm -rf /usr/local/tomcat/webapps/ROOT*
    # cp target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war
    # systemctl start tomcat
    # chown tomcat.tomcat /usr/local/tomcat/webapps -R
    ```
    

## Next, We WILL SETUP THE NGINX!!!