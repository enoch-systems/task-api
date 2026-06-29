# Task API

A RESTful Task Management API built with Node.js, TypeScript, Express, Prisma, and PostgreSQL.

## Features

- **Authentication** — Register, Login, Get Profile (JWT + bcrypt)
- **Tasks** — Full CRUD with search, filter, sort, and pagination
- **Categories** — Full CRUD
- **Authorization** — Ownership-based access control

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Runtime | Node.js |
| Language | TypeScript |
| Framework | Express.js |
| ORM | Prisma |
| Database | PostgreSQL |
| Auth | JWT + bcrypt |
| Validation | Zod |

## Architecture

```
Route → Controller → Service → Repository → Database
```

## Getting Started

### Prerequisites

- Node.js
- PostgreSQL

### Installation

```bash
# Clone the repo
git clone https://github.com/enoch-systems/task-api.git
cd task-api

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env
# Edit .env with your database URL and JWT secret

# Run migrations
npx prisma migrate dev

# Start the server
npm run dev
```

### Environment Variables

```
DATABASE_URL="postgresql://postgres:password@localhost:5432/task_api"
JWT_SECRET="your-secret-key"
PORT=3000
```

## API Endpoints

### Auth
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/auth/register` | Register a new user |
| POST | `/api/auth/login` | Login |
| GET | `/api/auth/profile` | Get current user (protected) |

### Categories (protected)
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/categories` | Get all categories |
| POST | `/api/categories` | Create a category |
| PATCH | `/api/categories/:id` | Update a category |
| DELETE | `/api/categories/:id` | Delete a category |

### Tasks (protected)
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/tasks` | Get all tasks (search, filter, sort, paginate) |
| GET | `/api/tasks/:id` | Get a single task |
| POST | `/api/tasks` | Create a task |
| PATCH | `/api/tasks/:id` | Update a task |
| DELETE | `/api/tasks/:id` | Delete a task |

### Query Parameters for GET /api/tasks

| Param | Example | Description |
|-------|---------|-------------|
| `search` | `?search=meeting` | Search by title/description |
| `status` | `?status=completed` | Filter by status |
| `priority` | `?priority=high` | Filter by priority |
| `categoryId` | `?categoryId=1` | Filter by category |
| `sortBy` | `?sortBy=dueDate` | Sort field |
| `order` | `?order=desc` | Sort order (asc/desc) |
| `page` | `?page=1` | Page number |
| `limit` | `?limit=10` | Items per page |