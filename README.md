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

Day 2: Step-by-Step Guide – Launch EC2 Instances in Public & Private Subnets
Today’s goal:
✅ Launch two EC2 instances (one in a public subnet, one in a private subnet)
✅ Configure Security Groups for secure access
✅ Connect to the public EC2 via SSH
✅ Connect to the private EC2 via the public instance (Bastion Host concept)

Step 1: Launch an EC2 Instance in the Public Subnet
📌 This instance will have a public IP and act as a Bastion Host.

1️⃣ Open AWS EC2 Dashboard
Log in to AWS Console
Navigate to EC2 → Instances → Launch Instance
2️⃣ Configure Instance Details
Choose AMI: Select Amazon Linux 2 or Ubuntu 20.04
Instance Type: t2.micro (Free Tier)
Choose VPC & Subnet:
VPC: Select the VPC you created on Day 1
Subnet: Select the public subnet
✅ Enable Auto-Assign Public IP
3️⃣ Configure Security Group
📌 This controls access to your EC2 instance.

Allow SSH (Port 22) from Your IP only
Allow HTTP (Port 80) if you want to test web access later
4️⃣ Create a Key Pair & Launch Instance
Create a new key pair: aws-key.pem
Download and store it safely
Click Launch Instance
Step 2: Launch an EC2 Instance in the Private Subnet
📌 This instance will NOT have a public IP.

1️⃣ Follow the Same Steps as Above, but Change These:
Subnet: Select the private subnet
Auto-Assign Public IP: Disabled
Security Group:
Allow SSH only from Public EC2 Instance (Bastion Host)
📌 Do not allow direct SSH from the internet!

Click Launch Instance
Step 3: Connect to the Public EC2 Instance
📌 Use SSH to connect to the public instance.

Find Public IP:

Go to EC2 Dashboard → Instances
Copy the Public IP Address of the public EC2
Open Terminal and Run:

bash
Copy
Edit
ssh -i aws-key.pem ec2-user@your-public-ip
✅ You are now inside your public EC2 instance!

Step 4: Connect to the Private EC2 Instance via Public EC2 (Bastion Host)
📌 The private instance has no public IP, so you need to access it through the public instance.

1️⃣ Find Private IP of Private EC2
Go to EC2 Dashboard → Instances → Private EC2
Copy its Private IP Address
2️⃣ Inside Public EC2, Run:
bash
Copy
Edit
ssh -i aws-key.pem ec2-user@private-instance-ip
✅ You are now inside the private EC2 instance!


