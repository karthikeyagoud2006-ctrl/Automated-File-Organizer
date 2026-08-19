# E-Commerce Backend (FastAPI)

> **Internship Project Submission**

---

## Intern Details

| Field | Details |
|---|---|
| **Intern Name** | Arshith Paidi |
| **Intern ID** | CITS8573 |
| **Project Name** | E-Commerce Backend (FastAPI) |
| **Duration** | 4 Weeks |
| **Primary Language** | Python |

---

## Project Overview

This repository contains an asynchronous, production-ready RESTful API for an **E-Commerce Backend System** developed using **Python** and **FastAPI**. Built over a 4-week internship, the project focuses on modular architecture, secure user authentication, product catalog management, dynamic shopping carts, order fulfillment, and relational database migrations.

---

## Key Features

* **Authentication & Security**: User registration, login handling, password hashing via `Bcrypt`, and stateless authorization using JWT (JSON Web Tokens).
* **Role-Based Access Control (RBAC)**: Distinct permissions for `Admin` (manage catalog/orders) and `Customer` (browse products, manage cart, place orders) roles.
* **Product Catalog**: Full CRUD operations for product listings and categories, featuring pagination, category filtering, and inventory tracking.
* **Shopping Cart & Checkout**: Interactive shopping cart management with dynamic item updates and transaction-safe order placement logic.
* **Order Processing**: Automatic order generation, order status updates (`Pending`, `Processing`, `Shipped`, `Delivered`), and historical order tracking per user.
* **Database & Migrations**: Async database integration via **SQLAlchemy 2.0** paired with **Alembic** for seamless schema migrations.

---

## Tech Stack

| Domain | Tool / Technology |
|---|---|
| **Language** | Python 3.11+ |
| **Framework** | FastAPI |
| **Database** | PostgreSQL |
| **ORM** | SQLAlchemy 2.0 (Async) |
| **Migrations** | Alembic |
| **Authentication** | PyJWT, Passlib (Bcrypt) |
| **Data Validation** | Pydantic v2 |
| **Documentation** | OpenAPI / Swagger UI |

---

## Project Structure

```text
├── app/
│   ├── api/          # Route definitions organized by endpoint modules
│   ├── core/         # Core configs, security/JWT handling, and DB sessions
│   ├── models/       # SQLAlchemy database models
│   ├── schemas/      # Pydantic models for request/response validation
│   └── services/     # Business logic and database operations
├── alembic/          # Database migration scripts and configurations
├── .env.example      # Sample environment variables configuration file
├── requirements.txt  # Project dependencies list
└── main.py           # Application entrypoint
```

---

## Setup & Local Installation

### Prerequisites

* Python 3.11+
* PostgreSQL server running locally or via container
* Git

### Step-by-Step Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/arshithpaidi/ecommerce-fastapi-backend.git
   cd ecommerce-fastapi-backend
   ```

2. **Set up a virtual environment**
   ```bash
   # On macOS/Linux
   python3 -m venv venv
   source venv/bin/activate

   # On Windows
   python -m venv venv
   venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment variables**
   Create a `.env` file in the project root based on `.env.example`:
   ```env
   SECRET_KEY=your_super_secret_jwt_key
   ALGORITHM=HS256
   ACCESS_TOKEN_EXPIRE_MINUTES=30
   DATABASE_URL=postgresql+asyncpg://postgres:password@localhost:5432/ecommerce_db
   ```

5. **Run database migrations**
   ```bash
   alembic upgrade head
   ```

6. **Start the application**
   ```bash
   uvicorn app.main:app --reload
   ```

---

## API Documentation

Once the application is running, interact with the API endpoints directly via interactive Swagger documentation:

* **Swagger UI**: `http://127.0.0.1:8000/docs`
* **ReDoc**: `http://127.0.0.1:8000/redoc`

---

## API Endpoint Summary

| Category | HTTP Method | Endpoint | Description | Access |
|---|---|---|---|---|
| **Auth** | `POST` | `/api/v1/auth/register` | Register a new user | Public |
| **Auth** | `POST` | `/api/v1/auth/login` | Authenticate and retrieve JWT token | Public |
| **Products** | `GET` | `/api/v1/products` | Retrieve product listings with pagination | Public |
| **Products** | `POST` | `/api/v1/products` | Add a new product to catalog | Admin |
| **Cart** | `POST` | `/api/v1/cart/items` | Add product item to user cart | Customer |
| **Orders** | `POST` | `/api/v1/orders` | Create order from active cart items | Customer |

---

## License

Distributed under the MIT License. Developed as part of internship coursework.
