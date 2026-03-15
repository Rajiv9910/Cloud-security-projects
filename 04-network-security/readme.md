# Network Security in AWS VPC
## Overview

This project demonstrates how AWS network security controls regulate traffic within a Virtual Private Cloud (VPC).

The focus is on understanding how **Security Groups** and **Network ACLs** work together to enforce layered network security.

Security Groups act as **instance-level firewalls**, while Network ACLs act as **subnet-level firewalls**, providing defense-in-depth protection.

---

## Architecture

The architecture consists of a VPC containing an EC2 instance protected by two layers of network security:

- **Security Groups** – control inbound and outbound traffic at the instance level.
- **Network ACLs** – control traffic entering and leaving the subnet.

Together they provide layered traffic filtering within the VPC.

![Network Security Architecture](images/network-security-architecture.png)

---

## Implementation Steps

### Create a Security Group

Created a security group for the EC2 instance and configured inbound rules to allow specific traffic such as HTTP.

### Configure Security Group Rules

Added inbound rules defining which ports and sources were allowed to communicate with the instance.

### Configure a Network ACL

Configured a Network ACL for the subnet to filter traffic entering and leaving the subnet.

### Apply Layered Network Security

Verified that both the Security Group and Network ACL worked together to control network traffic.

---

## Skills Demonstrated

- Security Group configuration
- Network ACL configuration
- Layered network security
- Instance-level vs subnet-level firewall rules
- Traffic filtering in AWS

---

## Screenshots

### Security Group Rules
![Security Group](images/security-group.png)

### Network ACL Rules
![Network ACL](images/network-acl.png)