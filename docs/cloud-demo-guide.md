# Cloud Demo Guide

## Demo goal

Show that the project is not only an AI prompt project. It is a cloud computing project using AWS services.

## Demo order

### 1. Open the GitHub repository

Show the folders:

* `web`
* `backend`
* `docs`
* `infrastructure`
* `ai-productivity-app`
* `ai-data-analysis`

Explain that the project started with AWS PartyRock and was upgraded to a serverless AWS architecture.

### 2. Show the architecture

Open `docs/architecture.md` and explain:

```text
S3 frontend
API Gateway
Lambda
DynamoDB
CloudWatch
PartyRock AI prototype
```

### 3. Show the S3 website files

Open `web/index.html` and explain that this is the frontend that can be uploaded to an S3 bucket for static website hosting.

### 4. Show Lambda

Open `backend/lambda_function.py` and explain that Lambda processes the learner support request.

### 5. Show DynamoDB

In the AWS Console show the DynamoDB table if created.

Suggested table name:

```text
educare-support-requests
```

### 6. Show API Gateway

Show the API Gateway endpoint connected to the Lambda function.

### 7. Show CloudWatch

Open CloudWatch logs for the Lambda function and show that requests were logged.

### 8. Show AWS PartyRock

Open the PartyRock app and show how it supports learners with study plans and intervention ideas.

## Demo script

My project is AWS EduCare Cloud Support Platform. It started as an AWS PartyRock AI education support prototype. I upgraded it into a cloud architecture to show how the idea can run on AWS.

The frontend can be hosted on Amazon S3. The frontend sends a support request to API Gateway. API Gateway triggers AWS Lambda. Lambda creates a recommendation and stores the request in DynamoDB. CloudWatch records logs so that I can monitor whether the backend ran successfully. AWS PartyRock remains the AI prototype layer for learner support.

This project demonstrates static hosting, serverless compute, API integration, cloud database storage, monitoring and cloud based AI.
