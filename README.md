```
# AWS Infrastructure Automation with CloudFormation & GitHub Actions (OIDC)

[![Deploy Ubuntu Nginx with CloudFormation](https://github.com/minobel/IAC-cloudformation-github-actions/actions/workflows/deploy.yml/badge.svg)](https://github.com/minobel/IAC-cloudformation-github-actions/actions)
[![AWS CloudFormation](https://img.shields.io/badge/AWS-CloudFormation-orange?logo=amazon-aws)](https://aws.amazon.com/cloudformation/)
[![GitHub Actions](https://img.shields.io/badge/CI%2FCD-GitHub%26nbsp%3BActions-2088FF?logo=github-actions&logoColor=white)](https://github.com/features/actions)

---

## 📌 Project Overview
Automated AWS Infrastructure deployment using **CloudFormation (IaC)** and **GitHub Actions (CI/CD)** with **Passwordless OIDC Authentication**.

* **IaC Engine:** AWS CloudFormation
* **CI/CD Pipeline:** GitHub Actions
* **Security:** AWS OIDC (No hardcoded credentials)
* **Compute:** Ubuntu 24.04 LTS + Nginx Web Server
* **Network:** Custom VPC, Public Subnet, Internet Gateway & Security Group[cite: 2]

---

## 📂 Repository Structure

```text
├── .github/
│   └── workflows/
│       └── deploy.yml          # CI/CD Pipeline Configuration
├── screenshots/
│   ├── actions-success.png     # Screenshot 1: Actions Pipeline
│   ├── cloudformation-stack.png# Screenshot 2: Stack Status
│   ├── ec2-instance-tags.png   # Screenshot 3: EC2 Instance & Tags
│   ├── website-preview.png     # Screenshot 4: Live Website
│   ├── second-push-tag.png     # Screenshot 5: Updated EC2 Tag
│   └── cleanup-stack.png       # Screenshot 6: Cleanup Confirmation
├── cloudformation.yaml         # AWS CloudFormation IaC Template
└── README.md                   # Project Documentation

```

## 🚀 Step-by-Step Implementation & Execution Proofs

### Step 1: AWS OIDC & GitHub IAM Role Setup

-   **Key Concept:** Passwordless Authentication.
    
    image_5922dd.png
    
-   **Action:** Configured GitHub as an Identity Provider in AWS IAM using OIDC and created an IAM Role (`github-iac-deploy-role`) with least-privilege permissions.
    
    image_5922dd.png
    

### Step 2: Trigger CI/CD Pipeline Deployment

-   **Key Concept:** Continuous Deployment.
    
    image_5922dd.png
    
-   **Action:** Pushed initial code to the GitHub repository.
    
    image_5922dd.png
    
-   **Repo Link:** [https://github.com/minobel/IAC-cloudformation-github-actions](https://github.com/minobel/IAC-cloudformation-github-actions)
    
    image_5922dd.png
    
-   📸 **Proof (Screenshot 1):**  [📁 View GitHub Actions Success Screenshot](https://www.google.com/search?q=./screenshots/actions-success.png)
    
    _(Shows successful workflow execution with green checkmarks)._
    

### Step 3: Verify CloudFormation Stack Creation

-   **Key Concept:** Infrastructure as Code (IaC) Provisioning.
    
    image_5922dd.png
    
-   **Action:** Verified stack provisioning inside AWS CloudFormation Console.
    
    image_5922dd.png
    
-   📸 **Proof (Screenshot 2):**  [📁 View CloudFormation Stack Status Screenshot](https://www.google.com/search?q=./screenshots/cloudformation-stack.png)
    
    _(Shows `bongodev-github-iac-dev` stack in `CREATE_COMPLETE` or `UPDATE_COMPLETE` status)._
    
    image_5922dd.png
    

### Step 4: Verify EC2 Instance & Custom Metadata Tags

-   **Key Concept:** Automated Resource Configuration.
    
    image_5922dd.png
    
-   **Action:** Inspected launched Ubuntu EC2 instance in AWS Console.
    
    image_5922dd.png
    
-   📸 **Proof (Screenshot 3):**  [📁 View EC2 Instance & Tags Screenshot](https://www.google.com/search?q=./screenshots/ec2-instance-tags.png)
    
    _(Shows running `t3.micro` instance with `Name`, `Environment`, and `Course` tags)._
    
    image_5922dd.png+ 1
    

### Step 5: Verify Live Web Server Application

-   **Key Concept:** UserData Bootstrapping & Nginx Deployment[cite: 2].
    
-   **Action:** Accessed the public IP address in the browser.
    
    image_5922dd.png
    
-   📸 **Proof (Screenshot 4):**  [📁 View Nginx Website Screenshot](https://www.google.com/search?q=./screenshots/website-preview.png)
    
    _(Displays live web page reading `Hello from bongoDev!` and `Environment: dev`)._
    
    image_5922dd.png+ 1
    

### Step 6: Test Infrastructure Update & Idempotency (Second Push)

-   **Key Concept:** State Management & In-Place Update.
    
    image_5922dd.png
    
-   **Action:** Updated `Course` tag in `cloudformation.yaml` and pushed changes to GitHub.
    
    image_5922dd.png
    
-   🔗 **Commit Link:** [View Tag Modification Commit](https://github.com/minobel/IAC-cloudformation-github-actions/commit/c99f60f58e519c8384d011a4b64b71b811a4505b)
    
    image_5922dd.png
    
-   📸 **Proof (Screenshot 5):**  [📁 View Stack Update / New EC2 Tag Screenshot](https://www.google.com/search?q=./screenshots/second-push-tag.png)
    
    _(Shows CloudFormation update event and modified EC2 tag)._
    
    image_5922dd.png
    

### Step 7: Teardown & Resource Cleanup

-   **Key Concept:** Cost Optimization & Resource Deletion.
    
    image_5922dd.png
    
-   **Action:** Deleted CloudFormation stack from AWS Console post-testing to avoid charges.
    
    image_5922dd.png
    
-   📸 **Proof (Screenshot 6):**  [📁 View Stack Cleanup Confirmation Screenshot](https://www.google.com/search?q=./screenshots/cleanup-stack.png)
    
    _(Shows stack deletion confirmation)._[cite: 1]
    

## 🔑 Core Concepts Summary

-   **What GitHub Actions does:** Functions as the CI/CD automation pipeline that checks out code and uses OIDC to securely deploy infrastructure to AWS on every commit[cite: 1].
    
-   **What CloudFormation does:** Functions as the IaC engine that reads the YAML template and automatically creates, updates, or destroys AWS resources (VPC, Subnet, SG, EC2).
    
    image_5922dd.png+ 1
    

> 🔒 **Security Notice:** No credentials, access keys, SSH keys, or unsafe wildcards are committed in this repository[cite: 1]. Authentication is handled entirely via short-lived OIDC tokens[cite: 1].


