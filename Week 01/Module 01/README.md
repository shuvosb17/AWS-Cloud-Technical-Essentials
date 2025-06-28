# Introduction to AWS: Key Concepts:

## 1. What is AWS and Cloud Computing?

**AWS (Amazon Web Services)** is a platform that provides cloud computing services.

**Cloud computing** means using remote servers on the internet to store, manage, and process data, instead of using your own computer or local servers.

### Why Use the Cloud?

- **Scalability:** Easily increase or decrease resources as needed.
- **Cost-effective:** Pay only for what you use.
- **Reliability:** High availability and fault tolerance.
- **Security:** Built-in security features.

---

## 2. AWS Global Infrastructure

AWS is made up of **Regions** and **Availability Zones**.

```
+-------------------+         +-------------------+
|    Region 1       |         |    Region 2       |
|  (e.g., US-East)  |         |  (e.g., EU-West)  |
|  +-------------+  |         |  +-------------+  |
|  | AZ1         |  |         |  | AZ1         |  |
|  | AZ2         |  |         |  | AZ2         |  |
|  +-------------+  |         |  +-------------+  |
+-------------------+         +-------------------+

```

- **Region:** A geographic area (like US-East, EU-West).
- **Availability Zone (AZ):** A data center within a region. Each region has multiple AZs for redundancy.

---

## 3. Building an App on AWS

You’ll build an **Employee Directory App** (CRUD: Create, Read, Update, Delete).

### Main AWS Services Used

```
+-------------------+
|  User's Browser   |
+--------+----------+
         |
         v
+-------------------+
|   Load Balancer   |  <-- Distributes traffic
+--------+----------+
         |
         v
+-------------------+
|      EC2          |  <-- Virtual servers (backend code)
+--------+----------+
         |
         v
+-------------------+
|      RDS          |  <-- Database (employee data)
+-------------------+

+-------------------+
|       S3          |  <-- Stores images/files
+-------------------+

+-------------------+
|      IAM          |  <-- Security & access control
+-------------------+

+-------------------+
|   CloudWatch      |  <-- Monitoring
+-------------------+

```

### How the App Works

- **VPC (Virtual Private Cloud):** Your own private network in AWS.
- **EC2:** Runs your app’s backend code.
- **RDS:** Stores employee data in a database.
- **S3:** Stores employee photos and other files.
- **Elastic Load Balancer:** Distributes incoming traffic to multiple EC2 instances.
- **Auto Scaling:** Automatically adds/removes EC2 instances based on demand.
- **IAM:** Manages who can access what in AWS.
- **CloudWatch:** Monitors your app’s health and performance.

---

## 4. Security Basics

- **IAM (Identity and Access Management):** Controls who can do what in your AWS account.
- **Start Secure:** Set up security from the beginning.

---

## 5. Learning Approach

- **Theory:** Understand the concepts.
- **Technical Knowledge:** Learn how to use AWS services.
- **Vocabulary:** Get familiar with AWS terms.
- **Practice:** Build and experiment with real AWS resources.

---

## 6. Fun Extras

- **Meowzy and Fluffy:** Mascots that give you tips and best practices during the course.

---

# Summary Diagram

```
+-------------------+      +-------------------+
|   User's Browser  | ---> |   Load Balancer   |
+-------------------+      +-------------------+
                                   |
                                   v
                        +-------------------+
                        |       EC2         |
                        +-------------------+
                                   |
                                   v
                        +-------------------+
                        |       RDS         |
                        +-------------------+
                                   |
                                   v
                        +-------------------+
                        |       S3          |
                        +-------------------+

Other Services:
- IAM (Security)
- CloudWatch (Monitoring)
- Auto Scaling (Scalability)

```

---

**In summary:**

You’ll learn AWS by building a real app, understanding both the theory and the practical steps, and using diagrams to see how everything fits together.

# What is the Cloud?

In the past, companies had to buy and maintain their own servers, storage, and networking equipment in physical data centers. This was expensive, slow, and required a lot of work.

## On-Premises vs. Cloud

```
On-Premises:                        Cloud Computing:
+---------------------+             +---------------------+
|  Your Data Center   |             |   AWS Data Center   |
|  (You buy/manage)   |             | (AWS manages it)    |
+---------------------+             +---------------------+
| Servers, Storage,   |             |  Virtual Servers,   |
| Networking, Power   |             |  Storage, Network   |
+---------------------+             +---------------------+
| You do everything   |             | You use over        |
| yourself            |             | the internet        |
+---------------------+             +---------------------+

```

- **On-premises:** You buy, install, and maintain all hardware.
- **Cloud:** AWS owns the hardware; you use what you need over the internet.

---

## What is Cloud Computing?

**Cloud computing** is the on-demand delivery of IT resources (like servers, storage, databases) over the internet with pay-as-you-go pricing.

- No need to buy or manage physical hardware.
- You can create or remove resources in minutes.

---

## Example: Testing a New Feature

**On-premises:**

To test a new feature, you must buy and set up new hardware, which takes days or weeks.

**Cloud:**

You can create a new environment in minutes, test your feature, and then delete it when done.

```
On-Premises:           Cloud:
[Buy hardware]         [Click to create]
[Install OS]           [Ready in minutes]
[Connect cables]       [Test feature]
[Wait days/weeks]      [Delete when done]

```

---

## Focus on What Matters

With cloud computing, AWS handles the “heavy lifting” (like hardware and backups), so you can focus on your code and your customers.

---

## Six Benefits of Cloud Computing

1. **Pay as you go:** Only pay for what you use.
2. **Economies of scale:** Lower costs because AWS serves many customers.
3. **No guessing capacity:** Scale up or down as needed.
4. **Speed and agility:** Get resources in minutes, not weeks.
5. **No data center maintenance:** Focus on your business, not hardware.
6. **Go global in minutes:** Deploy your app worldwide easily.

---

## Summary Diagram

```
+-------------------+      +-------------------+
|   Your Business   | ---> |     AWS Cloud     |
+-------------------+      +-------------------+
        |                          |
        v                          v
[Focus on code, customers]   [AWS handles hardware, scaling, backups]

```

---

**In short:**

Cloud computing lets you use IT resources over the internet, quickly and cost-effectively, so you can focus on what makes your business unique.

# Amazon Global Infrastructure

## Why Store Data in the Cloud?

If you keep your only copy of employee photos on your laptop and it breaks, you lose everything.

By uploading them to AWS, your photos are safe, accessible from anywhere, and protected from disasters.

---

## How AWS Protects Your Data: Redundancy

AWS uses **redundancy** to keep your data safe from disasters (even alien attacks!).

In AWS, **redundancy** means having multiple copies of resources (like data, servers, or entire data centers) so that if one part fails (due to hardware issues, disasters, etc.), another can take over without losing data or service.

**Example:**

If one data center goes down, another in the same Availability Zone (AZ) or Region can keep your app running. This ensures high availability and reliability.

### Data Center, Availability Zone, and Region

```
+-------------------+      +-------------------+
|   Data Center 1   |<---->|   Data Center 2   |   <-- Connected for redundancy
+-------------------+      +-------------------+
         |                          |
         +-------- Availability Zone (AZ) -------+
                          |
         +---------------------------------------+
         |           Region (e.g., N. Virginia)  |
         +---------------------------------------+

```

- **Data Center:** Physical building with servers.
- **Availability Zone (AZ):** One or more data centers, connected for backup.
- **Region:** A group of AZs in a geographic area (like "US East" or "London").

---

## Choosing an AWS Region

When picking a region, consider:

1. **Compliance:** Does your data need to stay in a specific country?
2. **Latency:** Choose a region close to your users for faster access.
3. **Pricing:** Costs can vary by region.
4. **Service Availability:** Not all AWS services are in every region.

---

## Global Edge Network

To make your app even faster for users worldwide, AWS uses **Edge Locations** and **Regional Edge Caches**.

### How Edge Locations Work

```
User in India
     |
     v
[Edge Location in India] <-- Cached content here
     |
     v
[AWS Region in Ohio] <-- Original content here

```

- **Edge Location:** Caches content closer to users, reducing wait time.
- **Regional Edge Cache:** Larger cache, sits between Edge Locations and Regions.

**Example:**

If your website is hosted in Ohio but users are in India, Edge Locations in India can serve cached content quickly.

---

## Recap Diagram

```
+-------------------+
|     Region        |  (e.g., US East)
|  +-------------+  |
|  |   AZ 1      |  |  <-- Each AZ = 1+ Data Centers
|  |   AZ 2      |  |
|  +-------------+  |
+-------------------+
         |
         v
+-------------------+
|  Edge Locations   |  <-- Cache content close to users
+-------------------+

```

---

**In summary:**

AWS global infrastructure is built for safety, speed, and reliability.

- Data is stored in multiple data centers (AZs) inside regions.
- Edge locations cache content worldwide for fast access.
- Choose your region based on compliance, latency, price, and available services.

# 🌍 AWS Global Infrastructure

Every cloud app still needs real hardware—servers, cables, and data centers. AWS organizes this physical infrastructure into **Regions** and **Availability Zones (AZs)**.

---

## 📍 Regions

**Regions** are geographic areas where AWS has data centers.

Each Region is independent and named after its location.

**Examples:**

- 🇺🇸 **us-east-1**: Northern Virginia, USA
- 🇯🇵 **ap-northeast-1**: Tokyo, Japan

> Real-world example:
> 
> 
> Imagine you’re a global company. You can store customer data in the closest Region to each customer for faster access and to meet local laws.
> 

**Note:** Data is NOT copied between Regions unless you set it up.

---

## 🤔 How to Choose a Region?

Consider these four factors:

1. **Latency** 🕒
    - Choose a Region near your users for faster response.
    - *Example: A gaming app for Europe should use a European Region for low lag.*
2. **Price** 💸
    - Prices vary by Region due to local costs.
    - *Example: Hosting in São Paulo may cost more than in Oregon.*
3. **Service Availability** 🛠️
    - Not all AWS services are in every Region.
    - *Example: A new AWS service might launch in N. Virginia first.*
4. **Compliance** 📜
    - Some data must stay in certain countries.
    - *Example: UK health data must stay in the London Region.*

---

## 🏢 Availability Zones (AZs)

Inside each Region are **Availability Zones**—clusters of one or more data centers with redundant power, networking, and connectivity.

**Naming Example:**

- **us-east-1a**: AZ “a” in Northern Virginia
- **sa-east-1b**: AZ “b” in São Paulo

> Real-world example:
> 
> 
> Think of AZs like fireproof safes in different rooms of a bank. If one room has a problem, your valuables in the other room are safe.
> 

---

## 🗺️ Diagram: Regions & AZs

```
+---------------------+      +---------------------+
|    Region: Oregon   |      |   Region: Tokyo     |
|  +---------------+  |      |  +---------------+  |
|  | AZ: us-west-2a|  |      |  | AZ: ap-northeast-1a|
|  | AZ: us-west-2b|  |      |  | AZ: ap-northeast-1b|
|  +---------------+  |      |  +---------------+  |
+---------------------+      +---------------------+

```

---

## 🌐 Service Scope

- **Region-scoped services:**
AWS manages redundancy for you. Just pick a Region.
- **AZ-scoped services:**
You pick the AZ. You must plan for redundancy (use at least 2 AZs).

---

## 🛡️ Maintain Resiliency

- Use managed, Region-scoped services for built-in high availability.
- If using AZ-scoped resources, always deploy in at least 2 AZs.
- **Example:**
If one AZ goes down (like a power outage in one building), your app keeps running in the other AZ.

---

**In summary:**

AWS’s global infrastructure is like a network of super-secure, well-connected banks around the world. You choose where to store your “valuables” (data), and AWS helps keep them safe, fast, and available—no matter what happens! 🌎💪

# 🖥️ Interacting with AWS

When you own physical servers, you can touch and manage them directly. But with AWS, everything is virtual—you manage your resources using software, not by physically plugging in cables!

---

## 🔗 How Do You Interact with AWS?

You interact with AWS using its **API (Application Programming Interface)**.

Every time you create, delete, or change something in AWS (like a server or storage), you’re making an API call.

---

## 🚦 Three Main Ways to Use AWS

### 1. AWS Management Console 🖱️

- **What is it?**
A web-based dashboard you access in your browser.
- **How it feels:**
Like online shopping—point, click, and follow prompts.
- **Best for:**
Beginners and anyone who prefers a visual interface.
- **Example:**
Creating a virtual server by clicking through menus.

---

### 2. AWS Command Line Interface (CLI) 💻

- **What is it?**
A tool you use in your terminal or command prompt.
- **How it feels:**
Like giving instructions to AWS by typing commands.
- **Best for:**
Power users, automation, and reducing human error.
- **Example:**
Launching a server with a single command instead of many clicks.

---

### 3. AWS Software Development Kits (SDKs) 👩‍💻

- **What is it?**
Libraries for popular programming languages (Python, Java, Node.js, etc.).
- **How it feels:**
Like writing code that talks directly to AWS.
- **Best for:**
Developers who want to automate AWS tasks from their applications.
- **Example:**
Your Python app uploads employee photos to AWS S3 using the Python SDK.

---

## 🛠️ Real-World Example

- **Console:** Like using a vending machine—choose what you want by pressing buttons.
- **CLI:** Like texting your order to the vending machine.
- **SDK:** Like programming a robot to buy snacks for you automatically.

---

## 📝 Recap

- **Console:** Easy, visual, great for beginners.
- **CLI:** Fast, scriptable, reduces mistakes.
- **SDKs:** Powerful, lets you automate AWS from your code.

> In this course, you’ll mostly use the Console, but feel free to try the CLI or SDKs as you get more comfortable! 🚀
> 

# 🤝 Interacting with AWS

Every action you take in AWS—creating a server, uploading a file, or deleting a database—is an **API call**. You can make these API calls in three main ways:

---

## 1. 🖱️ AWS Management Console

- **What is it?**
A web-based dashboard you access in your browser.
- **How it works:**
Click to create, manage, and view resources.
Services are grouped by category (compute, storage, security, etc.).
- **Region Selector:**
Change the Region in the top right to work in a different AWS location.
- **Real-world example:**
Like using an online banking website—point, click, and manage your money (or in this case, your cloud resources).

---

## 2. 💻 AWS Command Line Interface (CLI)

- **What is it?**
A tool you use in your terminal or command prompt.
- **How it works:**
Type commands to manage AWS resources. Great for automation and scripting.
- **Real-world example:**
Imagine you have 50 servers and want to collect data from all of them every day. Instead of clicking 50 times, you run a script!
- **Sample CLI command:**
    
    ```
    aws ec2 describe-instances
    
    ```
    
    - This command returns details about your EC2 servers.

---

## 3. 👩‍💻 AWS Software Development Kits (SDKs)

- **What is it?**
Libraries for popular programming languages (Python, Java, Node.js, etc.).
- **How it works:**
Write code that interacts with AWS directly from your app.
- **Real-world example:**
Your Python app receives a cat photo and uploads it to AWS S3 automatically.
- **Sample Python code:**
    
    ```python
    import boto3
    
    ec2 = boto3.client('ec2')
    response = ec2.describe_instances()
    print(response)
    
    ```
    

---

## 📝 Recap Table

| Method | Best For | Example Use Case |
| --- | --- | --- |
| Console | Beginners, visual users | Click to create a server |
| CLI | Automation, scripting | Script to collect server data |
| SDK | Developers, integration | Code uploads photos to AWS S3 |

---

**In summary:**

You can interact with AWS using the Console (easy and visual), the CLI (powerful and scriptable), or SDKs (integrate AWS into your code). Choose the one that fits your needs! 🚀

# 🔒 Security and the AWS Shared Responsibility Model

When you use AWS, you don’t have to manage everything yourself—AWS handles a lot of the heavy lifting. But security is a **shared responsibility** between you and AWS.

---

## 🤝 What is the Shared Responsibility Model?

- **AWS is responsible for:**
    
    **Security OF the cloud**
    
    (The physical data centers, hardware, networking, and the software that runs AWS services.)
    
- **You are responsible for:**
    
    **Security IN the cloud**
    
    (Your data, access controls, encryption, and how you configure your AWS resources.)
    

---

## 🏢 Real-World Example

Think of AWS as an apartment building:

- **AWS:** Builds and secures the building (locks, guards, cameras).
- **You:** Rent an apartment and must lock your own door and keep your valuables safe.

---

## 🛡️ What AWS Secures

- Data centers (physical security, guards, fences)
- Global network (fiber cables, connections)
- Hardware and virtualization layer (host OS, hypervisor)

---

## 🔑 What You Secure

- Your operating systems and applications (patching, updates)
- Data encryption (in transit and at rest)
- Firewalls and network rules
- User access and permissions

> Example:
> 
> 
> If you launch an EC2 virtual machine, AWS secures the physical server and virtualization.
> 
> **You** must patch your VM’s OS, set up firewalls, and control who can log in.
> 

---

## 📝 Key Points

- You **own your data** in AWS—protect it!
- Use AWS security features (like encryption and IAM) to secure your resources.
- The shared responsibility model can vary by service—always check what you’re responsible for.

---

**In summary:**

AWS keeps the cloud itself secure, but you must secure what you put in the cloud. Lock your “apartment” and keep your data safe! 🏢🔐

# 🔒 Security and the AWS Shared Responsibility Model

When you use AWS, **security** is a team effort between you and AWS.

This is called the **Shared Responsibility Model**.

---

## 🏢 What Does "Shared Responsibility" Mean?

- **AWS** protects the cloud itself (the buildings, computers, and networks).
- **You** protect what you put in the cloud (your data, settings, and who can access it).

---

## 🏗️ What AWS Does (Security OF the Cloud)

AWS is responsible for:

- Keeping data centers safe (guards, cameras, locked doors)
- Managing the hardware (physical computers and networking)
- Running the basic software (like the operating system for their servers)

---

## 👤 What You Do (Security IN the Cloud)

You are responsible for:

- Setting up your AWS services correctly
- Protecting your data (like using passwords and encryption)
- Deciding who can access your resources

---

## 📊 Table: Who Does What?

| Category | AWS Responsibility | Your Responsibility | Example Service |
| --- | --- | --- | --- |
| **Infrastructure** | Hardware, networking, basic software | OS, apps, data, access, encryption | EC2 (virtual server) |
| **Container** | Hardware, OS, app platform | Data, network security, backups | RDS (database) |
| **Abstracted** | Everything except your data (infra, OS, platform, encryption) | Data, client-side encryption | S3 (storage) |

---

## 🗝️ Real-World Example

- **AWS:** Like a landlord who secures the building and keeps the lights on.
- **You:** Like a tenant who locks your apartment door and keeps your valuables safe.

---

## 📝 Your Key Responsibilities

- **Choose the right Region** (where your data lives, for legal reasons)
- **Encrypt your data** (so only you can read it)
- **Control access** (decide who can see or change your stuff)
- **Back up your data** (so you don’t lose it)

---

## 🖼️ Diagram: Shared Responsibility

```
+---------------------+         +---------------------+
|  AWS (the landlord) |         |  You (the tenant)   |
|---------------------|         |---------------------|
| - Data centers      |         | - Your data         |
| - Hardware          |         | - Access control    |
| - Networking        |         | - Encryption        |
| - OS/platform (some)|         | - Backups           |
+---------------------+         +---------------------+

```

---

**In summary:**

AWS keeps the cloud safe and running.

You keep your data safe and control who can access it.

Always check what you’re responsible for, depending on the AWS service you use!
