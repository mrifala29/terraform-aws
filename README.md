# Terraform AWS Infrastructure – VPC, ALB & Auto Scaling

Infrastructure as Code (IaC) project using **Terraform** to provision a highly available AWS architecture consisting of:

- VPC
- Public Subnets across 2 Availability Zones
- Application Load Balancer (ALB)
- Launch Template
- Auto Scaling Group
- EC2 instances distributed across multiple AZs

This project follows modular and environment-based best practices suitable for real-world DevOps workflows.

---

## 📐 Architecture Overview

High-level flow:

Internet  
→ Application Load Balancer  
→ Target Group  
→ Auto Scaling Group  
→ EC2 Instances (Multi-AZ)  
→ Inside VPC  

The infrastructure is designed for:
- High availability (Multi-AZ)
- Scalability (Auto Scaling)
- Modularity (Reusable Terraform modules)
- Environment separation (dev / prod)

---

## 📂 Project Structure Explanation

This repository follows a modular and environment-based Terraform structure aligned with production-grade DevOps practices.


---

### 📦 modules/

The `modules` directory contains reusable Terraform building blocks.  
Each module represents a logical infrastructure component and is designed to be environment-agnostic.

Example modules:

- **vpc/** → Creates VPC, subnets, route tables, and internet gateway.
- **ec2/** → Defines Launch Template configuration.
- **alb/** → Provisions Application Load Balancer, Target Group, and Listener.
- **autoscaling/** → Creates Auto Scaling Group attached to ALB.

Each module typically contains:


All `.tf` files inside a module directory are automatically loaded and treated as a single logical unit.

---

### 🌍 environments/

The `environments` directory acts as the orchestration layer.

Each environment:
- Calls the required modules
- Defines environment-specific variables
- Configures provider and backend settings

Example:


This separation ensures:

- Clear isolation between `dev`, `staging`, and `prod`
- Independent state management per environment
- Safe multi-environment deployments

---

### 🌐 global/

The `global` directory contains shared infrastructure components that are not environment-specific.

Typical examples:

- S3 bucket for remote Terraform state
- DynamoDB table for state locking
- Shared IAM roles

Global resources are provisioned once and reused across environments.

---

### 🔒 .gitignore

Sensitive and generated files are excluded from version control:


This prevents:
- Accidental exposure of infrastructure state
- Credential leakage
- Local provider cache uploads

---

## 🧠 Design Philosophy

This project follows these principles:

- **Modularity** → Reusable infrastructure components
- **Environment Isolation** → Clean separation between dev and prod
- **Scalability** → Multi-AZ, load-balanced architecture
- **Maintainability** → Clear directory boundaries and responsibility separation

The structure mirrors real-world DevOps practices used in production environments.