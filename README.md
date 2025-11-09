# 🍄 ShroomShare — Backend (Spring Boot)

This repository contains the backend for **ShroomShare**, a full-stack web application built during the [**Vali IT!**](https://vali-it.ee/) Fullstack Development Program (2025).  
The project was created collaboratively by a team of three participants over a **three-week development sprint** as part of the program’s final assignment.

---

## 🧩 Project Overview

**ShroomShare** is an information system that allows users to discover, share, and discuss mushroom-picking locations across Estonia.  
The backend provides RESTful APIs for the Vue-based frontend, handling all data persistence, business logic, and user management.

The application supports complete **CRUD operations** for key entities such as:
- Users & profiles  
- Shrooms (mushroom entries)  
- Locations & maps  
- Comments & favorites  
- Images for shrooms and locations  

It also includes authentication, distance-calculation utilities, and structured error handling.

---

## 👥 Team Members

- [@InnarM](https://github.com/InnarM)  
- [@kristiinalokko](https://github.com/kristiinalokko)  
- [@mihkelaan](https://github.com/mihkelaan)

---

## ⚙️ Tech Stack

- **Java 17**  
- **Spring Boot 3**  
- **Spring Data JPA**  
- **PostgreSQL**  
- **REST API**  
- **Maven / Gradle**  
- **MapStruct** for DTO mapping  

---

## 🗃️ Database Structure

The `/database` folder contains SQL scripts for initializing and populating the project schema:

| File | Description |
|------|--------------|
| `1_reset_database.sql` | Creates a clean schema for the application |
| `2_create.sql` | Contains DDL statements generated from Vertabelo |
| `3_import.sql` | Optional data inserts for testing |

To initialize your local database:

```bash
psql -U postgres -f database/1_reset_database.sql
psql -U postgres -f database/2_create.sql
psql -U postgres -f database/3_import.sql
```

---

## 🚀 Getting Started

### Clone the repository
```bash
git clone https://github.com/<your-repo-name>.git
cd shroomshareback
```

### Configure the database connection
Edit `src/main/resources/application.properties`:
```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/shroomshare
spring.datasource.username=postgres
spring.datasource.password=yourpassword
```

### Run the backend
```bash
./mvnw spring-boot:run
```

The API will start on **http://localhost:8080**

---

## 🧠 Main Features

- RESTful API for all entities  
- Authentication / login / registration endpoints  
- Distance calculation for nearby shroom locations  
- Centralized exception handling via `RestExceptionHandler`  
- DTO-based communication with mappers (MapStruct)  
- Layered architecture:  
  `controller → service → persistence → database`

---

## 🧪 Example Endpoints

| Method | Endpoint | Description |
|---------|-----------|-------------|
| `POST` | `/register` | Create a new user |
| `POST` | `/login` | Authenticate user |
| `GET` | `/shrooms` | Retrieve all shrooms |
| `GET` | `/locations` | Retrieve available map locations |
| `POST` | `/comments` | Add a comment to a shroom |
| `GET` | `/favorites/{userId}` | List user favorites |

*(Endpoints may vary depending on frontend integration.)*

---

## 💡 About Vali IT!

[**Vali IT!**](https://vali-it.ee/) is an intensive Estonian full-stack development training program focusing on practical, project-based learning.  
Participants learn Java, Spring Boot, databases, and modern frontend development (Vue.js) while working in teams to build real-world applications.

---

## 🏁 Project Status

This repository represents the **MVP version** of ShroomShare.  
Due to the limited development timeframe (three weeks), some planned “nice-to-have” features may still be in progress.

---

## 📄 License

This project was developed for educational purposes as part of the **Vali IT! Fullstack Developer Program (2025)** and is not intended for commercial use.
