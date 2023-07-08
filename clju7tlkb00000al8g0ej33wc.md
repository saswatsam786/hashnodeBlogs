---
title: "🔒 DevOps 1.1: Linux File Permissions Unveiled! 🚀🔐"
seoTitle: "🔒 DevOps 1.1: Linux File Permissions Unveiled! 🚀🔐"
seoDescription: "Unveil the power of Linux file permissions with DevOps 1.1! Explore secure access control and master file protection. 🔒🚀 #Linux #DevOps"
datePublished: Sat Jul 08 2023 16:23:53 GMT+0000 (Coordinated Universal Time)
cuid: clju7tlkb00000al8g0ej33wc
slug: devops-11-linux-file-permissions-unveiled
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688734617745/9cbe99b4-0acd-4f60-bbdf-a7f45fbe96e1.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1688833132263/667debd2-e5b7-46f0-a15e-03003f78323b.jpeg
tags: linux, devops, linux-for-beginners, file-permission, wemakedevs

---

#   
🔒 File Permissions in Linux: Protecting Your Data! 📂🔐

File permissions in Linux determine who can access, modify, or execute files and directories. They ensure data security and maintain system integrity. Understanding file permissions is crucial for effective Linux administration. Let's unravel the power of file permissions! 💻🔑🔒

In Linux, file permissions are represented by a set of three permissions for three different user categories: owner, group, and others.

### The Fab Four basic permission! 💻🔐:

1. **Read (r):** Allows users to view the contents of a file or list the files within a directory.
    
2. **Write (w):** Permits users to modify or update a file's content or create, rename, or delete files within a directory.
    
3. **Execute (x):** Grants users permission to run or execute a file as a program or access files within a directory.
    
4. **\-:** No permission (in place of the r, w, or x).
    

### 🔍📝 Viewing Of File Permissions:

`ls -l /bin/login` : File permission can be viewed using **<mark>ls -l</mark>**.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688735259897/aace3ab3-0018-4a73-93bb-1b3ccf1bb25e.png align="center")

**Let's decode the above result🔍💡:**

1. **\-:** First bit denotes the file type.
    
2. **rwx:** Next 3 bits are for the user of the file. (Here the user root has permission to read, write and execute.)
    
3. **r-x:** These 3 bits are for the groups. (Here the group root has permission to only read and execute)
    
4. **r-x:** Last 3 bits are for the others.
    

### 🔑🔄 Changing Ownership: Master the Art of Ownership Transfers in Linux! 💻🔧

`chown -R ansible:devops /opt/devopsdir` - chown command is used to change the ownership.

**Note -** `R` flag will recursively change the subdirectories ownership too to ansible and devops. (Be careful while using it).

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688820691948/7879ce7e-667a-483d-8a62-bae29664e63f.png align="center")

As you can see root user and root group is changed to ansible and devops respectively.

### 🔒✨ Managing Permissions For Users, Groups, and Others in Linux! 💻🔧

`chmod o-x /opt/devopsdir` - chmod command is used to add or remove permissions. In the above command execute access is been removed for others.

Note - To add access use `+` instead of `-`. For group use `g` and for user use `u`. See the below example for more understanding.

```bash
[root@bazinga ~] ls -ld /opt/devopsdir/ # Current permissions
drwxr-xr-x. 2 ansible devops 6 Jul  7 06:19 /opt/devopsdir/
[root@bazinga ~] chmod o-x /opt/devopsdir # execute permission removed for others
[root@bazinga ~] ls -ld /opt/devopsdir/
drwxr-xr--. 2 ansible devops 6 Jul  7 06:19 /opt/devopsdir/
[root@bazinga ~] chmod o-r /opt/devopsdir # read permission removed from others
[root@bazinga ~] ls -ld /opt/devopsdir/
drwxr-x---. 2 ansible devops 6 Jul  7 06:19 /opt/devopsdir/
[root@bazinga ~] chmod g+r /opt/devopsdir # read permission added to the group
[root@bazinga ~] ls -ld /opt/devopsdir/
drwxr-x---. 2 ansible devops 6 Jul  7 06:19 /opt/devopsdir/
[root@bazinga ~] chmod g+w /opt/devopsdir # write permission added to the group
[root@bazinga ~] ls -ld /opt/devopsdir/
drwxrwx---. 2 ansible devops 6 Jul  7 06:19 /opt/devopsdir/
[root@bazinga ~] su - miles # switch to miles(other user) user
[miles@bazinga ~]$ ls /opt/devopsdir # miles is other user who cannot read this directory
ls: cannot open directory '/opt/devopsdir': Permission denied
[miles@bazinga ~]$ cd /opt/devopsdir # miles cannot go(execute) to that directory
-bash: cd: /opt/devopsdir: Permission denied
[miles@bazinga ~]$ touch /opt/devopsdir/test.txt # cannot write into the directory
touch: cannot touch '/opt/devopsdir/test.txt': Permission denied
[miles@bazinga ~]$ su - aws # switch to aws (it is in the devops group)
Password: 
Last login: Wed Jul  5 06:52:47 PDT 2023 on pts/0
[aws@bazinga ~]$ id
uid=1003(aws) gid=1003(aws) groups=1003(aws),1006(devops) context=unconfined_u:unconfined_r:unconfined_t:s0-s0:c0.c1023
[aws@bazinga ~]$ ls /opt/devopsdir # can access(read) the directory
[aws@bazinga ~]$ cd /opt/devopsdir # can enter(execute) to the directory
[aws@bazinga devopsdir]$ touch awsfiles # can write to the directory
[aws@bazinga devopsdir]$ cd ..
[aws@bazinga opt]$ ls -;
ls: cannot access '-': No such file or directory
[aws@bazinga opt]$ ls -l
total 0
drwxr-xr-x. 3 root    root   17 Jun  6 04:16 dev
drwxrwx---. 2 ansible devops 22 Jul  8 06:05 devopsdir
[aws@bazinga opt]$ exit 
logout
[miles@bazinga ~]$ exit
logout
[root@bazinga ~] 
```

### 🔢✨ Managing Permissions: Numeric Method Unleashed in Linux! 💪🚀

* Uses a three digit mode number:
    
    * First digit specifies owner's permission.
        
    * Second digit specifies group permission.
        
    * Third digit represents others' permissions.
        
* Permissions are calculated by adding:
    
    * 4 (for read)
        
    * 2 (for write)
        
    * 1(for execute)
        
* Example
    
    * `chmod 640 myfile.txt`
        

# Conclusion🎉:

In conclusion, understanding file permissions in Linux is 🔑 crucial for maintaining the security and integrity of your system. With the right permissions, you can control access to files and directories, ensuring privacy and preventing unauthorized modifications. So, 🚀 dive into the world of file permissions, master the art of access control, and safeguard your Linux environment! 💻🔒

### **💻🔒 Keep learning and exploring! 🌟✨**