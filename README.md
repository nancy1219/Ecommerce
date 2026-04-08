# Spring Boot E-Commerce Backend

A comprehensive RESTful backend for an e-commerce platform built on Java 17 and Spring Boot 2.7.0.

## Implementation Details

- **Database Framework:** Spring Data JPA with Hibernate. Data mapped via standard `javax.persistence` annotations.
- **Validation:** Utilizes Spring Validation (`@Valid`, `@NotBlank`, `@Size`, etc.) to enforce strict domain constraints before touching the database.
- **DTO Pattern:** The application explicitly uses DTOs (`ProductDTO`) to separate database schema and network models. The entity-to-DTO conversion is handled via `ModelMapper`.

Please refer to `docs/documentation.md` for a complete breakdown of endpoints, architecture, and setup instructions.
