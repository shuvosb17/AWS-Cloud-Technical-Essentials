# 🚀 Introduction to Week 2: Compute and Networking on AWS

## What’s Next?

- You’ve learned AWS basics, global infrastructure, and how to set up your account.
- Last lesson: You launched an **EC2 instance** (a virtual server) to run your app.

---

## What is Compute?

- **Compute** = The power (CPU, memory, networking) needed to run your app.
- **EC2** is one way to get compute on AWS, but there are others:
    - **ECS/EKS:** Run containers (small, portable app packages)
    - **Lambda:** Run code without managing servers (serverless)

---

## Where Do EC2 Instances Live?

- Every EC2 instance must be inside a **network**.
- On AWS, this network is called a **VPC (Virtual Private Cloud)**.
- You’ll learn how to set up and use VPCs for your apps.

---

## 🖼️ Diagram: Compute and Networking

```
+-------------------+
|   User's Browser  |
+-------------------+
         |
         v
+-------------------+
|      EC2          |  <-- Compute (runs your app)
+-------------------+
         |
         v
+-------------------+
|      VPC          |  <-- Network for your EC2
+-------------------+

```

---

## 🐱 Real-World Example

Think of EC2 as renting a computer, and VPC as the private office where you keep it safe and connected.

---

**In summary:**

You’ll explore different AWS compute options (EC2, containers, serverless) and learn how to connect them using VPCs. Keep an eye on the readings for extra tips and details!


# ⚡ Compute as a Service on AWS

## What is Compute?

- **Compute** means the processing power needed to run applications—like web servers, databases, or machine learning.
- Traditionally, companies had to buy, install, and manage their own physical servers (which is slow, expensive, and hard to scale).

---

## How AWS Makes Compute Easy

- **AWS already owns and manages the servers and data centers.**
- You can quickly “rent” the computing power you need, when you need it.
- No waiting for hardware, no big upfront costs, and you can scale up or down anytime.

---

## Main Compute Options on AWS

| Service | What It Is | Example Use Case |
| --- | --- | --- |
| **EC2** | Virtual machines (like renting a PC) | Hosting a website or database |
| **Containers** | Lightweight, portable app packages | Microservices, DevOps pipelines |
| **Serverless** | Run code without managing servers | Event-driven apps, automation |

---

## 🖼️ Diagram: Compute as a Service

```
+-------------------+
|   AWS Data Center |  <-- AWS owns & manages
+-------------------+
         |
         v
+-------------------+
|   EC2 / Containers / Serverless  |  <-- You choose what fits your app
+-------------------+
         |
         v
+-------------------+
|   Your Application|
+-------------------+

```

---

## 🐱 Real-World Example

Imagine you want to open a bakery:

- **Old way:** Buy the building, ovens, and equipment yourself (takes months, costs a lot).
- **AWS way:** Rent a fully-equipped kitchen by the hour—just show up and start baking!

---

**In summary:**

AWS Compute as a Service lets you run your apps without the hassle of buying and managing servers. You pick the right compute option (EC2, containers, or serverless) for your needs, and AWS handles the rest!


# 🖥️ Introduction to Amazon Elastic Compute Cloud (EC2)

## What is EC2?

- **EC2** is an AWS web service that provides secure, resizable virtual servers in the cloud.
- You get complete control over these virtual machines (called "instances").
- Pay only for what you use (per second or hour) and stop paying when you terminate the instance.

---

## Creating an EC2 Instance

To create an instance, you need to define:

1. **Hardware specifications:** CPU, memory, network, storage
2. **Logical configurations:** Network location, firewall rules, authentication, operating system

You can create and manage EC2 instances through:

- AWS Management Console (web interface)
- AWS Command Line Interface (CLI)
- AWS Software Development Kits (SDKs)
- Automation tools

---

## 🍰 AMIs: The Recipe for Your EC2 Instance

An **Amazon Machine Image (AMI)** is like a recipe or template for your server:

- Contains the operating system
- May include pre-installed software
- Defines storage mappings and architecture type (32-bit, 64-bit, ARM)

**Relationship Between AMI and EC2:**

- **AMI** = Recipe/blueprint/class
- **EC2 Instance** = Cake/built server/object

When you launch an instance, AWS:

1. Allocates a virtual machine on a hypervisor
2. Copies the AMI to the root device volume
3. Boots the volume
4. Gives you a server you can connect to

---

## Where to Find AMIs

| AMI Type | Description |
| --- | --- |
| **Quick Start AMIs** | Pre-made by AWS for common use cases |
| **AWS Marketplace AMIs** | Third-party vendor software |
| **My AMIs** | Created from your own EC2 instances |
| **Community AMIs** | Provided by the AWS user community |
| **Custom Images** | Built with EC2 Image Builder |

Each AMI has an ID like "ami-1234abcd" that's unique to each AWS region.

---

## Choosing an Instance Type

Instance types determine hardware capabilities:

- **General Purpose (M-family):** Balanced resources (web servers, apps)
- **Compute Optimized (C-family):** More CPU power
- **Memory Optimized (R-family):** More RAM
- **Storage Optimized (D-family):** Fast local storage
- **Graphics Optimized (G-family):** GPU for graphics work

Each type comes in different sizes (nano to 24xlarge), affecting resources and cost.

---

## 🖼️ Diagram: EC2 Process Flow

```
+-------------------+         +-------------------+
|   Select AMI      |  ---->  |  Instance Type    |
|  (OS & Software)  |         |  (Hardware)       |
+-------------------+         +-------------------+
         |                              |
         v                              v
+-------------------+         +-------------------+
| • Quick Start     |         | • T3 (budget)     |
| • Marketplace     |         | • M5 (balanced)   |
| • My AMIs         |         | • C5 (CPU)        |
| • Community       |         | • R5 (memory)     |
+-------------------+         +-------------------+
                                       |
                                       v
                             +-------------------+
                             |  Running Instance |
                             +-------------------+
                                       |
                                       v
                             +-------------------+
                             | Create Custom AMI | (for reuse)
                             +-------------------+

```

---

## AMI Reusability

One big advantage of AMIs is reusability:

1. Configure an EC2 instance with your web server and application
2. Create a new AMI from that configured instance
3. Launch new instances from this AMI—all with identical configuration
4. Save time and prevent human error when launching multiple servers

---

## Benefits of EC2

- **Flexibility:** Change instance types anytime as your needs change
- **Cost optimization:** Pay only for what you use
- **Speed:** Launch new servers in minutes
- **Experimentation:** Test different configurations quickly
- **Consistency:** Use AMIs for identical server environments
- **API-driven:** Automate everything through code

---

## 🚗 Real-World Example

Imagine you're opening a car rental business:

- **AMI** = The car model (sedan, SUV, truck)
- **Instance Type** = Features (basic, luxury, sport)
- **Instance Size** = Engine size (small, medium, large)
- **Running Instance** = The actual car you drive

**Reusable AMI Example:**

You customize a car perfectly for your business, then order 10 more exactly like it rather than customizing each one separately.

---

**In summary:**

EC2 gives you virtual servers in the cloud with complete control. Choose the right AMI and instance type for your needs, and create your own AMIs to easily replicate successful server configurations!
