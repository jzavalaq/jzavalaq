# Juan Zavala

**Senior Java Developer** · Spring Boot · Microservices · Cloud-Native APIs

---

## 👋 About Me

Backend engineer with 15+ years of expertise in Java and the Spring ecosystem. I specialize in building production-grade REST APIs, event-driven systems, and cloud-native microservices. Passionate about clean architecture, domain-driven design, and engineering excellence.

---

## 🛠️ Tech Stack

| Category | Technologies |
|----------|-------------|
| **Languages** | Java 17/21, SQL, JavaScript |
| **Frameworks** | Spring Boot 3.x, Spring Security, Spring Data, Spring WebFlux |
| **Data** | PostgreSQL, Redis, Elasticsearch, Flyway |
| **Messaging** | Apache Kafka, RabbitMQ, WebSocket (STOMP) |
| **DevOps** | Docker, Kubernetes, GitHub Actions, Maven |
| **Patterns** | DDD, CQRS, Event Sourcing, Saga, Hexagonal Architecture, Multi-tenancy |
| **Observability** | Prometheus, Grafana, ELK Stack, OpenTelemetry |

---

## 🏗️ Architecture Philosophy

```mermaid
flowchart TB
    subgraph Clients
        Web[Web App]
        Mobile[Mobile App]
        External[External Services]
    end

    subgraph "API Gateway Layer"
        GW[API Gateway<br/>Rate Limiting • Auth • Routing]
    end

    subgraph "Microservices Layer"
        Ledger[CQRS Ledger]
        Search[Search Analytics]
        Banking[Banking Service]
        Notification[Notification Hub]
        Commerce[E-Commerce Platform]
        Loan[Loan Origination]
    end

    subgraph "Event Layer"
        Kafka[Apache Kafka]
        WebSocket[WebSocket Server]
    end

    subgraph "Data Layer"
        PostgreSQL[(PostgreSQL)]
        Redis[(Redis Cache)]
        ES[(Elasticsearch)]
    end

    Web --> GW
    Mobile --> GW
    External --> GW

    GW --> Ledger
    GW --> Search
    GW --> Banking
    GW --> Notification
    GW --> Commerce
    GW --> Loan

    Ledger <--> Kafka
    Banking <--> Kafka
    Notification <--> Kafka
    Commerce <--> Kafka
    Loan <--> Kafka

    Notification <--> WebSocket

    Ledger --> PostgreSQL
    Banking --> PostgreSQL
    Commerce --> PostgreSQL
    Loan --> PostgreSQL

    Notification --> Redis
    Banking --> Redis

    Search --> ES
    Banking --> ES
```

---

## 📊 Featured Projects

| Project | Description | Tech Highlights |
|---------|-------------|-----------------|
| [cqrs-event-sourcing-ledger](https://github.com/jzavalaq/cqrs-event-sourcing-ledger) | Banking ledger implementing **CQRS and Event Sourcing** patterns with Axon Framework, event replay, and complete audit trail | **Axon Framework**, CQRS, Event Sourcing, DDD |
| [search-analytics-elasticsearch-api](https://github.com/jzavalaq/search-analytics-elasticsearch-api) | Full-text search and analytics API with **Elasticsearch 8.x** integration, fuzzy matching, and search analytics | **Elasticsearch 8.x**, Full-Text Search, Redis |
| [banking-financial-api](https://github.com/jzavalaq/banking-financial-api) | Complete banking system with multi-currency accounts, SWIFT/SEPA transfers, fraud detection, loans, and KYC compliance | Spring Boot 3.2, JWT, PostgreSQL, Flyway, K8s |
| [notification-hub-api](https://github.com/jzavalaq/notification-hub-api) | Multi-channel notification platform supporting email, SMS, push notifications with Redis caching and **WebSocket real-time** | Spring Boot, Redis, WebFlux, **WebSocket/STOMP** |
| [api-rate-limiting-gateway](https://github.com/jzavalaq/api-rate-limiting-gateway) | Reactive API gateway with token bucket rate limiting algorithm | **Spring WebFlux**, Bucket4j, Resilience4j |
| [multitenant-ecommerce-api](https://github.com/jzavalaq/multitenant-ecommerce-api) | Multi-tenant e-commerce platform with vendor isolation, product management, and shopping cart | Spring Boot, **Multi-tenancy**, JWT, RBAC |
| [loan-origination-credit-api](https://github.com/jzavalaq/loan-origination-credit-api) | Fintech loan origination system with FICO-style credit scoring engine and automated decision workflow | Spring Boot, Credit Scoring, Audit Logging |

---

## 🔄 System Design Example

### Banking Transaction Flow

```mermaid
sequenceDiagram
    participant Client
    participant Gateway as API Gateway
    participant Auth as Auth Service
    participant Banking as Banking Service
    participant Fraud as Fraud Detection
    participant DB as PostgreSQL
    participant Kafka

    Client->>Gateway: POST /api/v1/transfers
    Gateway->>Auth: Validate JWT
    Auth-->>Gateway: Token Valid

    Gateway->>Banking: Process Transfer
    Banking->>DB: Check Balance
    DB-->>Banking: Balance OK

    Banking->>Fraud: Analyze Transaction
    Fraud-->>Banking: Risk Score: LOW

    Banking->>DB: Execute Transfer
    Banking->>Kafka: Publish Transfer Event

    Kafka-->>Banking: Ack
    Banking-->>Gateway: Transfer Complete
    Gateway-->>Client: 200 OK
```

### Event-Driven Architecture

```mermaid
flowchart LR
    subgraph Producers
        Order[Order Service]
        Payment[Payment Service]
        Inventory[Inventory Service]
    end

    subgraph "Apache Kafka"
        Topics[Event Topics]
    end

    subgraph Consumers
        Notification2[Notification]
        Analytics[Analytics]
        Audit[Audit Log]
    end

    Order -->|OrderCreated| Topics
    Payment -->|PaymentProcessed| Topics
    Inventory -->|StockUpdated| Topics

    Topics -->|Consume| Notification2
    Topics -->|Consume| Analytics
    Topics -->|Consume| Audit
```

---

## ☁️ Cloud-Native Deployment

```mermaid
flowchart TB
    subgraph "Kubernetes Cluster"
        subgraph "Ingress Layer"
            Ingress[NGINX Ingress<br/>+ TLS]
        end

        subgraph "Application Namespace"
            Deploy1[Banking API<br/>Replicas: 3]
            Deploy2[Notification API<br/>Replicas: 2]
        end

        subgraph "Data Namespace"
            PG[(PostgreSQL<br/>Primary + Replica)]
            RD[(Redis<br/>Cluster)]
        end

        subgraph "Observability"
            Prom[Prometheus]
            Graf[Grafana]
        end
    end

    Internet --> Ingress
    Ingress --> Deploy1
    Ingress --> Deploy2

    Deploy1 --> PG
    Deploy1 --> RD
    Deploy2 --> RD

    Deploy1 -.->|Metrics| Prom
    Deploy2 -.->|Metrics| Prom
    Prom --> Graf
```

---

## 📈 GitHub Stats

![Juan's GitHub stats](https://github-readme-stats.vercel.app/api?username=jzavalaq&show_icons=true&theme=default&hide_border=true&count_private=true)

![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=jzavalaq&layout=compact&theme=default&hide_border=true)

---

## 🔗 Connect

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue)](https://linkedin.com/in/juanzavalaq)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-black?logo=github)](https://github.com/jzavalaq)

---

> "Building robust, scalable backend systems with clean architecture and enterprise best practices."
