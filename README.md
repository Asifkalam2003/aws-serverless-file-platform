# AWS Serverless File Upload & Processing Platform

## Project Overview

A serverless web application that allows users to
upload files to Amazon S3 and automatically process
them using AWS Lambda.

## Technologies

- HTML
- CSS
- JavaScript
- Python
- Amazon S3
- AWS Lambda
- Amazon API Gateway
- Amazon DynamoDB
- AWS IAM
- Amazon CloudWatch

## Planned Features

1. Upload files through a web interface.
2. Generate secure S3 presigned URLs.
3. Store files in Amazon S3.
4. Automatically process uploaded files.
5. Store file metadata in DynamoDB.
6. Display file-processing status.
7. Monitor errors using CloudWatch.

## Architecture

Frontend → API Gateway → Lambda → S3

S3 Event → Processing Lambda → DynamoDB

## Project Status

Day 1: Project planning and environment setup.