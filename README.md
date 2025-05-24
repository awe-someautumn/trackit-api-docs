# 📘 Trackit API Documentation

**Trackit API** is a lightweight personal task management API designed for users who want to stay organized across daily routines, work projects, personal hobbies, and even pet care.

This repository showcases the API documentation as part of a technical writing portfolio. It includes OpenAPI specifications, Postman collections, and a professionally formatted PDF document.

---

## 🧠 Project Background

Managing personal tasks often requires flexibility, simple structures, and intuitive categorization. Many enterprise-level tools are too complex for individuals who simply want to track daily tasks, writing projects, or even pet care routines.

**Trackit API** was designed as a fictional but realistic solution to this need—providing:
- Simple user authentication
- Project-based task grouping
- Prioritized task tracking
- Notification system for deadlines

This repository demonstrates how to document such an API clearly and professionally.

---

## ✨ Features

- RESTful API structure with semantic routes
- Token-based authentication using Bearer scheme
- Create/read/update/delete (CRUD) operations for:
  - Users
  - Projects
  - Tasks
- Task overview calendar with date filtering
- Notification endpoint for reminders and alerts

---

## 📁 Repository Structure

| Folder        | Description                                      |
|---------------|--------------------------------------------------|
| `openapi/`    | OpenAPI 3.0 Specification (YAML format)          |
| `postman/`    | Postman Collection for live testing              |
| `docs/`       | PDF version of the full API documentation        |

---

## 📡 Mock Server

> Base URL:  
> `https://698a9017-e4ab-4ee7-82d7-f605859ad87f.mock.pstmn.io/v1`

### 🔐 Authentication
Retrieve Bearer token via:
- `POST /register`
- `POST /login`

Use the following token in headers:
Authorisation: Bearer trackitMockToken

---

## 🧪 Usage Example

Here’s how to get started with the API:

1. **Register a user**
```http
POST /register
Content-Type: application/json

{
  "email": "johndoe@example.com",
  "password": "password123",
  "name": "John Doe"
}
```

2. **Log in to get a token**
```http
POST /login
Content-Type: application/json

{
  "email": "johndoe@example.com",
  "password": "password123"
}
```

3. **Create a new project**
```http
POST /projects
Authorization: Bearer trackitMockToken
Content-Type: application/json

{
  "title": "Writing Schedule",
  "color": "#FFD700"
}
```

---

## 📎 Quick Links

- [OpenAPI YAML Spec](./openapi/Trackit_api_v1.0.0.yaml)
- [Postman Collection](./postman/Trackit%20API.postman_collection.json)
- [API Documentation PDF](./docs/Trackit%20API.pdf)
- [Import Postman Collection (raw)](https://raw.githubusercontent.com/awe-someautumn/trackit-api-docs/main/postman/Trackit%20API.postman_collection.json)

---

## 🛠 Technology Stack

- OpenAPI 3.0
- Postman (Mock Server)
- Markdown / HTML
- PDF (exported from structured documentation)

---

🤝 Contributing
This repository is read-only as a documentation portfolio.
However, if you'd like to provide feedback or suggestions, feel free to open an issue or contact me directly via GitHub.

---

## 📄 License

This repository is part of a documentation portfolio project.  
© [awe-someautumn](https://github.com/awe-someautumn)

