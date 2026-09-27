# Social Media API

A simple RESTful **Social Media backend** built with **Spring Boot 3**, **Spring Data JPA**, and an in-memory **H2 database**. It models users, profiles, posts, and groups, and exposes basic CRUD endpoints for managing users.

## ✨ Features

- Create, fetch, and delete social media users
- JPA entity relationships:
  - `SocialUser` ⇄ `SocialProfile` (One-to-One)
  - `SocialUser` ⇄ `Post` (One-to-Many)
  - `SocialUser` ⇄ `SocialGroup` (Many-to-Many)
- In-memory H2 database with sample data pre-loaded on startup
- H2 web console enabled for quick inspection of data

## 🛠️ Tech Stack

- **Java 17**
- **Spring Boot 3.2.5**
- **Spring Data JPA**
- **Spring Web (REST)**
- **H2 Database** (in-memory)
- **Lombok**
- **Maven**

## 📁 Project Structure

```
media/
├── src/
│   ├── main/
│   │   ├── java/com/social/media/
│   │   │   ├── controllers/      # REST controllers
│   │   │   ├── models/           # JPA entities
│   │   │   ├── repositories/     # Spring Data repositories
│   │   │   ├── services/         # Business logic
│   │   │   ├── DataInitializer.java   # Seeds sample data on startup
│   │   │   └── MediaApplication.java  # Application entry point
│   │   └── resources/
│   │       └── application.properties
│   └── test/
│       └── java/com/social/media/MediaApplicationTests.java
└── pom.xml
```

## 🚀 Getting Started

### Prerequisites

- Java 17+
- Maven (or use the included `mvnw` wrapper)

### Run the application

```bash
# Clone the repository
git clone https://github.com/<your-username>/social-media-api.git
cd social-media-api/media

# Run using the Maven wrapper
./mvnw spring-boot:run
```

The application starts on **http://localhost:9090**.

### H2 Console

Access the H2 database console at:

```
http://localhost:9090/h2-console
```

Use the JDBC URL configured in `application.properties`:

```
jdbc:h2:mem:test
```

## 📡 API Endpoints

| Method | Endpoint                  | Description              |
|--------|----------------------------|---------------------------|
| GET    | `/social/users`            | Get all users              |
| POST   | `/social/users`            | Create a new user           |
| DELETE | `/social/users/{userId}`   | Delete a user by ID         |

### Example: Create a user

```bash
curl -X POST http://localhost:9090/social/users \
  -H "Content-Type: application/json" \
  -d '{}'
```

### Example: Get all users

```bash
curl http://localhost:9090/social/users
```

### Example: Delete a user

```bash
curl -X DELETE http://localhost:9090/social/users/1
```

## 🗄️ Data Model

- **SocialUser** – core user entity, linked to a profile, posts, and groups
- **SocialProfile** – one-to-one profile info (e.g., description) for a user
- **Post** – belongs to a single user
- **SocialGroup** – many-to-many group membership between users

Sample data (3 users, 2 groups, 3 posts, 3 profiles) is automatically seeded on application startup via `DataInitializer`.

## 🧪 Running Tests

```bash
./mvnw test
```
