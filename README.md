# AWS Static Website Hosting

## Overview
This project hosts a static website using AWS services including S3, CloudFront, and Route 53.

## Architecture
- Amazon S3 for static website hosting
- CloudFront for CDN
- Route 53 for DNS
- ACM for HTTPS

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
4. Configured CloudFront distribution
5. Set up HTTPS with ACM
6. Configured DNS with Route 53

## Live Demo
http://thaotppham-portfolio-website-2026.s3-website-us-east-1.amazonaws.com/

## Technologies Used
- HTML
- CSS
- AWS S3
- AWS CloudFront
- AWS Route 53

## What I Learned
- Buckets are private by default and require explicit public access
- Importance of least-privilege permissions (s3:GetObject only)
- Difference between local development and cloud deployment
- How CDN improves performance
- DNS configuration basics
- Securing websites with HTTPS
