# Miraku System Architecture

## Overview

Miraku follows a modern client-server architecture.

The application consists of three primary layers:

- Frontend
- Backend
- Database

Each layer has a dedicated responsibility and communicates through REST APIs.

---

## Architecture

```
+----------------------+
|      Frontend        |
|  Next.js + React     |
+----------+-----------+
           |
           | HTTP Requests (REST API)
           |
+----------v-----------+
|       Backend        |
|  Flask + SQLAlchemy  |
+----------+-----------+
           |
           |
+----------v-----------+
|      Database        |
| SQLite / PostgreSQL  |
+----------------------+
```

---

## Frontend Responsibilities

The frontend is responsible for:

- User interface
- Navigation
- Forms
- Search
- User interaction
- Responsive layout
- API communication

Technologies:

- Next.js
- React
- TypeScript
- Tailwind CSS

---

## Backend Responsibilities

The backend is responsible for:

- Business logic
- Authentication
- Authorization
- Data validation
- Database operations
- REST API

Technologies:

- Flask
- SQLAlchemy

---

## Database Responsibilities

The database stores:

- Users
- Anime
- Genres
- Categories
- Ratings
- Watch progress
- Settings

Development:
- SQLite

Production:
- PostgreSQL

---

## Authentication Flow

1. User registers.
2. Password is securely hashed.
3. User logs in.
4. Backend validates credentials.
5. Backend returns a JWT.
6. Frontend stores the token securely.
7. Protected API routes require a valid token.

---

## Communication Flow

Frontend

↓

REST API

↓

Flask Backend

↓

SQLAlchemy

↓

Database

↓

Response returned to frontend

---

## Design Principles

- Separation of concerns
- Modular architecture
- Scalability
- Security
- Maintainability
- Responsive design