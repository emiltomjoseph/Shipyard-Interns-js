# Secura
Secura is a secure project management system built using **Next.js**, **Express.js**, and **SQLite**. It demonstrates **JWT-based authentication** and **role-based authorization**.

## Features

* User Registration
* User Login
* Password Hashing with bcrypt
* JWT Authentication
* Protected Routes
* Role-Based Authorization (dev, lead, admin)
* Project Creation
* Project Viewing
* Project Updating
* Project Deletion
* Owner/Admin Access Control

## Tech Stack

* Frontend: Next.js
* Backend: Express.js
* Database: SQLite
* Authentication: JWT
* Security: bcrypt

## Authorization Rules

* Only authenticated users can access project routes.
* Project owners can update or delete their own projects.
* Admins can update or delete any project.
* Unauthorized users receive an access denied response.

## Run the Project

### Backend

```bash
cd backend
npm install
npm start
```

Server runs on:

```text
http://localhost:5000
```

## Sample Users

### Admin

```json
{
  "email": "emil@example.com",
  "password": "123456"
}
```

### Developer

```json
{
  "email": "dev@example.com",
  "password": "123456"
}
```

## Author

Emil Tom Joseph
