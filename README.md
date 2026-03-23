# AWS Static Website Hosting

## Overview
This project hosts a static website using AWS services including S3, CloudFront, and NameCheap.

## Architecture
User → DNS (Namecheap) → CloudFront (CDN + HTTPS + WAF) → S3 (private bucket via OAC)

## Steps
1. Build Website Locally
- Created a simple portfolio using HTML, CSS, and JavaScript
- Structured files for deployment
- Tested locally in browser
2. Created S3 bucket, enabled static hosting and uploaded website files
- Created S3 bucket
- Disabled block public access
- Enabled static website hosting
- Configured index document (index.html)
- Applied bucket policy for public read access
- Uploaded website files
- Verified website using S3 endpoint
3. Configured CloudFront distribution
- Created a CloudFront distribution in front of the S3-hosted static website
- Selected the S3 bucket as the origin
- Enabled HTTP-to-HTTPS redirection
- Applied the CachingOptimized policy to improve content delivery performance
- Verified website access through the CloudFront distribution URL
* Tested two CloudFront origin models:
  - S3 bucket origin: returned AccessDenied under the current configuration
  - S3 website endpoint: worked successfully with static website hosting enabled
  -> Conclusion: Used the S3 website endpoint for the initial working deployment, with the option to migrate later to a more secure S3 bucket origin + OAC architecture.
4. Set Up Origin Access Control
- Configured Origin Access Control so CloudFront could securely access S3 content
- Updated the CloudFront origin to use the S3 bucket instead of the website endpoint
- Replaced public S3 read access with a restricted bucket policy for CloudFront only
- Improved security by preventing direct public access to website objects
5. Register Domain + Provision SSL Certificate
- Registered domain using Namecheap
- Requested SSL certificate using AWS Certificate Manager (ACM)
- Validated domain ownership via DNS records
- Configured CloudFront with custom domain and SSL certificate
- Updated DNS records to point domain to CloudFront distribution
- Attached ACM SSL certificate for HTTPS
- Updated DNS records in Namecheap to point domain to CloudFront
- Verified secure access via custom domain
  * Note:
  Due to DNS limitations, the root domain was redirected to the www subdomain, which is connected     to the CloudFront distribution.
6. Configure WAF Protection + Set Up DNS Records
- Security protections from WAF are included in the plan

## Live Demo
https://www.thaotppham-portfolio.com/

## Technologies Used
- HTML
- CSS
- AWS S3
- AWS CloudFront
- AWS Certificate Manager (ACM)
- AWS WAF

## What I Learned
- Buckets are private by default and require explicit public access
- Importance of least-privilege permissions (s3:GetObject only)
- Difference between local development and cloud deployment
- How CDN improves performance
- DNS configuration basics
- Securing websites with HTTPS
