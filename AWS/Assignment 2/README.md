# Assignment 2 - Application Load Balancer (ALB)

## Overview

This project demonstrates how to deploy multiple Amazon EC2 instances behind an Application Load Balancer (ALB). The objective was to distribute incoming traffic across multiple servers, perform health checks, and improve security by preventing direct public access to the EC2 instances.

## Architecture

```text
Internet
    │
    ▼
Application Load Balancer (ALB)
    │
    ▼
Target Group
 ┌─────────────┬─────────────┐
 ▼             ▼
EC2 Instance 1 EC2 Instance 2
(Server 1)     (Server 2)
```

## Objectives

* Launch two EC2 instances within the same VPC.
* Install a web server using EC2 User Data.
* Configure each instance to display different content.
* Create an Application Load Balancer.
* Create and configure a Target Group.
* Register both EC2 instances with the Target Group.
* Configure health checks.
* Restrict direct access to EC2 instances using Security Groups.
* Verify traffic is distributed between both instances.

## Services Used

* Amazon EC2
* Application Load Balancer (ALB)
* Target Groups
* Security Groups
* VPC

## EC2 Configuration

### Instance 1

Displays:

```html
<h1>Server 1</h1>
```

### Instance 2

Displays:

```html
<h1>Server 2</h1>
```

### User Data Script

```bash
#!/bin/bash
yum update -y
yum install -y httpd
systemctl start httpd
systemctl enable httpd
echo "<h1>Server 1</h1>" > /var/www/html/index.html
```

The second instance used the same script with "Server 2" as the webpage content.

## Target Group Configuration

* Target Type: Instance
* Protocol: HTTP
* Port: 80
* Health Check Path: /

Both EC2 instances were registered as targets and successfully passed health checks.

## Application Load Balancer Configuration

* Type: Application Load Balancer
* Scheme: Internet-facing
* Listener: HTTP (Port 80)
* Availability Zones: Two Availability Zones
* Routing: Forward requests to the Target Group

## Security Configuration

### ALB Security Group

Inbound Rules:

* HTTP (Port 80) from `0.0.0.0/0`

### EC2 Security Group

Inbound Rules:

* SSH (Port 22) from my IP address
* HTTP (Port 80) from the ALB Security Group only

This configuration prevents users from accessing the EC2 instances directly and ensures all traffic passes through the ALB.

## Testing

### Load Balancer Testing

The ALB DNS name was accessed through a web browser.

Refreshing the page alternated between:

* Server 1
* Server 2

confirming that the Application Load Balancer was successfully distributing traffic across both EC2 instances.

### Security Testing

Direct access to the EC2 public IP addresses was blocked after updating the security group rules.

This confirmed that only the ALB could communicate with the EC2 instances.

## Results

* Two EC2 instances deployed successfully.
* Application Load Balancer created and configured.
* Health checks passed successfully.
* Traffic distributed across both EC2 instances.
* Direct public access to EC2 instances blocked.
* Assignment objectives achieved successfully.

## Screenshots

Include screenshots of:

1. EC2 Instances running.
2. Server 1 webpage.
3. Server 2 webpage.
4. Target Group showing healthy targets.
5. Application Load Balancer configuration.
6. ALB DNS page displaying Server 1 and Server 2.
7. Security Group configuration showing HTTP access restricted to the ALB Security Group.

