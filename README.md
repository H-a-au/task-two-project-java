# Spring Boot REST API Project

This project is a Spring Boot application that provides a REST API for managing products, with endpoints for creating and retrieving products. Below is a concise overview of the development and troubleshooting process to reach the current state.

## Project Overview
- **Artifact**: `demo`
- **Group ID**: `com.example`
- **Spring Boot Version**: 3.4.5
- **Java Version**: initially 24
- **Endpoints**:
  - `POST /api/v1/products`: Create a product
  - `GET /api/v1/products/{id}`: Retrieve a product by ID
- **Tools**: Maven, Git Bash (Windows), Postman, Swagger UI

## Development and Troubleshooting Steps

1. **Initial Setup**
   - Created a Spring Boot project with `spring-boot-starter-web`, `spring-boot-starter-data-jpa`, `h2`, and `devtools`.
   - Defined `ProductController`, `ProductService`, and `ProductRepository` with an in-memory `HashMap` storage.
   - Set `server.port=8081` in `application.properties`.

2. **Resolved Postman 404 Errors**
   - Encountered "404 Not Found" and "No static resource" errors in Postman for `/api/v1/products`.
   - Added `FirstRestApiSpringApplication` as the main class in `pl.edu.vistula.firstrestapispring`.
   - Configured `pom.xml` with `spring-boot-maven-plugin` and `<mainClass>pl.edu.vistula.firstrestapispring.FirstRestApiSpringApplication</mainClass>`.
   - Adjusted file hierarchy and rebuilt with `mvn clean install`.
   - Tested with a GET `/test` endpoint to confirm controller scanning.

3. **Fixed Port Conflicts**
   - Identified port 8081 conflicts in Git Bash using `netstat -aon | grep :8081`.
   - Terminated conflicting processes with `cmd //c taskkill /PID <PID> /F` in Git Bash as admin.

4. **Addressed 500 Internal Server Error**
   - Added a GET `/api/v1/products/{id}` endpoint, triggering a 500 error due to unhandled `NoSuchElementException`.
   - Updated `ProductService` to use `orElseThrow` with a custom message.
   - Implemented exception handling in `ProductController` to return 404 for missing products.

5. **Added Custom Exception Handling**
   - Created `ProductNotFoundException` and `ProductExceptionSupplier` in `pl.edu.vistula.firstrestapispring.product.support.exception`.
   - Integrated them into `ProductService` to throw `ProductNotFoundException` when a product is not found.
   - Resolved compilation errors by correcting package declarations and imports.

6. **Integrated Swagger UI**
   - Added `springdoc-openapi-starter-webmvc-ui` dependency to `pom.xml`.
   - Attempted to access `http://localhost:8081/swagger-ui/index.html`
   - Updated `pom.xml` to manage OpenAPI version via parent POM.
   - Added `SwaggerConfig` to ensure resource serving, rebuilt, and tested.

## Current Status
- **API Functionality**: POST and GET endpoints work in Postman after exception handling fixes.
- **Swagger UI**
- **H2 Database**: works as intended

## How to Run
1. Ensure JDK 21 is installed and set as `JAVA_HOME`.
2. Build the project: `mvn clean install` in Git Bash.
3. Run the app: `java -jar target/demo-0.0.1-SNAPSHOT.jar`.
4. Test endpoints in Postman:
   - POST `http://localhost:8081/api/v1/products` with `{"name": "Test Product"}`.
   - GET `http://localhost:8081/api/v1/products/1`.
5. Access Swagger UI at `http://localhost:8081/swagger-ui/index.html` 

## Troubleshooting Tips
- Check logs for exceptions if errors persist.
- Verify package structure (e.g., `pl.edu.vistula.firstrestapispring.product.support.exception`).
- Use `netstat -aon | grep :8081` to ensure port availability.

## Dependencies
- `spring-boot-starter-web`
- `spring-boot-starter-data-jpa`
- `h2`
- `springdoc-openapi-starter-webmvc-ui`

## Screenshots
![http___localhost_8081_api_v1_products - My Workspace 5_21_2025 2_23_59 PM](https://github.com/user-attachments/assets/04b708d4-7fbd-4d55-ba6f-5e1837f2f39a)

- GET Endpoint running with Error 500:
![http___localhost_8081_api_v1_products_1 - My Workspace 5_21_2025 4_04_57 PM](https://github.com/user-attachments/assets/f82a7fb5-da08-46c4-b49e-0186fc5bf30d)

- H2 Database:
![h2](https://github.com/user-attachments/assets/331cbd65-db26-401d-b896-11b4128391b7)

---
