# StoreTrae

Full-stack e-commerce platform built for small businesses. Customers browse a product catalog, manage a cart, and check out with shipping details; store owners use a protected admin area to manage inventory, review orders, and view sales metrics.

## Features

### Storefront

- Home page with featured products and category highlights
- Product catalog and browsing
- Shopping cart (React context) with slide-out cart panel
- Guest checkout (name, email, phone, shipping address)
- Order confirmation page

### Admin (JWT-protected)

- Admin login with role-based access
- Dashboard overview
- Product CRUD with image upload (up to 5 MB)
- Order list and details
- Sales reports (total orders, revenue, items sold, average order value)

### API & data

- REST API with Swagger/OpenAPI in development
- PostgreSQL schema with users, products, orders, and order line items
- Stock decremented on checkout; price snapshots stored on order items
- SQL views for monthly sales, top products, low stock, and order summaries
- Database columns prepared for future payment providers (e.g. Telebirr, Chapa)

## Tech stack

| Layer     | Technologies                                                      |
| --------- | ----------------------------------------------------------------- |
| Frontend  | React 18, TypeScript, Vite, React Router, Axios                   |
| Backend   | ASP.NET Core 8, Entity Framework Core, JWT Bearer, BCrypt, Swagger |
| Database  | PostgreSQL 16 (Docker Compose optional)                           |

## Project structure

```
store-trae/
├── frontend/     # React SPA (port 3000)
├── backend/      # StoreTrae.Api (port 5000)
└── database/     # Schema, seeds, migrations, Docker setup
```

## Prerequisites

- [.NET 8 SDK](https://dotnet.microsoft.com/download)
- [Node.js](https://nodejs.org/) (LTS)
- PostgreSQL 16 **or** [Docker Desktop](https://www.docker.com/products/docker-desktop/) for the bundled database

## Getting started

### 1. Database

**Docker (recommended):**

```bash
cd database
docker compose up -d
```

Default connection: `Host=localhost;Port=5432;Database=storetrae;Username=postgres;Password=postgres`

See [database/README.md](database/README.md) for manual setup and troubleshooting.

### 2. Backend API

```bash
cd backend
dotnet run
```

API: `http://localhost:5000`  
Swagger UI (Development): `http://localhost:5000/swagger`

### 3. Frontend

```bash
cd frontend
npm install
npm run dev
```

App: `http://localhost:3000` (Vite proxies `/api` to the backend)

## Default admin credentials

| Field    | Value      |
| -------- | ---------- |
| Username | `admin`    |
| Password | `admin123` |

Use **Admin → Login** at `/admin/login`.

## API overview

| Endpoint                       | Access | Description              |
| ------------------------------ | ------ | ------------------------ |
| `POST /api/auth/login`         | Public | Admin login, returns JWT |
| `GET /api/products`            | Public | List products            |
| `GET /api/products/{id}`       | Public | Product details          |
| `POST /api/products`           | Admin  | Create product           |
| `PUT /api/products/{id}`       | Admin  | Update product           |
| `DELETE /api/products/{id}`    | Admin  | Delete product           |
| `POST /api/products/image`     | Admin  | Upload product image     |
| `POST /api/orders`             | Public | Place order              |
| `GET /api/orders`              | Admin  | List orders              |
| `GET /api/orders/report/sales` | Admin  | Sales summary            |

## Development notes

- CORS and JWT settings are in `backend/appsettings.json` and `appsettings.Development.json`.
- Product images are served from `/uploads` on the API host.
- In Development, the API may call `EnsureCreated()` on startup if PostgreSQL is available.

## License

Add your license here (e.g. MIT).
