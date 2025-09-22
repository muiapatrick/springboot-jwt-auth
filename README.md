# Spring Boot JWT Authentication

A simple Spring Boot application demonstrating how to implement JWT (JSON Web Token) based authentication to secure REST APIs without relying on server-side sessions.

This project is built to showcase backend development skills, Spring Security configuration, and token-based authentication commonly used in modern microservices and web applications.

---

## 🚀 Features
- 🔒 User Authentication with JWT (login endpoint issues token).
- 🚫 Stateless Security – no server-side session storage.
- 🛡️ Role-Based Authorization (e.g., USER, ADMIN).
- 🔑 Custom Authentication Filter to validate tokens.
- 🧑‍💻 Spring Security 6 integration with SecurityFilterChain.
- 💾 BCrypt Password Hashing for secure password storage.
- 📂 Modular structure – easy to extend and integrate.

---

## 🛠️ Tech Stack
- Java 17+
- Spring Boot 3
- Spring Security 6
- JWT (jjwt)
- Maven

---

## ⚙️ Getting Started

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/muiapatrick/springboot-jwt-auth.git
cd springboot-jwt-auth
```

### 2️⃣ Build and Run the App
Using Maven Wrapper:
```bash
./mvnw spring-boot:run
```

Or, package and run the jar:
```bash
./mvnw clean package
java -jar target/*.jar
```

The application will start on:  
👉 `http://localhost:8080`

---

### 3️⃣ Test the API Endpoints

#### 🔑 Authenticate (Login)
Request a JWT token by sending credentials:
```bash
curl -X POST http://localhost:8080/auth/login \
  -H "Content-Type: application/json" \
  -d '{"username":"user","password":"password"}'
```

Response:
```json
"eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
```

#### 🔒 Access a Secured Endpoint
Use the token in the `Authorization` header:
```bash
curl -X GET http://localhost:8080/api/hello \
  -H "Authorization: Bearer <your-jwt-token>"
```

Response:
```json
"Hello, secured world!"
```

---

### 4️⃣ Register a New User
If you don’t have a user yet, create one via the registration endpoint:
```bash
curl -X POST http://localhost:8080/auth/register \
  -H "Content-Type: application/json" \
  -d '{
    "username": "newuser",
    "password": "newpassword",
    "roles": ["USER"]
  }'
```

Successful response:
```json
{
  "id": 1,
  "username": "newuser",
  "roles": ["USER"]
}
```

Now you can use these credentials to **login** and get a JWT token (Step 3).

---



