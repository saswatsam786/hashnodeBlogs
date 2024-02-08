---
title: "🚀💾 DevOps 7.6: Mastering EBS (Elastic Block Storage) 🌐🔍"
seoTitle: "🚀💾 DevOps 7.6: Mastering EBS (Elastic Block Storage) 🌐🔍"
seoDescription: ""Unlock the Power of AWS EBS! Learn to Optimize Elastic Block Storage for Scalability and Reliability. Dive Deep into Storage Management with DevOps""
datePublished: Thu Feb 08 2024 17:35:36 GMT+0000 (Coordinated Universal Time)
cuid: clsdi1z1b00000aleba8yabzm
slug: devops-76-mastering-ebs-elastic-block-storage
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1707396158171/272a3dc3-2e08-4f65-9119-eb858afbfb32.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1707413703398/3a7da9a6-89be-4d47-a2ed-00268d3df29d.png
tags: linux, aws, cloud-computing, devops, snapshot, ebs, wemakedevs

---

# Introduction:

Elastic Block Storage (EBS) is a scalable and high-performance block storage service on AWS, offering reliable and flexible storage volumes for EC2 instances. With EBS, you can easily attach and detach volumes to EC2 instances, providing durable and low-latency storage solutions for various applications and workloads. Dive into the world of EBS to harness the full potential of AWS storage capabilities.

# EBS Types ?

Amazon EBS (Elastic Block Store) offers different types of volumes to cater to diverse performance and cost requirements. Here are the main types:

1. **General Purpose (gp2):**
    
    * Suitable for a broad range of workloads.
        
    * Balanced performance of 3 IOPS per GB with up to 16,000 IOPS and a throughput of 250 MiB/s.
        
    * Cost-effective choice for various applications.
        
2. **Provisioned IOPS (io1):**
    
    * Designed for I/O-intensive applications such as large relational or NoSQL databases.
        
    * Allows provision of a specific amount of IOPS (Input/Output Operations Per Second) per volume.
        
    * Suitable for applications that require predictable and high-performance storage.
        
3. **Throughput Optimized (st1):**
    
    * Ideal for frequently accessed, large datasets.
        
    * Optimized for throughput rather than IOPS.
        
    * Cost-effective for big data, data warehousing, and log processing.
        
4. **Cold HDD (sc1):**
    
    * Lowest cost per gigabyte EBS volume.
        
    * Suited for less frequently accessed workloads with large amounts of cold data.
        
    * Ideal for scenarios where the lowest storage cost is a priority.
        
5. **Magnetic (standard):**
    
    * Legacy storage type.
        
    * Lowest cost per gigabyte among EBS volume types.
        
    * Suitable for workloads where data access is infrequent.
        

Choosing the right EBS type depends on your application's specific performance and cost requirements.

## Lets Get Started:

For this blog we have to create an Centos EC2 instance with below provisioning details -

### Steps are as follow's:

1. You can follow the same steps for launching an instance.  
    [https://saswatblogs.hashnode.dev/devops-72-getting-started-with-ec2](https://saswatblogs.hashnode.dev/devops-72-getting-started-with-ec2)
    
2. ssh into your intsance (refer to the above link).
    
3. ```bash
    #!/bin/bash
    yum install httpd wget unzip -y
    systemctl start httpd
    systemctl enable httpd
    cd /tmp
    wget https://www.tooplate.com/zip-templates/2119_gymso_fitness.zip
    unzip -o 2119_gymso_fitness.zip
    cp -r 2119_gymso_fitness/* /var/www/html/
    systemctl restart httpd
    ```
    
4. Enter the above details in the shell.
    
5. Now let's get back to the storage tab present in the instance. Go to the volume section and name the volume.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707404182854/5384590f-0f66-4d3e-98e7-d2297a4aa725.png align="center")
    
6. So, we hosted an web service, which has images. So our requirement is to store that image in separate volume. Click on "Create Volume".
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707404437405/a2fe9d92-31d3-425b-87b2-d249578eeef4.png align="center")
    
7. You can fill the above details but ensure that the instance and volume should be in the same availability zone. And Create the Volume.
    
8. Now select the volume. And Click on Actions and Attach the volume as shown.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707404634896/1919988e-e997-4e0b-9408-11ce8b0905aa.png align="center")
    
9. Select the instance and Click "Attach".
    
10. Now let's go to shell and type `fdisk -l` - It shows information about the available disks on the system.
    
11. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707404924884/fa6005bd-3086-41fa-be32-76ffb5c1cca1.png align="center")
    
    You can see /dev/xvdf of 5gb we created has been attached.
    
    NOTE: The `df -h` command is used to display information about disk space usage on the system.
    
12. **Lets create a partion.** You can follow the below screenshot for it.
    
13. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707405900096/a61be52d-718a-45d2-99c8-3a9b64e3d23f.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707405998764/e7399a46-dec6-47eb-9836-9516afc3ee9c.png align="center")
    
    Now if you do `fdisk -l` , you can see the partition.
    
14. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707406075530/0abfe929-33be-4269-bebb-81c21716b3f6.png align="center")
    
    So next part is formatting it. Linux basically provides multiple utility for formatting.
    
15. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707406419429/bd0fe6a3-5f19-4e21-a243-f3847eb11fdf.png align="center")
    
    So with the above we can see the partitioning is formatted with extension4.  
    Using the command `mkfs.ext4` - This command is used to create an ext4 file system on a Linux system.
    
16. Formatting is done. Now let's mount it.
    
17. Below you can see all the images have been moved /tmp/img-backups. First we will do temporary mounts.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707406660026/097e7b93-d554-4ea2-a1c5-72978bbbc341.png align="center")
    
18. You can see below the disk is mounted and you can see the space used.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707406927308/68a0a0f4-88f6-4a4e-8c43-ed2f0076f250.png align="center")
    
19. To unmount you can use -
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707407074289/1de07ca4-5938-4c4d-9c77-7deb7f50d75a.png align="center")
    
20. The above was temporary mount for permanent mount we have to do the following.
    
21. Do `vi /etc/fstab` - `/etc/fstab` which is a system configuration file on Linux systems that controls how disk partitions or logical volumes are mounted and used. Each line in the file represents a different file system or partition.
    
22. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707407922852/8e8f9688-a614-4e97-8702-1b9feda398b5.png align="center")
    
    Add the last line as shown. And do `mount -a` to apply changes. Follow the below image to permanently mount.
    
23. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707408125415/45a7c88f-6c97-4421-a08d-3075f630518a.png align="center")
    
    You can verify the same by doing `ls /var/www/html/images` and check the website if it is images is visible.
    

# EBS Snapshots:

### Steps:

1. First let's umount the above using - `umount /var/www/html/images` .  
    And then detach the volume from the volumes dashboard using detach volume option in the actions. And you should also delete the unused volume to avoid charges.
    
2. Same way create another volume named db01 as discussed above. And attach it to the ec2 instance.
    
3. Go to your shell and format it as shown below
    
4. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707409501600/7695da80-abd2-4b27-b717-e1840a1a17a7.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707409599349/d1d7284c-ed98-480b-8092-ae97af0addf5.png align="center")
    
    Now we are going to mount it -
    
5. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707410004379/85796b96-ab5d-4991-bb93-55d7f1f2d36b.png align="center")
    
6. Match the below contents for /etc/fstab file -
    
    ```bash
    #
    # /etc/fstab
    # Created by anaconda on Mon Dec 19 11:24:05 2022
    #
    # Accessible filesystems, by reference, are maintained under '/dev/disk/'.
    # See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info.
    #
    # After editing this file, run 'systemctl daemon-reload' to update systemd
    # units generated from this file.
    #
    UUID=d5ae404e-d570-441c-bd68-fb544b5ebbb9 /                       xfs     defaults        0 0
    /dev/xvdf1      /var/lib/mysql  ext4 defaults   0 0
    ```
    
7. Check it is mounted -
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707410116243/21513bd5-4ef9-4f1b-974f-bf716a2c6b0a.png align="center")
    
8. Now we are going to install mysql service - `yum install mariadb-server -y` and start the service as follows.
    
9. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707410475017/079b599b-c050-4f88-979f-40d5df523178.png align="center")
    
    Here below you can see the db data.
    
10. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707410614373/ec09810b-cd25-4403-ac02-de8d68d127d0.png align="center")
    
    **What will happen if the data is deleted ? That is where snapshot comes in.**
    
    1) First you have to unmount the partition.  
    2) Then detach volume which is corrupted.  
    3) Create new volume from the snapshot.  
    4) Attach the volume created from snapshot.  
    5) Mount it back.
    
11. So first select the volume and in actions, select on "Create Snapshot". And fill the details and submit.
    
12. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707411581241/6e04d607-4f15-44ca-a442-af664ca64727.png align="center")
    
    Now lets delete the data as shown below -
    
13. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707411684145/9f605cb6-b316-4e6f-ace2-c32088874188.png align="center")
    
    Unmount it -
    
14. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707412248414/d9745495-c750-4881-94fb-643442da60d7.png align="center")
    
    Now detach that particular volume for volume dashboard in aws.
    
15. So now you can go to snapshots and select the snapshot and in actions you can select "Create Volume".
    
16. Go through the selections and create volume.
    
17. And attach the volume to the instance. Now we can see we have got all the data.
    
18. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707413116243/08c4a4e1-d46e-44e7-9f4d-a19b32a5d936.png align="center")
    
    So this is how you recover your data
    

Now terminate all the instance and delete all the EBS to avoid charges.

# 🌐💡Conclusion💾🚀:

In this journey through Elastic Block Storage (EBS), we delved into its nuances, understanding the types of EBS volumes, how to attach and detach them, and the critical concept of snapshots. Snapshots provide data redundancy and recovery capabilities, offering a safeguard for your valuable data.

📸 **Snapshot Safeguard:** We learned about creating snapshots, which capture the state of your EBS volumes at a specific point. These snapshots act as backups, enabling you to restore or clone volumes, ensuring the resilience and durability of your data.

🔜 **Next Stop: Elastic Load Balancing:** Stay tuned for the next installment where we explore the dynamic world of Elastic Load Balancing (ELB), optimizing the distribution of incoming application traffic across multiple targets. Elevate your AWS mastery with our upcoming insights into ELB.