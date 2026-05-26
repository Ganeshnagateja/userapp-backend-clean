# User Management REST API

A backend REST API built with **Java 17** and **Spring Boot 4**, connected to **MongoDB Atlas** for data storage. Follows a clean layered architecture and is containerised with Docker.

---

## Tech Stack

| Layer | Technology |
|---|---|
| Language | Java 17 |
| Framework | Spring Boot 4.0.2 |
| Database | MongoDB Atlas |
| Architecture | Controller → Service → Repository |
| Containerisation | Docker |
| Deployment | Render |

---

## Project Structure

```
src/
└── main/
    └── java/com/example/userapp/
        ├── controller/
        │   └── UserController.java      # REST endpoints
        ├── service/
        │   └── UserService.java         # Business logic
        ├── repository/
        │   └── UserRepository.java      # MongoDB operations
        ├── model/
        │   └── User.java                # User data model
        ├── config/
        │   └── WebConfig.java           # CORS configuration
        └── UserappApplication.java      # Entry point
```

---

## API Endpoints

### Get All Users
```
GET /api/users
```
**Response:**
```json
[
  {
    "id": "665abc123def456",
    "name": "Ganesh",
    "email": "ganesh@example.com",
    "phone": "9876543210"
  }
]
```

### Create a User
```
POST /api/users
Content-Type: application/json
```
**Request Body:**
```json
{
  "name": "Ganesh",
  "email": "ganesh@example.com",
  "phone": "9876543210",
  "password": "yourpassword"
}
```
**Response:** Returns the saved user object with generated `id`.

---

## Run Locally

### Prerequisites
- Java 17+
- Maven
- MongoDB Atlas account (free tier works)

### 1. Clone the repo
```bash
git clone https://github.com/Ganeshnagateja/userapp-backend.git
cd userapp-backend
```

### 2. Set environment variable

**Windows:**
```bash
set MONGODB_URI=mongodb+srv://<username>:<password>@cluster0.mongodb.net/?appName=Cluster0
```

**Mac/Linux:**
```bash
export MONGODB_URI=mongodb+srv://<username>:<password>@cluster0.mongodb.net/?appName=Cluster0
```

Or create a `.env` file (never commit this):
```
MONGODB_URI=mongodb+srv://<username>:<password>@cluster0.mongodb.net/?appName=Cluster0
```

### 3. Run the app
```bash
./mvnw spring-boot:run
```

API will be available at: `http://localhost:8080`

---

## Run with Docker

### Build the image
```bash
docker build -t userapp-backend .
```

### Run the container
```bash
docker run -p 8080:8080 -e MONGODB_URI=your_mongodb_uri userapp-backend
```

---

## Environment Variables

| Variable | Description |
|---|---|
| `MONGODB_URI` | MongoDB Atlas connection string |

Create a `.env.example` file locally (see `.env.example` in repo for reference). Never commit your actual `.env` file.

---

## How It Works

1. Client sends a request to a REST endpoint in `UserController`
2. Controller calls the appropriate method in `UserService`
3. `UserService` delegates data operations to `UserRepository`
4. `UserRepository` extends `MongoRepository` — handles all MongoDB queries
5. Response is returned as JSON

---

## What I Learned

- Setting up a Spring Boot project from scratch with Maven
- Designing a layered REST API architecture (Controller → Service → Repository)
- Connecting Spring Boot to MongoDB Atlas using `MongoRepository`
- Configuring CORS for cross-origin frontend requests
- Containerising a Java app with Docker and deploying on Render
- Managing secrets safely using environment variables

---

## Author

**Boddu Ganesh Naga Teja**
[LinkedIn](https://www.linkedin.com/in/ganesh-naga-teja-boddu-199953324/) • [GitHub](https://github.com/Ganeshnagateja)
