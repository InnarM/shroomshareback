# 🍄 ShroomShare — Backend (Spring Boot, Gradle)

This repository contains the backend for **ShroomShare**, a full‑stack web application built during the [**Vali IT!**](https://vali-it.ee/) Fullstack Development Program (2025).  
The project was created collaboratively by a team of three participants over a **three‑week development sprint** as part of the program’s final assignment.

---

## 🧩 Project Overview

**ShroomShare** is an information system that allows users to discover, share, and discuss mushroom‑picking locations across Estonia.  
The backend exposes RESTful APIs used by the Vue frontend, handling persistence, business logic, and authentication.

This service provides complete **CRUD** for the core domain and related media:

- Users & profiles
- Shrooms (mushroom entries)
- Locations & map data
- Comments & favorites
- Images for shrooms and locations

Utilities include distance calculations and centralized error handling.

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
- **Gradle** (wrapper included)
- **MapStruct** for DTO mapping

> Package root: `ee.valiit.shroomshareback`

---

## 📦 Notable Packages

```
controller/
  comment/         # CommentController (+ DTOs)
  favorite/        # FavoriteController (+ DTOs)
  location/        # LocationController (+ map & extended info DTOs)
  locationimage/   # LocationImageController
  login/           # LoginController
  maplocation/     # MapLocationController
  profile/         # ProfileController
  register/        # RegistrationController
  shroom/          # ShroomController (+ detailed/info DTOs)
  shroomimage/     # ShroomImageController
  shroomlocation/  # ShroomLocationController

persistence/       # Entities, repositories, mappers (MapStruct)
service/           # Business logic services
infrastructure/    # Exception handling, config, etc.
util/              # BytesConverter, DistanceCalculator
```

---

## 🗃️ Database

SQL scripts live under `/database`:

| File | Purpose |
|---|---|
| `1_reset_database.sql` | Creates/clears schema |
| `2_create.sql` | DDL generated from Vertabelo |
| `3_import.sql` | Optional seed inserts |

Initialize locally:

```bash
psql -U postgres -f database/1_reset_database.sql
psql -U postgres -f database/2_create.sql
psql -U postgres -f database/3_import.sql
```

Edit `src/main/resources/application.properties` as needed:

```properties
spring.datasource.url=jdbc:postgresql://localhost:5432/shroomshare
spring.datasource.username=postgres
spring.datasource.password=yourpassword
spring.jpa.hibernate.ddl-auto=validate
```

---

## 🚀 Getting Started (Gradle)

### Clone
```bash
git clone https://github.com/<your-backend-repo>.git
cd shroomshareback
```

### Run (dev)
```bash
./gradlew bootRun
```

### Build (jar)
```bash
./gradlew clean build
```

API base URL: **http://localhost:8080**

---

## 🌐 Companion Frontend

Frontend repository: **ShroomShare — Frontend (Vue.js)**  
👉 https://github.com/InnarM/shroomsharefront

---

## 🧠 Main Features

- RESTful API for shrooms, locations, images, comments, favorites, users
- Authentication (login/registration)
- DTO mapping with MapStruct
- Centralized exception handling (`RestExceptionHandler`)
- Distance calculation helpers
- Clear layered architecture: `controller → service → persistence → database`

---

## 🧪 Example Endpoint Groups

> Exact paths may vary with versioning and integration.

| Area | Typical routes (examples) |
|---|---|
| Auth | `POST /register`, `POST /login` |
| Shrooms | `GET /shrooms`, `GET /shrooms/{id}`, `POST /shrooms`, `PUT /shrooms/{id}`, `DELETE /shrooms/{id}` |
| Locations | `GET /locations`, `GET /locations/{id}` |
| Map Locations | `POST /map-locations` (query by bounds/filters) |
| Comments | `GET /comments?shroomId=...`, `POST /comments` |
| Favorites | `GET /favorites/{userId}`, `POST /favorites`, `DELETE /favorites/{id}` |
| Shroom Images | `POST /shroom-image`, `GET /shroom-image/{id}` |
| Location Images | `POST /location-image`, `GET /location-image/{id}` |
| Profiles | `GET /profile/{userId}`, `PUT /profile/{userId}` |

---

## 💡 About Vali IT!

[**Vali IT!**](https://vali-it.ee/) is an intensive Estonian full‑stack development training program focused on practical, project‑based learning. Participants build real applications in teams using **Java/Spring** on the backend and **Vue.js** on the frontend.

---

## 🏁 Project Status

This repository represents the **MVP version** of ShroomShare.  
Due to the three‑week timeframe, some planned “nice‑to‑have” features may still be in progress.

---

## 📄 License

Created for educational purposes as part of the **Vali IT! Fullstack Developer Program (2025)** and not intended for commercial use.
