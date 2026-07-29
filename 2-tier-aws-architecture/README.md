# Building a Secure Two-Tier Architecture on AWS

> A secure AWS architecture demonstrating networking, private compute, scalable content delivery, and cloud best practices.

## 📖 Project Overview

This project showcases the design and implementation of a **secure two-tier architecture on Amazon Web Services (AWS)**. Rather than focusing on application complexity, the emphasis is placed on **building a resilient, secure, and scalable cloud infrastructure** that follows common production design patterns.

The solution separates the frontend and backend into dedicated layers:

- The **frontend** is hosted as a static website in **Amazon S3** and delivered globally through **Amazon CloudFront**, providing fast, secure, and highly available content delivery.
- The **backend** runs on a **private Amazon EC2 instance** with **no public IP address**, ensuring it cannot be accessed directly from the internet.
- An **Application Load Balancer (ALB)** acts as the application's only public entry point, routing incoming requests to the backend while continuously performing health checks.
- A **NAT Gateway** enables the private EC2 instance to securely access the internet for software updates without exposing it to inbound traffic.

The project demonstrates several core cloud engineering principles, including:

- 🔒 Secure network segmentation
- 🌐 High availability design
- 🚦 Controlled public access
- 📦 Static website hosting
- ⚡ Content delivery optimization
- 💰 Cost-aware storage management

---

# 🎯 Project Objectives

This project was built to demonstrate how to:

- Design a secure AWS network architecture
- Deploy compute resources in private subnets
- Expose applications through an Application Load Balancer
- Host static websites using Amazon S3
- Secure S3 access using CloudFront
- Configure lifecycle policies to reduce long-term storage costs
- Apply cloud security best practices

---

# 💡 Key Design Decisions

### Why place the backend in a private subnet?

Keeping the backend private significantly reduces the attack surface. Users never communicate directly with the EC2 instance; instead, all traffic flows through the Application Load Balancer.

---

### Why separate the frontend and backend?

Serving static content from Amazon S3 and CloudFront reduces the workload on compute resources, improves scalability, and simplifies frontend deployments.

---

### Why use an Application Load Balancer?

The ALB provides a single, controlled entry point into the application while continuously monitoring backend health and enabling future horizontal scaling.



# 📚 What I Learned

This project reinforced several important cloud engineering concepts:

- Designing secure network boundaries
- Separating frontend and backend responsibilities
- Building highly available architectures
- Troubleshooting CloudFront and S3 integrations
- Applying AWS security best practices
- Thinking beyond deployment to operational considerations such as scalability, resilience, and cost optimization

