# Secura - Technical Documentation

## Introduction
Secura is a secure project management system developed to demonstrate JWT-based authentication and role-based authorization using Express.js and SQLite.

The application allows users to securely access protected resources while enforcing ownership and role-based access control.

---

# System Architecture
```text
Client
   │
   ▼
Express API
   │
   ▼
Authentication Middleware
   │
   ▼
Authorization Middleware
   │
   ▼
SQLite Database
```

---

# Authentication Flow
## User Registration
1. User submits registration details.
2. Password is hashed using bcrypt.
3. User data is stored in SQLite database.
4. Registration response is returned.

### Stored User Data
```text
id
name
email
password (hashed)
role
```

---

## User Login

1. User submits email and password.
2. System retrieves user from database.
3. bcrypt compares entered password with stored hash.
4. JWT token is generated.
5. Token is returned to the user.

### Example JWT Payload

```json
{
  "id": 1,
  "role": "admin"
}
```

---

# JWT Authentication

JWT (JSON Web Token) is used to authenticate users.

### Login Process

```text
User Login
    ↓
Credential Verification
    ↓
JWT Generation
    ↓
Token Sent To Client
```

### Protected Request

```text
Client Request
    ↓
Authorization Header
    ↓
JWT Verification
    ↓
Access Granted
```

### Authorization Header Format

```http
Authorization: Bearer <token>
```

### Token Expiry

Tokens are configured to expire after one hour.

```javascript
expiresIn: "1h"
```

---

# Authorization Flow

Authorization determines what actions a user can perform after successful authentication.

## Roles

### Developer (dev)

* View Projects
* Create Projects
* Modify Own Projects

### Lead (lead)

* View Projects
* Create Projects
* Modify Own Projects

### Administrator (admin)

* Full Access
* Modify Any Project
* Delete Any Project

---

# Owner-Based Authorization

Each project contains an ownerId field.

```text
Project
   │
   └── ownerId
```

Only:

* Project Owner
* Administrator

can update or delete the project.

---

# Database Schema

## Users Table

| Column   | Type    |
| -------- | ------- |
| id       | INTEGER |
| name     | TEXT    |
| email    | TEXT    |
| password | TEXT    |
| role     | TEXT    |

---

## Projects Table

| Column      | Type    |
| ----------- | ------- |
| id          | INTEGER |
| name        | TEXT    |
| description | TEXT    |
| status      | TEXT    |
| ownerId     | INTEGER |

---

# Middleware

## Authentication Middleware

File:

```text
authMiddleware.js
```

Responsibilities:

* Extract JWT token
* Verify JWT signature
* Decode user information
* Attach user data to request

---

## Authorization Middleware

File:

```text
authorizationMiddleware.js
```

Responsibilities:

* Verify project ownership
* Verify administrator access
* Prevent unauthorized modifications

---

# Security Measures

The application implements several security mechanisms:

* Password Hashing using bcrypt
* JWT Authentication
* Protected Routes
* Role-Based Authorization
* Owner-Based Authorization
* Token Expiry Handling

---

# API Summary

## Authentication

```http
POST /api/auth/register
POST /api/auth/login
```

## Projects

```http
GET    /api/projects
POST   /api/projects
PUT    /api/projects/:id
DELETE /api/projects/:id
```

---

# Conclusion

Secura successfully demonstrates secure authentication and authorization using Express.js, SQLite, JWT, and bcrypt. The system implements role-based and owner-based access control to ensure that resources are only accessible by authorized users.
