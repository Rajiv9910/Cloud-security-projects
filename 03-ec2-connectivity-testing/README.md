# EC2 Deployment and VPC Connectivity Testing

## Overview
This project demonstrates how to launch EC2 instances in both public and private subnets within an Amazon VPC.

The goal was to understand how subnet placement affects access, how security groups differ for public and private resources, and how AWS tools such as key pairs and the VPC resource map simplify deployment.

---

## Architecture

The architecture consists of a single VPC with both public and private subnets.

- **Public subnet** – hosts an EC2 instance that can be accessed directly from the internet through an Internet Gateway.
- **Private subnet** – hosts an EC2 instance that is isolated from direct internet access.
- **Security groups** – configured separately to control traffic to the public and private instances.
- **Key pair** – created to allow secure SSH access to the EC2 instance.
- **VPC resource map** – used through the **VPC and more** workflow to visualise the deployed infrastructure.

The following diagram illustrates the deployment of EC2 instances across public and private subnets within the VPC.

![VPC Architecture](images/vpc-architecture.png)

---

## Implementation Steps

### Create a Key Pair
Created a key pair in `.pem` format to securely authenticate to the EC2 instance.

### Launch a Public EC2 Instance
Deployed an EC2 instance into the public subnet and configured its networking settings so it used the custom VPC environment.

### Launch a Private EC2 Instance
Deployed a second EC2 instance into the private subnet with a dedicated security group to restrict access and prevent direct internet connectivity.

### Configure Security Groups
Used separate security groups for the public and private instances to reflect different access requirements.

### Use the VPC and More Workflow
Used the **VPC and more** option to create the VPC, subnets, route tables, and Internet Gateway more efficiently while using the AWS resource map to visualise the architecture.

---

## Connectivity Testing

After deploying the EC2 instances, connectivity tests were performed to verify that the VPC networking configuration was functioning correctly.

### Connecting to the Public EC2 Instance

Used **EC2 Instance Connect** to access the public EC2 instance through the AWS console.  
The first connection attempt failed because the security group only allowed HTTP traffic while SSH access was required.

This issue was resolved by updating the security group to allow **SSH (port 22)** access, after which the connection was successful.

### Testing Connectivity Between Instances

Used the **ping** command from the public server to test connectivity to the private server using its private IP address.
ping 10.0.130.143

This verified that the two instances could communicate internally within the VPC network.

### Testing Internet Connectivity

Used the **curl** command from the public EC2 instance to test connectivity to an external website.

The command returned HTML content from the website, confirming that the public instance had internet connectivity through the Internet Gateway.

---

## Skills Demonstrated
- EC2 deployment in public and private subnets
- SSH key pair usage
- Security group configuration
- Public vs private workload placement
- AWS VPC resource map usage
- Cloud network architecture design

---

## Screenshots

### VPC Creation Using "VPC and More"
![VPC Creation](images/vpc-and-more.png)

### Public EC2 Instance
![Public EC2](images/public-ec2.png)

### Private Security Group
![Private Security Group](images/private-security-group.png)

### Connecting to the EC2 Instance
![EC2 Connection](images/ec2-connection.png)

### Initial Connectivity Test
![Initial Ping](images/initial-ping.png)

### Successful Ping Between Instances
![Successful Ping](images/successful-ping.png)

### Internet Connectivity Test (curl)
![Curl Test](images/curl.png)