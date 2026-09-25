# AWS EduCare Cloud Support Platform Architecture

## Project name

AWS EduCare Cloud Support Platform

## Purpose

EduCare is an education support platform that combines an AI learner support prototype with an AWS cloud backend.

The original prototype used AWS PartyRock for generative AI learner support. The upgraded architecture adds a cloud platform layer with serverless processing, managed data storage, API access, monitoring and infrastructure as code.

The goal is to show how a learner support idea can grow from an AI prototype into a cloud based system that can support parents, learners, tutors and education support teams.

---

## 1. System context diagram

This diagram shows the main users and cloud services involved in the system.

```mermaid
flowchart LR
    Learner["Learner"]
    Parent["Parent"]
    Tutor["Tutor or Support Professional"]

    PartyRock["AWS PartyRock\nAI support prototype"]
    Web["EduCare Web Interface\nStatic frontend"]
    API["Amazon API Gateway\nHTTPS API layer"]
    Lambda["AWS Lambda\nServerless backend"]
    DB["Amazon DynamoDB\nLearner support requests"]
    Logs["Amazon CloudWatch\nLogs and monitoring"]

    Learner --> PartyRock
    Parent --> PartyRock
    Tutor --> PartyRock

    Learner --> Web
    Parent --> Web
    Web --> API
    API --> Lambda
    Lambda --> DB
    Lambda --> Logs
```

---

## 2. Cloud architecture diagram

This diagram shows the cloud platform layer and how each AWS service fits into the solution.

```mermaid
flowchart TB
    subgraph ClientLayer["Client and AI Experience Layer"]
        Browser["Learner or Parent Browser"]
        AI["AWS PartyRock\nAI study support layer"]
    end

    subgraph AWSCloud["AWS Cloud Platform Layer"]
        S3["Amazon S3\nStatic website hosting"]
        APIGW["Amazon API Gateway\nREST endpoint"]
        LAMBDA["AWS Lambda\nSupport request handler"]
        DDB["Amazon DynamoDB\nSupport request database"]
        CW["Amazon CloudWatch\nExecution logs"]
        IAM["AWS IAM Role\nService permissions"]
    end

    subgraph IaC["Infrastructure as Code"]
        CFN["AWS CloudFormation\nCreates stack resources"]
    end

    Browser --> S3
    Browser --> AI
    S3 --> APIGW
    APIGW --> LAMBDA
    LAMBDA --> DDB
    LAMBDA --> CW
    IAM --> LAMBDA
    CFN --> S3
    CFN --> APIGW
    CFN --> LAMBDA
    CFN --> DDB
    CFN --> IAM
```

---

## 3. Request processing sequence diagram

This UML sequence diagram explains what happens when a learner support request is processed.

```mermaid
sequenceDiagram
    actor Parent as Parent or Learner
    participant Web as EduCare Web Interface
    participant API as API Gateway
    participant Lambda as Lambda Function
    participant DynamoDB as DynamoDB Table
    participant CloudWatch as CloudWatch Logs

    Parent->>Web: Enters learner support details
    Web->>API: Sends support request
    API->>Lambda: Invokes support request handler
    Lambda->>Lambda: Validates request and builds recommendation
    Lambda->>DynamoDB: Saves learner support request
    Lambda->>CloudWatch: Writes execution logs
    Lambda-->>API: Returns status and recommendation
    API-->>Web: Sends response to frontend
    Web-->>Parent: Shows support recommendation
```

---

## 4. Data model diagram

This diagram shows the current DynamoDB item structure used to store learner support requests.

```mermaid
erDiagram
    SUPPORT_REQUEST {
        string request_id PK
        string learner_name
        string grade
        string challenge
        string parent_contact
        string recommendation
        string created_at
    }
```

---

## 5. Infrastructure as Code resource map

This diagram shows the resources created by the CloudFormation template.

```mermaid
flowchart LR
    Template["cloudformation-template.yaml"]
    Stack["CloudFormation Stack\neducare-cloud-demo"]
    Role["IAM Role\nLambda execution permissions"]
    Function["Lambda Function\neducare-support-request-handler"]
    Table["DynamoDB Table\neducare-support-requests"]
    Api["API Gateway\neducare-support-api"]
    Logs["CloudWatch Log Group\n/aws/lambda/educare-support-request-handler"]

    Template --> Stack
    Stack --> Role
    Stack --> Function
    Stack --> Table
    Stack --> Api
    Function --> Logs
    Role --> Function
    Function --> Table
    Api --> Function
```

---

## 6. Logical component view

This diagram separates the system into clear responsibility areas.

```mermaid
flowchart TB
    subgraph AIPrototype["AI Prototype Layer"]
        PartyRockApp["EduCare AI CAPS Exam Success Coach\nAWS PartyRock app"]
    end

    subgraph ApplicationLayer["Application Layer"]
        Frontend["Static web interface\nweb/index.html"]
        Backend["Serverless backend\nbackend/lambda_function.py"]
    end

    subgraph DataLayer["Data Layer"]
        Requests["Learner support request records\nDynamoDB"]
    end

    subgraph OperationsLayer["Operations Layer"]
        Monitoring["CloudWatch logs"]
        IaCTemplate["CloudFormation template"]
    end

    PartyRockApp --> Frontend
    Frontend --> Backend
    Backend --> Requests
    Backend --> Monitoring
    IaCTemplate --> Frontend
    IaCTemplate --> Backend
    IaCTemplate --> Requests
    IaCTemplate --> Monitoring
```

---

## 7. Current AWS implementation

The current AWS implementation has been deployed in the Europe Stockholm region.

```text
CloudFormation stack: educare-cloud-demo
Region: Europe Stockholm eu-north-1
DynamoDB table: educare-support-requests
Lambda function: educare-support-request-handler
API Gateway: educare-support-api
CloudWatch log group: /aws/lambda/educare-support-request-handler
```

The Lambda function was tested with a learner support request. The request was processed successfully and stored in the DynamoDB table.

---

## 8. AWS services used

| AWS service | System role | Reason for use |
|---|---|---|
| AWS PartyRock | AI support prototype | Fast AI app creation for study support and intervention guidance |
| Amazon S3 | Static frontend hosting | Hosts a lightweight web interface without managing servers |
| Amazon API Gateway | API layer | Provides an HTTPS endpoint between the frontend and backend |
| AWS Lambda | Serverless backend | Processes support requests only when invoked |
| Amazon DynamoDB | Managed database | Stores learner support request items without managing database servers |
| Amazon CloudWatch | Monitoring | Stores Lambda execution logs and supports troubleshooting |
| AWS IAM | Permissions | Allows services to access only what they need |
| AWS CloudFormation | Infrastructure as code | Recreates the stack from a template |

---

## 9. Why serverless

Serverless is a good fit for this project because:

* there is no server to manage
* Lambda only runs when a request is made
* DynamoDB is managed by AWS
* CloudWatch gives automatic logs
* CloudFormation makes the cloud setup repeatable
* the project can start small and scale later

---

## 10. Production improvements

A production version can add:

* Amazon Cognito for parent, learner and tutor login
* CloudFront in front of S3 for content delivery
* Amazon Bedrock for production AI integration
* stricter IAM least privilege permissions
* API Gateway connected directly to the frontend form
* dashboards for learner intervention trends
* CI CD deployment with GitHub Actions
