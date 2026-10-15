# AutoLoc API

Backend REST API for **AutoLoc**, a vehicle rental management system.
Project developed for the UP ASI (Architecture des Systèmes d'Information) course at ESPRIT, Atelier 1.

## Current status

First commit: project skeleton and first JPA entity.

- Spring Boot + Maven project initialized
- MySQL connection configured
- Entity `Vehicule` with enums `StatutVehicule` and `CategorieVehicule`
- Database schema generated automatically by Hibernate at startup

Associations, services, controllers and DTOs will be added in the following workshops.

## Tech stack

- Java 17
- Spring Boot (Web, Data JPA, Validation, DevTools)
- Hibernate / JPA
- MySQL
- Lombok
- Maven

## Prerequisites

- JDK 17 or higher
- Maven (or the Maven wrapper included in the project)
- MySQL server running on `localhost:3306`
- IntelliJ IDEA with the Lombok plugin and annotation processing enabled

## Configuration

Edit `src/main/resources/application.properties`:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/archisi
spring.datasource.username=root
spring.datasource.password=

spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
```


Note: `ddl-auto=update` is intended for development only.

## Run the application

```bash
mvn spring-boot:run
```

Or run the main application class from IntelliJ IDEA.
On success, the console shows `Started ... in ... seconds` and the Hibernate log shows `create table vehicule`.

## Project structure

```
src/main/java/tn/esprit/.../
├── domain        JPA entities and enums
├── repository    Spring Data JPA repositories
├── service       Business logic
└── web
    ├── controller   REST controllers
    └── dto          Data transfer objects
```

## Domain model (Vehicule)

| Field            | Type              | Constraints               |
|------------------|-------------------|---------------------------|
| idVehicule       | Long              | Primary key, auto-generated |
| immatriculation  | String            | Not null, unique          |
| marque           | String            | Not null                  |
| modele           | String            | Not null                  |
| categorie        | CategorieVehicule | Not null                  |
| tarifJournalier  | BigDecimal        | Not null                  |
| statut           | StatutVehicule    | Not null                  |

## Author

Kacem Mabrouki, ESPRIT, Cycle d'Ingénieur
