# AWS Static Website Portfolio

## Overview

This project demonstrates how to host a static website on Amazon Web Services (AWS) using Amazon S3, Amazon CloudFront, AWS Certificate Manager (ACM), Route 53, and a custom domain.

The website is hosted in an S3 bucket, delivered globally through CloudFront, secured with HTTPS using an ACM SSL/TLS certificate, and accessed through a custom subdomain.

**Website URL:**

https://aws.zakariyaalab.com

---

## Architecture

User
↓
Route 53
↓
CloudFront Distribution
↓
Amazon S3 Bucket

---

## Services Used

### Amazon S3 (Simple Storage Service)
- Stores the website files.
- Configured for static website hosting.
- Hosts the `index.html` page.

### Amazon CloudFront
- Content Delivery Network (CDN).
- Delivers website content from edge locations worldwide.
- Provides improved performance and lower latency.
- Integrates with ACM for HTTPS.

### AWS Certificate Manager (ACM)
- Issued a public SSL/TLS certificate.
- Enabled secure HTTPS access.
- Certificate validated using DNS records.

### Amazon Route 53
- Managed DNS records.
- Created an Alias record pointing the subdomain to CloudFront.

### Cloudflare
- Domain registrar and DNS provider.
- Used for DNS validation during certificate issuance.

---

## Implementation Steps

### 1. Create an S3 Bucket
- Created an S3 bucket.
- Enabled Static Website Hosting.
- Uploaded website files.
- Configured `index.html` as the default document.

### 2. Create a CloudFront Distribution
- Selected the S3 website endpoint as the origin.
- Configured default cache settings.
- Set the default root object to:

```text
index.html
```

### 3. Request an SSL Certificate
- Requested a certificate through ACM.
- Added DNS validation records in Cloudflare.
- Waited for certificate status to become:

```text
Issued
```

### 4. Configure CloudFront HTTPS
- Added custom domain:

```text
aws.zakariyaalab.com
```

- Attached ACM certificate.
- Enabled HTTPS support.

### 5. Configure Route 53
- Created a hosted zone.
- Added an Alias A Record.

```text
aws.zakariyaalab.com
        ↓
CloudFront Distribution
```

### 6. Verify Website Access
Successfully accessed the website using:

```text
https://aws.zakariyaalab.com
```

---

## Challenges Encountered

### SSL Certificate Errors
Encountered:

```text
NET::ERR_CERT_COMMON_NAME_INVALID
```

and

```text
ERR_SSL_VERSION_OR_CIPHER_MISMATCH
```

**Resolution:**
- Added correct DNS validation records.
- Attached ACM certificate to CloudFront.
- Waited for CloudFront deployment to complete.

### CloudFront 403 Error
Encountered:

```text
403 ERROR
The request could not be satisfied.
```

**Resolution:**
- Configured the correct S3 website endpoint.
- Added `index.html` as the default root object.

---

## Skills Demonstrated

- Amazon S3
- Amazon CloudFront
- AWS Certificate Manager (ACM)
- Amazon Route 53
- DNS Management
- SSL/TLS Certificates
- Static Website Hosting
- Content Delivery Networks (CDN)
- Troubleshooting AWS Services

---

## Future Improvements

- Add a professional portfolio homepage.
- Include AWS project documentation.
- Add GitHub and LinkedIn links.
- Create additional subdomains for future projects.
- Integrate CI/CD deployment using GitHub Actions.

## Screenshots 
- AWS portfolio screen after secured with HTTPS
- AWS portfolio screen before it was given the domain name
- Settings of the Cloudfront CDN 
- S3 bucket and the files in it
