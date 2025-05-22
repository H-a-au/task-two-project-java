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
   

2. **Resolved Postman 404 Errors**
   

3. **Fixed Port Conflicts**
   

4. **Addressed 500 Internal Server Error**
 
5. **Added Custom Exception Handling**
   
6. **Integrated Swagger UI**
 

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
