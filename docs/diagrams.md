# EduCare Cloud Architecture Diagrams

This document explains the EduCare Cloud Support Platform using professional architecture and UML-style diagrams.

The diagrams show how the AI prototype layer, web interface, API layer, serverless backend, database and monitoring services connect together.

---

## 1. High level system architecture

```mermaid
flowchart TD
    A[Parent or Learner] --> B[EduCare Web Interface]
    B --> C[Amazon API Gateway]
    C --> D[AWS Lambda Function]
    D --> E[Amazon DynamoDB]
    D --> F[Amazon CloudWatch Logs]
    A --> G[AWS PartyRock AI Prototype]
    G --> H[Study Plan, Practice Questions, Parent Guidance]

    subgraph AI Support Layer
        G
        H
    end

    subgraph Cloud Platform Layer
        B
        C
        D
        E
        F
    end
```

---

## 2. Request processing sequence

```mermaid
sequenceDiagram
    actor User as Parent or Learner
    participant Web as EduCare Web Interface
    participant API as Amazon API Gateway
    participant Lambda as AWS Lambda
    participant DB as Amazon DynamoDB
    participant Logs as Amazon CloudWatch
    participant AI as AWS PartyRock

    User->>AI: Open AI support prototype
    AI-->>User: Return CAPS-aligned study guidance

    User->>Web: Submit learner support request
    Web->>API: Send HTTPS request
    API->>Lambda: Invoke serverless backend
    Lambda->>Lambda: Create support recommendation
    Lambda->>DB: Store learner support request
    Lambda->>Logs: Write execution logs
    Lambda-->>API: Return success response
    API-->>Web: Return processed result
    Web-->>User: Show recommendation status
```

---

## 3. Cloud component diagram

```mermaid
flowchart LR
    subgraph Frontend
        Web[Static Web Interface]
    end

    subgraph API Layer
        APIGW[Amazon API Gateway]
    end

    subgraph Compute Layer
        Lambda[AWS Lambda]
    end

    subgraph Data Layer
        DynamoDB[(Amazon DynamoDB)]
    end

    subgraph Monitoring Layer
        CloudWatch[Amazon CloudWatch Logs]
    end

    subgraph AI Prototype Layer
        PartyRock[AWS PartyRock]
    end

    Web --> APIGW
    APIGW --> Lambda
    Lambda --> DynamoDB
    Lambda --> CloudWatch
    PartyRock --> Web
```

---

## 4. UML-style use case diagram

```mermaid
flowchart TB
    Parent((Parent))
    Learner((Learner))
    Tutor((Tutor))
    Admin((Education Support Team))

    UC1[Get AI study support]
    UC2[Generate CAPS-aligned study plan]
    UC3[Submit learner support request]
    UC4[Process request with Lambda]
    UC5[Store request in DynamoDB]
    UC6[Monitor backend in CloudWatch]
    UC7[Review learner intervention data]

    Parent --> UC1
    Parent --> UC3
    Learner --> UC1
    Learner --> UC2
    Tutor --> UC7
    Admin --> UC6
    Admin --> UC7

    UC1 --> UC2
    UC3 --> UC4
    UC4 --> UC5
    UC4 --> UC6
```

---

## 5. Data model

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

## 6. Deployment and infrastructure view

```mermaid
flowchart TD
    Repo[GitHub Repository] --> Template[CloudFormation Template]
    Template --> Stack[CloudFormation Stack: educare-cloud-demo]
    Stack --> Role[IAM Execution Role]
    Stack --> Lambda[AWS Lambda Function]
    Stack --> Table[DynamoDB Table]
    Stack --> API[API Gateway]
    Stack --> Logs[CloudWatch Logs]

    Role --> Lambda
    Lambda --> Table
    Lambda --> Logs
    API --> Lambda
```

---

## 7. System explanation

EduCare has two main layers:

1. **AI support layer**  
   AWS PartyRock is used to prototype the learner support experience. It generates CAPS-aligned study plans, revision support, practice questions and parent guidance.

2. **Cloud platform layer**  
   AWS services are used to process and store learner support requests. API Gateway exposes the API, Lambda processes requests, DynamoDB stores data and CloudWatch records logs.

This structure shows how an AI education idea can grow into a proper AWS cloud architecture.
