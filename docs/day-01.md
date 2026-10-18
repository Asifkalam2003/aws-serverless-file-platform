# Day 1 — AWS Fundamentals and Project Setup

**Project:** AWS Serverless File Upload & Processing Platform
**Learning Level:** Beginner to Advanced
**Estimated Study Time:** 1–2 Hours
**Status:** Completed — Local Project Setup

---

## 1. Day 1 Learning Objectives

The main goal of Day 1 was to understand the fundamentals of AWS cloud computing and prepare the local development environment.

### Learning Goals

- Understand what a server is.
- Understand cloud computing.
- Learn the difference between traditional and serverless architecture.
- Understand the purpose of AWS.
- Identify the AWS services required for our project.
- Understand how file uploads will work.
- Create the initial project directory and files.
- Learn basic terminal commands.
- Prepare the project for GitHub version control.

## 2. What Is a Server?

A server is a computer or software system that provides resources or services to other computers over a network.

For example, when a user opens a website, their browser sends an HTTP request to a server. The server processes the request and returns a response.

### Request and Response Flow

```text
User
 |
 v
Web Browser
 |
 | HTTP Request
 v
Web Server
 |
 | HTTP Response
 v
Web Browser
```

### Why Do Applications Need Servers?

Servers can perform several tasks:

1. Execute backend application code.
2. Handle HTTP requests.
3. Authenticate users.
4. Communicate with databases.
5. Store or retrieve application data.
6. Process uploaded files.

In traditional hosting, developers may need to maintain server infrastructure, including operating systems, security updates, and scaling.

## 3. What Is Cloud Computing?

Cloud computing is the delivery of computing resources such as servers, storage, databases, and networking over the internet.

Instead of purchasing and maintaining physical servers, developers can use services provided by cloud platforms.

### Popular Cloud Providers

- Amazon Web Services (AWS)
- Microsoft Azure
- Google Cloud Platform (GCP)

### Advantages of Cloud Computing

- On-demand resource provisioning.
- Flexible scaling.
- Managed infrastructure.
- Global service availability.
- Usage-based pricing.
- Built-in monitoring and security tools.

Cloud services are not necessarily free. Costs depend on resource usage and pricing.

## 4. What Is AWS?

AWS stands for Amazon Web Services.

AWS is a cloud computing platform that provides services for application hosting, computing, storage, databases, networking, security, and monitoring.

### AWS Services Selected for Our Project

| Service            | Purpose                 |
| ------------------ | ----------------------- |
| Amazon S3          | Store uploaded files    |
| AWS Lambda         | Execute backend code    |
| Amazon API Gateway | Expose HTTP endpoints   |
| Amazon DynamoDB    | Store file metadata     |
| AWS IAM            | Manage permissions      |
| Amazon CloudWatch  | Monitor logs and errors |
| AWS Budgets        | Monitor cloud spending  |

## 5. What Is Serverless Computing?

Serverless computing allows developers to execute application logic without directly managing the underlying servers.

Servers still exist, but the cloud provider handles much of the infrastructure management.

### Traditional Architecture

```text
User
 |
 v
Frontend
 |
 v
Backend Server
 |
 v
Database
```

### Serverless Architecture

```text
User
 |
 v
Frontend
 |
 v
API Gateway
 |
 v
AWS Lambda
 |
 v
DynamoDB
```

### Why We Chose Serverless

- No need to manage a continuously running backend server.
- AWS Lambda can execute in response to events.
- Managed services simplify infrastructure management.
- Scaling is handled by AWS within service limits.
- Suitable for learning event-driven cloud architecture.

## 6. Project Overview

Our project is a web application that will allow users to upload files to Amazon S3 and automatically process them using AWS Lambda.

### Planned Features

1. Upload images and PDF files.
2. Generate secure S3 presigned URLs.
3. Store files in a private S3 bucket.
4. Automatically trigger Lambda after uploads.
5. Process supported file types.
6. Store file metadata in DynamoDB.
7. Display file-processing status.
8. Monitor application errors.

These features are planned and have not yet been implemented.

## 7. Project Architecture

```text
                  USER
                   |
                   v
            WEB APPLICATION
             HTML/CSS/JS
                   |
                   v
             API GATEWAY
                   |
                   v
             UPLOAD LAMBDA
                   |
                   v
         GENERATE PRESIGNED URL
                   |
                   v
              FRONTEND
                   |
                   v
              AMAZON S3
                   |
                   v
          S3 EVENT NOTIFICATION
                   |
                   v
           PROCESSING LAMBDA
                   |
                   v
              DYNAMODB
                   |
                   v
              STATUS API
                   |
                   v
          FRONTEND DASHBOARD
```

### Architecture Explanation

**Step 1:** The user selects a file in the frontend.

**Step 2:** JavaScript requests an upload URL from API Gateway.

**Step 3:** API Gateway invokes the upload Lambda function.

**Step 4:** Lambda generates a temporary presigned S3 URL.

**Step 5:** The frontend uploads the file directly to Amazon S3.

**Step 6:** S3 sends an event notification when the object is created.

**Step 7:** The file-processing Lambda executes automatically.

**Step 8:** Lambda processes the file and updates its metadata in DynamoDB.

**Step 9:** The frontend retrieves processing status through a separate API endpoint.

## 8. Why We Are Using Each Technology

### HTML

HTML defines the structure of our web application.

We will use it to create the upload form, file list, and dashboard.

### CSS

CSS controls the appearance of the frontend.

We will use it for responsive layouts, colors, buttons, and file upload components.

### JavaScript

JavaScript handles browser-side functionality.

It will manage file selection, HTTP requests, uploads, and processing-status updates.

### Python

Python will be used to implement our Lambda functions.

### Amazon S3

S3 stores uploaded files as objects inside buckets.

We selected S3 because it is designed for durable object storage.

### AWS Lambda

Lambda executes backend functions when invoked by API Gateway or AWS events.

### API Gateway

API Gateway exposes HTTP endpoints that our frontend can call.

### DynamoDB

DynamoDB stores structured metadata such as file names, identifiers, and processing status.

### AWS IAM

IAM manages which identities and AWS services can access resources.

### Amazon CloudWatch

CloudWatch helps us inspect application logs and troubleshoot failures.

## 9. Development Environment

### Tools

- macOS
- Visual Studio Code
- Terminal
- Git
- GitHub
- AWS Management Console

### Project Directory

```text
~/Desktop/aws-serverless-file-platform
```

## 10. Practical Implementation

### Step 1 — Create the Project Folder

```bash
mkdir -p ~/Desktop/aws-serverless-file-platform
```

**Explanation:**

- `mkdir` creates a directory.
- `-p` creates missing parent directories and avoids errors if the directory already exists.
- `~/Desktop/` points to the Desktop directory.
- `aws-serverless-file-platform` is the project folder name.

### Step 2 — Navigate to the Folder

```bash
cd ~/Desktop/aws-serverless-file-platform
```

The `cd` command changes the current working directory.

### Step 3 — Create Project Directories

```bash
mkdir -p frontend backend/upload_api backend/file_processor infrastructure tests
```

This creates the frontend, backend, infrastructure, and testing directories.

### Step 4 — Create Frontend Files

```bash
touch frontend/index.html
touch frontend/style.css
touch frontend/script.js
```

These files will contain the frontend implementation.

### Step 5 — Create Backend Files

```bash
touch backend/upload_api/lambda_function.py
touch backend/file_processor/lambda_function.py
```

The upload API function will generate presigned URLs.

The file processor will handle uploaded files after receiving S3 events.

### Step 6 — Create Documentation Files

```bash
touch README.md
touch .gitignore
```

`README.md` documents the project.

`.gitignore` tells Git which files should not be tracked.

## 11. Project Folder Structure

```text
aws-serverless-file-platform/
|
|-- frontend/
|   |-- index.html
|   |-- style.css
|   |-- script.js
|
|-- backend/
|   |-- upload_api/
|   |   |-- lambda_function.py
|   |
|   |-- file_processor/
|       |-- lambda_function.py
|
|-- infrastructure/
|-- tests/
|
|-- README.md
|-- .gitignore
```

## 12. Testing and Verification

### Verify Current Directory

```bash
pwd
```

Actual output:

```text
/Users/asifkalam/Desktop/aws-serverless-file-platform
```

### Verify Project Files

```bash
ls -la
```

The terminal output confirmed the following:

- `frontend/`
- `backend/`
- `infrastructure/`
- `tests/`
- `README.md`
- `.gitignore`

### Verify Frontend

```bash
ls frontend
```

Actual output:

```text
index.html
script.js
style.css
```

### Verify Upload API Directory

```bash
ls backend/upload_api
```

Actual output:

```text
lambda_function.py
```

### Verification Result

The main project structure and frontend/upload API files were verified successfully.

The file-processing function was created using the terminal commands, but its contents and execution have not yet been tested.

## 13. Git and GitHub Learning

Git is a version control system used to track changes to project files.

GitHub is a platform used to host Git repositories and collaborate on software projects.

### Important Git Commands

```bash
git init
git status
git add .
git commit -m "Day 1: AWS fundamentals and project setup"
git branch -M main
git push -u origin main
```

### Command Explanations

- `git init` — Initialize a local Git repository.
- `git status` — Display the working tree status.
- `git add .` — Stage changes for committing.
- `git commit` — Save a snapshot of staged changes.
- `git branch -M main` — Rename the current branch to main.
- `git push` — Upload local commits to a remote repository.

A GitHub remote must be configured and authentication must be available before pushing.

## 14. Day 1 Knowledge Check

1. What is a server?
2. What is cloud computing?
3. What does AWS stand for?
4. What is serverless computing?
5. What is the difference between a traditional server and AWS Lambda?
6. Why are we using Amazon S3?
7. Why do we need API Gateway?
8. What information will DynamoDB store?
9. What is the purpose of Git?
10. Why do we use a `.gitignore` file?

## 15. Day 1 Completion Checklist

- [x] Study cloud computing fundamentals.
- [x] Study serverless architecture.
- [x] Understand the planned AWS services.
- [x] Review the project architecture.
- [x] Create the main project directory.
- [x] Create frontend and backend directories.
- [x] Create infrastructure and tests directories.
- [x] Create initial source files.
- [x] Create README.md.
- [x] Create .gitignore.
- [x] Verify the local project structure.
- [x] Confirm Day 1 documentation is committed and pushed to GitHub.

## 16. Next Lesson — Day 2

AWS IAM, Security and Cost Management.

Topics:

- IAM users, groups, roles, and policies.
- Least-privilege permissions.
- IAM JSON policy structure.
- AWS account security.
- AWS Budget configuration.
- Lambda execution roles.

## Day 1 Summary

Successfully prepared the initial local development environment for the AWS Serverless File Upload & Processing Platform.

Learned the fundamentals of cloud computing, serverless architecture, and the purpose of the AWS services selected for this project.

**Day 1 Result:** Local project structure created and verified. Cloud resources and application functionality will be implemented in later lessons.
