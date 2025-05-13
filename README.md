 # 🛒 E-Commerce Backend - Microservices Architecture

This project is a modular, production-style **e-commerce backend** built using Spring Boot and Spring Cloud. It follows the **microservices architecture** to ensure scalability, maintainability, and clear separation of concerns.

> ✅ Actively being developed | 📌 Microservices structure

---

## ⚙️ Tech Stack
- **Language**: Java 17
- **Frameworks**: Spring Boot, Spring Cloud (Gateway, Eureka)
- **Authentication**: JWT (role-based)
- **Databases**: PostgreSQL (one per microservice)
- **Messaging Broker**: RabbitMQ (for asynchronous events)
- **Build Tool**: Maven
- **Utilities**: Lombok, ModelMapper
- **Testing**: JUnit, Mockito (planned)
- **CI/CD**: GitHub Actions (planned)
- **Containers & Deployment**: Docker & Docker Compose (planned)

---

## 🧩 Microservices Overview

Each service is hosted in its own GitHub repository. Use the links below to explore their codebases:

| Service | Description |
|--------|-------------|
| [**API Gateway**](https://github.com/Surya1824/Api-Gateway) | Centralized entry point. Handles routing, filtering, and request forwarding. Secures routes using JWT validation. |
| [**Service Discovery**](https://github.com/Surya1824/Service-Discovery-Hub) | Eureka server for registering and discovering all microservices dynamically. |
| [**User Management Service**](https://github.com/Surya1824/User-Management-Svc) | Handles customer/admin registration and login. Generates role-based JWTs. |
| [**Product Catalog Service**](https://github.com/Surya1824/Product-Catalog-Svc) | Manages product details, categories, subcategories, discounts. Supports admin-level CRUD operations. |
| [**Order Management Service**](https://github.com/Surya1824/Order-Management-Svc) | Manages order placement, history, and cancellations. Uses product snapshots and interacts with inventory. |
| [**Inventory Service**](https://github.com/Surya1824/Inventory-Management-Svc) | Updates and tracks product stock. Consumes order events for stock adjustment. |
| **Payment Service** _(coming soon)_ | Simulate or integrate payment processing. Trigger order updates upon success/failure. |
| **Notification Service** _(coming soon)_ | Will send email or SMS alerts for orders and updates. |

> 🗄️ Each service uses a **dedicated PostgreSQL database**.  
> 🔁 Inter-service communication is **synchronous (REST)** and **asynchronous (RabbitMQ events)** where appropriate.

---

## 🔐 Authentication & Security

- Role-based authentication (`CUSTOMER`, `ADMIN`) via **JWT tokens**
- Auth tokens are validated at the **API Gateway** level
- Public endpoints:  
  - `POST /auth/customer-register`  
  - `POST /auth/customer-login`  
- Private endpoints: Protected using role-based access control

---

## 🧱 Project Architecture

```text
       [ Frontend (Angular) ]
                |
          [ API Gateway ]
                |
 ┌──────────────┼──────────────┐
 ↓              ↓              ↓
[User]      [Product]        [Order]
   ↓              ↓              ↓
[Inventory]   [Payment]    [Notification]
