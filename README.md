# User Service - University Social Network

This microservice is part of the University Social Network project, handling user management including registration, authentication, and profile updates. It's specifically designed for Ecuadorian university students, validating institutional email addresses.

## Features

- User registration with institutional email validation (.edu.ec)
- User authentication
- Profile information updates
- Password encryption
- Input validation
- Exception handling
- CORS configuration

## Tech Stack

- Java 17
- Spring Boot 3.2.2
- Spring Security
- Spring Data JPA
- PostgreSQL
- Maven
- Lombok
- JWT for authentication

## Prerequisites

- JDK 17 or higher
- Maven 3.6 or higher
- PostgreSQL 12 or higher
- IDE (IntelliJ IDEA recommended)

## Database Configuration

Create a PostgreSQL database:

```sql
CREATE DATABASE unisocial;
```

The application will automatically create the required tables through JPA.

## Project Setup

1. Clone the repository:
```bash
git clone https://github.com/your-username/user-service.git
cd user-service
```

2. Configure database connection in `application.yml`:
```yaml
spring:
  datasource:
    url: jdbc:postgresql://localhost:5432/unisocial
    username: your_username
    password: your_password
```

3. Build the project:
```bash
mvn clean install
```

4. Run the application:
```bash
mvn spring-boot:run
```

The service will start on `http://localhost:8081`

## API Endpoints

### Register User
```http
POST /api/users/register
Content-Type: application/json

{
    "username": "testuser",
    "email": "user@university.edu.ec",
    "password": "password123"
}
```

### Login User
```http
POST /api/users/login
Content-Type: application/json

{
    "email": "user@university.edu.ec",
    "password": "password123"
}
```

### Update User
```http
PUT /api/users/{userId}
Content-Type: application/json

{
    "username": "newUsername",
    "password": "newPassword123"
}
```

## Project Structure

```
src/main/java/com/unisocial/userservice/
├── config/           # Configuration classes
├── controller/       # REST controllers
├── dto/             # Data Transfer Objects
├── exception/       # Custom exceptions and handlers
├── model/           # Entity classes
├── repository/      # JPA repositories
└── service/         # Business logic
```

## Security

- BCrypt password encryption
- Email domain validation
- Input validation
- CORS configuration
- Spring Security implementation

## Testing

Run the tests using:
```bash
mvn test
```

## Error Handling

The service includes global exception handling for:
- Invalid input data
- User already exists
- User not found
- Authentication failures
- Validation errors

## Development

To contribute to this project:

1. Create a feature branch:
```bash
git checkout -b feature/your-feature-name
```

2. Commit your changes:
```bash
git commit -m "feat: description of your changes"
```

3. Push to your branch:
```bash
git push origin feature/your-feature-name
```

4. Create a Pull Request

## Environment Variables

Configure these environment variables or update `application.yml`:

- `DB_URL`: Database URL
- `DB_USERNAME`: Database username
- `DB_PASSWORD`: Database password
- `SERVER_PORT`: Application port (default: 8081)

## Logging

Logging is configured in `application.yml`:
```yaml
logging:
  level:
    root: INFO
    com.unisocial: DEBUG
```

## Monitoring

The service includes Spring Boot Actuator for monitoring:
- Health check: `/actuator/health`
- Metrics: `/actuator/metrics`
- Info: `/actuator/info`
