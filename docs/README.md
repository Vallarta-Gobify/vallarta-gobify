# Gobify Platform

> A comprehensive government civic administration platform for managing citizen services, social programs, reports, and municipal operations.

## Overview

Gobify is a modern, full-stack web platform designed for government agencies to efficiently manage their civic operations. The platform provides tools for citizen registration, social program management, report tracking, geographic information management, and administrative procedures.

### Key Features

- **Citizen Management**: Complete citizen profiles with personal information, addresses, and geolocation
- **Social Programs**: Management of federal and local social assistance programs with request tracking
- **Interactive Maps**: Mapbox-powered visualizations with clustering for geographic data
- **Reports System**: Citizen reports with photo uploads and geolocation
- **Street & Neighborhood Management**: Comprehensive address catalog system
- **Document Generation**: PDF receipts and Excel exports for program deliveries
- **QR Code Integration**: QR code generation and scanning for verification
- **Multi-tenant Architecture**: Support for multiple government agencies
- **Full-text Search**: Meilisearch integration for fast program request searches
- **Real-time KPIs**: Dashboard with statistics and analytics

## Architecture

Gobify follows a modern microservices architecture with clear separation between backend and frontend:

```
┌─────────────────────────────────────────────────────────────┐
│                      Frontend Layer                          │
│  ┌────────────────────────────────────────────────────┐     │
│  │         gobify-admin-portal (Next.js 15)           │     │
│  │  - App Router with Server Actions                  │     │
│  │  - TanStack Query for state management             │     │
│  │  - NextUI components + Tailwind CSS                │     │
│  │  - Mapbox GL for maps                              │     │
│  │  - AG Grid for data tables                         │     │
│  └────────────────────────────────────────────────────┘     │
└─────────────────────────────────────────────────────────────┘
                            ↕ REST API
┌─────────────────────────────────────────────────────────────┐
│                      Backend Layer                           │
│  ┌────────────────────────────────────────────────────┐     │
│  │         gobify-backend (Strapi 5 CMS)              │     │
│  │  - Headless CMS with REST API                      │     │
│  │  - JWT Authentication                              │     │
│  │  - 17 Content Types                                │     │
│  │  - Meilisearch for full-text search               │     │
│  │  - Firebase Storage for file uploads              │     │
│  └────────────────────────────────────────────────────┘     │
└─────────────────────────────────────────────────────────────┘
                            ↕
┌─────────────────────────────────────────────────────────────┐
│                      Data Layer                              │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │  PostgreSQL  │  │  Meilisearch │  │   Firebase   │      │
│  │   Database   │  │    Search    │  │   Storage    │      │
│  └──────────────┘  └──────────────┘  └──────────────┘      │
└─────────────────────────────────────────────────────────────┘
```

### Technology Stack

**Backend:**
- [Strapi 5.15.0](https://strapi.io/) - Headless CMS
- [PostgreSQL](https://www.postgresql.org/) - Relational database
- [Meilisearch](https://www.meilisearch.com/) - Full-text search engine
- [Firebase Storage](https://firebase.google.com/docs/storage) - File storage
- [Node.js 18+](https://nodejs.org/) - Runtime environment

**Frontend:**
- [Next.js 15](https://nextjs.org/) - React framework with App Router
- [React 18.3.1](https://react.dev/) - UI library
- [TypeScript 5.7](https://www.typescriptlang.org/) - Type safety
- [TanStack Query](https://tanstack.com/query) - Server state management
- [NextUI](https://nextui.org/) - Component library
- [Tailwind CSS](https://tailwindcss.com/) - Utility-first CSS
- [Mapbox GL](https://www.mapbox.com/) - Interactive maps
- [AG Grid](https://www.ag-grid.com/) - Data tables
- [Formik + Yup](https://formik.org/) - Form management
- [Turborepo](https://turbo.build/) - Monorepo build system

## Quick Start

### Prerequisites

- Node.js 18 or higher
- npm 9.8.1 or higher
- PostgreSQL 14 or higher
- Git

### Installation

1. **Clone the repository**
```bash
git clone <repository-url>
cd Vallarta-Gobify
```

2. **Backend Setup**
```bash
cd gobify-backend
npm install
# Configure environment variables (see INSTALLATION.md)
npm run dev
```

3. **Frontend Setup**
```bash
cd gobify-portals
npm install
npm run dev
```

Visit:
- Frontend: http://localhost:3000
- Backend Admin: http://localhost:1337/admin

## Repository Structure

```
Vallarta-Gobify/
├── docs/                          # Documentation files
│   ├── README.md                  # This file
│   ├── INSTALLATION.md            # Detailed installation guide
│   ├── BACKEND.md                 # Backend documentation
│   ├── FRONTEND.md                # Frontend documentation
│   ├── API-REFERENCE.md           # API endpoints reference
│   └── DEPLOYMENT.md              # Deployment guide
├── gobify-backend/                # Strapi backend
│   ├── src/
│   │   ├── api/                   # Content types (17 entities)
│   │   ├── components/            # Reusable components
│   │   └── extensions/            # Plugin extensions
│   ├── config/                    # Configuration files
│   ├── scripts/                   # Seed scripts
│   ├── Dockerfile                 # Docker configuration
│   └── package.json
├── gobify-portals/                # Frontend monorepo
│   ├── apps/
│   │   └── gobify-admin-portal/   # Main admin application
│   ├── packages/
│   │   ├── strapi-client/         # API client
│   │   ├── pdf-generator/         # PDF generation
│   │   ├── ui/                    # Shared components
│   │   ├── eslint-config/         # ESLint configuration
│   │   └── typescript-config/     # TypeScript configuration
│   ├── turbo.json                 # Turborepo configuration
│   └── package.json
└── user-manual/                   # End-user documentation
```

## Core Entities

The platform manages the following main entities:

| Entity | Description | Key Features |
|--------|-------------|--------------|
| **Profile** | Citizen profiles | Personal info, address, geolocation, CURP |
| **Social Program** | Assistance programs | Federal/local types, target audience, description |
| **Social Program Request** | Program applications | Status tracking, photos, delivery info |
| **Social Program Log** | Activity logs | Audit trail for requests |
| **Department** | Government departments | Organizational structure |
| **Area** | Administrative areas | Sub-divisions of departments |
| **Report** | Citizen reports | Photos, geolocation, status tracking |
| **Report Type** | Report categories | Classification system |
| **Article** | News/content | Rich content with categories |
| **Procedure** | Administrative procedures | Requirements, costs, steps |
| **Calle** | Streets catalog | Type, name, municipality |
| **Colonia** | Neighborhoods catalog | Name, postal code, municipality |
| **Tenant** | Multi-tenant root | Organization configuration |

## Development Workflow

### Backend Development
```bash
cd gobify-backend
npm run dev              # Development mode with auto-reload
npm run build            # Build admin panel
npm run start            # Production mode
npm run seed:example     # Seed database with sample data
```

### Frontend Development
```bash
cd gobify-portals
npm run dev              # Start all apps in development
npm run build            # Build all apps
npm run lint             # Lint all code
npm run format           # Format with Prettier
```

### Admin Portal Specific
```bash
cd gobify-portals/apps/gobify-admin-portal
npm run dev              # Development server
npm run dev:turbo        # Development with Turbo
npm test                 # Run tests
npm run test:watch       # Watch mode
```

## API Access

The REST API is available at:
- **Base URL**: https://api.gobify.app/api
- **Authentication**: JWT tokens via `/api/auth/local`
- **Documentation**: Available through Strapi documentation plugin

Example API call:
```javascript
// Fetch all profiles
const response = await fetch('https://api.gobify.app/api/profiles', {
  headers: {
    'Authorization': `Bearer ${token}`
  }
});
```

## Key Features Deep Dive

### Social Programs Management
- Create and manage federal/local programs
- Track applications with status workflow (En proceso → Validado → Entregado)
- Generate PDF delivery receipts
- Export data to Excel
- Interactive map view with clustering
- School-based programs with student information
- Material/supply tracking

### Citizen Management
- Comprehensive profile system
- Address with geocoding
- CURP validation
- Multiple phone numbers
- Report and program request history
- AG Grid-powered table with filtering and sorting

### Geographic Management
- Street catalog with type classification (Avenida, Calle, Privada, etc.)
- Neighborhood catalog with postal codes
- Address search and autocomplete
- Map-based visualization

### Document Generation
- PDF receipts for program deliveries
- Excel exports with progress tracking
- QR code generation for verification
- Batch processing support

## Documentation

For detailed information, see:

- **[INSTALLATION.md](./INSTALLATION.md)** - Complete installation and setup guide
- **[BACKEND.md](./BACKEND.md)** - Backend architecture, content types, and configuration
- **[FRONTEND.md](./FRONTEND.md)** - Frontend structure, components, and patterns
- **[API-REFERENCE.md](./API-REFERENCE.md)** - Complete API endpoints documentation
- **[DEPLOYMENT.md](./DEPLOYMENT.md)** - Production deployment guide

## Environment Configuration

### Backend (.env)
```env
HOST=0.0.0.0
PORT=1337
DATABASE_URL=postgresql://user:pass@localhost:5432/gobify
JWT_SECRET=your-secret-key
# See INSTALLATION.md for complete list
```

### Frontend (.env.local)
```env
NEXT_PUBLIC_API_URL=https://api.gobify.app/api
NEXT_PUBLIC_MAPBOX_TOKEN=your-mapbox-token
# See INSTALLATION.md for complete list
```

## Testing

### Backend
Strapi provides built-in testing capabilities. Custom tests can be added in the `tests/` directory.

### Frontend
```bash
# Run all tests
npm test

# Watch mode
npm run test:watch

# Test coverage
npm run test:coverage
```

## Contributing

1. Create a feature branch: `git checkout -b feature/your-feature`
2. Make your changes
3. Run tests: `npm test`
4. Commit with descriptive message
5. Push and create a pull request

## Support

For issues, questions, or contributions:
- Create an issue in the repository
- Contact the development team
- Refer to the documentation in the `/docs` folder

## License

Proprietary - All rights reserved

---

**Version**: 1.0.0
**Last Updated**: December 2024
**Maintained by**: Gobify Development Team
