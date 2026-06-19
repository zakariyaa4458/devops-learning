# AWS Assignment 1 – Custom VPC with Public and Private Subnets

## Overview

This project demonstrates the creation of a secure AWS networking environment using Amazon Virtual Private Cloud (VPC). The infrastructure includes public and private subnets, internet connectivity through an Internet Gateway and NAT Gateway, EC2 instances, security groups, and CloudWatch monitoring.

---

## Objectives

The goal of this assignment was to:

* Create a custom VPC
* Configure one public subnet and one private subnet
* Enable internet connectivity using an Internet Gateway and NAT Gateway
* Deploy EC2 instances into both subnets
* Secure access using Security Groups
* Configure CloudWatch monitoring

---

## Architecture Components

* Amazon VPC (10.0.0.0/16)
* Public Subnet
* Private Subnet
* Internet Gateway (IGW)
* Elastic IP (EIP)
* NAT Gateway
* Public EC2 Instance
* Private EC2 Instance
* Security Groups
* Amazon CloudWatch Alarm

---

## VPC Configuration

| Resource       | Configuration |
| -------------- | ------------- |
| VPC CIDR Block | 10.0.0.0/16   |
| Public Subnet  | Created       |
| Private Subnet | Created       |

The VPC provides an isolated network environment within AWS. The public subnet hosts resources that require internet access, while the private subnet hosts resources that should not be directly accessible from the internet.

---

## Internet Access Configuration

### Internet Gateway

An Internet Gateway was attached to the VPC to provide internet connectivity for resources located in the public subnet.

### Elastic IP

An Elastic IP address was allocated and associated with the NAT Gateway.

### NAT Gateway

A NAT Gateway was deployed within the public subnet.

Purpose:

* Allows instances in the private subnet to access the internet.
* Prevents direct inbound connections from the internet to private resources.
* Enables software updates and package downloads for private instances.

---

## Route Tables

### Public Route Table

| Destination | Target           |
| ----------- | ---------------- |
| 10.0.0.0/16 | Local            |
| 0.0.0.0/0   | Internet Gateway |

### Private Route Table

| Destination | Target      |
| ----------- | ----------- |
| 10.0.0.0/16 | Local       |
| 0.0.0.0/0   | NAT Gateway |

These route tables ensure that public resources can communicate directly with the internet while private resources use the NAT Gateway for outbound internet access.

---

## EC2 Instances

### Public EC2 Instance

Configuration:

* Deployed in the Public Subnet
* Public IPv4 address enabled
* Instance type: t3.micro

Purpose:

* Accessible from the internet
* Used to demonstrate a publicly accessible workload

### Private EC2 Instance

Configuration:

* Deployed in the Private Subnet
* No Public IPv4 address
* Instance type: t3.micro

Purpose:

* Not directly accessible from the internet
* Used to demonstrate secure internal resources

---

## Security Groups

### Public EC2 Security Group

Inbound Rules:

| Protocol | Port | Source       |
| -------- | ---- | ------------ |
| SSH      | 22   | My Public IP |
| HTTP     | 80   | My Public IP |

### Private EC2 Security Group

Inbound Rules:

| Protocol | Port | Source      |
| -------- | ---- | ----------- |
| SSH      | 22   | 10.0.0.0/16 |

This configuration restricts access to the private instance and follows the principle of least privilege.

---

## CloudWatch Monitoring

Amazon CloudWatch was configured to monitor EC2 instance performance.

Metrics monitored include:

* CPU Utilization
* EBS Read Operations
* EBS Write Operations

A CloudWatch alarm was created to demonstrate monitoring and alerting capabilities.

---

## Screenshots Included

* VPC Configuration
* Public and Private Subnets
* Internet Gateway
* NAT Gateway
* Route Tables
* Public EC2 Instance
* Private EC2 Instance
* Security Groups
* CloudWatch Alarm

---

## Skills Demonstrated

* AWS Networking
* Amazon VPC Configuration
* Subnet Design
* Internet Gateway Configuration
* NAT Gateway Deployment
* Route Table Configuration
* EC2 Deployment
* Security Group Management
* CloudWatch Monitoring
* Cloud Infrastructure Fundamentals

---

## Outcome

This project successfully implemented a secure AWS network architecture using public and private subnets. Internet access was controlled through an Internet Gateway and NAT Gateway, EC2 instances were deployed according to network requirements, and CloudWatch was used to monitor instance performance.

