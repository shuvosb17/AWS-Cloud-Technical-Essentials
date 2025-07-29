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


Here's a clear, beginner-friendly summary of **Reading 2.3: Container Services on AWS** with diagrams, tables, and easy explanations:

---


# 📦 Container Services on AWS:

## What is a Container?

- A **container** is like a standardized shipping box for your application code.
- It packages your app and everything it needs to run (dependencies, libraries, etc.).
- Runs the same way everywhere—development, testing, production.

**Think of it like:** A food truck that has everything needed to serve food, can move anywhere and work the same way.

---

## Container vs Virtual Machine

| Feature | Container | Virtual Machine |
|---------|-----------|-----------------|
| **Operating System** | Shares host OS | Has its own OS |
| **Size** | Lightweight | Heavier |
| **Startup Time** | Almost instant | Takes minutes |
| **Resource Usage** | More efficient | Uses more resources |
| **Isolation** | Process-level | Full OS isolation |

---

## 🖼️ Diagram: Container vs VM

````plaintext
CONTAINERS                           VIRTUAL MACHINES
+-------------------+               +-------------------+
|   App A   App B   |               |   App A   App B   |
+-------------------+               +-------------------+
| Container Runtime |               |  Guest OS  Guest OS|
+-------------------+               +-------------------+
|    Host OS        |               |    Host OS        |
+-------------------+               +-------------------+
|    Hardware       |               |    Hardware       |
+-------------------+               +-------------------+
````

---

## What is Docker?

- **Docker** is the most popular container platform.
- Makes it easy to create, package, and run containers.
- Like having a standardized way to build and ship your "application boxes."

---

## Container Orchestration on AWS

When you have many containers across multiple servers, you need **orchestration** to manage:
- Where to place containers
- What happens when containers fail
- How to scale up/down
- How to monitor everything

---

## AWS Container Services

### 1. Amazon ECS (Elastic Container Service)

- **AWS's own** container orchestration service
- **Fully managed** by AWS
- Runs on EC2 instances with ECS Agent installed

**Key Components:**
- **Container Instance:** EC2 with ECS Agent
- **Task Definition:** JSON blueprint describing your containers
- **Task:** Running instance of your task definition

**ECS Task Definition Example:**
````json
{
  "family": "webserver",
  "containerDefinitions": [{
    "name": "web",
    "image": "nginx",
    "memory": "100",
    "cpu": "99"
  }],
  "requiresCompatibilities": ["FARGATE"],
  "networkMode": "awsvpc",
  "memory": "512",
  "cpu": "256"
}
````

### 2. Amazon EKS (Elastic Kubernetes Service)

- **Kubernetes-based** container orchestration
- Uses **open-source Kubernetes**
- Good if you already use Kubernetes elsewhere

**ECS vs EKS Terminology:**

| ECS | EKS |
|-----|-----|
| Container Instance | Worker Node |
| Task | Pod |
| AWS Native | Kubernetes-based |

---

## 🖼️ AWS Container Architecture

````plaintext
+-------------------+         +-------------------+
|   Your App Code   |  ---->  |    Container      |
+-------------------+         +-------------------+
                                       |
                                       v
+-------------------+         +-------------------+
|   ECS/EKS         |  <----  | EC2 Instances     |
| (Orchestration)   |         | (Container Hosts) |
+-------------------+         +-------------------+
````

---

## 🐱 Real-World Example

**Traditional Approach:**
You're opening multiple restaurants. Each needs its own building, kitchen, staff—expensive and slow to set up.

**Container Approach:**
You use food trucks (containers). Each truck has everything needed, can move anywhere, and you can quickly add more trucks during busy times.

**Orchestration:**
You need a dispatch center (ECS/EKS) to coordinate all your food trucks—where they go, when they open, what happens if one breaks down.

---

## When to Use Containers?

**Good for:**
- Microservices applications
- Development/testing environments
- Applications that need to scale quickly
- Moving apps between environments

**Consider VMs if:**
- You need full OS control
- Running legacy applications
- Need dedicated resources
- Security requires full isolation

---

**In summary:**  
Containers are lightweight, portable packages for your applications. AWS offers ECS (AWS-native) and EKS (Kubernetes-based) to help you manage containers at scale across multiple servers!

Here's a clear, beginner-friendly summary of **Serverless Computing on AWS** with diagrams, tables, and easy explanations:

---


# ⚡ Serverless Computing on AWS:

## The Management Spectrum

When choosing compute services, you're choosing between **control** and **convenience**.

### EC2/Container Management (More Control)

With EC2 and containers, **you manage:**
- Patching operating systems and software
- Scaling instances up/down
- High availability across multiple AZs
- Server maintenance and updates
- Monitoring and troubleshooting

**Benefit:** Complete control over your environment
**Drawback:** More operational overhead

### Serverless (More Convenience)

With serverless, **AWS manages:**
- All underlying infrastructure
- Scaling automatically
- High availability
- Server maintenance and patching
- Operating system updates

**Benefit:** Focus only on your application code
**Drawback:** Less control over the underlying system

---

## 🖼️ Diagram: Control vs Convenience Spectrum

````plaintext
CONTROL                                           CONVENIENCE
<--------------------------------------------------------->
|                    |                    |              |
EC2                 Containers          Lambda      Managed Services
(Full Control)      (Medium)         (Serverless)   (Fully Managed)

You Manage:         You Manage:       AWS Manages:    AWS Manages:
- OS Patching       - App Code        - Everything    - Everything
- Scaling           - Containers      - Scaling       - Database
- Monitoring        - Orchestration   - Patching      - Backups
- Networking        - Some Scaling    - Monitoring    - Updates
````

---

## What is Serverless?

- **Serverless** = You can't see or access the underlying servers
- AWS handles all the infrastructure management
- You only focus on your application code
- Pay only for what you use (no idle server costs)

**Important:** "Serverless" doesn't mean there are no servers—it means you don't manage them!

---

## Shared Responsibility Model Impact

| Service Type | Your Responsibilities | AWS Responsibilities |
|--------------|----------------------|---------------------|
| **EC2** | OS patching, scaling, app code, data encryption | Hardware, hypervisor, network |
| **Serverless** | App code, data encryption, access management | Everything else (OS, scaling, patching, hardware) |

---

## 🖼️ Diagram: Responsibility Comparison

````plaintext
EC2 RESPONSIBILITIES                 SERVERLESS RESPONSIBILITIES
+-------------------+               +-------------------+
|   Your App Code   | <-- You       |   Your App Code   | <-- You
+-------------------+               +-------------------+
|   OS Patching     | <-- You       |                   |
+-------------------+               |                   |
|   Scaling Setup   | <-- You       |   Everything Else | <-- AWS
+-------------------+               |   (Managed by AWS)|
|   Server Mgmt     | <-- You       |                   |
+-------------------+               +-------------------+
|   Hardware        | <-- AWS       |   Hardware        | <-- AWS
+-------------------+               +-------------------+
````

---

## 🐱 Real-World Example

**Traditional Approach (EC2):**
Like owning a restaurant—you control everything but must:
- Hire and manage all staff
- Maintain all equipment
- Handle busy/slow periods
- Fix problems when they occur

**Serverless Approach (Lambda):**
Like hiring a catering service—you provide the menu (code), they handle:
- Bringing the right number of chefs
- All equipment and setup
- Scaling for different event sizes
- Cleaning up afterwards

---

## When to Choose What?

### Choose EC2/Containers When:
- You need full control over the environment
- Running legacy applications
- Specific OS or software requirements
- Long-running processes
- Predictable, steady workloads

### Choose Serverless When:
- You want to focus on business logic
- Event-driven applications
- Variable or unpredictable workloads
- Quick development and deployment
- Don't want to manage infrastructure

---

## Benefits of Serverless

| Benefit | Description |
|---------|-------------|
| **No Server Management** | AWS handles all infrastructure |
| **Automatic Scaling** | Scales up/down based on demand |
| **Pay-per-Use** | Only pay when code is running |
| **High Availability** | Built-in fault tolerance |
| **Faster Development** | Focus on code, not infrastructure |

---

**In summary:**  
Serverless computing lets you focus on writing application code while AWS handles all the infrastructure management. Choose based on whether you need more control (EC2/containers) or more convenience (serverless) for your specific use case!

Here's a clear, beginner-friendly summary of **AWS Fargate: Serverless Containers** with diagrams, tables, and easy explanations:

---


# 🚀 AWS Fargate: Serverless Containers:

## What is AWS Fargate?

- **AWS Fargate** is a serverless compute platform for running containers.
- Works with both **ECS** and **EKS** (container orchestrators).
- You focus on your app—AWS manages all the infrastructure.

---

## Container Platform Options

| Platform | Management Level | You Manage | AWS Manages |
|----------|-----------------|------------|-------------|
| **EC2** | Full Control | OS patching, scaling, instances | Hardware, hypervisor |
| **Fargate** | Serverless | Just your app code | Everything else |

---

## 🖼️ Diagram: Container Architecture Options

````plaintext
TRADITIONAL EC2 APPROACH                 FARGATE SERVERLESS APPROACH
+-------------------+                   +-------------------+
|   Your App Code   |                   |   Your App Code   |
+-------------------+                   +-------------------+
|   ECS/EKS         |                   |   ECS/EKS         |
+-------------------+                   +-------------------+
| EC2 Instances     | <-- You manage    |                   |
| - OS Patching     |                   |   AWS Fargate     | <-- AWS manages
| - Scaling         |                   |   (Serverless)    |
| - Monitoring      |                   |                   |
+-------------------+                   +-------------------+
|   AWS Hardware    |                   |   AWS Hardware    |
+-------------------+                   +-------------------+
````

---

## How Fargate Works (4 Simple Steps)

### 1. Build & Store Container Images
- Create your container images
- Push them to **Amazon ECR** (Elastic Container Registry)
- ECR = AWS's container image storage service

### 2. Define Resources
- Specify how much **CPU** and **memory** your app needs
- Set **networking** and **storage** requirements
- No need to choose instance types!

### 3. Run Containers
- Deploy using ECS or EKS
- Fargate automatically provisions the infrastructure

### 4. Pay for Usage
- Pay only for **vCPU**, **memory**, and **storage** consumed
- No paying for idle servers

---

## 🖼️ Diagram: Fargate Workflow

````plaintext
+-------------------+         +-------------------+
|  1. Build Image   |  ---->  |  2. Push to ECR   |
+-------------------+         +-------------------+
         |                              |
         v                              v
+-------------------+         +-------------------+
|  4. Run on        |  <----  |  3. Define Task   |
|     Fargate       |         |     (CPU/Memory)  |
+-------------------+         +-------------------+
````

---

## Benefits of Fargate

| Benefit | Description |
|---------|-------------|
| **No Server Management** | No EC2 instances to patch or maintain |
| **Automatic Scaling** | Scales containers based on demand |
| **Built-in Fault Tolerance** | High availability without setup |
| **Pay-per-Use** | Only pay for resources consumed |
| **Focus on Apps** | Spend time on business logic, not infrastructure |

---

## Fargate vs EC2 for Containers

| Factor | EC2 | Fargate |
|--------|-----|---------|
| **Setup Complexity** | High (manage instances) | Low (just define tasks) |
| **Cost Model** | Pay for instances (even when idle) | Pay for actual usage |
| **Scaling** | Manual setup required | Automatic |
| **Maintenance** | You patch OS | AWS handles everything |
| **Control** | Full control over instances | Less control, more convenience |

---

## Common Use Cases

- **Microservices:** Each service runs in its own container
- **Batch Processing:** Run jobs without managing servers
- **Machine Learning:** Train models without infrastructure hassle
- **Application Migration:** Move on-premises apps to cloud easily

---

## 🐱 Real-World Example

**Traditional Approach (EC2):**
Like owning a delivery fleet—you buy trucks, hire drivers, maintain vehicles, plan routes.

**Fargate Approach:**
Like using Uber Eats—you just order food delivery. Someone else handles the drivers, vehicles, and logistics. You pay only when you order.

---

## Pricing Options

Fargate supports cost optimization features:
- **Spot Pricing:** Use spare capacity at discounted rates
- **Compute Savings Plans:** Commit to usage for lower prices
- Similar flexibility to EC2 pricing options

---

**In summary:**  
AWS Fargate lets you run containers without managing servers. You define what your app needs (CPU, memory), and AWS handles all the infrastructure management, scaling, and maintenance. Perfect for when you want the benefits of containers without the operational overhead!


---


# ⚡ AWS Lambda: Serverless Computing:

## What is AWS Lambda?

- **AWS Lambda** is a serverless compute service that runs your code without managing servers.
- You upload your code as a **Lambda function**.
- Functions run only when **triggered**—not running 24/7 like EC2 instances.
- **Perfect for:** Quick processing tasks, event-driven applications, microservices.

---

## How Lambda Works

1. **Upload your code** to create a Lambda function
2. **Configure a trigger** (what starts your function)
3. **AWS waits** for the trigger event
4. **When triggered,** AWS runs your code automatically
5. **Function scales** from 1 to 1,000+ concurrent executions
6. **Pay only** for actual execution time (rounded to nearest millisecond)

---

## 🖼️ Lambda Trigger Examples

````plaintext
+-------------------+         +-------------------+
|   HTTP Request    |  ---->  |   Lambda Function |
+-------------------+         +-------------------+

+-------------------+         +-------------------+
|   S3 File Upload  |  ---->  |   Lambda Function |
+-------------------+         +-------------------+

+-------------------+         +-------------------+
|   Mobile App Event|  ---->  |   Lambda Function |
+-------------------+         +-------------------+
````

---

## Lambda Limitations

| Feature | Limit |
|---------|-------|
| **Maximum Runtime** | 15 minutes |
| **Memory** | 128 MB to 10,240 MB |
| **Good For** | Quick processing, web backends, microservices |
| **Not Good For** | Long-running processes, deep learning, WordPress sites |

---

## 🎯 Demo: Image Resize Function

### Use Case
When someone uploads a photo to the employee directory, automatically create a thumbnail version.

### Architecture
````plaintext
+-------------------+         +-------------------+         +-------------------+
|   User Uploads    |  ---->  |   S3 Bucket       |  ---->  | Lambda Function   |
|   Photo to S3     |         |   (input folder)  |         | (ResizeImage)     |
+-------------------+         +-------------------+         +-------------------+
                                                                      |
                                                                      v
                              +-------------------+         +-------------------+
                              |   S3 Bucket       |  <----  | Resized Image     |
                              |   (output folder) |         | Created           |
                              +-------------------+         +-------------------+
````

---

## 📋 Step-by-Step Demo Process

### 1. Create Lambda Function
- Go to AWS Lambda console
- Click **"Create function"**
- Choose **"Author from scratch"**
- Function name: **ResizeImage**
- Runtime: **Python 3.9**
- Permissions: Use existing role **LambdaS3FullAccess**

### 2. Configure S3 Trigger
- Click **"Add trigger"**
- Trigger source: **S3**
- Bucket: **photo-upload-bucket-mw**
- Event type: **PUT** (file uploads)
- Prefix: **input/** (only trigger for files in input folder)
- Acknowledge recursive invocation warning

### 3. Upload Function Code
- Go to **Code tab**
- Click **"Upload from" → "zip file"**
- Upload **ResizeImage.zip**
- Click **Save**

### 4. Test the Function
- Go to S3 bucket
- Upload image to **input/** folder
- Check **output/** folder for resized thumbnail

---

## 🖼️ Lambda Function Components

````plaintext
+-------------------+
|   Function Code   |  <-- Your application logic
+-------------------+
         |
         v
+-------------------+
|     Trigger       |  <-- What starts the function
+-------------------+
         |
         v
+-------------------+
|   IAM Role        |  <-- Permissions to access other AWS services
+-------------------+
         |
         v
+-------------------+
|   Runtime Env     |  <-- Managed by AWS (Python, Node.js, etc.)
+-------------------+
````

---

## Lambda vs EC2 Comparison

| Factor | Lambda | EC2 |
|--------|---------|-----|
| **Management** | Serverless (AWS manages) | You manage servers |
| **Scaling** | Automatic | Manual setup required |
| **Billing** | Pay per execution | Pay for running time |
| **Runtime** | Max 15 minutes | Unlimited |
| **Use Cases** | Event-driven, quick tasks | Long-running applications |

---

## 🐱 Real-World Example

**Traditional Approach (EC2):**
Like hiring a full-time photographer who sits at your store all day waiting for customers to take photos—expensive!

**Lambda Approach:**
Like calling a photographer only when you need them—they show up, take the photo, process it, and leave. You only pay for the time they actually work.

---

## Common Lambda Use Cases

- **Image/video processing** (like the demo)
- **Web API backends** (handle HTTP requests)
- **Data processing** (process files, logs, streams)
- **IoT backends** (respond to sensor data)
- **Chatbots** (process messages)
- **Scheduled tasks** (daily reports, cleanup jobs)

---

## Benefits of Lambda

| Benefit | Description |
|---------|-------------|
| **No Server Management** | AWS handles all infrastructure |
| **Automatic Scaling** | From 0 to 1000+ concurrent executions |
| **Pay-per-Use** | Only pay for actual execution time |
| **High Availability** | Built-in fault tolerance |
| **Multiple Languages** | Python, Node.js, Java, C#, Go, Ruby |

---

**In summary:**  
AWS Lambda lets you run code without managing servers. Perfect for event-driven applications where you want to respond to triggers (like file uploads) quickly and cost-effectively. You only pay for what you use, and AWS handles all the scaling and infrastructure management!




# ⚡Choose the Right Compute Service:
---

````markdown
# 🎮 Choose the Right AWS Compute Service (Game Show Edition!)

## The Game Show Format

Welcome to "Which AWS Compute Service Should I Choose?" - Let's play through three real-world scenarios!

---

## 🎯 Scenario 1: Quarterly Inventory Upload

**The Challenge:**
- Online store needs to update inventory database
- Currently done manually (slow, error-prone)
- Goal: Upload spreadsheet to S3 → automatically update database
- **Frequency:** Only once per quarter

**Options:**
- **EC2:** Could work, but runs 24/7 for quarterly task = expensive
- **Lambda:** Perfect! Only runs when triggered, pay per use

**✅ Winner: AWS Lambda**

**Why Lambda Wins:**
- **Cost-effective:** Only pay when code runs
- **Event-driven:** S3 upload triggers Lambda function
- **Perfect fit:** Infrequent, short-duration tasks

````plaintext
+-------------------+         +-------------------+         +-------------------+
|  Upload to S3     |  ---->  |  Lambda Triggered |  ---->  |  Database Updated |
|  (Quarterly)      |         |  (Runs only then)|         |  (Automatically)  |
+-------------------+         +-------------------+         +-------------------+
````

---

## 🎯 Scenario 2: Migrate On-Premises Linux App

**The Challenge:**
- Move existing Linux application from data center to AWS
- **Minimize refactoring** (key requirement!)
- Need elastic scaling for varying demand

**Analysis:**
- **Lambda:** Would require significant code changes ❌
- **Containers (ECS/EKS):** Would need containerization refactoring ❌
- **EC2:** Minimal changes, same Linux environment ✅

**✅ Winner: Amazon EC2**

**Why EC2 Wins:**
- **Lift and shift:** Move app with minimal changes
- **Linux AMIs:** Same environment as on-premises
- **Auto Scaling:** Can handle varying demand
- **Familiar:** Works like traditional servers

---

## 🎯 Scenario 3: New Microservices Application

**The Challenge:**
- Building brand-new microservices architecture
- Need quick scaling up/down
- Want to reduce deployment risk

**Analysis:**
- **EC2:** Slower boot times, heavier infrastructure ❌
- **Lambda:** Good for some microservices, but limited runtime ⚠️
- **Containers (ECS/EKS):** Perfect for microservices! ✅

**✅ Winner: Amazon ECS or EKS**

**Why Containers Win:**
- **Fast scaling:** Containers start almost instantly
- **Consistency:** Same container runs everywhere (dev → test → prod)
- **Microservices-friendly:** Natural fit for service-oriented design
- **Lower deployment risk:** "Works on my machine" → "Works everywhere"

---

## 🖼️ Decision Tree Diagram

````plaintext
                    Start: Need Compute?
                           |
                           v
               +-----------+-----------+
               |                       |
        Existing App?              New App?
               |                       |
               v                       v
    +----------+----------+    +------+------+
    |                     |    |             |
Minimize Changes?    Modernize?   Microservices?  Simple Functions?
    |                     |    |             |
    v                     v    v             v
   EC2              Containers  ECS/EKS    Lambda
````

---

## 📋 Quick Reference Guide

| Use Case | Best Service | Why? |
|----------|-------------|------|
| **Lift & Shift Migration** | EC2 | Minimal refactoring needed |
| **Event-Driven Tasks** | Lambda | Pay-per-use, auto-scaling |
| **Microservices (New)** | ECS/EKS | Fast scaling, consistency |
| **Long-Running Apps** | EC2 | Predictable workloads |
| **Variable Workloads** | Lambda | Automatic scaling to zero |
| **Container Modernization** | ECS/EKS | Portability and efficiency |

---

## 💡 Key Decision Factors

### Choose EC2 When:
- Migrating existing applications
- Need full OS control
- Long-running processes
- Predictable workloads

### Choose Lambda When:
- Event-driven architecture
- Infrequent, short tasks
- Want automatic scaling to zero
- Pay-per-execution preferred

### Choose Containers (ECS/EKS) When:
- Building microservices
- Need fast scaling
- Want application portability
- Modernizing development practices

---

## 🐱 Real-World Examples

**Lambda Example:**
Like hiring a photographer only for special events—they show up, do the job, leave. You only pay when you actually need them.

**EC2 Example:**
Like renting a full office space—you have complete control and it's always available, but you pay whether you use it or not.

**Containers Example:**
Like using food trucks for a festival—quick to set up, easy to move around, and each truck serves a specific purpose.

---

## 🎯 Pro Tips

1. **Don't use the same service for everything** - Pick the right tool for each job
2. **Consider cost patterns** - Frequent use = EC2, Infrequent = Lambda
3. **Think about maintenance** - Less management = Serverless, More control = EC2
4. **Plan for scale** - Containers great for microservices, Lambda for events
5. **Re-evaluate regularly** - AWS keeps improving services

---

**In summary:**
Choose your compute service based on your specific needs: EC2 for control and migrations, Lambda for events and cost efficiency, and Containers for modern microservices architecture. The right choice depends on your use case, not just what's newest or coolest!
````

#⚡ Reading 2.4: Serverless and AWS Lambda:

**🏗️ Remove the Undifferentiated Heavy Lifting**

Think of building software like constructing a house. With traditional approaches, you spend tons of time on plumbing, electrical work, and foundation - stuff that doesn't make your house unique. AWS serverless lets you focus on the fun parts like interior design and layout!

**📊 Responsibility Comparison Table**

| What You're Responsible For | EC2 | Containers on EC2 | Serverless |
|----------------------------|-----|-------------------|------------|
| Physical Hardware | ❌ AWS | ❌ AWS | ❌ AWS |
| Operating System | ✅ You | ✅ You | ❌ AWS |
| Security & Patching | ✅ You | ✅ You | ❌ AWS |
| Scaling | ✅ You | ✅ You | ❌ AWS |
| Application Code | ✅ You | ✅ You | ✅ You |

**🚀 What is Serverless? (The Big Four)**

1. **No servers to provision or manage** - Like having a magical kitchen that appears when you want to cook
2. **Scales with usage** - More guests show up? More tables automatically appear
3. **Never pay for idle resources** - Only pay when the kitchen is actually cooking
4. **Built-in availability and fault tolerance** - If one kitchen breaks, another instantly takes over

**🏠 Real-World Example: Running a Food Truck Business**

Traditional Way (EC2): You buy and maintain the truck, hire full-time staff, pay insurance 24/7 even when parked

Serverless Way: You call a magical food truck that only appears when customers want food, comes fully staffed, and disappears when done. You only pay for the minutes it's serving customers.

**📦 AWS Fargate: Serverless Containers**

Fargate is like having a food truck rental service. You provide the recipes (containers), they provide the trucks and drivers. You don't worry about truck maintenance, just focus on making great food!

**Container Deployment Modes Comparison**

| Feature | EC2 Mode | Fargate Mode |
|---------|----------|--------------|
| Server Management | You handle | AWS handles |
| Scaling | Manual setup | Automatic |
| Cost When Idle | Still paying | Pay only for usage |
| Real-World Example | Own the restaurant building | Rent space only when cooking |

**⚡ AWS Lambda: The Ultimate Serverless**

Lambda is like having a genie that only appears when you rub the lamp, does exactly what you ask, then disappears. No monthly rent, no feeding, no management - just results when you need them!

**Perfect Lambda Use Cases:**
- 📸 Resize photos when uploaded (like Instagram filters)
- 📧 Send emails when someone fills a form
- 🔔 Process IoT sensor data when readings come in
- 📊 Generate reports when requested
- 🎮 Handle game score updates

**🎯 Three Components of Lambda Function**

```
TRIGGER (When?) → CODE (What?) → CONFIGURATION (How?)

Example: Photo Upload
S3 Upload → Resize Image → Use 512MB memory, Python runtime
```

**Lambda Code Sources Comparison**

| Source | Difficulty | Time to Deploy | Example |
|--------|------------|----------------|---------|
| From Scratch | 🔴 Hard | Hours/Days | Custom business logic |
| AWS Blueprints | 🟡 Medium | Minutes | Basic web APIs |
| Serverless App Repository | 🟢 Easy | Seconds | Image resizing, Alexa skills |

**💻 Lambda Function Structure (Python Example)**

```
def lambda_handler(event, context):
    # Your magic happens here
    return "Done!"
```

**Naming Convention:**
- **File:** lambda_function.py (like naming your recipe book)
- **Function:** lambda_handler (like the main recipe inside)
- **Full Name:** lambda_function.lambda_handler

**💰 Lambda Billing: Pay Only for What You Use**

Traditional Server vs Lambda Cost Comparison:

```
MONTHLY COST FOR PROCESSING 1000 PHOTOS

Traditional Server (EC2):
Running 24/7: $50/month
Even when doing nothing: $50/month
Total: $50/month

Lambda:
1000 photo processes × 0.1 seconds each = 100 seconds
100 seconds × $0.0000166667 = $0.0017
Total: Less than 1 cent!
```

**Lambda Pricing Components:**
1. **Requests** - How many times your function runs (like counting how many times you use the genie)
2. **Duration** - How long it runs (measured to the nearest millisecond!)

**⏱️ When Lambda is Super Cost-Effective:**
- Functions under 100ms (like quick calculations)
- Low-traffic APIs (occasional use)
- Event-driven tasks (only when something happens)

**📈 Scaling Behavior Comparison**

```
HANDLING SUDDEN TRAFFIC SPIKE (1 user → 10,000 users)

Traditional Server:
[████    ] → Crashes or slow response

Lambda:
[█       ] → [██████████] Automatically scales to handle all users
```

**🎯 When to Choose What**

| Choose Lambda When | Choose Fargate When | Choose EC2 When |
|-------------------|-------------------|-----------------|
| Quick tasks (under 15 min) | Containerized apps | Full OS control needed |
| Event-driven | Microservices | Long-running processes |
| Unpredictable traffic | Medium complexity | Predictable workloads |
| Want zero management | Some container control | Maximum flexibility |

**🏆 Key Takeaway Quote**

Amazon's CTO Werner Vogels: *"No server is easier to manage than no server."*

This perfectly captures the serverless philosophy - focus on solving your business problems, not managing infrastructure!

**🚦 Traffic Light Decision Guide**

🟢 **Go Lambda:** Event-driven, short tasks, variable traffic
🟡 **Consider Fargate:** Containerized apps, microservices
🔴 **Stick with EC2:** Need OS control, long-running apps, specialized hardware

Serverless isn't just a technology choice - it's a mindset shift from "managing servers" to "delivering value!"
