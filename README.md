# ws-vpc-project
# 🌩️ AWS VPC Project - Day 1 (Manual Setup)

## 📌 Project Overview
This project involves setting up a secure AWS VPC with public and private subnets manually using the AWS Console.

## 🛠️ AWS Services Used
- **VPC** (CIDR: 10.0.0.0/16)
- **Subnets** (1 Public, 1 Private)
- **Internet Gateway**
- **Route Tables**
- **Security Groups**

## 🚀 Steps Performed
1. **Created a VPC**
   - CIDR Block: `10.0.0.0/16`
2. **Created Subnets**
   - Public Subnet (`10.0.1.0/24`)
   - Private Subnet (`10.0.2.0/24`)
3. **Added an Internet Gateway**
   - Attached it to the VPC
4. **Configured Route Tables**
   - Public Subnet: Route to Internet Gateway
   - Private Subnet: No direct internet access
5. **Updated Security Groups**
   - Allowed SSH access for Public EC2 instance


---
