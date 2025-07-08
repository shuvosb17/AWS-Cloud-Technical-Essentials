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
