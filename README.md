# NestJS Prisma Boilerplate

A production-ready NestJS boilerplate built with **Clean Architecture**, **DDD**, **CQRS**, and **Prisma ORM**. It provides a complete foundation for secure backend applications with authentication, authorization, user management, file storage, and an optional admin panel.

## Features

- **Authentication** — JWT access/refresh tokens, email verification, password reset, and two-factor authentication (2FA)
- **Authorization** — Role-based access control (RBAC) with granular permissions
- **Clean Architecture** — Separation of domain, application, infrastructure, and presentation layers
- **CQRS** — Command/query separation for clear business logic
- **Prisma ORM** — Type-safe database access with PostgreSQL
- **File Storage** — MinIO/S3-compatible storage with public and private buckets
- **Internationalization** — Built-in i18n support (English and Arabic)
- **API Documentation** — Swagger/OpenAPI with basic auth protection
- **Admin Panel** — React + Refine admin UI (see [README-ADMIN.md](./README-ADMIN.md))
- **Testing** — Unit, integration, and e2e test setup with Jest

## Tech Stack

| Layer | Technology |
|-------|------------|
| Framework | NestJS 11 |
| Language | TypeScript |
| Database | PostgreSQL + Prisma |
| Auth | Passport JWT, bcrypt, speakeasy (2FA) |
| Storage | MinIO / AWS S3 |
| Email | Nodemailer (MailHog for local dev) |
| Admin UI | React, Vite, Refine, Ant Design |

## Quick Start

### Prerequisites

- Node.js 20+
- Docker & Docker Compose

### 1. Clone and install

```bash
git clone https://github.com/your-username/nestjs-prisma-boilerplate.git
cd nestjs-prisma-boilerplate
npm install
```

### 2. Configure environment

```bash
cp .env.example .env
```

Update `.env` with your secrets (JWT, OTP, session keys, etc.).

### 3. Start infrastructure

```bash
docker compose up -d
```

This starts PostgreSQL, MailHog, and MinIO.

### 4. Set up the database

```bash
npm run db:generate
npm run db:migrate
npm run db:seed
```

### 5. Run the API

```bash
npm run start:dev
```

The API is available at `http://localhost:3000/api` and Swagger docs at `http://localhost:3000/docs`.

### 6. (Optional) Run the admin panel

```bash
cd admin
npm install
npm run dev
```

Admin panel: `http://localhost:3001` — see [README-ADMIN.md](./README-ADMIN.md) for details.

## Scripts

| Command | Description |
|---------|-------------|
| `npm run start:dev` | Start API in watch mode |
| `npm run build` | Build for production |
| `npm run test` | Run unit tests |
| `npm run test:e2e` | Run end-to-end tests |
| `npm run db:generate` | Generate Prisma client |
| `npm run db:migrate` | Run database migrations |
| `npm run db:seed` | Seed the database |
| `npm run lint` | Lint and fix source files |

## Project Structure

```
src/
├── application/     # Commands, queries, DTOs, mappers
├── core/            # Domain entities, value objects, services
├── infrastructure/  # Prisma repos, email, storage, i18n
└── presentation/    # Controllers, guards, filters, modules
prisma/              # Schema, migrations, seed
admin/               # React admin panel
docs/                # Architecture and development docs
test/                # E2E tests
```

## Documentation

- [Architecture Overview](./docs/01-overview/ARCHITECTURE_OVERVIEW.md)
- [API Authentication](./docs/API_AUTH.md)
- [Authorization](./docs/AUTHORIZATION.md)
- [Database](./docs/DATABASE.md)
- [Storage](./docs/STORAGE.md)
- [Testing](./docs/TESTING.md)
- [Deployment Guide](./docs/04-deployment/deployment-guide.md)
- [Contributing](./CONTRIBUTING.md)

## License

[MIT](./LICENSE)
