# Miraku Database Schema

## Overview

Miraku uses a relational database to manage users, anime, genres, categories, ratings, and user preferences.

The schema is designed to be scalable, maintainable, and compatible with both SQLite (development) and PostgreSQL (production).

---

# Database Tables

## Users

Stores user account information.

| Field | Type | Description |
|--------|------|-------------|
| id | Integer | Primary Key |
| username | String | Unique username |
| email | String | Unique email |
| password_hash | String | Hashed password |
| profile_picture | String | Optional profile image |
| created_at | Timestamp | Account creation date |

---

## Anime

Stores anime information added by users.

| Field | Type | Description |
|--------|------|-------------|
| id | Integer | Primary Key |
| user_id | Integer | Owner of the anime |
| title | String | Anime title |
| description | Text | Optional notes |
| release_year | Integer | Release year |
| rating | Float | User rating |
| status_id | Integer | Current watch status |
| created_at | Timestamp | Added date |

---

## Status

Represents the user's watch progress.

Examples:

- Watching
- Completed
- Plan to Watch
- On Hold
- Dropped

| Field | Type |
|--------|------|
| id | Integer |
| name | String |

---

## Genres

Stores available genres.

Examples:

- Action
- Comedy
- Romance
- Mystery

Users can also create custom genres.

| Field | Type |
|--------|------|
| id | Integer |
| name | String |
| created_by | Integer (Nullable) |

---

## AnimeGenres

Many-to-many relationship between Anime and Genres.

| Field | Type |
|--------|------|
| anime_id | Integer |
| genre_id | Integer |

---

## Settings

Stores user preferences.

Examples:

- Dark mode
- Language
- Theme

| Field | Type |
|--------|------|
| id | Integer |
| user_id | Integer |
| theme | String |
| language | String |

---

# Relationships

User

↓

Many Anime

Anime

↓

One Status

Anime

↓

Many Genres

Genre

↓

Many Anime

User

↓

One Settings

---

# Relationship Summary

Users
    │
    ├──────────────┐
    │              │
    ▼              ▼
Anime          Settings
    │
    ▼
Status

Anime
    ▲
    │
AnimeGenres
    │
    ▼
Genres

---

# Future Expansion

The database is designed to support future features such as:

- Favorites
- Episode tracking
- Reviews
- Recommendations
- Friends
- Public profiles
- Activity feed