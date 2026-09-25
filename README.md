# AWS EduCare Cloud Support Platform

## Overview

EduCare Cloud Support Platform is a growing education technology project focused on learner support, parent guidance, intervention planning and education data insights.

The project started as an AWS PartyRock educational AI prototype. It is now being expanded into a broader AWS cloud platform that combines a cloud hosted frontend, serverless backend processing, managed database storage, monitoring and an AI support layer.

The long term goal is to build a practical cloud based education support system that can help learners, parents, tutors and education support teams understand learner challenges earlier and respond with better support.

---

## Project vision

EduCare is designed around a simple problem:

```text
Many learners need support before they fail.
Parents often do not know what support is needed.
Tutors and schools need better information to recommend interventions.
Cloud and AI can help make support more accessible and scalable.
```

The platform explores how AWS services can be used to collect learner support requests, process them through a serverless backend, store them in a managed database and connect them to AI powered learning guidance.

---

## Cloud architecture

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

## AWS services used

| Cloud area | AWS service | Purpose |
|---|---|---|
| Static hosting | Amazon S3 | Hosts the frontend demo site |
| Serverless compute | AWS Lambda | Processes learner support requests |
| API layer | Amazon API Gateway | Exposes an HTTPS endpoint for the frontend |
| Cloud database | Amazon DynamoDB | Stores learner support requests |
| Monitoring | Amazon CloudWatch | Stores Lambda logs and backend activity |
| AI prototype layer | AWS PartyRock | Provides AI based learner guidance and intervention ideas |
| Infrastructure planning | CloudFormation | Documents how the cloud stack can be recreated |

---

## Main features

### 1. Learner support request frontend

A lightweight web interface can be hosted on Amazon S3. It allows a learner or parent to submit a learning support request.

### 2. Serverless support request processing

AWS Lambda processes the support request and returns a basic recommendation based on the learner challenge.

### 3. Managed cloud database

Amazon DynamoDB stores support request records such as learner name, grade, subject, challenge and recommendation.

### 4. Monitoring and logs

Amazon CloudWatch is used to view Lambda execution logs and confirm that the backend ran successfully.

### 5. AI learning support layer

AWS PartyRock is used as the AI prototype layer for CAPS aligned study support, revision planning, parent guidance, tutor intervention suggestions and learner motivation.

---

## Repository structure

```text
aws-partyrock-educare-ai-sa
│
├── ai-productivity-app
│   ├── EduCare-AI-CAPS-Exam-Success-Coach.pdf
│   ├── EduCare-AI-SA-Demo.mp4.mp4
│   └── partyrock-link.txt.txt
│
├── ai-data-analysis
│   ├── foundational-learning-dataset.csv
│   ├── findings.md
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

## Demo flow

The project can be demonstrated in this order:

1. Open the GitHub repository and explain the architecture
2. Show the S3 static website frontend in `web/index.html`
3. Show the Lambda backend in `backend/lambda_function.py`
4. Show the DynamoDB table for learner support requests
5. Test the Lambda function and show a response
6. Open CloudWatch logs to prove the function executed
7. Show the CloudFormation template as the infrastructure plan
8. Open the AWS PartyRock app as the AI support prototype layer

---

## Design decisions

### Why S3

S3 is a simple and cost effective way to host a static frontend without running a server.

### Why Lambda

Lambda allows the backend to run only when a request is made. This supports a serverless model and reduces infrastructure management.

### Why DynamoDB

DynamoDB is a managed NoSQL database that fits simple request records and can scale without managing database servers.

### Why CloudWatch

CloudWatch makes the backend observable by storing logs and helping with troubleshooting.

### Why PartyRock

PartyRock allows rapid prototyping of the AI learning support experience before moving to a deeper Amazon Bedrock integration in future.

---

## Current project status

The repository contains:

* AWS PartyRock education support prototype material
* learner support dataset and analysis material
* S3 frontend demo file
* Lambda backend code
* CloudFormation infrastructure plan
* architecture documentation
* cloud demo guide

The cloud implementation can continue growing by connecting the S3 frontend to API Gateway, Lambda and DynamoDB in AWS Console.

---

## Future improvements

The next version can include:

* Amazon Cognito login for parents, learners and tutors
* Amazon Bedrock API integration for production AI support
* CloudFront distribution for faster frontend delivery
* API Gateway connected to the web form
* DynamoDB dashboards for learner intervention trends
* IAM least privilege policies
* AWS SAM or CDK for repeatable deployment

---

## Author

**Adelaide Mhuntana**

Aspiring Data Engineer and Cloud Engineer