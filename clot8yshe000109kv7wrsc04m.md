---
title: "DevOps 6.2: Grand Finale of Scripts"
seoTitle: "DevOps 6.2: Grand Finale of Scripts"
seoDescription: "Check the implementation of Scripts in the multi-os web setup"
datePublished: Fri Nov 10 2023 23:26:41 GMT+0000 (Coordinated Universal Time)
cuid: clot8yshe000109kv7wrsc04m
slug: devops-62-grand-finale-of-scripts
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1699658676654/2492e1af-d25c-4889-ae5c-52d0cf4dcb8a.webp
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1699658771322/a45e2e97-3566-454d-bdbd-e5b362b09eb5.webp
tags: linux, devops, bash-script, wemakedevs

---

# How to run a multi-OS web setup using a single script file?

### Steps:

1. `cd /opt/scripts`
    
2. `mkdir remote_websetup`
    
3. `cd remote_websetup` .
    
4. `vim remhosts`
    
5. Paste the below into the file
    
    ```bash
    web01
    web02
    web03
    ```
    
6. Run the following command - `for host in cat remhosts; do ssh devops@$host sudo yum install git -y;done` .
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699656307916/2e162342-39bd-4d66-91af-6f2e1fda63e4.png align="center")
    
7. Create `vim remoteweb_os.sh`
    
8. Paste the below code -
    
    ```bash
    #!/bin/bash
    
    # Variable Declaration
    #PACKAGE="httpd wget unzip"
    #SVC="httpd"
    URL='https://www.tooplate.com/zip-templates/2098_health.zip'
    ART_NAME='2098_health'
    TEMPDIR="/tmp/webfiles"
    
    yum --help &> /dev/null
    
    if [ $? -eq 0 ]
    then
       # Set Variables for CentOS
       PACKAGE="httpd wget unzip"
       SVC="httpd"
    
       echo "Running Setup on CentOS"
       # Installing Dependencies
       echo "########################################"
       echo "Installing packages."
       echo "########################################"
       sudo yum install $PACKAGE -y > /dev/null
       echo
    
       # Start & Enable Service
       echo "########################################"
       echo "Start & Enable HTTPD Service"
       echo "########################################"
       sudo systemctl start $SVC
       sudo systemctl enable $SVC
       echo
    
       # Creating Temp Directory
       echo "########################################"
       echo "Starting Artifact Deployment"
       echo "########################################"
       mkdir -p $TEMPDIR
       cd $TEMPDIR
       echo
    
       wget $URL > /dev/null
       unzip $ART_NAME.zip > /dev/null
       sudo cp -r $ART_NAME/* /var/www/html/
       echo
    
       # Bounce Service
       echo "########################################"
       echo "Restarting HTTPD service"
       echo "########################################"
       systemctl restart $SVC
       echo
    
       # Clean Up
       echo "########################################"
       echo "Removing Temporary Files"
       echo "########################################"
       rm -rf $TEMPDIR
       echo
    
       sudo systemctl status $SVC
       ls /var/www/html/
    
    else
        # Set Variables for Ubuntu
       PACKAGE="apache2 wget unzip"
       SVC="apache2"
    
       echo "Running Setup on CentOS"
       # Installing Dependencies
       echo "########################################"
       echo "Installing packages."
       echo "########################################"
       sudo apt update
       sudo apt install $PACKAGE -y > /dev/null
       echo
    
       # Start & Enable Service
       echo "########################################"
       echo "Start & Enable HTTPD Service"
       echo "########################################"
       sudo systemctl start $SVC
       sudo systemctl enable $SVC
       echo
    
       # Creating Temp Directory
       echo "########################################"
       echo "Starting Artifact Deployment"
       echo "########################################"
       mkdir -p $TEMPDIR
       cd $TEMPDIR
       echo
    
       wget $URL > /dev/null
       unzip $ART_NAME.zip > /dev/null
       sudo cp -r $ART_NAME/* /var/www/html/
       echo
    
       # Bounce Service
       echo "########################################"
       echo "Restarting HTTPD service"
       echo "########################################"
       systemctl restart $SVC
       echo
    
       # Clean Up
       echo "########################################"
       echo "Removing Temporary Files"
       echo "########################################"
       rm -rf $TEMPDIR
       echo
    
       sudo systemctl status $SVC
       ls /var/www/html/
    fi 
    ```
    
9. Run the script file to see it in action.
    

## Push the above script to all the connected VMs using another script -

1. `vim webdeploy.sh` do and paste the below code.
    
    ```bash
    #!/bin/bash
    
    # Define the username for connecting to remote hosts
    USR='devops'
    
    # Iterate through the list of hosts from the file "remhosts"
    for host in `cat remhosts`
    do
       echo
       echo "#########################################################"
       echo "Connecting to $host"
       echo "Pushing Script to $host"
       
       # Copy the script "multios_websetup.sh" to the remote host's /tmp/ directory
       scp multios_websetup.sh $USR@$host:/tmp/
       
       echo "Executing Script on $host"
       
       # Execute the script on the remote host using SSH and sudo
       ssh $USR@$host sudo /tmp/multios_websetup.sh
       
       # Remove the script from the remote host's /tmp/ directory after execution
       ssh $USR@$host sudo rm -rf /tmp/multios_websetup.sh
       
       echo "#########################################################"
       echo
    done
    ```
    
2. And then run the script to see it in action.
    
3. You can check the website by accessing the IP address of the VMs from `/etc/host` .