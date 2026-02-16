# Building a Spring Boot Microservice with In-Memory Database & Swagger

---
## IT22212504 - Rajapaksha R.P.D.T.

---
**Module:** Current Trends in Software Engineering (SE4010)  
**Lab:** DevOps Lab 3  
---
This project implements a simple **Spring Boot RESTful microservice** for managing products, using:

- Spring Boot
- Spring Web (REST APIs)
- Spring Data JPA
- H2 in-memory database
- Springdoc OpenAPI / Swagger UI for API documentation

It demonstrates basic **CRUD** operations with proper HTTP status codes and interactive API documentation.

---
## Features

- CRUD operations for Product entities (Create, Read, Update is not implemented, Delete)
- In-memory persistence using **H2 database**
- Automatic table creation via Hibernate
- H2 web console for database inspection
- Interactive API documentation via **Swagger UI**
- Proper REST response status codes (201, 200, 204, 404, etc.)
---
## Project Structure
```aiignore
product-service/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/sliit/product_service/
│   │   │       ├── Product.java                 # JPA Entity
│   │   │       ├── ProductRepository.java       # JPA Repository interface
│   │   │       ├── ProductController.java       # REST Controller with CRUD
│   │   │       └── ProductServiceApplication.java  # Main Spring Boot class
│   │   └── resources/
│   │       └── application.properties           # H2 + JPA + Swagger config
│   └── test/                                    # (tests not implemented in this lab)
├── pom.xml                                      # Maven dependencies & build config
└── README.md                                    # This file
```
---

## Technologies / Dependencies

| Dependency                          | Purpose                              |
|-------------------------------------|--------------------------------------|
| Spring Boot Starter Web             | REST API support                     |
| Spring Boot Starter Data JPA        | ORM / Repository abstraction         |
| H2 Database                         | In-memory database for development   |
| Springdoc OpenAPI Starter WebMVC UI | Swagger UI / OpenAPI 3 documentation |
---

## How to Run the Application

1. **Prerequisites**
    - Java 17+ (JDK)
    - Maven 3.6+
    - IntelliJ IDEA / VS Code / any Java IDE

2. **Clone the repository** (if needed)

   ```bash
   git clone https://github.com/DinithiTR/IT22212504_CTSE_Lab3.git
   cd product-service
   
3. **Build the project**
    ```bash
   mvn clean install

4. **Run the application**
    ```bash
   mvn spring-boot:run
or run **ProductServiceApplication.java** directly from your IDE.

---
## H2 Database Configuration

The application uses an in-memory H2 database.

### application.properties

```properties
spring.application.name=product-service

spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.driverClassName=org.h2.Driver
spring.datasource.username=sa
spring.datasource.password=

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

spring.h2.console.enabled=true
```
### H2 Console Login Details

* **JDBC URL:** jdbc:h2:mem:testdb
* **Username:** sa
* **Password:** (empty)

---

## Product Entity

The Product entity contains:

* `id` (Long) – Primary Key (Auto Generated)
* `name` (String)
* `price` (double)

---
## Expose API documentation using Swagger UI
**Steps:**

1. Add `springdoc-openapi` dependency
2. Start the application
3. Access Swagger UI at:  
   http://localhost:8080/swagger-ui.html
4. Test APIs using Swagger UI

---

## Access the Application

| Endpoint                                | Description                                |
|-----------------------------------------|--------------------------------------------|
| http://localhost:8080/h2-console        | H2 Database Console                        |
| http://localhost:8080/swagger-ui.html   | Swagger UI – Interactive API documentation |
| http://localhost:8080/v3/api-docs       | Raw OpenAPI JSON specification             |

---

## API Endpoints (via Swagger)

| Method | Endpoint            | Description                        | Status Codes   |
|--------|---------------------|------------------------------------|----------------|
| POST   | `/products`         | Create a new product               | 200            |
| GET    | `/products`         | Get all products                   | 200            |
| GET    | `/products/{id}`    | Get product by ID                  | 200 / 404      |
| DELETE | `/products/{id}`    | Delete product by ID               | 204 / 404      |

**Example POST request body (JSON):**

```json
{
  "name": "Laptop",
  "price": 999.99
}
```
---
## Assignment Requirements Covered

* Spring Boot project created using Spring Initializr
* Product entity created
* JpaRepository implemented
* CRUD REST endpoints implemented
* H2 database configured and verified
* Swagger UI enabled
* Project uploaded to GitHub
