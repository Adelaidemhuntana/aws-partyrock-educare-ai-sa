# Cloud Architecture

## Project name

AWS EduCare Cloud Support Platform

## Purpose

The platform demonstrates how an education support idea can be upgraded into a cloud based system using AWS managed services.

The original prototype used AWS PartyRock for generative AI learner support. The upgraded architecture adds static hosting, an API layer, serverless compute, cloud storage and monitoring.

## Architecture flow

```text
Parent or Learner Browser
        ↓
Amazon S3 Static Website
        ↓
Amazon API Gateway
        ↓
AWS Lambda
        ↓
Amazon DynamoDB
        ↓
Amazon CloudWatch Logs
```

AWS PartyRock remains the AI prototype layer for generating study support, learner intervention ideas and educational guidance.

## AWS services used

### Amazon S3

Used to host the static frontend files from the `web` folder.

### Amazon API Gateway

Used to expose an HTTPS endpoint that the frontend can call.

### AWS Lambda

Used as the serverless backend. It receives learner support requests and creates a recommendation.

### Amazon DynamoDB

Used as the cloud database for learner support requests.

### Amazon CloudWatch

Used to monitor Lambda logs and confirm that the backend executed successfully.

### AWS PartyRock

Used as the cloud based AI prototype layer for educational support.

## Why serverless

Serverless is a good fit for this project because:

* there is no server to manage
* Lambda only runs when a request is made
* DynamoDB is managed by AWS
* CloudWatch gives automatic logs
* the project can start small and scale later

## Production improvements

A production version can add:

* Amazon Cognito for login
* CloudFront in front of S3
* Amazon Bedrock instead of manual PartyRock use
* stricter IAM permissions
* CI CD deployment with GitHub Actions
* dashboards for learner intervention trends
