# Rental Property Management System (RPMS) - Backend API

This repository hosts the server-side RESTful API for the Rental Property Management System. It manages the core business rules, user authentication profiles, lease triggers, database operations, and maintenance schedules.

## 🛠️ Tech Stack

* **Runtime Environment:** Node.js with Express.js (or Python with Django/FastAPI)
* **Database:** PostgreSQL or MongoDB (Stores Users, Properties, Leases, Payments, Tickets)
* **ORM/ODM:** Prisma / Mongoose
* **Security & Auth:** JSON Web Tokens (JWT) & bcrypt password encryption
* **Validation:** Zod / Joi validation middleware

## 📂 Core API Architecture & Routes

The API enforces distinct Role-Based Access Control (RBAC) levels. Key endpoints include:

### Authentication & Profiles
* `POST /api/v1/auth/register` - Register a new user (Tenant or Landlord).
* `POST /api/v1/auth/login` - Authenticate users and return session tokens.

### Property Listings (CRUD)
* `GET /api/v1/properties` - Public endpoint to retrieve and filter available properties.
* `POST /api/v1/properties` - Create a new unit listing (Landlord only).

### Leases & Payments
* `POST /api/v1/leases` - Draft and approve a rental agreement contract.
* `GET /api/v1/payments/history` - Fetch invoice statements and transaction records.

### Maintenance Ticketing
* `POST /api/v1/maintenance` - Open a repair request ticket with details (Tenant only).
* `PATCH /api/v1/maintenance/:id` - Adjust ticket statuses (Pending, In Progress, Resolved).

## ⚙️ Getting Started

### Prerequisites
* Node.js installed locally.
* A live instance of PostgreSQL or MongoDB (Local or cloud-hosted).

### Installation & Local Run

1. Navigate to the backend directory:
   ```bash
   cd backend
   ```

2. Install server dependencies:
   ```bash
   npm install
   ```

3. Setup environment configuration:
   Create a `.env` file in the root of this folder:
   ```env
   PORT=5000
   DATABASE_URL=your_database_connection_string
   JWT_SECRET=your_jwt_signing_secret_string
   ```

4. Execute database migrations (if utilizing a relational DB schema):
   ```bash
   npx prisma migrate dev  # If using Prisma
   ```

5. Initialize the development server:
   ```bash
   npm run dev
   ```
   The backend API endpoints will be live at [http://localhost:5000](http://localhost:5000).
