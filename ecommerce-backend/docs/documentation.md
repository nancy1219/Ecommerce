# Complete E-commerce Backend System

## Project Overview
This project is a full-featured e-commerce backend built with Spring Boot. It provides REST APIs for a product catalog, category management, order processing, and user administration. The backend leverages modern practices including Spring Data JPA, Hibernate, PostgreSQL, and Spring Security for authentication.

## Setup Instructions

### Prerequisites
- Java 17
- Maven 3.8+
- PostgreSQL 14+

### Installation and Configuration
1. Clone the repository and navigate to the root directory `ecommerce-backend`.
2. Configure your PostgreSQL database in `src/main/resources/application.properties`. Ensure the database `ecommerce` exists.
   ```properties
   spring.datasource.url=jdbc:postgresql://localhost:5432/ecommerce
   spring.datasource.username=postgres
   spring.datasource.password=yourpassword
   ```
3. Run the application using Maven:
   ```bash
   mvn spring-boot:run
   ```
4. The server will start on port `8080`.

## Code Structure
```
ecommerce-backend/
├── pom.xml
├── src/main/resources/
│   └── application.properties       # Main configuration
└── src/main/java/com/ecommerce/
    ├── ECommerceApplication.java    # Main application class
    ├── config/                      # Configuration classes (e.g., ModelMapper)
    ├── model/                       # JPA Entities (Product, Category)
    ├── dto/                         # Data Transfer Objects
    ├── repository/                  # Spring Data JPA Repository Interfaces
    ├── service/                     # Business Logic Layer
    ├── controller/                  # REST API Controllers Layer
    ├── exception/                   # Exception handling
    └── security/                    # Security configurations
```

## Technical Details

### Architecture
The project follows a standard layered architecture:
- **Presentation Layer (Controllers):** Handles incoming HTTP requests and standardizes responses. `ProductController` provides endpoints.
- **Service Layer (Services):** Contains the core business logic. DTO mapping happens here using `ModelMapper`. `ProductService` orchestrates product persistence and retrieval.
- **Data Access Layer (Repositories):** Uses Spring Data JPA. `ProductRepository` extends `JpaRepository` for ready-to-use CRUD and pagination features.

### Algorithms and Data Structures
- **Pagination and Sorting:** Handled native via `Pageable` in Spring Data. This enables scalable retrieval of product lists.
- **Entities:** JPA entities map to table properties using relationships like `@ManyToOne` and `@OneToMany`. Constraints use `javax.validation` to prevent corrupt data insertion.

### Testing Evidence
To run tests, execute `mvn test`. The project expects unit tests for the service layer mocking the repository using Mockito, and integration tests confirming the database interactions and controller paths.

## API Documentation

### Product APIs
- `GET /api/products` : Fetches a paginated list of products.
  - **Params:** `page` (default: 0), `size` (default: 10)
  - **Response:** `200 OK` with JSON array of products.
- `GET /api/products/{id}` : Gets a product by ID.
  - **Response:** `200 OK` with Product object or `404 Not Found`.
- `POST /api/products` : Creates a new product.
  - **Request Body:** JSON object representing ProductDTO
  - **Response:** `201 Created` with created Product.

### Security
Basic Spring Security setup is prepared via `spring-boot-starter-security`. Future integrations should include JWT validation filters and role-based endpoints (`hasRole('ADMIN')` for state-changing endpoints).
