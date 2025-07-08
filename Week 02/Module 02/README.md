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
