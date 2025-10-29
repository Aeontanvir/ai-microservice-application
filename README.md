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
