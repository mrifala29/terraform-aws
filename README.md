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
