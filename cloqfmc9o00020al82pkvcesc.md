---
title: "🚀🛠️ DevOps 5.2: Microservices 💡🐳"
seoTitle: "🚀🛠️ DevOps 5.2: Microservices 💡🐳"
seoDescription: ""Unleashing Microservices 🚀 - DevOps 5.2""
datePublished: Thu Nov 09 2023 00:09:39 GMT+0000 (Coordinated Universal Time)
cuid: cloqfmc9o00020al82pkvcesc
slug: devops-52-microservices
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1699480204025/a46e3eae-1f81-40d1-8a5f-04c1d1795d2c.jpeg
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1699488563219/debb5cb7-66a7-4810-a2b6-b6fa59caa782.jpeg
tags: microservices, docker, devops, docker-compose, wemakedevs

---

# What is Monolithic Architecture?

Monolithic architecture refers to a traditional software design approach in which an entire application is built as a single, self-contained unit. In a monolithic application, all components and functionalities, such as user interfaces, databases, and business logic, are tightly integrated and run within the same process. This architecture is in contrast to microservices, where an application is divided into smaller, loosely coupled services that can be developed, deployed, and scaled independently. Monolithic architectures are characterized by their simplicity but can become complex and difficult to maintain as applications grow in size and scope.

# What is Microservice Architecture?

Microservice architecture is a software development approach where an application is structured as a collection of loosely coupled, small, independent services that communicate with each other through well-defined APIs. Each microservice typically represents a specific piece of functionality, and they can be developed, deployed, and scaled independently. This architectural style promotes flexibility, scalability, and ease of maintenance in large and complex applications.

The key characteristics of microservices include:

1. **Independence**: Microservices are self-contained, meaning each service has its own codebase, data storage, and often its own database.
    
2. **Decentralized**: Microservices are independently developed, deployed, and managed. Teams can work on different services simultaneously.
    
3. **Lightweight Communication**: Services communicate through lightweight protocols such as HTTP/REST or message queues.
    
4. **Scalability**: Individual services can be scaled independently based on demand, making the architecture suitable for high traffic applications.
    
5. **Resilience**: Failure in one microservice doesn't necessarily bring down the entire application.
    
6. **Technology Heterogeneity**: Different services can use different technologies or programming languages as long as they expose standard APIs.
    
7. **Easy Maintenance**: Smaller codebases are easier to understand, maintain, and update.
    
8. **Rapid Development**: Microservices allow for agile and continuous development practices.
    

Microservices are often used in modern cloud-based and containerized environments, enabling organizations to build and scale applications more efficiently. However, adopting a microservices architecture comes with its own challenges, particularly in terms of managing the increased complexity of the distributed system and ensuring effective communication between services.

# Mircorservice Project:

### Emart API Architecture:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699482792080/45b67e67-19e0-417c-aa98-98dac1a77ac9.jpeg align="center")

**STEPS:**

1. Use the vagrant file from the previous blog in this series
    
2. Do `vagrant up` and `vagrant ssh` .
    
3. Go to root user using `sudo -i`.
    
4. Clone the project using `git clone` [`https://github.com/saswatsam786/emart-devops`](https://github.com/saswatsam786/emart-devops) .
    
5. cd into emart folder.
    
6. So, build using `docker compose up -d` .
    
7. To see the application live in the browser get the ip address of the VM or machine and run it on port 80
    
8. Then you can delete the container if you want using `docker compose down`.