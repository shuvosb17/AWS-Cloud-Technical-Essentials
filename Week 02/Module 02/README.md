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



# 🔄 Amazon EC2 Instance Lifecycle: 

## What Makes Up an EC2 Instance?

An EC2 instance is a combination of:
- **vCPUs** (virtual processors)
- **Memory** (RAM)
- **Network** capacity
- **Storage** (sometimes local, sometimes external)
- **GPUs** (for graphics-intensive work, optional)

---

## Instance Types and Families

Instance types follow a naming pattern: **c5.large**
- **c5** = instance family and generation (5th generation compute-optimized)
- **large** = size/capacity

### Instance Family Types

| Family Type | Best For | Example Use Cases |
|-------------|----------|-------------------|
| **General Purpose** | Balanced resources | Web servers, small databases |
| **Compute Optimized** | CPU-heavy tasks | Scientific computing, gaming servers |
| **Memory Optimized** | RAM-intensive work | Large databases, analytics |
| **Accelerated Computing** | GPU/specialized hardware | 3D rendering, machine learning |
| **Storage Optimized** | High-speed storage | NoSQL databases, data warehousing |

---

## 🖼️ EC2 Instance Lifecycle Diagram

````plaintext
+-------------------+
|     PENDING       | <-- Setting up (no billing yet)
+-------------------+
         |
         v
+-------------------+
|     RUNNING       | <-- Ready to use (billing starts)
+-------------------+
    |    |    |
    v    v    v
+--------+ +--------+ +--------+
|REBOOT  | | STOP   | |TERMINATE|
+--------+ +--------+ +--------+
    |         |           |
    v         v           v
+--------+ +--------+ +--------+
| RUNNING| |STOPPED | |TERMINATED|
+--------+ +--------+ +--------+
             |
             v
         +--------+
         | START  |
         +--------+
             |
             v
         +--------+
         | RUNNING|
         +--------+
````

---

## Instance State Actions

| Action | What Happens | IP Address | Data on Instance Store | Billing |
|--------|--------------|------------|----------------------|---------|
| **Reboot** | Restart OS on same server | Keeps same | Keeps data | Continues |
| **Stop/Start** | Move to new server | New public, same private | Loses data | Stops/resumes |
| **Terminate** | Permanently delete | Loses both | Loses data | Stops forever |
| **Stop-Hibernate** | Save RAM to disk | New public, same private | Saves RAM data | Stops |

---

## High Availability Best Practices

**Problem:** Single instance = single point of failure
**Solution:** Use multiple instances across different Availability Zones

````plaintext
+-------------------+         +-------------------+
|   AZ-1 (US-East)  |         |   AZ-2 (US-East)  |
|  +-------------+  |         |  +-------------+  |
|  | EC2 Instance|  |         |  | EC2 Instance|  |
|  +-------------+  |         |  +-------------+  |
+-------------------+         +-------------------+
````

**Better:** If one instance fails, the other keeps your app running!

---

## 💰 EC2 Pricing Options

### 1. On-Demand Instances
- **Pay as you go** (per second/hour)
- **No commitment**
- **Most expensive** but most flexible
- **Best for:** Unpredictable workloads, testing

### 2. Reserved Instances (RIs)
- **Commit for 1-3 years**
- **Big discounts** (up to 75% off)
- **Payment options:** All upfront, partial upfront, no upfront
- **Best for:** Steady, predictable workloads (like web servers)

### 3. Spot Instances
- **Use spare AWS capacity**
- **Up to 90% discount**
- **Can be interrupted** with 2-minute warning
- **Best for:** Fault-tolerant work (batch processing, testing)

---

## 🖼️ Pricing Comparison Diagram

````plaintext
Cost
 ^
 |
 |  +-----------+ On-Demand (Most expensive, most flexible)
 |  |           |
 |  |     +-----+ Reserved (Medium cost, 1-3 year commitment)
 |  |     |     |
 |  |     | +---+ Spot (Cheapest, can be interrupted)
 |  |     | |   |
 +--|-----|-----|----> Time
    1     2     3
````

---

## 🐱 Real-World Example

Imagine you're running a pizza delivery service:

- **On-Demand:** Rent delivery cars by the hour—expensive but flexible
- **Reserved:** Lease cars for 1-3 years—cheaper if you need them regularly
- **Spot:** Use surplus rental cars—cheapest, but they might take them back with short notice

---

**In summary:**  
EC2 instances go through different states (pending → running → stopped/terminated). Choose the right instance family for your workload, plan for high availability with multiple instances, and pick the pricing model that fits your usage pattern!




Here's a clear, beginner-friendly summary of **Demonstration: Launching the Employee Directory Application** with a step-by-step guide, diagram, and easy explanations:





# 🚀 Demonstration: Launching the Employee Directory Application: 

## What Happened in the Demo?

The instructor launched an EC2 instance to run the Employee Directory application using the AWS console.

---

## 📋 Step-by-Step Process

### 1. Navigate to EC2 and Launch Instance
- Go to EC2 dashboard in AWS console
- Click "Launch Instance"
- Give it a name: "employee directory app"

### 2. Choose AMI (Amazon Machine Image)
- Selected **Amazon Linux 2023 AMI**
- AMI = template with operating system and pre-installed software
- Other options: AWS Marketplace AMIs, custom AMIs, organization-approved AMIs

### 3. Select Instance Type
- Chose **t2.micro** (free tier eligible)
- Determines CPU, memory, and hardware specs
- Some instances include GPUs for special workloads

### 4. Configure Key Pair
- Selected "Proceed without a key pair"
- Alternative: Can connect via AWS console's "Connect" button
- Key pairs normally used for SSH access

### 5. Network Settings
- Used **default VPC** and **default subnet**
- Default VPC has internet access (internet gateway attached)
- Enabled **auto-assign public IP** for direct access

### 6. Configure Security Group (Firewall)
- **Disabled SSH** (not needed)
- **Enabled HTTP** (port 80) for web traffic
- **Enabled HTTPS** (port 443) for secure web traffic

### 7. Storage Configuration
- Left default root volume
- No additional EBS volumes added

### 8. Advanced Settings
- **IAM Instance Profile:** Selected "employee web app role"
- Role allows access to S3 and DynamoDB
- **User Data Script:** Added bash script to set up the application

---

## 🖼️ Architecture Diagram

````plaintext
+-------------------+
|   User's Browser  |
+-------------------+
         |
         v (HTTP/HTTPS)
+-------------------+
| EC2 Instance      |
| - Amazon Linux    |
| - Flask App       |
| - Public IP       |
+-------------------+
         |
         v (Future connections)
+-------------------+      +-------------------+
|       S3          |      |    DynamoDB       |
| (Employee Photos) |      | (Employee Data)   |
+-------------------+      +-------------------+
````

---

## 📝 User Data Script Breakdown

The script automatically sets up the application:

````bash
#!/bin/bash -ex                                    # Bash script declaration
wget [S3-ZIP-URL]                                  # Download app files
unzip FlaskApp.zip                                 # Extract files
cd FlaskApp/                                       # Navigate to app folder
yum -y install python3-pip                        # Install Python & pip
pip install -r requirements.txt                   # Install app dependencies
yum -y install stress                              # Install stress testing tool
export PHOTOS_BUCKET=${SUB_PHOTOS_BUCKET}         # Set S3 bucket variable
export AWS_DEFAULT_REGION=us-west-2                # Set AWS region
export DYNAMO_MODE=on                              # Enable DynamoDB mode
FLASK_APP=application.py /usr/local/bin/flask run --host=0.0.0.0 --port=80  # Start app
````

---

## ⏱️ Launch Process

1. **Instance State:** Pending → Running
2. **Status Checks:** Wait for both to pass
   - System status check
   - Instance status check
3. **Access:** Copy public IP address and open in browser

---

## 🐱 Real-World Example

Think of this like setting up a food truck:
1. **Choose the truck** (AMI = truck type)
2. **Pick engine size** (instance type = truck capabilities)
3. **Get permits** (security group = what traffic is allowed)
4. **Park in public spot** (public IP = customers can find you)
5. **Install equipment** (user data script = set up kitchen automatically)
6. **Open for business** (application running and accessible)

---

## 🎯 Current State

- **✅ What Works:** Application launches and displays empty employee directory
- **⏳ What's Missing:** 
  - S3 bucket (for storing employee photos)
  - DynamoDB table (for storing employee data)
  - Custom VPC (more secure networking)
  - High availability setup

---

**In summary:**  
Successfully launched an EC2 instance running the Employee Directory application! The app is accessible via public IP but shows empty data since the database and storage components haven't been set up yet. Next steps will include adding S3, DynamoDB, and custom networking.
