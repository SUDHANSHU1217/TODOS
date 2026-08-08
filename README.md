# 📝 TODOS

A full-stack Todo Management application built with Angular and ASP.NET Core Web API.

## 🌐 Live Application

**Frontend:**  
https://melodic-marshmallow-c56baf.netlify.app/

**Backend API:**  
https://todo-backend-e0fj.onrender.com/

**Swagger API Documentation:**  
https://todo-backend-e0fj.onrender.com/swagger

## 📦 Repositories

- [Angular Frontend](https://github.com/SUDHANSHU1217/Todo-Frontend)
- [ASP.NET Core Backend](https://github.com/SUDHANSHU1217/Todo-Backend)
# 📝 TODOS — Full Stack Todo Management Application

A full-stack Todo Management application built using **Angular** and **ASP.NET Core Web API**, with **JWT-based authentication**, **PostgreSQL** database integration, and cloud deployment.

The application allows users to register, securely log in, and manage their own Todo items through a responsive web interface.

## 🚀 Live Demo

**Frontend:**
https://melodic-marshmallow-c56baf.netlify.app/

**Backend API:**
https://todo-backend-e0fj.onrender.com/

**API Documentation:**
https://todo-backend-e0fj.onrender.com/swagger

---

## ✨ Features

### 🔐 Authentication & Authorization

* User registration
* User login
* JWT token-based authentication
* Protected dashboard routes
* User-specific Todo access
* Logout functionality
* Authentication guard in Angular
* JWT token stored in browser local storage

### 📋 Todo Management

* View all Todos
* Add new Todo
* Edit existing Todo
* Delete Todo
* Todos are associated with the authenticated user
* Users cannot access another user's Todos

### 🎨 Frontend

* Responsive Angular UI
* Login and registration pages
* Dashboard
* Todo list
* Add/Edit Todo form
* Navigation bar with authentication-aware controls
* Form validation
* User-friendly error messages
* SweetAlert2 notifications

### ⚙️ Backend

* RESTful Web API
* Repository pattern
* Service layer
* DTO-based request/response handling
* Entity Framework Core
* PostgreSQL database
* JWT authentication
* Global exception-handling middleware
* Swagger/OpenAPI documentation
* CORS configuration

---

## 🏗️ Architecture

```text
                    ┌─────────────────────┐
                    │      Angular UI     │
                    │     (Netlify)       │
                    └──────────┬──────────┘
                               │
                               │ HTTP / REST API
                               ▼
                    ┌─────────────────────┐
                    │   ASP.NET Core API  │
                    │      (Render)       │
                    └──────────┬──────────┘
                               │
                 ┌─────────────┴─────────────┐
                 │                           │
                 ▼                           ▼
        ┌─────────────────┐        ┌─────────────────┐
        │ Authentication  │        │ Todo Management │
        │   JWT / Claims  │        │ Repository /    │
        │                 │        │ Service Layer   │
        └─────────────────┘        └────────┬────────┘
                                            │
                                            ▼
                                  ┌─────────────────┐
                                  │   PostgreSQL    │
                                  │    Database     │
                                  └─────────────────┘
```

---

## 🛠️ Technology Stack

### Frontend

* Angular
* TypeScript
* HTML5
* CSS3
* Bootstrap
* SweetAlert2
* Angular Router
* Angular HttpClient

### Backend

* C#
* ASP.NET Core Web API
* .NET 8
* Entity Framework Core
* JWT Bearer Authentication
* Swagger / OpenAPI
* Repository Pattern
* Service Layer
* Middleware

### Database

* PostgreSQL
* Entity Framework Core / Npgsql

### Development Tools

* Visual Studio
* Visual Studio Code
* Git
* GitHub
* Postman
* Swagger

### Deployment

* **Netlify** — Angular frontend
* **Render** — ASP.NET Core backend
* **PostgreSQL** — production database

---

## 📂 Project Structure

### Angular Frontend

```text
ToDoUI/
│
├── src/
│   └── app/
│       ├── components/
│       │   ├── dashboard/
│       │   ├── login/
│       │   ├── register/
│       │   ├── todo-form/
│       │   ├── todo-list/
│       │   └── navbar/
│       │
│       ├── guards/
│       │   └── auth-guard.ts
│       │
│       ├── services/
│       │   ├── auth.ts
│       │   └── todo.ts
│       │
│       ├── models/
│       │
│       └── app.routes.ts
│
├── angular.json
├── package.json
└── tsconfig.json
```

### ASP.NET Core Backend

```text
ToDoList/
│
├── Controllers/
│
├── Data/
│
├── DTOs/
│
├── Interfaces/
│
├── Middleware/
│
├── Models/
│
├── Repositories/
│
├── Services/
│
├── Program.cs
├── appsettings.json
├── Dockerfile
└── ToDoList.csproj
```

---

## 🔑 Authentication Flow

The application uses JWT Bearer authentication.

```text
User
 │
 │ Login
 ▼
Angular
 │
 │ POST /api/Auth/login
 ▼
ASP.NET Core API
 │
 │ Validate credentials
 ▼
JWT Token
 │
 ▼
Angular
 │
 │ Store token
 ▼
Protected API Requests
 │
 │ Authorization: Bearer <token>
 ▼
ASP.NET Core
 │
 │ Validate JWT
 ▼
User-specific Todo data
```

The authenticated user's ID is stored as a JWT claim and used by the backend to ensure that Todo operations are performed only on the user's own records.

---

## 🔒 Security

The application implements:

* JWT Bearer authentication
* User-specific authorization
* Password hashing using SHA-256
* CORS policy
* Protected Angular routes
* Backend authorization checks
* Global exception handling
* Configuration-based JWT settings

> Production secrets and database credentials should be supplied through environment variables rather than committed to source control.

---

## 🌐 API Endpoints

### Authentication

| Method | Endpoint             | Description                       |
| ------ | -------------------- | --------------------------------- |
| POST   | `/api/Auth/register` | Register a new user               |
| POST   | `/api/Auth/login`    | Authenticate user and receive JWT |

### Todo

| Method | Endpoint         | Description                    |
| ------ | ---------------- | ------------------------------ |
| GET    | `/api/Todo`      | Get authenticated user's Todos |
| POST   | `/api/Todo`      | Create a Todo                  |
| PUT    | `/api/Todo/{id}` | Update a Todo                  |
| DELETE | `/api/Todo/{id}` | Delete a Todo                  |

Todo endpoints require JWT authentication.

---

## 🐳 Docker

The backend is containerized using Docker.

The Docker image uses:

```text
.NET 8 SDK
        ↓
Build & Publish
        ↓
.NET 8 ASP.NET Runtime
```

The container is deployed on Render.

---

## 💻 Running Locally

### Prerequisites

Make sure you have:

* Node.js
* Angular CLI
* .NET 8 SDK
* PostgreSQL
* Git

### Clone the repositories

```bash
git clone https://github.com/SUDHANSHU1217/Todo-Backend.git
git clone https://github.com/SUDHANSHU1217/ToDoUI.git
```

---

### Run the Backend

Navigate to the backend:

```bash
cd Todo-Backend
```

Restore dependencies:

```bash
dotnet restore
```

Update the database connection configuration and JWT configuration for your local environment.

Run:

```bash
dotnet run
```

The API can then be accessed through the configured local URL.

Swagger is available at:

```text
/swagger
```

---

### Run the Angular Frontend

Navigate to the frontend:

```bash
cd ToDoUI
```

Install dependencies:

```bash
npm install
```

Start the development server:

```bash
ng serve
```

Open:

```text
http://localhost:4200
```

---

## 📦 Production Deployment

### Frontend — Netlify

The Angular application is automatically deployed from GitHub.

```text
GitHub
   ↓
Netlify
   ↓
Angular Production Build
   ↓
Live Website
```

### Backend — Render

The ASP.NET Core API is deployed using Docker.

```text
GitHub
   ↓
Render
   ↓
Docker Build
   ↓
.NET 8 Application
   ↓
Live API
```

---

## 🧪 Testing

The application was tested for:

* User registration
* User login
* Invalid login handling
* JWT authentication
* Protected routes
* Todo creation
* Todo retrieval
* Todo update
* Todo deletion
* User-specific Todo access
* Logout
* Production frontend → backend communication
* Production database connectivity

The Angular production build completes successfully.

---

## 📌 Key Learning Outcomes

This project helped demonstrate practical experience with:

* Building RESTful APIs using ASP.NET Core
* Angular frontend development
* JWT authentication and authorization
* Entity Framework Core
* PostgreSQL
* Repository and service-layer architecture
* Dependency injection
* Middleware
* DTOs
* CORS
* Docker
* Cloud deployment
* Git/GitHub workflow
* Debugging frontend/backend integration issues

---

## 👨‍💻 Author

**Sudhanshu Ranjan**

Computer Science & Engineering

GitHub:
https://github.com/SUDHANSHU1217

---

## 📄 License

This project is intended for learning and portfolio purposes.
