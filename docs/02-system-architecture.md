# 02. System Architecture

## 1. Overview

The AI Interview Platform follows a **Modular Monolith Architecture**.

Instead of dividing the application into independent microservices, the system is organized into independent business modules within a single backend application.

Each module is responsible for one business domain and follows the same internal architecture.

This approach provides:

- Clean separation of business domains
- Easier development and debugging
- Single deployment
- Better maintainability
- Easy migration to microservices in the future

---

## 2. Architecture Style

Architecture Type:
- Modular Monolith

Design Pattern:
- Layered Architecture

Dependency Management:
- Manual Dependency Injection

Communication:
- REST APIs

Authentication:
- JWT Authentication

Authorization:
- Role-Based Access Control (RBAC)

---

## 3. High-Level Architecture

```
                React Frontend
                       │
                 REST API
                       │
               Express Backend
                       │
      ┌─────────┬──────────┬─────────┬──────────┐
      │         │          │         │
    Auth     Resume    Interview   Coding
      │         │          │         │
      └─────────┴──────────┴─────────┘
                    │
              Shared Module
                    │
               MongoDB Database
```

---

## 4. Request Flow

```
Client

↓

Routes

↓

Middleware

↓

Controller

↓

Service

↓

Repository

↓

Database

↓

Response
```

---

## 5. Module Architecture

Every module follows the same internal structure.

```
Module

├── routes
├── controller
├── service
├── repository
├── model
├── validation
└── utils
```

This ensures consistency throughout the application.

---

## 6. Project Structure

```
src/

├── auth/
├── resume/
├── interview/
├── coding/
├── dashboard/
├── admin/
│
├── shared/
│   ├── middleware/
│   ├── config/
│   ├── constants/
│   ├── utils/
│   └── errors/
│
├── app.js
└── server.js
```

---

## 7. Layer Responsibilities

### Routes

Maps REST endpoints to controllers.

---

### Controller

Handles HTTP requests and responses.

---

### Service

Contains business logic.

---

### Repository

Performs database operations.

---

### Model

Defines MongoDB schemas.

---

### Shared

Contains reusable components used across multiple modules.

---

## 8. Technology Stack

Frontend
- React
- Tailwind CSS

Backend
- Node.js
- Express.js

Database
- MongoDB

Authentication
- JWT
- bcrypt

AI
- Gemini / OpenAI

Caching (Future)
- Redis

Queue (Future)
- BullMQ

Deployment
- Docker

---

## 9. Design Principles

- Modular Design
- Separation of Concerns
- Single Responsibility Principle
- Stateless Authentication
- Dependency Injection
- RESTful APIs
- Reusability
- Scalability

---

## 10. Future Evolution

The application is intentionally designed as a Modular Monolith.

As the platform grows, individual modules such as Interview, Resume, or AI Processing can be extracted into independent microservices without significant architectural changes.

Potential future improvements include:

- Redis Caching
- Background Job Processing
- Horizontal Scaling
- Load Balancer
- Docker Orchestration
- Kubernetes