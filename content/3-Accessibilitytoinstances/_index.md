---
title: "Connect to EC2 via Session Manager"
date: 2025-07-02
weight: 3
chapter: false
pre: " <b> 3. </b> "
---

#### Connect to EC2 Public and Private Instances

In this section, we will connect to both **public** and **private EC2 instances** using **AWS Systems Manager Session Manager**, without opening SSH port 22.

We will demonstrate how to:
- Connect to a **public instance** using SSM.
- Connect to a **private instance** within a VPC using **VPC Interface Endpoint**.

This approach improves security by avoiding SSH and limiting internet exposure.

🧭 **Steps Overview:**
- The **public instance** requires an IAM role and outbound access on port 443 to communicate with Session Manager.
- The **private instance** connects through a **VPC endpoint for Systems Manager**, eliminating the need for outbound internet access.

### Content

- [3.1 - Connect to EC2 Public Instance](./3.1-Receive Notification via Gmail/)  
- [3.2 - Connect to EC2 Private Instance](./3.2-Receive Notification via CloudWatch/)
