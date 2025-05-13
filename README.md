# 🛒 E-Commerce Microservices System

A full-fledged backend system for an e-commerce platform built using Java and Spring Boot with a clean microservices architecture. The project is designed to be scalable, modular, and ready for production deployment using modern tools and best practices.

---

## 📦 Tech Stack

- **Java 17**, **Spring Boot**, **Spring Cloud**
- **JWT Authentication (HS256)** with role-based access
- **MySQL** for persistent storage
- **Eureka** for service discovery
- **Spring Cloud Gateway** for API routing
- **RabbitMQ / Kafka** for asynchronous communication
- **Lombok**, **ModelMapper**, **MapStruct** (optional)
- **Docker** (optional), **ELK Stack**, **Swagger UI**

---

## 🧱 Microservices Overview

| Service                | Description |
|------------------------|-------------|
| `api-gateway`          | Centralized API entry point. Routes requests to internal services securely using JWT tokens. |
| `service-discovery`    | Eureka Server to manage dynamic registration and discovery of microservices. |
| `user-service`         | Handles customer & admin registration/login. Issues JWT tokens. Manages user roles and authentication. |
| `product-catalog`      | Allows CRUD operations on products. Includes category/subcategory structure, pricing, discount logic, and filtering. |
| `order-service`        | Manages customer orders. Supports placing, viewing, and canceling orders. Coordinates with inventory service. |
| `inventory-service`    | Tracks product stock. Updates inventory when orders are placed/canceled. Can support locking/reservation mechanisms. |
| `common-lib` (optional)| Shared models and utilities used across services to avoid duplication. |

---

## 🔐 Authentication

- Role-based JWT issued on login via `/auth/customer-login`
- Token is passed in `Authorization` header for all secure endpoints.
- Admin-only routes protected at gateway/service level.

---

## 🚀 Running the Project (Dev Setup)

> Prerequisite: Java 17+, MySQL, RabbitMQ (if used), Docker (optional)

1. Clone the repo:
   ```bash
   git clone https://github.com/your-username/ecommerce-microservices.git
   cd ecommerce-microservices
.
