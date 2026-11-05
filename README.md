<div align="center">
  <h1>📋 RollCall API</h1>
  <p><strong>A REST API for managing student records.</strong></p>

  ![Java](https://img.shields.io/badge/Java-18-ED8B00?logo=openjdk&logoColor=white)
  ![Spring Boot](https://img.shields.io/badge/Spring_Boot-2.7-6DB33F?logo=springboot&logoColor=white)
  ![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white)
</div>

## About

Add, view, update and delete students with a simple REST API, built with Spring Boot and PostgreSQL. Each student's email has to be unique, and their age is worked out from their date of birth.

## Endpoints

Base URL: `http://localhost:8080/api/v1/student`

| Method | Path | What it does |
| --- | --- | --- |
| `GET` | `/` | Get all students |
| `POST` | `/` | Add a student |
| `PUT` | `/{id}?name=&email=` | Update a student's name or email |
| `DELETE` | `/{id}` | Delete a student |

### Add a student

```bash
curl -X POST http://localhost:8080/api/v1/student \
  -H "Content-Type: application/json" \
  -d '{"name":"Jane Doe","email":"jane@example.com","dub":"2001-05-20"}'
```

`dub` is the student's date of birth.

### Update a student

```bash
curl -X PUT "http://localhost:8080/api/v1/student/1?name=Jane&email=jane.doe@example.com"
```

### Example response

```json
[
  {
    "id": 1,
    "name": "JohnAppleseed",
    "age": 26,
    "dub": "1999-12-01",
    "email": "johnappleseed@icloud.com"
  }
]
```

## Run it locally

You'll need Java 18 and Docker.

**1. Start PostgreSQL**

```bash
docker run -d --name student-db \
  -e POSTGRES_USER=pran \
  -e POSTGRES_PASSWORD=4754 \
  -e POSTGRES_DB=student \
  -p 5432:5432 postgres:16
```

**2. Start the app**

```bash
git clone https://github.com/PranavTiwari44/Springboot_Student_API.git
cd Springboot_Student_API/demo/students
./mvnw spring-boot:run
```

The app starts with two sample students. The database is reset each time the app restarts, so anything you add is cleared.

## To do

- Keep data between restarts
