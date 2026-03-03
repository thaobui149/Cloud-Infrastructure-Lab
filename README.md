# Cloud Infrastructure Lab – WordPress Deployment on AWS

## Overview

This project demonstrates the deployment of a highly available WordPress application on AWS using Terraform (Infrastructure as Code).

The goal was to design and provision a structured multi-tier architecture including networking, compute, database, and security components.

The project was implemented as part of an AWS Cloud Computing Bootcamp.

---

## Architecture
![Architecture Diagram](diagram/architecture-v01.png)


### Network Design
- Custom VPC (10.0.0.0/16)
- Public Subnets (ALB, Bastion, NAT)
- Private Subnets (EC2, RDS)
- NAT Gateway for outbound traffic
- No public IPs for application servers

---

## Implemented Components

### Compute
- Application Load Balancer
- Auto Scaling Group (min 2, max 3)
- Launch Template with automated WordPress installation
- Bastion Host for administrative access

### Database
- Amazon RDS MySQL 8.x
- Deployed in private subnets
- Security group restricted access

### Storage
- Amazon EFS (shared wp-content directory)
- Amazon S3 (prepared for backups/static assets)

### Security
- Security Groups (least privilege principle)
- Private EC2 instances
- IAM roles for service permissions
- Optional WAF integration

### Monitoring
- CloudWatch metrics
- Basic scaling policies

---

## Infrastructure as Code

All infrastructure components are provisioned using Terraform:

- VPC, Subnets, Route Tables
- ALB & Target Groups
- Auto Scaling Group
- RDS
- EFS
- S3
- IAM Roles
- Security Groups

Remote state managed via Terraform Cloud.

---

## Deployment

```bash
terraform init
terraform plan
terraform apply
```
---
## Result

- Van Gogh Gallery accessible via ALB DNS
- High availability across two Availability Zones
- Fully automated and repeatable infrastructure

---

## Author

Thao Bui  
Bootcamp Capstone Project  
AWS | Terraform | Linux

