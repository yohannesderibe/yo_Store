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