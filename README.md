# AWS EduCare Cloud Support Platform

## Verification code

```text
WTC-BEJEV8E3
```

---

## Overview

EduCare Cloud Support Platform is a growing education technology project focused on learner support, parent guidance, intervention planning and education data insights.

The project started as an AWS PartyRock educational AI prototype. It is now being expanded into a broader AWS cloud platform that combines a cloud hosted frontend, serverless backend processing, managed database storage, monitoring and an AI support layer.

The long term goal is to build a practical cloud based education support system that can help learners, parents, tutors and education support teams understand learner challenges earlier and respond with better support.

---

## Live AI prototype

The AI support prototype was built with AWS PartyRock.

[Open EduCare AI CAPS Exam Success Coach](https://partyrock.aws/u/adelaidemhuntana/LLVCHZG5T/EduCare-AI-CAPS-Exam-Success-Coach)

This PartyRock prototype is the AI layer of the project. It supports learners and parents with CAPS aligned study plans, revision support, practice questions, parent guidance, tutor intervention suggestions and learning support pathways.

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

## System architecture

```text
Learner or Parent
        ↓
EduCare web interface
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

The architecture separates the project into two layers:

1. **AI support layer**: AWS PartyRock is used to prototype the learner support experience.
2. **Cloud platform layer**: AWS services are used to process, store and monitor learner support requests.

---

## Professional architecture and UML diagrams

The full architecture documentation is in:

[`docs/architecture.md`](docs/architecture.md)

It includes:

* system context diagram
* AWS cloud architecture diagram
* UML sequence diagram for request processing
* DynamoDB data model diagram
* CloudFormation resource map
* logical component view

These diagrams make it easier to understand how the AI prototype, frontend, API, Lambda backend, DynamoDB storage, CloudWatch monitoring and CloudFormation infrastructure fit together.

---

## How the system works

### Step 1: Learner support experience

A learner or parent uses the EduCare AI prototype to receive CAPS aligned study support, revision guidance, practice questions, parent guidance and intervention ideas.

### Step 2: Support request capture

The cloud platform is designed to capture a learner support request from a web interface or API request. A request can include the learner name, grade, learning challenge and parent contact.

### Step 3: Serverless processing

AWS Lambda receives the request and applies simple backend logic to create a support recommendation. For example, a reading challenge returns a reading support plan recommendation.

### Step 4: Cloud database storage

The processed learner support request is stored in Amazon DynamoDB. This makes the request available for future dashboards, intervention tracking and reporting.

### Step 5: Monitoring

Amazon CloudWatch records the Lambda execution logs. This helps with monitoring, troubleshooting and proving that the backend executed successfully.

---

## AWS services used

| Cloud area | AWS service | Purpose |
|---|---|---|
| Static hosting | Amazon S3 | Hosts the frontend demo site or static web interface |
| API layer | Amazon API Gateway | Exposes an HTTPS endpoint for the backend |
| Serverless compute | AWS Lambda | Processes learner support requests |
| Cloud database | Amazon DynamoDB | Stores learner support requests |
| Monitoring | Amazon CloudWatch | Stores Lambda logs and backend activity |
| AI prototype layer | AWS PartyRock | Provides AI based learner guidance and intervention ideas |
| Infrastructure as code | AWS CloudFormation | Creates the cloud resources from a template |
| Security and permissions | AWS IAM | Allows Lambda to write to DynamoDB and CloudWatch |

---

## Current cloud implementation

The current AWS implementation includes a deployed CloudFormation stack that creates the main backend resources.

```text
CloudFormation stack: educare-cloud-demo
Region: Europe Stockholm eu-north-1
DynamoDB table: educare-support-requests
Lambda function: educare-support-request-handler
API Gateway: educare-support-api
CloudWatch log group: /aws/lambda/educare-support-request-handler
```

The Lambda function has been tested with a learner support request. The request was processed successfully and stored in the DynamoDB table.

---

## Main features

### 1. Learner support request frontend

A lightweight web interface can be hosted on Amazon S3. It allows a learner or parent to submit a learning support request.

### 2. Serverless support request processing

AWS Lambda processes the support request and returns a basic recommendation based on the learner challenge.

### 3. Managed cloud database

Amazon DynamoDB stores support request records such as learner name, grade, challenge, parent contact and recommendation.

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

## Important files

| File | Purpose |
|---|---|
| `backend/lambda_function.py` | Serverless backend logic for learner support requests |
| `infrastructure/cloudformation-template.yaml` | Infrastructure as code for AWS resources |
| `web/index.html` | Static web interface concept |
| `docs/architecture.md` | Professional architecture and UML diagrams |
| `ai-productivity-app/partyrock-link.txt.txt` | Live PartyRock prototype link |

---

## Design decisions

### Why S3

S3 is a simple and cost effective way to host a static frontend without running a server.

### Why API Gateway

API Gateway provides an HTTPS entry point for the frontend to send requests to Lambda.

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
* static frontend concept
* Lambda backend code
* deployed CloudFormation infrastructure plan
* professional architecture and UML documentation
* live PartyRock AI prototype link
* working DynamoDB storage for learner support requests
* CloudWatch monitoring for Lambda execution logs

---

## Future improvements

The next version can include:

* Amazon Cognito login for parents, learners and tutors
* Amazon Bedrock API integration for production AI support
* CloudFront distribution for faster frontend delivery
* API Gateway connected directly to the web form
* dashboards for learner intervention trends
* IAM least privilege policies for production use
* AWS SAM or CDK for repeatable deployment

---

## Author

**Adelaide Mhuntana**

Aspiring Data Engineer and Cloud Engineer