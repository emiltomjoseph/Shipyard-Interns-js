# Secura

A JWT-Based Authentication and Role-Based Authorization System built with Next.js, Express.js, and SQLite.

## Overview

Secura is a secure project management system designed to demonstrate authentication and authorization concepts. The application allows users to register, log in, and manage projects while enforcing access control through user roles and ownership verification.

The system uses JWT (JSON Web Token) for authentication, bcrypt for password hashing, and SQLite for database management.

---

## Features

### Authentication

* User Registration
* User Login
* Password Hashing using bcrypt
* JWT Token Generation
* Token Validation
* Token Expiry Handling

### Authorization

* Role-Based Access Control
* Roles: dev, lead, admin
* Owner-Based Access Control
* Protected Routes

### Project Management

* Create Project
* View Projects
* Update Project
* Delete Project

---

## Tech Stack

### Frontend

* Next.js

### Backend

* Express.js

### Database

* SQLite

### Authentication & Security

* JWT (jsonwebtoken)
* bcryptjs

### Additional Packages

* dotenv
* cors

---

## Installation

### Clone Repository

```bash
git clone <repository-url>
cd Shipyard-Interns-js
```

### Backend Setup

```bash
cd backend
npm install
npm start
```

Backend will run on:

```text
http://localhost:5000
```

---

## Environment Variables

Create a `.env` file inside the backend directory.

```env
PORT=5000
JWT_SECRET=shipyard_secret_key
```

---

## API Endpoints

### Authentication

#### Register User

```http
POST /api/auth/register
```

#### Login User

```http
POST /api/auth/login
```

---

### Projects

#### Get All Projects

```http
GET /api/projects
```

#### Create Project

```http
POST /api/projects
```

#### Update Project

```http
PUT /api/projects/:id
```

#### Delete Project

```http
DELETE /api/projects/:id
```

---

## Sample Users

### Admin User

```json
{
  "email": "emil@example.com",
  "password": "123456"
}
```

### Developer User

```json
{
  "email": "dev@example.com",
  "password": "123456"
}
```

---

## Authorization Rules

* Only authenticated users can access project routes.
* Project owners can update or delete their own projects.
* Administrators can update or delete any project.
* Unauthorized users receive an Access Denied response.

---

## Project Structure

```text
backend/
│
├── src/
│   ├── config/
│   ├── controllers/
│   ├── middleware/
│   ├── routes/
│   └── app.js
│
├── database.sqlite
├── package.json
└── .env

frontend/

README.md
documentation.md
```

---

## Author
Emil Tom Joseph
