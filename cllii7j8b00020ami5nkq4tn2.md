---
title: "🗄️🚀 DevOps 1.5: Archiving and Ubuntu Commands 📦🔑"
seoTitle: ""DevOps 1.5: Archiving & Ubuntu Commands Guide""
seoDescription: "Learn archiving using tar and zip commands in DevOps. Understand Ubuntu and Fedora differences. Enhance your Linux skills."
datePublished: Sat Aug 19 2023 21:00:50 GMT+0000 (Coordinated Universal Time)
cuid: cllii7j8b00020ami5nkq4tn2
slug: devops-15-archiving-and-ubuntu-commands
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1692472193811/fda8983e-6f37-4e3c-8ab2-1d74bb6e88be.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1692478738333/950b5e7c-0276-4145-a009-7765515ac10a.jpeg
tags: ubuntu, linux, devops, linux-for-beginners, wemakedevs

---

# Archiving Intro:

Archiving is like creating a digital "box" to store multiple files and folders. It helps keep things organized, saves space, and makes sharing easier. Just like packing items in a physical box, you bundle files into one archive file for convenience.

## Let's Start:

Currently, I am in the log directory and now let's archive the jenkins log.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692472672204/b6c11b44-1624-4a82-9705-5a8ed3cd2504.png align="center")

The `tar` command in Linux is used for archiving files and directories. It creates a single archive file by combining multiple files and folders. It can also compress the archive to save space. The name "tar" stands for "tape archive," stemming from its original use for creating backups on magnetic tape.

`tar -czvf jenkins_20072023.tar.gz jenkins` - Archiving jenkins directory command.

Let's break down the command `tar -czvf jenkins_20072023.tar.gz jenkins`:

1. `tar`: This is the command itself, which stands for "tape archive." It's used for creating and manipulating archive files.
    
2. `-czvf`: These are options and flags that modify how the `tar` command behaves:
    
    * `-c`: This flag indicates that you are creating a new archive.
        
    * `-z`: This flag tells `tar` to compress the archive using gzip compression.
        
    * `-v`: This flag stands for "verbose," and it makes the `tar` command print the files it's working on.
        
    * `-f`: This option specifies the filename of the archive you are creating. In this case, it's `jenkins_20072023.tar.gz`.
        
3. `jenkins_20072023.tar.gz`: This is the name of the archive file you are creating. It follows the format of `<filename>.tar.gz`, where `.tar.gz` indicates that the archive is compressed using gzip. The number is basically a time stamp.
    
4. `jenkins`: This is the name of the directory or file that you want to include in the archive. In this case, you are including the "jenkins" directory.
    

So, the command is creating a compressed archive file named `jenkins_20072023.tar.gz`, and it's including the contents of the "jenkins" directory in the archive while using gzip compression.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692473335057/9df3d1e6-7ad9-4b0d-ad17-78aedf4ab49a.png align="center")

As you can see zip file was created and we can see it is gzip file.

### Now let's extract the tar file in the tmp directory:

First, move the the file to `tmp/` directory as shown below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692473536249/4a9327e6-6d30-4292-b74a-20e0f22a8a08.png align="center")

`tar -xzvf jenkins_20072023.tar.gz` - To extract the tar file. `-x` is for extract. Now you can see the jenkins directory at the top.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692473831155/b3fa73de-5ab3-4f72-b73d-0578856c98b6.png align="center")

Now if you want to extract it in any other directory then `tar -xzvf jenkins_20072023.tar.gz -C /opt`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692474023175/62131e60-6346-4708-9eba-8f4bedbf09b0.png align="center")

The `tar` command, while effective, can feel somewhat dated. Opting for the `zip` and `unzip` command can offer a more straightforward approach, streamlining processes further. `zip` and `unzip` command may not be available by default. First, let's install the zip command using `yum install zip unzip -y`.

`zip -r jenkins_20072023.zip jenkins` - zip the jenkins folder to the .zip file.

`-r`: This option stands for "recursive," which means that the command will include all the files and subdirectories within the specified directory (`jenkins`) and compress them into the archive.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692474432173/ddf93fd9-4c40-4ab7-ae8e-a9182082451d.png align="center")

Now let's move this to opt directory and unzip the zipped file as shown below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692475112514/0121544a-6205-44ac-b168-2070d913359a.png align="center")

# UBUNTU COMMANDS:

Now, the majority of the commands we've covered previously work on both Ubuntu and Fedora, with just a few exceptions. As we explore the differences, you'll realize that these operating systems are more similar than not.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692475449054/da1d6ddb-d1e0-4159-a43f-03c3a770c9c0.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692475502083/04ff835e-2285-4019-ac2c-d885a85e66aa.png align="center")

`useradd devops`command doesn't work correctly in Ubuntu. So in place of `useradd` use `adduser`.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1692477252705/cf237375-d60f-49fd-b208-9dfda6430a79.png align="center")

`visudo` - In Ubuntu default video editor is nano. But if you want to change it to vim then just type `export EDITOR=vim.`

Earlier we had `yum` to install packages here we have `apt`.

`apt purge tree` - It will remove all the data and its configuration too.

# Conclusion:

In conclusion, understanding archiving techniques and the nuances of Ubuntu commands is a valuable asset in the realm of DevOps. These skills enable efficient management and manipulation of files, making system administration more streamlined and effective. Embrace the power of archiving and the command line to enhance your proficiency in the DevOps landscape. 📦🚀

> Zipping, compressing, decompressing and unzipping too much too handle. Who wants simplicity when you have archiving --- teehee.

"Feel absolutely free to drop a like, leave your thoughts, and generously sprinkle suggestions if you happen to spot even a hint of an error. Your input is more valuable than gold!" 💬👍🔍