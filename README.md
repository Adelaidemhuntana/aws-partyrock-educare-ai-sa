# AWS EduCare Cloud Support Platform

## Project purpose

This repository is my **Cloud Computing solo project** for WeThinkCode_ elective proof of work.

The project started as an AWS PartyRock educational AI prototype. I upgraded the concept into a cloud architecture that shows how an education support platform can run on AWS using serverless services.

The goal is to support learners, parents and education support teams with AI guidance, learner support requests, intervention recommendations and cloud hosted reporting.

---

## Why this is a cloud project

This project demonstrates cloud computing concepts beyond only AI.

It uses and documents the following AWS cloud services:

| Cloud area | AWS service | Purpose |
|---|---|---|
| Static hosting | Amazon S3 | Hosts the frontend demo site |
| Serverless compute | AWS Lambda | Processes learner support requests |
| API layer | Amazon API Gateway | Exposes an HTTPS endpoint for the frontend |
| Cloud database | Amazon DynamoDB | Stores learner support requests |
| Monitoring | Amazon CloudWatch | Stores Lambda logs and execution events |
| Generative AI prototype | AWS PartyRock | Provides the AI learning support prototype |
| Infrastructure planning | CloudFormation template | Documents how the cloud stack can be recreated |

This makes the project suitable for a Cloud Computing elective because it covers hosting, serverless computing, APIs, managed databases, monitoring, IAM and cloud architecture.

---

## System architecture

```text
Learner or Parent Browser
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

AWS PartyRock
        ↓
AI study support and intervention prototype
```

---

## Project features

### 1. Cloud hosted frontend

A small web interface can be hosted on Amazon S3. It allows a parent or learner to submit a support request.

### 2. Serverless backend

AWS Lambda receives the request from API Gateway and returns a support recommendation.

### 3. Cloud database

DynamoDB stores learner support requests with the learner name, grade, challenge and suggested intervention.

### 4. Monitoring

CloudWatch logs show when the Lambda function runs and whether requests are successful.

### 5. AI layer with AWS PartyRock

AWS PartyRock is used as the generative AI prototype layer for learner study support, CAPS aligned guidance and educational intervention ideas.

---

## Repository structure

```text
aws-partyrock-educare-ai-sa
│
├── ai-productivity-app
│   ├── project-description.md
│   ├── partyrock-link.txt
│   ├── screenshots
│   └── exports
│
├── ai-data-analysis
│   ├── foundational-learning-dataset.csv
│   ├── findings.md
│   ├── screenshots
│   └── analysis-exports
│
├── backend
│   └── lambda_function.py
│
├── docs
│   ├── architecture.md
│   └── cloud-demo-guide.md
│
├── infrastructure
│   └── cloudformation-template.yaml
│
├── web
│   └── index.html
│
└── README.md
```

---

## Demo plan

In the demo video I show:

1. The GitHub repository and project structure
2. The AWS PartyRock AI app
3. The S3 bucket used for static website hosting
4. The Lambda function that processes learner support requests
5. The API Gateway endpoint
6. The DynamoDB table storing requests
7. The CloudWatch logs showing backend execution
8. The architecture and design decisions

---

## What I learned

Through this project I learned how cloud systems are designed using managed AWS services:

* how to host a frontend on S3
* how serverless compute works with Lambda
* how APIs are exposed with API Gateway
* how DynamoDB stores application data
* how CloudWatch helps with monitoring
* how PartyRock can be part of a cloud AI prototype
* how to explain a cloud architecture from frontend to database

---

## Future improvements

The next version can include:

* Amazon Cognito login for parents and tutors
* Amazon Bedrock API integration instead of only PartyRock
* CloudFront for better content delivery
* AWS SAM or CDK deployment
* dashboards for learner intervention trends
* stronger IAM least privilege policies

---

## Author

**Adelaide Mhuntana**

WeThinkCode_ Cohort 2025

Aspiring Data Engineer and Cloud Engineer