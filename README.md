# Spring Boot Thymeleaf Application

A Spring Boot 3.x web application using Thymeleaf, MyBatis, and PostgreSQL.

## Tech Stack

- **Framework**: Spring Boot 3.5.7 (Spring MVC, Spring JDBC)
- **Server**: Embedded Tomcat (Spring Boot)
- **Database**: PostgreSQL 18
- **Build**: Gradle 9.2.0
- **View**: Thymeleaf
- **ORM**: MyBatis 3.0.3

## Getting Started

### Prerequisites

- JDK 21
- Docker & Docker Compose (for PostgreSQL)
- Gradle 9.2.0 (or use included gradlew)

### Quick Start

1. Start PostgreSQL database:

```bash
docker-compose up -d
```

2. Run the application:

```bash
./gradlew bootRun
```

3. Access the application:
```
http://localhost:8080
```

### Development Mode

Spring Boot DevTools is included for automatic restart and live reload:

- Code changes automatically trigger application restart
- Template changes (Thymeleaf) are hot-reloaded without restart
- Static resources are served with cache disabled

Simply edit your code and refresh the browser!

### Production Build

Build the executable JAR:

```bash
./gradlew build
```

Run the JAR file:

```bash
java -jar build/libs/spring-boot-thymeleaf-1.0.0.jar
```

Or build a WAR file for deployment:

```bash
./gradlew war
```

The WAR file will be generated at `build/libs/app.war`

## Available Gradle Tasks

- `./gradlew bootRun` - Run the Spring Boot application
- `./gradlew build` - Build the project and create JAR file
- `./gradlew war` - Build WAR file for external Tomcat deployment
- `./gradlew clean` - Clean build directory
- `./gradlew test` - Run tests

## Docker Services

- **PostgreSQL**: localhost:5432
  - Database: `spring-framework-db`
  - User: `user`
  - Password: `password`

## Project Structure

```
src/
├── main/
│   ├── java/com/example/
│   │   ├── controller/     # Spring MVC Controllers
│   │   ├── service/        # Business Logic
│   │   ├── mapper/         # MyBatis Mappers
│   │   ├── model/          # Domain Models
│   │   └── config/         # Spring Configuration
│   └── resources/
│       ├── templates/      # Thymeleaf Templates
│       ├── mappers/        # MyBatis XML Mappers
│       └── application.yml # Application Configuration
```

## Configuration

Application configuration is in `src/main/resources/application.yml`:

- Database connection (can be overridden with environment variables)
- Thymeleaf settings (cache disabled for development)
- MyBatis configuration
- Server port (default: 8080)

## Development Notes

- Spring Boot DevTools provides automatic restart on code changes
- Thymeleaf cache is disabled in development for hot reload
- Database connection settings can be overridden via environment variables:
  - `DB_HOST`, `DB_PORT`, `DB_NAME`, `DB_USER`, `DB_PASSWORD`
- Init scripts in `init-scripts/` directory are automatically executed on PostgreSQL startup
- Templates are located in `src/main/resources/templates/`

## Stopping the Application

Stop the Spring Boot application: `Ctrl+C`

Stop the database:

```bash
docker-compose down
```