# Host a Static Website on AWS

## Overview
This project demonstrates how to host a static HTML web application on AWS using various AWS services. The deployment process includes configuring networking components, securing the infrastructure, and ensuring high availability and scalability.

## Project Repository
The reference diagram and deployment scripts are available in the project’s GitHub repository:(https://github.com/Vic299/AWS-Static-Website.git)

## AWS Resources Utilized
1. **Virtual Private Cloud (VPC)**: Configured with both public and private subnets across two availability zones.
2. **Internet Gateway**: Facilitates connectivity between VPC instances and the Internet.
3. **Security Groups**: Used as a network firewall mechanism.
4. **Availability Zones**: Ensures reliability and fault tolerance.
5. **Public Subnets**: Used for infrastructure components like NAT Gateway and Application Load Balancer.
6. **EC2 Instance Connect Endpoint**: Secure connections to assets in both public and private subnets.
7. **Private Subnets**: Web servers (EC2 instances) positioned within private subnets for security.
8. **NAT Gateway**: Enables instances in private application and data subnets to access the Internet.
9. **EC2 Instances**: Hosts the website.
10. **Application Load Balancer (ALB) & Target Group**: Distributes web traffic evenly across an Auto Scaling Group of EC2 instances.
11. **Auto Scaling Group**: Ensures website availability, scalability, fault tolerance, and elasticity.
12. **GitHub**: Stores web files for version control and collaboration.
13. **AWS Certificate Manager**: Secures application communications.
14. **Amazon Simple Notification Service (SNS)**: Sends alerts about activities within the Auto Scaling Group.
15. **Amazon Route 53**: Registers the domain name and manages DNS records.

## Deployment Script
The following bash script automates the deployment of the static website on an EC2 instance:

```bash
#!/bin/bash
# Switch to root user
sudo su

# Update installed packages
yum update -y

# Install Apache HTTP Server
yum install -y httpd

# Change to Apache web root directory
cd /var/www/html

# Install Git
yum install git -y

# Clone the project repository
git clone https://github.com/aosnotes77/host-a-static-website-on-aws.git

# Copy all files from the cloned repository to Apache web root
cp -R host-a-static-website-on-aws/. /var/www/html/

# Remove the cloned repository directory
rm -rf host-a-static-website-on-aws

# Enable and start Apache HTTP Server
systemctl enable httpd
systemctl start httpd
```

## How to Use
1. Launch an EC2 instance within the configured AWS environment.
2. Connect to the instance via SSH.
3. Execute the provided script to set up the web server.
4. Access the website through the domain name registered in Route 53.

## Conclusion
This project highlights best practices in AWS networking, security, and scalability while hosting a static website. By leveraging AWS services like ALB, Auto Scaling, and Route 53, the website achieves high availability and fault tolerance.

