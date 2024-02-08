---
title: "🌐💻 DevOps 7.5: Exploring AWS CLI 🔧🚀"
seoTitle: "🌐💻 DevOps 7.5: Exploring AWS CLI 🔧🚀"
seoDescription: ""Unleashing the Power of AWS CLI: Navigate the Cloud with Command-Line Mastery""
datePublished: Thu Feb 08 2024 12:34:03 GMT+0000 (Coordinated Universal Time)
cuid: clsd7a6gi000909lghrdoav3u
slug: devops-75-exploring-aws-cli
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1707395576387/edf73383-c54d-4722-ab42-20007dd965bb.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1707395590736/4c1829fb-45d9-4402-8fea-6e8441ff1897.png
tags: linux, aws, cloud-computing, devops, amazon-web-services, aws-cli, wemakedevs

---

# Introduction:

AWS CLI (Command Line Interface) is a powerful tool that allows users to interact with Amazon Web Services through a command-line interface. It provides a set of commands for controlling AWS services, managing resources, and automating tasks. With AWS CLI, users can efficiently navigate and manipulate various AWS functionalities directly from the command line, streamlining the management of cloud resources. Whether you're a developer, system administrator, or DevOps professional, AWS CLI offers a flexible and efficient way to work with AWS services in a text-based environment.

## Installation:

First Install aws-cli in local computer using the installation documentation.  
For e.g. - you can use brew - `brew install awscli`

### Configuring aws-cli:

1. First we have create an IAM user.
    
2. Go to IAM dashboard. Then go "Users" present in the sidebar.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707394042380/1f4ea737-c5fa-438f-9150-cba5e21fd7c2.png align="center")
    
3. Click on create user. And go to "Next"
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707394212817/977fce98-197c-4f6d-bbb2-486e5760ed2c.png align="center")
    
4. Now set the policies. And go to "Next". And click "Create User".
    
5. So now click awscli user. Go to "security credentials"
    
6. Click on "Create Access Key".
    
7. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707394503491/4f9632b4-ed0e-45f4-9fa6-1f3069188a30.png align="center")
    
    Select Command Line Interface. And click next and next again.
    
8. <mark>NOTE: Do not reveal your access key and secret access key to anyone.</mark>
    
9. Go into your CLI and type "`aws configure`". And Enter access and secret access key.
    
10. You can enter region as us-east-1 and output as json.
    
11. All the information will be stored in this path `ls ~/.aws/` .
    
12. You can `aws ec2 describe-instances`.To show all the instances.
    

Do refer to awscli documentation for installation and commands - [https://docs.aws.amazon.com/cli/](https://docs.aws.amazon.com/cli/)

  
I trust you've mastered the art of crafting IAM users and configuring AWS CLI to seamlessly navigate the expansive world of Amazon Web Services.