# Day 2 — AWS IAM, Security & Cost Management

## Project
AWS Serverless File Upload & Processing Platform

## Day 2 Objectives
- Understand AWS IAM and its importance.
- Learn about IAM users, groups, roles, and policies.
- Understand the principle of least privilege.
- Learn the structure of IAM JSON policies.
- Configure AWS cost monitoring.
- Prepare to create a Lambda execution role.

## 1. AWS IAM Fundamentals

IAM stands for Identity and Access Management.

IAM helps control which identities can access AWS resources and what actions they can perform.

### IAM User
An identity within an AWS account that can have credentials and permissions.

### IAM Group
A collection of IAM users managed together through shared permissions.

### IAM Role
An identity that trusted services or principals can assume to obtain temporary permissions.

### IAM Policy
A JSON document defining allowed or denied actions on AWS resources.

## 2. Principle of Least Privilege

Only grant the permissions necessary to perform a task.

For example, our file-processing Lambda may need to read objects from a specific S3 bucket, but it should not have permission to delete every S3 bucket.

## 3. IAM Policy Example

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::example-bucket/*"
    }
  ]
}
```

This example allows reading objects from the specified bucket. It does not grant permission to upload or delete them.

## 4. AWS Services Studied

| Service | Purpose |
|---|---|
| AWS IAM | Manage access and permissions |
| AWS Lambda | Run backend functions |
| Amazon S3 | Store uploaded files |
| Amazon CloudWatch | Monitor execution logs |
| AWS Budgets | Monitor AWS spending |

## 5. Practical Work

### AWS Budget

Successfully created an AWS Budget.

- Budget name: `serverless-learning-budget`
- Monthly threshold: $1 USD
- Displayed spending at verification: $0.00
- Threshold status: OK
- Health status: Healthy

Important: AWS Budgets alerts do not prevent spending beyond the configured threshold.

### AWS Free Tier

Learned that AWS Free Tier eligibility depends on the account and services used.

Account eligibility and available credits still need verification.

### Lambda IAM Role

Planned role name:

`serverless-file-processor-role`

Planned managed policy:

`AWSLambdaBasicExecutionRole`

This policy allows basic CloudWatch logging. Specific S3 and DynamoDB permissions will be configured later.

## 6. Practical Task Checklist

- [x] Study IAM fundamentals.
- [x] Study users, groups, roles, and policies.
- [x] Understand the least-privilege principle.
- [x] Study an IAM JSON policy.
- [x] Create an AWS Budget.
- [ ] Verify budget email notifications.
- [ ] Verify MFA configuration.
- [ ] Verify AWS Free Tier eligibility and credits.
- [ ] Select the project Region `ap-south-1`.
- [ ] Create the Lambda execution role.
- [ ] Verify role permissions and trust policy.

## 7. Day 2 Interview Questions

1. What is AWS IAM?
2. What is the difference between an IAM user and a role?
3. What is an IAM policy?
4. What is the principle of least privilege?
5. Why does AWS Lambda need an execution role?
6. What is an ARN?
7. Does an AWS Budget prevent charges?

## 8. Next Steps

Complete the remaining Day 2 security tasks before deploying resources.

## Day 3 Preview — Amazon S3

- Understand S3 buckets and objects.
- Learn about S3 storage classes.
- Create a private S3 bucket.
- Configure Block Public Access.
- Upload and download test files.
- Understand S3 pricing and permissions.
- Verify the results.
- Push Day 3 notes and implementation to GitHub.

## Day 2 Status

Study notes and AWS Budget creation completed. Security verification and IAM role creation remain pending.
