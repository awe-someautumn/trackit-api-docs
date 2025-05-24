# 📘 Trackit API Documentation

**Trackit API** is a lightweight personal task management API designed for users who want to stay organized across daily routines, work projects, personal hobbies, and even pet care.

This repository showcases the API documentation as part of a technical writing portfolio. It includes OpenAPI specifications, Postman collections, and a professionally formatted PDF document.

---

## ✨ Features

- RESTful API endpoints with JSON responses
- Token-based authentication (Bearer)
- CRUD operations for users, projects, and tasks
- Real-time status updates and notifications
- Overview endpoint for calendar-based task management

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

## 📎 Quick Links

- 🔹 [OpenAPI YAML Spec](./openapi/Trackit_api_v1.0.0.yaml)
- 🔹 [Postman Collection](./postman/Trackit%20API.postman_collection.json)
- 🔹 [API Documentation PDF](./docs/Trackit%20API.pdf)
- 🔹 [Import Postman Collection (raw)](https://raw.githubusercontent.com/awe-someautumn/trackit-api-docs/main/postman/Trackit%20API.postman_collection.json)

---

## 🛠 Technology Stack

- OpenAPI 3.0
- Postman (Mock Server)
- Markdown / HTML
- PDF (exported from structured documentation)

---

## 📄 License

This repository is part of a documentation portfolio project.  
© [awe-someautumn](https://github.com/awe-someautumn)

