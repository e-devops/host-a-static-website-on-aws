![Alt text](/e-devops-Host_a_Static_Website_on_AWS.png)

# Host a Static Website on AWS

This project demonstrates how to host a static HTML web app on AWS, leveraging a range of AWS resources to ensure security, scalability, and reliability. The website is deployed on EC2 instances within a Virtual Private Cloud (VPC) and utilizes various AWS services to enhance its performance and availability.

## Table of Contents

- [Overview](#overview)
- [Architecture](#architecture)
- [Prerequisites](#prerequisites)
- [Deployment](#deployment)
- [AWS Resources Used](#aws-resources-used)
- [Scripts](#scripts)
- [Contact](#contact)

## Overview

This project involves hosting a static HTML web application on AWS using a robust architecture that includes VPC, EC2, Internet Gateway, NAT Gateway, Application Load Balancer, Auto Scaling Group, and more. The web app is designed to be highly available, scalable, and secure.

## Architecture

The architecture consists of the following key components:

1. **VPC**: Configured with both public and private subnets across two availability zones.
2. **Internet Gateway**: Facilitates connectivity between VPC instances and the wider Internet.
3. **Security Groups**: Act as a network firewall mechanism.
4. **Availability Zones**: Leverage multiple zones for fault tolerance.
5. **Public Subnets**: Host infrastructure components like the NAT Gateway and Application Load Balancer.
6. **Private Subnets**: Host web servers (EC2 instances) for enhanced security.
7. **NAT Gateway**: Allows instances in private subnets to access the Internet.
8. **Application Load Balancer**: Distributes web traffic evenly across EC2 instances.
9. **Auto Scaling Group**: Automatically manages EC2 instances for scalability and availability.
10. **Certificate Manager**: Secures application communications.
11. **SNS**: Configured to send alerts about Auto Scaling Group activities.
12. **Route 53**: Used for domain name registration and DNS configuration.

## Prerequisites

Before deploying this project, ensure you have the following:

- An AWS account with necessary permissions.
- A registered domain name.
- Basic knowledge of AWS services (VPC, EC2, S3, Route 53, etc.).
- Git installed on your local machine.

## Deployment

### Step 1: Clone the Repository

```bash
git clone https://github.com/e-devops/host-a-static-website-on-aws.git
cd host-a-static-website-on-aws
```

### Step 2: Configure AWS Services

- **VPC and Subnets**: Configure a VPC with public and private subnets across two availability zones.
- **Internet Gateway**: Attach an Internet Gateway to the VPC.
- **Security Groups**: Create security groups for web servers and load balancers.
- **NAT Gateway**: Deploy a NAT Gateway in the public subnet.
- **EC2 Instances**: Launch EC2 instances in private subnets.
- **Application Load Balancer**: Set up an Application Load Balancer and target group.
- **Auto Scaling Group**: Create an Auto Scaling Group for the EC2 instances.
- **Certificate Manager**: Secure communications using SSL/TLS certificates.
- **SNS**: Set up notifications for Auto Scaling Group activities.
- **Route 53**: Register your domain and configure DNS settings.

### Step 3: Deploy the Web App

Run the following script on your EC2 instance:

```bash
#!/bin/bash

# Switch to the root user
sudo su

# Update installed packages
yum update -y

# Install Apache HTTP Server
yum install -y httpd

# Change to the Apache web root directory
cd /var/www/html

# Install Git
yum install git -y

# Clone the project repository
git clone https://github.com/e-devops/host-a-static-website-on-aws.git

# Copy all files to the web root
cp -R host-a-static-website-on-aws/. /var/www/html/

# Clean up unnecessary files
rm -rf host-a-static-website-on-aws

# Enable Apache to start at boot
systemctl enable httpd 

# Start Apache HTTP Server
systemctl start httpd
```

### Step 4: Access the Website

After deployment, access your website using the domain name registered with Route 53.

## AWS Resources Used

This project utilizes the following AWS resources:

1. **VPC**: Virtual Private Cloud with multiple subnets.
2. **Internet Gateway**: For internet connectivity.
3. **Security Groups**: For network security.
4. **EC2 Instances**: Hosts the static web app.
5. **NAT Gateway**: Enables outbound internet access from private subnets.
6. **Application Load Balancer**: Distributes traffic.
7. **Auto Scaling Group**: Manages EC2 instances.
8. **Certificate Manager**: Secures communications.
9. **SNS**: Sends notifications.
10. **Route 53**: Domain name registration and DNS management.

## Scripts

The deployment script used in this project is included in the repository:

- [Deployment Script](#)

## Contact

For any questions or feedback, feel free to reach out:

- Your Name - [@e-devops] - dev-sec-ops@outlook.com
- Project Link: [https://github.com/e-devops/host-a-static-website-on-aws](https://github.com/e-devops/host-a-static-website-on-aws)

---

You can customize this README to fit your project’s needs further.
