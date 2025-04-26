# Spring Boot JDBC with PostgreSQL Connection Demo

This project demonstrates a **simple Spring Boot application** that connects to a **PostgreSQL database** using **Spring's JDBC abstraction layer**.

The application retrieves and logs records from a `widgets` table.

## Technologies Used
- Java 17 
- Spring Boot
- Spring JDBC
- PostgreSQL
- Docker & Docker Compose

## Project Structure

- **`DatabaseApplication.java`** — Main application class
- **`application.properties`** — Database connection settings
- **`docker-compose.yml`** — Spins up a local PostgreSQL database
- **SQL scripts** — Create and populate the `widgets` table

## How to Run

### 1. Start PostgreSQL via Docker Compose

```bash
docker-compose up
```

This starts a **PostgreSQL** database container listening on **localhost:5431**.

### 2. Run the Spring Boot application

You can run it from your IDE or via command line:

```bash
./mvnw spring-boot:run
```

The application will connect to PostgreSQL, run a `SELECT * FROM widgets`, and log the output.

## Example Output

```
Datasource: HikariDataSource (PostgreSQL connection)
Widget: Widget A - Used for testing purposes.
Widget: Widget B - Designed for entertainment.
Widget: Widget C - Enhances productivity.
...
```

---

## Database Schema

The `widgets` table is created with the following structure:

```sql
CREATE TABLE widgets (
    id BIGINT PRIMARY KEY,
    name TEXT,
    purpose TEXT
);
```

Example records are inserted automatically using SQL scripts.

## Configuration Overview

The important Spring Boot properties (`src/main/resources/application.properties`) are:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5431/postgres
spring.datasource.username=postgres
spring.datasource.password=${POSTGRES_PASSWORD:password}
spring.datasource.driver-class-name=org.postgresql.Driver
spring.sql.init.mode=always
```

---

## Important Notes

- Make sure port **5431** is free before running Docker Compose.
- Default PostgreSQL user is `postgres` with password `password` (development only!).
- For production, always use **secure credentials** and **environment variables**.

## What This Project Shows

- Basic connection to **PostgreSQL** using **Spring JDBC**  
- Executing **simple queries** and **processing ResultSet**  
- Using **Docker** for local database setup  
- Configuring **Spring Boot** database properties

## Future Improvements

- Use `JdbcTemplate` with prepared statements.
- Add custom exception handling.
- Migrate to Spring Data JPA for more advanced CRUD operations.

---

# Conclusion

This project is a lightweight demonstration of connecting a **Spring Boot** application to a **PostgreSQL** database using **Spring JDBC** for simple data retrieval and logging.
