# AI-Powered Fitness Application

Welcome to our comprehensive fitness application built on a modern microservices architecture. This project combines the power of Spring Boot microservices with React frontend, enhanced by AI capabilities through Google Gemini API integration.

## 🌟 Highlights

- **Microservices Architecture**: Fully featured fitness application built on a scalable and maintainable microservices architecture
- **AI Integration**: Smart fitness recommendations and personalized workout plans powered by Google Gemini API
- **Step-by-Step Guide**: Comprehensive documentation for easy implementation and understanding

## 🚀 Technology Stack

### Backend
- **Spring Boot**: Core framework for building microservices
- **Spring Cloud Netflix (Eureka)**: Service discovery and registration
- **Spring Cloud Gateway**: API Gateway for routing and cross-cutting concerns
- **Spring Cloud Config Server**: Centralized configuration management
- **Spring AMQP with RabbitMQ**: Asynchronous messaging between services
- **Keycloak**: Identity and access management
- **Database**: PostgreSQL/MySQL for data persistence

### Frontend
- **React**: Modern, component-based UI development
- **React Router**: Client-side routing
- **Redux/Context API**: State management
- **Material-UI/Tailwind**: UI component library

### AI Integration
- **Google Gemini API**: Advanced AI capabilities for personalized fitness recommendations

## 🏗️ Architecture Overview

The application follows a microservices architecture with the following key components:

1. **API Gateway**: Entry point for all client requests
2. **Service Registry (Eureka)**: Service discovery and registration
3. **Config Server**: Centralized configuration management
4. **Auth Service**: User authentication and authorization using Keycloak
5. **Core Services**:
   - User Profile Service
   - Workout Service
   - Nutrition Service
   - AI Recommendation Service
6. **Message Broker**: RabbitMQ for asynchronous communication

## 🔧 Getting Started

Detailed setup instructions and documentation will be added as the project progresses.

## 🏛️ Architecture (detailed)

This section expands the high-level architecture and maps directly to the diagram included with the project.

![Architecture diagram](./architecture.png)

*Figure: System architecture — API Gateway, Auth (Keycloak), Eureka, Config Server, RabbitMQ, services, databases and AI integration.*

Components
- API Gateway (Spring Cloud Gateway): the single entry point for all client requests (web/mobile). It handles routing, rate-limiting, and common cross-cutting concerns.
- Auth Server (Keycloak): handles authentication and authorization. Clients authenticate here (OAuth2/OpenID Connect) and present tokens to the gateway and services.
- Service Registry (Eureka): services register themselves with Eureka for service discovery and resiliency.
- Config Server (Spring Cloud Config Server): centralized externalized configuration for all microservices.
- Message Broker (RabbitMQ): used for async, event-driven communication (e.g., activity events, recommendation requests, background processing).
- Datastores:
   - MySQL/PostgreSQL: relational storage for user accounts and relational data (User service).
   - MongoDB: document storage for activity logs, AI results, and other unstructured or semi-structured data used by the AI service and activity service.
- Core Services:
   - User Service: manages user accounts, profiles and persistence in the relational DB.
   - Activity Service: ingests workout/activity events and stores them in MongoDB. Publishes events to RabbitMQ when activity data needs processing.
   - AI Recommendation Service: consumes messages from RabbitMQ or accepts REST requests to generate personalized workout/nutrition recommendations. Stores AI artifacts/results in MongoDB and may push results back via messaging or expose them via REST.
   - Workout/Nutrition Services: domain services that manage plans, goals, progress and interact with AI service for personalization.

AI Integration
- The AI Recommendation Service acts as the bridge between application data and the Google Gemini API. Typical flow:
   1. An activity event or recommendation request is created by the Activity/Workout service.
   2. The event is published to RabbitMQ (or sent directly via REST) and consumed by the AI Recommendation Service.
   3. The AI service prepares context (user profile, activity history, preferences) and calls the Google Gemini API to generate suggestions.
   4. The AI service stores the generated recommendation in MongoDB and notifies interested services (via RabbitMQ) or the client via the API Gateway.

Request & Event Flow (from diagram)
- Client (Web/Mobile) → API Gateway
- API Gateway validates tokens (Keycloak) and routes to the appropriate microservice
- Services discover each other through Eureka and use the Config Server for configuration values
- Activity and domain events flow through RabbitMQ to decouple producers and consumers (e.g., Activity Service → RabbitMQ → AI Service)
- AI Service calls Google Gemini (external) for advanced reasoning / personalized responses and persists results in MongoDB

Deployment & Ops notes
- Each microservice is packaged separately (typical Spring Boot JAR or containerized image). Use Docker and Docker Compose or Kubernetes for local and production deployments.
- Provide environment-specific configuration via the Config Server and secure sensitive values using a vault solution or Keycloak-protected endpoints.
- Monitor the message broker and keep visibility into queue lengths to avoid processing bottlenecks.

Diagram reference
- The included architecture diagram shows these components and the flow between them (API Gateway, Keycloak, Eureka, Config Server, RabbitMQ, MySQL/Postgres, MongoDB, AI Service and Google Gemini server).

Ports/Placeholders (example local defaults)
- API Gateway: 8080
- Eureka Server: 8761
- Config Server: 8888
- Keycloak: 8081 (or container default)
- RabbitMQ: 5672 (AMQP), 15672 (management)
- MySQL/Postgres: 5432 / 3306
- MongoDB: 27017

Security
- All inter-service communication should be secured. Use mTLS or JWT tokens validated by Keycloak for service-to-service calls. Keep credentials and API keys out of the repository and in the Config Server or a vault.

Next steps
- Add service-specific run instructions and docker-compose / k8s manifests.
- Add sample environment files (*.env) with placeholders for database URLs, Keycloak realm client IDs, and Google Gemini API keys.
## 📝 Project Structure

The project is organized into multiple microservices, each with its own responsibility:

```
/fitness-app
├── api-gateway/
├── service-registry/
├── config-server/
├── auth-service/
├── user-service/
├── workout-service/
├── nutrition-service/
├── ai-service/
└── frontend/
```

## 🛠️ Setup Requirements

- Java 21
- Node.js 22
- Docker & Docker Compose
- PostgreSQL/MySQL
- RabbitMQ
- Keycloak

More details and setup instructions will be added as the project develops.

## 🤝 Contributing

Guidelines for contributing will be added soon.

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---
⚠️ This project is under active development. Documentation will be updated regularly as new features are implemented.
