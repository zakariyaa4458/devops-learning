# EC2 + NGINX + DNS Project

## Overview

This project involved deploying a web server on AWS EC2, installing NGINX, and connecting a custom domain using Cloudflare DNS.

Domain used:

zakariyaalab.com

## What I Built

I launched an Amazon EC2 instance running Amazon Linux 2023.

I configured security groups to allow SSH and HTTP traffic.

I connected to the server using EC2 Instance Connect.

I installed and started NGINX.

I configured DNS A records in Cloudflare to point my domain to the EC2 public IP address.

The website is accessible using both the public IP address and the domain name.

## Architecture

Browser
↓
zakariyaalab.com
↓
Cloudflare DNS
↓
AWS EC2
↓
NGINX
↓
Web Page

## What I Learned

- How DNS translates domain names into IP addresses.
- How EC2 instances work in AWS.
- How Security Groups act as firewalls.
- How to connect to Linux servers using SSH.
- How to install and manage services using systemctl.
- How NGINX serves web content.
- How domains are connected to servers using DNS A records.

## Challenges

### Challenge 1

Initially the website did not load when using the public IP address.

### Solution

I verified that NGINX was running and confirmed that HTTP traffic on port 80 was allowed through the Security Group.

### Challenge 2

I had never used AWS before.

### Solution

I learned how to launch EC2 instances, configure security groups and use EC2 Instance Connect to manage a Linux server.

## Result

The domain zakariyaalab.com successfully loads the NGINX welcome page hosted on an AWS EC2 instance.
