## AWS Static Website Hosting

## Overview
Designed and deployed a secure, scalable static website using AWS cloud-native services with CDN, HTTPS, and access control.

## Architecture
User → DNS (Namecheap) → CloudFront (CDN + HTTPS + WAF) → S3 (private bucket via OAC)

## Key Features
- Global content delivery using CloudFront (low latency)
- HTTPS with AWS Certificate Manager
- Private S3 bucket with Origin Access Control (OAC)
- Web security layer using AWS WAF
- Custom domain integration via external DNS (Namecheap)

## Engineering Decisions
1. S3 Website Endpoint vs S3 Origin
- Initial attempt with S3 origin resulted in AccessDenied
- Switched to website endpoint for testing
- Migrated to S3 + OAC for production-grade security

2. Security Design
- Removed public bucket access
- Applied least-privilege policy (s3:GetObject via CloudFront only)
- Enabled WAF protections (included in plan)

3. CDN Optimization
- Used CloudFront caching (CachingOptimized policy)
- Reduced latency and improved performance globally

## Challenges & Solutions
- Issue: AccessDenied when using S3 origin
- Root Cause: Missing proper permissions between CloudFront and S3
- Solution:
  - Implemented Origin Access Control (OAC)
  - Updated bucket policy to allow only CloudFront

## Deployment Steps (Simplified)
1.	Built static website (HTML, CSS, JS)
2.	Configured S3 bucket
3.	Set up CloudFront distribution
4.	Implemented OAC and secured bucket
5.	Configured ACM SSL certificate
6.	Connected domain via Namecheap DNS

## Live Demo
https://www.thaotppham-portfolio.com/

## Skills Demonstrated
- Cloud architecture design
- CDN and caching strategies
- IAM and least-privilege security
- DNS and domain integration
- Troubleshooting AWS permission issues
