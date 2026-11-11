```
# AWS Infrastructure Automation with CloudFormation & GitHub Actions (OIDC)

[![Deploy Ubuntu Nginx with CloudFormation](https://github.com/minobel/IAC-cloudformation-github-actions/actions/workflows/deploy.yml/badge.svg)](https://github.com/minobel/IAC-cloudformation-github-actions/actions) [![AWS CloudFormation](https://img.shields.io/badge/AWS-CloudFormation-orange?logo=amazon-aws)](https://aws.amazon.com/cloudformation/) [![GitHub Actions](https://img.shields.io/badge/CI%2FCD-GitHub%20Actions-2088FF?logo=github-actions&logoColor=white)](https://github.com/features/actions)

---

## 📌 Project Overview
Automated AWS Infrastructure deployment using **CloudFormation (IaC)** and **GitHub Actions (CI/CD)** with **Passwordless OIDC Authentication**.

- **IaC Engine:** AWS CloudFormation
- **CI/CD Pipeline:** GitHub Actions
- **Security:** AWS OIDC (No hardcoded credentials)
- **Compute:** Ubuntu 24.04 LTS + Nginx Web Server
- **Network:** Custom VPC, Public Subnet, Internet Gateway & Security Group

---

## 📂 Repository Structure

```text
.
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
    
-   **Action:** Configured GitHub as an Identity Provider in AWS IAM using OIDC and created an IAM Role (`github-iac-deploy-role`) with least-privilege permissions.
    

### Step 2: Trigger CI/CD Pipeline Deployment

-   **Key Concept:** Continuous Deployment.
    
-   **Action:** Pushed initial code to the GitHub repository.
    
-   **Repo Link:** [https://github.com/minobel/IAC-cloudformation-github-actions](https://github.com/minobel/IAC-cloudformation-github-actions)
    
-   📸 **Proof (Screenshot 1):**  [📁 View GitHub Actions Success Screenshot](https://github.com/minobel/IAC-cloudformation-github-actions/blob/main/screenshots/actions-success.png)
    
    _(Shows successful workflow execution with green checkmarks)._
    

### Step 3: Verify CloudFormation Stack Creation

-   **Key Concept:** Infrastructure as Code (IaC) Provisioning.
    
-   **Action:** Verified stack provisioning inside AWS CloudFormation Console.
    
-   📸 **Proof (Screenshot 2):**  [📁 View CloudFormation Stack Status Screenshot](https://github.com/minobel/IAC-cloudformation-github-actions/blob/main/screenshots/cloudformation-stack.png)
    
    _(Shows `bongodev-github-iac-dev` stack in `UPDATE_COMPLETE` status)._
    

### Step 4: Verify EC2 Instance & Custom Metadata Tags

-   **Key Concept:** Automated Resource Configuration.
    
-   **Action:** Inspected launched Ubuntu EC2 instance in AWS Console.
    
-   📸 **Proof (Screenshot 3):**  [📁 View EC2 Instance & Tags Screenshot](https://github.com/minobel/IAC-cloudformation-github-actions/blob/main/screenshots/ec2-instance-tags.png)
    
    (Shows running `t3.micro` instance with `Name`, `Environment`, and `Course` tags).
    

### Step 5: Verify Live Web Server Application

-   **Key Concept:** UserData Bootstrapping & Nginx Deployment[cite: 2].
    
-   **Action:** Accessed the public IP address in the browser.
    
-   📸 **Proof (Screenshot 4):**  [📁 View Nginx Website Screenshot](https://github.com/minobel/IAC-cloudformation-github-actions/blob/main/screenshots/website-preview.png)
    
    _(Displays live web page reading `Hello from bongoDev!` and `Environment: dev`)._
    

### Step 6: Test Infrastructure Update & Idempotency (Second Push)

-   **Key Concept:** State Management & In-Place Update.
    
-   **Action:** Updated `Course` tag in `cloudformation.yaml` and pushed changes to GitHub.
    
-   🔗 **Commit Link:** [View Tag Modification Commit](https://github.com/minobel/IAC-cloudformation-github-actions/commit/c99f60f58e519c8384d011a4b64b71b811a4505b)
    
-   📸 **Proof (Screenshot 5):**  [📁 View Stack Update / New EC2 Tag Screenshot](https://github.com/minobel/IAC-cloudformation-github-actions/blob/main/screenshots/second-push-tag.png)
    
    (Shows CloudFormation update event and modified EC2 tag).
    

### Step 7: Teardown & Resource Cleanup

-   **Key Concept:** Cost Optimization & Resource Deletion.
    
-   **Action:** Deleted CloudFormation stack from AWS Console post-testing to avoid charges.
    
-   📸 **Proof (Screenshot 6):**  [📁 View Stack Cleanup Confirmation Screenshot](https://github.com/minobel/IAC-cloudformation-github-actions/blob/main/screenshots/cleanup-stack.png)
    
    (Shows stack deletion confirmation).
    

## 🔑 Core Concepts Summary

-   **What GitHub Actions does:** Functions as the CI/CD automation pipeline that checks out code and uses OIDC to securely deploy infrastructure to AWS on every commit.
    
-   **What CloudFormation does:** Functions as the IaC engine that reads the YAML template and automatically creates, updates, or destroys AWS resources (VPC, Subnet, SG, EC2).
    

> 🔒 **Security Notice:** No credentials, access keys, SSH keys, or unsafe wildcards are committed in this repository. Authentication is handled entirely via short-lived OIDC tokens.


