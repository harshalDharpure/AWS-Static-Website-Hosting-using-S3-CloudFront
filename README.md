# AWS-Static-Website-Hosting-using-S3-CloudFront
AWS Static Website Hosting using S3 + CloudFront
# 🚀 AWS Static Website Hosting using S3 + CloudFront

## 🌍 Live Demo

https://d23uw2emxc165m.cloudfront.net

---

## 📌 Project Overview

This project demonstrates how to deploy a static website using AWS services. The website is hosted on Amazon S3 and delivered globally using Amazon CloudFront CDN for low latency and high availability.

---

## 🧱 Architecture

User → CloudFront (CDN) → S3 Bucket → Static Website Files

---

## 🛠️ Services Used

### 🪣 Amazon S3 (Simple Storage Service)

* Used to store static files (HTML, CSS)
* Enabled static website hosting
* Acts as origin server

### 🌐 Amazon CloudFront

* Content Delivery Network (CDN)
* Distributes content globally
* Caches content at edge locations

---

## ⚙️ Step-by-Step Implementation

### 🔹 Step 1: Create Static Website

* Create `index.html` and optional `style.css`
* Add basic HTML structure
* Ensure UTF-8 encoding:

```html
<meta charset="UTF-8">
```

---

### 🔹 Step 2: Create S3 Bucket

* Go to AWS S3 → Create bucket
* Bucket name must be globally unique
* Disable “Block all public access”

---

### 🔹 Step 3: Upload Files

* Upload `index.html` and other assets to bucket

---

### 🔹 Step 4: Enable Static Website Hosting

* Go to Properties → Static Website Hosting
* Enable it
* Set:

  * Index document: `index.html`

---

### 🔹 Step 5: Configure Bucket Policy (Public Access)

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicRead",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::harshal-static-site-123/*"
    }
  ]
}
```

---

### 🔹 Step 6: Create CloudFront Distribution

* Go to CloudFront → Create Distribution
* Origin domain: S3 website endpoint
* Viewer protocol: Redirect HTTP to HTTPS

---

### 🔹 Step 7: Set Default Root Object

* Go to Distribution Settings
* Set:

```
index.html
```

---

### 🔹 Step 8: Invalidate Cache

* Go to Invalidations
* Add:

```
/*
```

---

## ❗ Issues Faced & Fixes

### 🔴 1. 504 Gateway Timeout

Cause:

* Wrong origin endpoint

Fix:

* Use correct S3 website endpoint

---

### 🔴 2. AccessDenied Error

Cause:

* Incorrect bucket policy or mixed configuration

Fix:

* Use public bucket policy
* Ensure block public access is disabled

---

### 🔴 3. Emoji Encoding Issue

Cause:

* Missing UTF-8 encoding

Fix:

```html
<meta charset="UTF-8">
```

---

## 🧠 Key Learnings

* Difference between S3 bucket endpoint and website endpoint
* How CDN caching works
* Importance of permissions in AWS
* Debugging real-world cloud issues

---

## 🚀 Outcome

* Successfully hosted a live website
* Achieved global content delivery using CDN
* Learned real AWS architecture and troubleshooting

---

## 🔮 Future Improvements

* Add custom domain using Route 53
* Enable HTTPS with SSL (ACM)
* CI/CD integration with GitHub Actions
* Move to private bucket using OAC

---

## 👨‍💻 Author

Harshal Dharpure
