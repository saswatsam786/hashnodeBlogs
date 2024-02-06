---
title: "DevOps 7.1 : AWS Initial Setup"
seoTitle: "DevOps 7.1 : AWS Initial Setup"
seoDescription: ""Empower Your AWS Journey: From IAM User Creation to Billing Alarms and Website Certificate Setup""
datePublished: Tue Feb 06 2024 13:27:07 GMT+0000 (Coordinated Universal Time)
cuid: clsaeapqi000009lj6gsz7nzb
slug: devops-71-aws-initial-setup
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1707215077057/f1962323-6135-4ab7-b45a-3161924f9032.avif
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1707226009819/35a516b9-f58c-48af-a436-489ba36af1a3.avif
tags: aws, developer, cloud-computing, devops, iam

---

# Creating IAM User:

Creating an IAM user instead of directly using the root user enhances security by adhering to the principle of least privilege. IAM users allow you to assign specific permissions needed for tasks, reducing the risk associated with using the powerful and all-encompassing root user credentials. This practice improves access control, traceability, and overall security posture within AWS services

### STEP are as follows:

1. Search for IAM user in the search bar. And Click the IAM service.
    
2. Click on the Add MFA visble on the screen.
    
3. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707215441584/3b204508-4041-49d5-9cb0-12d9c531c8c9.png align="center")
    
    Give your device name e.g. myphone and select the **Authenticator app** option.
    
4. Open the APP and click on the plus button on the app.
    
5. Scan the QR and enter the two MFA codes consecutively refresh after 30 seconds each.
    
6. Now go to Users (it is present in the sidebar) and creat IAM user by clicking Create User.
    
7. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707215961150/817b04b9-18db-4594-9328-8b9d5c9c9578.png align="center")
    
    Set the below details as shown.
    
8. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707216036861/3b1a48ad-c8b3-472d-a4df-712483814645.png align="center")
    
    Click on the required fields to set permission for IAM User. And Click Next
    
9. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707216129550/1a19693a-7adc-4119-a4f3-90f72058f963.png align="center")
    
    Click next again and the click on **create user. Now download the .csv file shown in the page.**
    
10. This .csv file contains username and password to login in to the **Console sign-in URL** option shown in the page. Now click on **Return to users list.**
    
11. Let's setup MFA for the above user we had created. Click on **itadmin** (The user we just created).
    
12. Click on **security credentials and the click on Assign MFA device.**
    
13. And follow the same process we did for the root user.
    

### Let's Login through IAM User:

1. Go to IAM service and click on dashboard.
    
2. In the right side click on create alias. Give a alias name and click on create alias.
    
3. Now copy the url sign-in url below. And sign in with credentials present in the .csv file.
    
4. So now you are logged in with itadmin.
    

Now you can explore the option for the itadmin user.

# Let's Setup the Billing Alarm:

Setting up a billing alarm is crucial for cost management in AWS. It helps you monitor your usage, avoid unexpected charges, and ensures that you stay within budget constraints. This step is fundamental to maintaining financial control and optimizing your AWS resources. We will using cloudwatch service for it.

### Steps are as follow's:

1. Click on your username and select Billing and Cost Management.
    
2. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707216918271/711aac26-85fb-4d01-b3e9-b0db86e7aea1.png align="center")
    
    In the sidebar click on **Billing preferences.**
    
3. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707217091177/c7005871-768b-48de-b509-2d9bb6eb0d97.png align="center")
    
    Click on Edit option in **Invoice delivery preferences. And checkmark the field and click update**
    
4. Click Edit on Alert preferences and select the below option and click update.
    
5. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707217245413/42e23416-0a63-493c-a160-46f8a6b2776a.png align="center")
    
    Now in the search bar search for an service called CloudWatch.
    
6. In the sidebar click on All alarms and then click on **Create Alarm.**
    
7. Click on Select Metric on what you want set the alarm.
    
8. Click on Billing -&gt; Total Estimated Charge. Select the currency USD. And Click on Select Mertric.
    
9. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707220071977/5b707ea0-435d-4673-a557-d6975b518b07.png align="center")
    
    Give the threshold value up to which you want set. And then click on Next.
    
10. Click on Create Topic, give topic name and email address. And then click on Create Topic and then click on Next.
    
11. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707220383135/2fb3d62e-42e8-4df7-b5b9-cf4edfd32658.png align="center")
    
    Enter name and description of message and click Next. And then click on Create Alarm.
    
12. Confirm the subscription which is sent to your email.
    
13. Now you set your billing alarm.
    

# Create a Certificate:

We will be generating a secure certificate using AWS Certificate Manager service, enhancing the security and trustworthiness of our system.

**<mark>NOTE: This part is required only if you have purchased a domain otherwise you can skip this part.</mark>**

### Steps are as follow's:

1. Search for Certificate Manager in the AWS search bar and click on the service.
    
2. Click on the Request a Certificate button.
    
3. And then click on request a public certificate and click next.
    
4. Go to tags set key as Name and value as your domain name e.g. example.xyz
    
5. Refresh and click on the id.
    
6. In the domains part you will see cname and cname value. Copy the value and add it to record in your domain registrar.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707224369640/953f4238-c7ed-4511-bdae-1fe0f45eb163.png align="center")
    
7. If the status shows issued then validation is completed.
    

So that's how add certification to your website.

# Conclusion:

In this comprehensive guide, we've covered the essential steps for securing and optimizing your AWS environment. From creating a dedicated IAM user for enhanced security to setting up a billing alarm for financial control and ensuring trust with SSL certificates for your website. Empower your AWS journey with these foundational practices.