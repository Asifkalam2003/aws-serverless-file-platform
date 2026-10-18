# AWS Serverless File Upload & Processing Platform

A cloud-based serverless application that allows users to securely upload files to Amazon S3 and automatically process them using AWS Lambda.

This project is being developed as part of a **20-day hands-on AWS learning journey**, covering cloud computing, serverless architecture, backend development, security, deployment, and monitoring.

## Project Overview

The application will allow users to upload images and documents through a web interface. Files will be stored in Amazon S3, automatically processed by AWS Lambda, and tracked using Amazon DynamoDB.

### Project Objectives

- Learn AWS services through practical implementation.
- Understand serverless application architecture.
- Develop frontend and backend components.
- Implement secure file uploads.
- Automate file processing using event-driven architecture.
- Monitor and troubleshoot cloud applications.
- Deploy a working project to AWS.
- Document progress and publish source code on GitHub.

## Technologies Used

| Technology         | Purpose                             |
| ------------------ | ----------------------------------- |
| HTML               | Frontend page structure             |
| CSS                | User interface design               |
| JavaScript         | File upload and API integration     |
| Python             | AWS Lambda backend functions        |
| Amazon S3          | File storage                        |
| AWS Lambda         | Serverless file processing          |
| Amazon API Gateway | HTTP API endpoints                  |
| Amazon DynamoDB    | File metadata and processing status |
| AWS IAM            | Access control and permissions      |
| Amazon CloudWatch  | Application logs and monitoring     |
| AWS Budgets        | Cost monitoring                     |
| Git and GitHub     | Version control and documentation   |

## Planned Features

1. Upload files through a web interface.
2. Generate secure S3 presigned upload URLs.
3. Store files in a private Amazon S3 bucket.
4. Automatically trigger AWS Lambda when a file is uploaded.
5. Process supported files.
6. Store file metadata and processing status in DynamoDB.
7. Display uploaded files and their processing status.
8. Monitor errors using CloudWatch.
9. Implement secure IAM permissions.
10. Deploy the application to AWS.

## System Architecture

```text
User
 |
 v
Frontend (HTML, CSS, JavaScript)
 |
 v
Amazon API Gateway
 |
 v
Upload API Lambda
 |
 v
Generate S3 Presigned URL
 |
 v
Frontend uploads file directly to S3
 |
 v
Amazon S3
 |
 v
S3 Event Notification
 |
 v
File Processor Lambda
 |
 v
Amazon DynamoDB
 |
 v
Status API
 |
 v
Frontend Dashboard
```

The status API will retrieve processing information from DynamoDB so the frontend can display file-processing results.

## Project Folder Structure

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
|-- docs/
|   |-- day-01.md
|   |-- day-02.md
|
|-- README.md
|-- .gitignore
```

## Development Progress

| Day        | Topic                                 | Status    |
| ---------- | ------------------------------------- | --------- |
| Day 1      | AWS Fundamentals and Project Setup    | Completed |
| Day 2      | AWS IAM, Security and Cost Management | Completed |
| Day 3      | Amazon S3 Fundamentals                | Planned   |
| Day 4      | S3 Permissions and File Uploads       | Planned   |
| Day 5      | AWS Lambda Fundamentals               | Planned   |
| Days 6–10  | Backend and Database Development      | Planned   |
| Days 11–15 | Frontend and API Integration          | Planned   |
| Days 16–20 | Testing, Deployment and Documentation | Planned   |

## Day 1 — AWS Fundamentals and Project Setup

### Concepts Studied

- Introduction to cloud computing.
- Traditional servers versus serverless computing.
- AWS global infrastructure basics.
- Overview of AWS services used in this project.
- Understanding the serverless file upload architecture.

### Practical Work Completed

- Created the project directory.
- Created frontend and backend directories.
- Created infrastructure and tests directories.
- Created initial HTML, CSS, JavaScript and Python files.
- Created README.md and .gitignore.
- Verified the project structure using terminal commands.

## Day 2 — AWS IAM, Security and Cost Management

### Concepts Studied

- AWS Identity and Access Management (IAM).
- IAM users, groups, roles and policies.
- Principle of least privilege.
- IAM policy JSON structure.
- AWS Lambda execution roles.
- AWS Free Tier and usage-based pricing.
- AWS Budgets and cost monitoring.

### Practical Work Completed

**AWS Budget Configuration**

- Budget name: `serverless-learning-budget`
- Monthly budget threshold: $1 USD
- Budget creation: Successful
- Threshold status at verification: OK
- Health status at verification: Healthy
- Displayed spending at verification: $0.00

The AWS Budget is used for cost monitoring. It does not automatically prevent charges beyond the configured amount.

### Remaining Day 2 Tasks

- [x] Verify MFA configuration.
- [x] Verify AWS Free Tier eligibility and available credits.
- [x] Verify AWS Budget email notifications.
- [x] Select AWS Region `ap-south-1`.
- [x] Create the Lambda execution role.
- [x] Attach the `AWSLambdaBasicExecutionRole` policy.
- [x] Verify the role's trust relationship.

### Planned Lambda Execution Role

Role name:

`serverless-file-processor-role`

Initial managed policy:

`AWSLambdaBasicExecutionRole`

Additional permissions for S3 and DynamoDB will be configured when those resources are created.

## Day 3 — Amazon S3 (Upcoming)

### Learning Objectives

- Understand Amazon S3.
- Learn about S3 buckets and objects.
- Understand S3 storage classes.
- Learn S3 permissions and security.
- Understand S3 pricing and Free Tier allowances.

### Planned Practical Tasks

1. Open the Amazon S3 console.
2. Create a private S3 bucket.
3. Configure Block Public Access.
4. Upload a test file.
5. Download and verify the file.
6. Review bucket permissions.
7. Document the results.
8. Push Day 3 progress to GitHub.

## Security Practices

- Never commit AWS credentials or secrets to GitHub.
- Use least-privilege IAM permissions.
- Keep uploaded files private by default.
- Use presigned URLs for controlled file uploads.
- Enable appropriate monitoring.
- Track cloud spending with AWS Budgets.

## Learning Approach

Each development day includes:

1. Theory and AWS concepts.
2. Architecture explanation.
3. Practical implementation.
4. Code explanation.
5. Testing and verification.
6. Documentation.
7. GitHub commit.

## Project Status

**Current milestone:** Day 2 — AWS IAM and Security.

**Completed:** Local project setup, introductory AWS study, and AWS Budget creation.

**Next:** Complete the remaining Day 2 security tasks and begin Amazon S3 implementation.

The application is currently under development and has not yet been deployed.
