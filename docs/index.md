# Payment Gateway System

A comprehensive microservices-based payment gateway system built with Spring Boot and Spring Cloud Gateway. This system provides secure payment processing, transaction management, merchant services, and financial reporting capabilities.

## Architecture

This project follows a microservices architecture pattern, where each service is responsible for a specific domain of functionality. The system uses Spring Cloud Gateway as the API gateway to route requests to appropriate microservices.

### System Components

```
┌─────────────────┐
│   API Gateway   │ (Port: 4004)
└────────┬────────┘
         │
    ┌────┴────┬──────────────────┬──────────────┐
    │         │                  │              │
┌───▼───┐ ┌──▼────┐ ┌───────────▼──┐ ┌─────────▼──┐
│ Auth  │ │Payment│ │ Transaction  │ │  Merchant  │
│Service│ │Service│ │   Service    │ │  Service   │
└───────┘ └───────┘ └──────────────┘ └────────────┘
    │         │                  │              │
┌───▼───┐ ┌──▼────┐ ┌───────────▼──┐ ┌─────────▼──┐
│Ledger │ │Settle │ │ Notification │ │ Reporting  │
│Service│ │Service│ │   Service    │ │  Service   │
└───────┘ └───────┘ └──────────────┘ └────────────┘
    │
┌───▼──────────┐
│Third-Party   │
│   Service    │
└──────────────┘
```

## Services

### 1. **API Gateway** (Port: 4004)
- Central entry point for all client requests
- Routes requests to appropriate microservices
- Implements JWT token validation
- Handles cross-cutting concerns (authentication, routing, load balancing)

### 2. **Auth Service** (Port: 4005)
- User authentication and authorization
- JWT token generation and validation
- User management and security

### 3. **Payment Service**
- Handles incoming payment requests
- Payment validation and authorization
- Transaction lifecycle management
- Payment processing logic

### 4. **Transaction Service**
- Transaction record management
- Transaction history and tracking
- Transaction status updates

### 5. **Merchant Service**
- Merchant account management
- Merchant registration and onboarding
- Merchant profile management

### 6. **Ledger Service**
- Financial ledger management
- Account balance tracking
- Double-entry bookkeeping

### 7. **Settlement Service**
- Settlement processing
- Fund transfers and reconciliation
- Settlement reporting

### 8. **Notification Service**
- Email and SMS notifications
- Payment status notifications
- Alert management

### 9. **Reporting Service**
- Financial reports generation
- Transaction analytics
- Business intelligence

### 10. **Third-Party Service**
- Integration with external payment processors
- Third-party API management
- Payment gateway integrations

## Technology Stack

- **Java**: 21
- **Spring Boot**: 3.5.6
- **Spring Cloud Gateway**: 2024.0.0
- **Spring Security**: For authentication and authorization
- **Maven**: Build and dependency management
- **Lombok**: For reducing boilerplate code
- **Docker**: Containerization support

## Prerequisites

Before running this project, ensure you have the following installed:

- **Java Development Kit (JDK)**: Version 21 or higher
- **Maven**: Version 3.6+
- **Docker** (optional): For containerized deployment
- **IDE**: IntelliJ IDEA, Eclipse, or VS Code with Java extensions

## Getting Started

### 1. Clone the Repository

```bash
git clone <repository-url>
cd payment-gateway
```

### 2. Build the Project

Build all services using Maven:

```bash
# Build all services
mvn clean install

# Or build a specific service
cd api-gateway
mvn clean install
```

### 3. Run Services

#### Option 1: Run Individual Services

Each service can be run independently:

```bash
# Run API Gateway
cd api-gateway
mvn spring-boot:run

# Run Auth Service
cd auth-service
mvn spring-boot:run

# Run Payment Service
cd payment-sevice
mvn spring-boot:run

# ... and so on for other services
```

#### Option 2: Docker Deployment

Build and run using Docker:

```bash
# Build Docker image for API Gateway
cd api-gateway
docker build -t api-gateway:latest .

# Run the container
docker run -p 4004:4004 api-gateway:latest
```

### 4. Service Ports

Default ports for each service:

- **API Gateway**: 4004
- **Auth Service**: 4005
- **Payment Service**: 400 (as configured in gateway routes)
- Other services: Check individual `application.properties` files

## Authentication

The API Gateway implements JWT token validation. To access protected endpoints:

1. Authenticate with the Auth Service to obtain a JWT token
2. Include the token in the `Authorization` header:
   ```
   Authorization: Bearer <your-jwt-token>
   ```

## 📡 API Routes

The API Gateway routes requests as follows:

- `/auth/**` → Auth Service
- `/api/payments/**` → Payment Service

Additional routes can be configured in `api-gateway/src/main/resources/application.yml`.

## Project Structure

```
payment-gateway/
├── api-gateway/              # API Gateway service
│   ├── src/
│   │   ├── main/
│   │   │   ├── java/
│   │   │   │   └── com/poa/apigateway/
│   │   │   │       ├── ApiGatewayApplication.java
│   │   │   │       ├── filter/
│   │   │   │       │   └── JwtValidationGatewayFilterFactory.java
│   │   │   │       └── exception/
│   │   │   │           └── GlobalExceptionHandler.java
│   │   │   └── resources/
│   │   │       ├── application.yml
│   │   │       └── application-prod.yml
│   │   └── test/
│   └── Dockerfile
├── auth-service/             # Authentication service
├── payment-sevice/           # Payment processing service
├── transaction-service/      # Transaction management service
├── merchant-service/         # Merchant management service
├── ledger-service/          # Ledger management service
├── settlement-service/       # Settlement processing service
├── notification-service/    # Notification service
├── reporting-service/        # Reporting service
└── third-party-service/      # Third-party integrations service
```

## Testing

Run tests for all services:

```bash
# Run all tests
mvn test

# Run tests for a specific service
cd <service-name>
mvn test
```

## 🔧 Configuration

Each service has its own configuration file located at:
```
<service-name>/src/main/resources/application.properties
```

For the API Gateway, configuration is in YAML format:
```
api-gateway/src/main/resources/application.yml
```

### Environment-Specific Configuration

- **Development**: `application.yml` or `application.properties`
- **Production**: `application-prod.yml` or `application-prod.properties`

## Development Guidelines

1. **Code Style**: Follow Java coding conventions and Spring Boot best practices
2. **Security**: Always validate JWT tokens for protected endpoints
3. **Error Handling**: Use the global exception handler in the API Gateway
4. **Logging**: Implement proper logging for debugging and monitoring
5. **Testing**: Write unit and integration tests for all services

## Contributing

1. Create a feature branch from `main`
2. Make your changes
3. Write/update tests
4. Ensure all tests pass
5. Submit a pull request

## License

[Specify your license here]

## Authors

- **k.mirkamali** - Initial work

## Related Documentation

- [Spring Boot Documentation](https://spring.io/projects/spring-boot)
- [Spring Cloud Gateway Documentation](https://spring.io/projects/spring-cloud-gateway)
- [Spring Security Documentation](https://spring.io/projects/spring-security)

## Support

For issues, questions, or contributions, please open an issue in the repository.

---

**Note**: This is a microservices-based system. Ensure all required services are running before making API calls through the gateway.

