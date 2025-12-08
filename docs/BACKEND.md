# Backend Documentation

Comprehensive documentation for the Gobify backend built with Strapi 5 CMS.

## Table of Contents

- [Overview](#overview)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Content Types](#content-types)
- [API Endpoints](#api-endpoints)
- [Authentication](#authentication)
- [Plugins](#plugins)
- [Database Schema](#database-schema)
- [Configuration](#configuration)
- [Development](#development)
- [Testing](#testing)

## Overview

The Gobify backend is a headless CMS built on Strapi 5.15.0 that provides RESTful APIs for managing government civic administration data. It serves as the data layer and API provider for all frontend applications.

### Key Characteristics

- **Headless CMS**: API-first architecture with no business logic
- **Content Management**: 17 content types for comprehensive data modeling
- **Multi-tenant**: Support for multiple government agencies
- **Full-text Search**: Meilisearch integration for fast searches
- **File Storage**: Firebase Storage for scalable file uploads
- **JWT Authentication**: Secure token-based authentication
- **Auto-generated API**: REST endpoints auto-created from content types

### Philosophy

> **Important**: Strapi serves ONLY as a data persistence and API exposure layer. No custom business logic should be implemented in Strapi controllers or services. All business logic resides in the frontend applications.

## Technology Stack

| Component | Technology | Version | Purpose |
|-----------|-----------|---------|---------|
| **Framework** | Strapi CMS | 5.15.0 | Headless CMS platform |
| **Runtime** | Node.js | 18+ | JavaScript runtime |
| **Database** | PostgreSQL | 14+ | Relational database |
| **Search** | Meilisearch | Latest | Full-text search engine |
| **Storage** | Firebase Storage | Latest | File/image storage |
| **ORM** | Strapi ORM | Built-in | Database abstraction |
| **Auth** | JWT | Built-in | Token-based authentication |

### Key Dependencies

```json
{
  "@strapi/strapi": "5.15.0",
  "@strapi/plugin-users-permissions": "5.15.0",
  "@strapi/plugin-documentation": "5.15.1",
  "strapi-plugin-meilisearch": "0.13.2",
  "strapi-provider-firebase-storage": "1.0.4",
  "pg": "8.14.1",
  "react": "18.0.0",
  "react-dom": "18.0.0"
}
```

## Project Structure

```
gobify-backend/
├── config/                          # Configuration files
│   ├── admin.ts                    # Admin panel configuration
│   ├── api.ts                      # API configuration
│   ├── database.ts                 # Database connection
│   ├── middlewares.ts              # Middleware configuration
│   ├── plugins.ts                  # Plugin configuration
│   └── server.ts                   # Server configuration
├── src/
│   ├── admin/                      # Admin panel customization
│   │   ├── app.tsx                # Admin app entry point
│   │   └── webpack.config.ts      # Webpack customization
│   ├── api/                        # Content types
│   │   ├── about/                 # About page content
│   │   ├── area/                  # Administrative areas
│   │   ├── article/               # News articles
│   │   ├── article-category/      # Article categories
│   │   ├── calle/                 # Streets catalog
│   │   ├── colonia/               # Neighborhoods catalog
│   │   ├── comment/               # User comments
│   │   ├── department/            # Government departments
│   │   ├── global/                # Global settings
│   │   ├── procedure/             # Administrative procedures
│   │   ├── profile/               # Citizen profiles
│   │   ├── report/                # Citizen reports
│   │   ├── report-type/           # Report categories
│   │   ├── social-program/        # Social programs
│   │   ├── social-program-log/    # Activity logs
│   │   ├── social-program-request/# Program requests
│   │   └── tenant/                # Multi-tenant root
│   ├── components/                 # Reusable components
│   │   └── shared/                # Shared components
│   │       ├── media.json         # Media component
│   │       ├── rich-text.json     # Rich text component
│   │       └── slider.json        # Slider component
│   ├── extensions/                 # Plugin extensions
│   │   └── documentation/         # API documentation config
│   └── index.ts                    # App entry point
├── scripts/                        # Utility scripts
│   ├── seed.js                    # Database seeding script
│   └── data.json                  # Seed data
├── public/                         # Public assets
│   └── uploads/                   # Local file uploads (dev only)
├── .env                           # Environment variables
├── .env.example                   # Environment template
├── Dockerfile                     # Docker configuration
├── package.json                   # Dependencies
└── tsconfig.json                  # TypeScript configuration
```

### Content Type Structure

Each content type follows this structure:

```
api/{content-type}/
├── content-types/
│   └── {content-type}/
│       └── schema.json            # Content type definition
├── controllers/
│   └── {content-type}.ts          # Custom controllers (optional)
├── routes/
│   └── {content-type}.ts          # Custom routes (optional)
└── services/
    └── {content-type}.ts          # Custom services (optional)
```

## Content Types

The backend defines 17 content types that model all data entities in the system.

### 1. Tenant (Multi-tenant Root)

Multi-tenant organization configuration.

**Collection Name**: `tenants`

**Schema**:
```json
{
  "name": "string",              // Organization name
  "slug": "string"               // URL-friendly identifier
}
```

**Relations**:
- Has many: `profiles`, `social_programs`, `reports`, `departments`

**Use Case**: Allows multiple government agencies to use the same platform with isolated data.

---

### 2. Profile (Citizen Profile)

Complete citizen information with personal data and geolocation.

**Collection Name**: `profiles`

**Schema**:
```json
{
  "user": "relation",                // Link to auth user
  "tenant": "relation",              // Organization
  "name": "string",                  // First name
  "first_last_name": "string",       // Paternal surname
  "second_last_name": "string",      // Maternal surname
  "curp": "string",                  // Mexican national ID
  "birthdate": "date",               // Date of birth
  "phone": "string",                 // Primary phone
  "phone2": "string",                // Secondary phone
  "sector": "string",                // Sector/district
  "address": "string",               // Full address
  "lat": "float",                    // Latitude
  "lng": "float"                     // Longitude
}
```

**Relations**:
- Belongs to: `tenant`, `user` (users-permissions)
- Has many: `social_program_requests`, `reports`, `comments`

**Indexes**: `curp`, `tenant`, `user`

**Use Case**: Store comprehensive citizen data for program applications and service delivery.

---

### 3. Social Program

Federal or local social assistance programs.

**Collection Name**: `social_programs`

**Schema**:
```json
{
  "name": "string",                  // Program name
  "type": "enum",                    // "federal" | "local"
  "target_audience": "text",         // Target beneficiaries
  "description": "dynamiczone",      // Rich content (slider, text, media)
  "tenant": "relation",              // Organization
  "department": "relation",          // Responsible department
  "area": "relation"                 // Responsible area
}
```

**Dynamic Zone Components**:
- `shared.slider` - Image carousel
- `shared.rich-text` - Formatted text content
- `shared.media` - Media files

**Relations**:
- Belongs to: `tenant`, `department`, `area`
- Has many: `social_program_requests`

**Use Case**: Define social assistance programs with flexible content structure.

---

### 4. Social Program Request

Individual applications for social programs with delivery tracking.

**Collection Name**: `social_program_requests`

**Schema**:
```json
{
  // Core Fields
  "folio": "integer",                     // Unique request number
  "type": "enum",                         // "local" | "federal"
  "request_status": "enum",               // Status workflow
  "material": "string",                   // Material/supply description
  "motivo_cancelacion": "text",           // Cancellation reason

  // Relations
  "user": "relation",                     // Profile (beneficiary)
  "social_program": "relation",           // Program

  // Address Fields
  "calle": "string",                      // Street name
  "numero_exterior": "string",            // Exterior number
  "numero_interior": "string",            // Interior number
  "entre_calle": "string",                // Between street 1
  "y_calle": "string",                    // Between street 2
  "colonia": "string",                    // Neighborhood

  // Photos
  "foto_vivienda": "media",               // Home photo
  "foto_entrega": "media",                // Delivery photo

  // School Program Fields (optional)
  "codigo_escuela": "string",             // School code
  "grado": "string",                      // Grade level
  "grupo": "string",                      // Group/class
  "alumno_nombre": "string",              // Student first name
  "alumno_primer_apellido": "string",     // Student paternal surname
  "alumno_segundo_apellido": "string",    // Student maternal surname
  "alumno_curp": "string",                // Student CURP
  "sexo": "enum",                         // "MASCULINO" | "FEMENINO"
  "talla_uniforme": "string",             // Uniform size
  "talla_zapato": "string",               // Shoe size

  // Tutor Fields
  "tutor_nombre": "string",               // Tutor first name
  "tutor_primer_apellido": "string",      // Tutor paternal surname
  "tutor_segundo_apellido": "string",     // Tutor maternal surname

  // Contact
  "telefono": "string",                   // Primary phone
  "telefono_secundario": "string",        // Secondary phone
  "referidor": "text",                    // Referrer info

  // Auxiliary Beneficiary (for material programs)
  "aux_nombre": "string",                 // Aux first name
  "aux_primer_apellido": "string",        // Aux paternal surname
  "aux_segundo_apellido": "string",       // Aux maternal surname
  "aux_calle": "string",                  // Aux street
  "aux_numero_interior": "string",        // Aux interior number
  "aux_numero_exterior": "string",        // Aux exterior number
  "aux_colonia": "string",                // Aux neighborhood
  "aux_telefono": "string"                // Aux phone
}
```

**Enumerations**:
- `request_status`: `"En proceso"`, `"Validado"`, `"Entregado"`, `"Negado"`
- `type`: `"local"`, `"federal"`
- `sexo`: `"MASCULINO"`, `"FEMENINO"`

**Relations**:
- Belongs to: `user` (profile), `social_program`
- Has many: `social_program_logs`

**Meilisearch Indexed**: Yes (for fast search by documentId and program)

**Use Case**: Track program applications from request through validation to delivery. Supports both material delivery programs and school-based programs with student information.

---

### 5. Social Program Log

Activity logs for program request tracking.

**Collection Name**: `social_program_logs`

**Schema**:
```json
{
  "action": "string",                // Action description
  "timestamp": "datetime",           // When action occurred
  "user": "string",                  // Who performed action
  "details": "text",                 // Additional details
  "social_program_request": "relation" // Related request
}
```

**Relations**:
- Belongs to: `social_program_request`

**Use Case**: Audit trail for all actions on program requests (status changes, updates, deliveries).

---

### 6. Department

Government departments and their organizational structure.

**Collection Name**: `departments`

**Schema**:
```json
{
  "name": "string",                  // Department name
  "description": "text",             // Department description
  "tenant": "relation",              // Organization
  "areas": "relation",               // Areas within department
  "social_programs": "relation",     // Programs managed
  "procedures": "relation"           // Administrative procedures
}
```

**Relations**:
- Belongs to: `tenant`
- Has many: `areas`, `social_programs`, `procedures`

**Use Case**: Organize government structure and assign responsibilities.

---

### 7. Area

Administrative areas within departments.

**Collection Name**: `areas`

**Schema**:
```json
{
  "name": "string",                  // Area name
  "description": "text",             // Area description
  "department": "relation",          // Parent department
  "social_programs": "relation"      // Programs managed by area
}
```

**Relations**:
- Belongs to: `department`
- Has many: `social_programs`

**Use Case**: Sub-divisions of departments for finer organizational control.

---

### 8. Report

Citizen-submitted reports with geolocation and photos.

**Collection Name**: `reports`

**Schema**:
```json
{
  "title": "string",                 // Report title
  "description": "text",             // Report details
  "status": "enum",                  // Report status
  "lat": "float",                    // Latitude
  "lng": "float",                    // Longitude
  "address": "string",               // Address
  "photos": "media",                 // Report photos (multiple)
  "user": "relation",                // Citizen who reported
  "report_type": "relation",         // Report category
  "tenant": "relation"               // Organization
}
```

**Relations**:
- Belongs to: `user` (profile), `report_type`, `tenant`

**Use Case**: Citizens report issues (potholes, broken lights, etc.) with location and photos.

---

### 9. Report Type

Categories for citizen reports.

**Collection Name**: `report_types`

**Schema**:
```json
{
  "name": "string",                  // Type name
  "description": "text",             // Type description
  "icon": "string",                  // Icon identifier
  "reports": "relation"              // Reports of this type
}
```

**Relations**:
- Has many: `reports`

**Use Case**: Categorize reports for routing and statistics.

---

### 10. Article

News articles and content with rich formatting.

**Collection Name**: `articles`

**Schema**:
```json
{
  "title": "string",                 // Article title
  "slug": "string",                  // URL slug
  "content": "richtext",             // Article body
  "excerpt": "text",                 // Short summary
  "cover_image": "media",            // Featured image
  "published_at": "datetime",        // Publication date
  "author": "relation",              // Article author
  "article_category": "relation",    // Category
  "comments": "relation"             // User comments
}
```

**Relations**:
- Belongs to: `article_category`, `author` (users-permissions)
- Has many: `comments`

**Use Case**: Publish news, announcements, and informational content.

---

### 11. Article Category

Categories for organizing articles.

**Collection Name**: `article_categories`

**Schema**:
```json
{
  "name": "string",                  // Category name
  "slug": "string",                  // URL slug
  "description": "text",             // Category description
  "articles": "relation"             // Articles in category
}
```

**Relations**:
- Has many: `articles`

**Use Case**: Organize articles by topic or department.

---

### 12. Comment

User comments on articles.

**Collection Name**: `comments`

**Schema**:
```json
{
  "content": "text",                 // Comment text
  "profile": "relation",             // Commenter profile
  "article": "relation"              // Article commented on
}
```

**Relations**:
- Belongs to: `profile`, `article`

**Use Case**: Enable citizen engagement with published content.

---

### 13. Procedure

Administrative procedures with requirements and costs.

**Collection Name**: `procedures`

**Schema**:
```json
{
  "name": "string",                  // Procedure name
  "description": "text",             // Procedure details
  "requirements": "richtext",        // Required documents
  "cost": "decimal",                 // Procedure cost
  "duration": "string",              // Processing time
  "department": "relation"           // Responsible department
}
```

**Relations**:
- Belongs to: `department`

**Use Case**: Inform citizens about government procedures, requirements, and costs.

---

### 14. Calle (Street)

Street catalog for address management.

**Collection Name**: `calles`

**Schema**:
```json
{
  "tipo": "string",                  // Street type (Avenida, Calle, etc.)
  "nombre": "string",                // Street name
  "municipio": "string"              // Municipality
}
```

**Indexes**: Compound index on `tipo` + `nombre` for fast lookups

**Use Case**: Standardized street catalog for address autocomplete and validation.

**Common Street Types**:
- Avenida (Avenue)
- Calle (Street)
- Privada (Private road)
- Callejón (Alley)
- Cerrada (Closed street)
- Boulevard

---

### 15. Colonia (Neighborhood)

Neighborhood catalog with postal codes.

**Collection Name**: `colonias`

**Schema**:
```json
{
  "nombre": "string",                // Neighborhood name
  "codigo_postal": "string",         // Postal code (ZIP)
  "municipio": "string"              // Municipality
}
```

**Indexes**: `codigo_postal`, `nombre`

**Use Case**: Neighborhood lookup for addresses and postal code validation.

---

### 16. Global

Global application settings.

**Collection Name**: `global` (Single Type)

**Schema**:
```json
{
  "site_name": "string",             // Site name
  "site_description": "text",        // Site description
  "logo": "media",                   // Organization logo
  "favicon": "media",                // Site favicon
  "contact_email": "email",          // Contact email
  "contact_phone": "string"          // Contact phone
}
```

**Type**: Single Type (only one instance)

**Use Case**: Store global configuration values accessible across the platform.

---

### 17. About

About page content.

**Collection Name**: `about` (Single Type)

**Schema**:
```json
{
  "title": "string",                 // Page title
  "content": "richtext",             // Page content
  "team": "component[]",             // Team members
  "mission": "text",                 // Mission statement
  "vision": "text"                   // Vision statement
}
```

**Type**: Single Type (only one instance)

**Use Case**: Manage "About Us" page content.

---

## API Endpoints

All content types automatically expose RESTful API endpoints following Strapi conventions.

### Base URL

```
https://api.gobify.app/api
```

### Standard Endpoints

For each collection type `{entity}`, the following endpoints are available:

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| `GET` | `/api/{entity}` | List all entries | Configurable |
| `GET` | `/api/{entity}/:id` | Get single entry | Configurable |
| `POST` | `/api/{entity}` | Create new entry | Yes |
| `PUT` | `/api/{entity}/:id` | Update entry | Yes |
| `DELETE` | `/api/{entity}/:id` | Delete entry | Yes |

### Query Parameters

Strapi supports powerful query parameters:

#### Pagination

```
GET /api/profiles?pagination[page]=1&pagination[pageSize]=25
```

#### Filtering

```
GET /api/profiles?filters[name][$containsi]=juan
GET /api/social-programs?filters[type][$eq]=federal
```

#### Population

```
GET /api/social-program-requests?populate=*
GET /api/social-program-requests?populate[user][populate][0]=tenant
```

#### Sorting

```
GET /api/profiles?sort=createdAt:desc
GET /api/calles?sort[0]=tipo:asc&sort[1]=nombre:asc
```

### Response Format

All responses follow this structure:

```json
{
  "data": [
    {
      "id": 1,
      "documentId": "xyz123",
      "attributes": {
        "name": "Juan Pérez",
        "curp": "JUAP850101HJCRRN01",
        "createdAt": "2024-01-15T10:30:00.000Z",
        "updatedAt": "2024-01-15T10:30:00.000Z"
      }
    }
  ],
  "meta": {
    "pagination": {
      "page": 1,
      "pageSize": 25,
      "pageCount": 10,
      "total": 250
    }
  }
}
```

### Error Responses

```json
{
  "error": {
    "status": 400,
    "name": "ValidationError",
    "message": "Invalid data",
    "details": {}
  }
}
```

## Authentication

### JWT Token System

Gobify uses JWT (JSON Web Tokens) for authentication via the `users-permissions` plugin.

#### Login

```http
POST /api/auth/local
Content-Type: application/json

{
  "identifier": "user@example.com",
  "password": "SecurePassword123"
}
```

**Response**:
```json
{
  "jwt": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "id": 1,
    "username": "user@example.com",
    "email": "user@example.com",
    "confirmed": true,
    "blocked": false
  }
}
```

#### Using the Token

Include the JWT in the `Authorization` header:

```http
GET /api/profiles
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

#### Register

```http
POST /api/auth/local/register
Content-Type: application/json

{
  "username": "newuser",
  "email": "newuser@example.com",
  "password": "SecurePassword123"
}
```

### Roles & Permissions

The system has three default roles:

1. **Public**: Unauthenticated users
   - Can read public content
   - Cannot create/update/delete

2. **Authenticated**: Logged-in users
   - Can read most content
   - Can create their own content
   - Can update their own content

3. **Admin**: Administrators
   - Full access to all content
   - Can access Strapi admin panel

Configure permissions in: **Settings** → **Users & Permissions** → **Roles**

## Plugins

### 1. Meilisearch Plugin

**Purpose**: Fast full-text search for social program requests

**Configuration** (`config/plugins.ts`):

```typescript
meilisearch: {
  enabled: true,
  config: {
    'social-program-request': {
      entriesQuery: {
        populate: '*',
      },
      transformEntry({ entry }) {
        return {
          ...entry,
          social_program_document_id: entry.social_program.documentId,
        }
      },
      settings: {
        "filterableAttributes": [
          "documentId",
          "social_program_document_id",
        ],
      }
    }
  }
}
```

**Usage**:
```javascript
// Search requests
const results = await meiliClient.index('social-program-request')
  .search('juan', {
    filter: 'social_program_document_id = "abc123"'
  });
```

**Features**:
- Auto-sync on create/update/delete
- Typo tolerance
- Fast prefix search
- Filterable by program and request ID

---

### 2. Firebase Storage Plugin

**Purpose**: Scalable file/image storage

**Configuration** (`config/plugins.ts`):

```typescript
upload: {
  config: {
    provider: "strapi-provider-firebase-storage",
    providerOptions: {
      serviceAccount: { /* Firebase credentials */ },
      bucket: "gobify-app.appspot.com",
      sortInStorage: true,
      debug: false,
    },
    breakpoints: {
      xlarge: 1920,
      large: 1000,
      medium: 750,
      small: 500,
      xsmall: 64
    },
  },
}
```

**Features**:
- Automatic image resizing
- Multiple format generation
- Direct Firebase Storage uploads
- Public URL generation

**Breakpoints**: Images are automatically resized to multiple sizes for responsive delivery.

---

### 3. Documentation Plugin

**Purpose**: Auto-generated OpenAPI documentation

**Access**: http://localhost:1337/documentation

**Features**:
- Interactive API documentation
- Try-it-now functionality
- Schema definitions
- Example requests/responses

---

### 4. Users & Permissions Plugin

**Purpose**: Authentication and authorization

**Features**:
- JWT token generation
- Role-based access control (RBAC)
- User registration
- Email confirmation
- Password reset
- OAuth providers (optional)

## Database Schema

### PostgreSQL Database

The database is automatically created from content type definitions.

**Connection Configuration** (`config/database.ts`):

```typescript
export default ({ env }) => ({
  connection: {
    client: 'postgres',
    connection: {
      connectionString: env('DATABASE_URL'),
      ssl: env.bool('DATABASE_SSL', false) && {
        rejectUnauthorized: false
      }
    },
    pool: {
      min: 2,
      max: 10
    }
  }
});
```

### Key Tables

| Table | Description | Rows (typical) |
|-------|-------------|----------------|
| `profiles` | Citizen profiles | 10,000+ |
| `social_program_requests` | Program applications | 50,000+ |
| `social_programs` | Program definitions | 50-100 |
| `calles` | Street catalog | 5,000+ |
| `colonias` | Neighborhood catalog | 500+ |
| `reports` | Citizen reports | 5,000+ |
| `departments` | Government depts | 10-50 |
| `up_users` | Auth users | 10,000+ |

### Indexes

Automatically created indexes:
- Primary keys (`id`)
- Foreign keys (relations)
- `documentId` (Strapi 5 document identifier)
- Timestamps (`createdAt`, `updatedAt`)

### Migrations

Strapi automatically manages schema migrations. No manual migration files needed.

**Run migrations**:
```bash
npm run strapi db:migrate
```

## Configuration

### Environment Variables

**Required Variables** (`.env`):

```env
# Server
HOST=0.0.0.0
PORT=1337

# Security
APP_KEYS="key1,key2,key3,key4"
API_TOKEN_SALT=random-string
ADMIN_JWT_SECRET=random-string
TRANSFER_TOKEN_SALT=random-string
JWT_SECRET=random-string

# Database
DATABASE_URL=postgresql://user:pass@localhost:5432/gobify

# Meilisearch
MEILISEARCH_HOST=http://localhost:7700
MEILISEARCH_API_KEY=master-key

# Firebase
STORAGE_BUCKET_URL=gobify-app.appspot.com

# Environment
NODE_ENV=development
```

### Admin Panel Configuration

**File**: `config/admin.ts`

```typescript
export default ({ env }) => ({
  auth: {
    secret: env('ADMIN_JWT_SECRET'),
  },
  apiToken: {
    salt: env('API_TOKEN_SALT'),
  },
});
```

### Server Configuration

**File**: `config/server.ts`

```typescript
export default ({ env }) => ({
  host: env('HOST', '0.0.0.0'),
  port: env.int('PORT', 1337),
  url: env('PUBLIC_URL', 'http://localhost:1337'),
  app: {
    keys: env.array('APP_KEYS'),
  },
});
```

### Middleware Configuration

**File**: `config/middlewares.ts`

```typescript
export default [
  'strapi::errors',
  'strapi::security',
  'strapi::cors',
  'strapi::poweredBy',
  'strapi::logger',
  'strapi::query',
  'strapi::body',
  'strapi::session',
  'strapi::favicon',
  'strapi::public',
];
```

## Development

### Running Development Server

```bash
npm run dev
```

**Features**:
- Auto-reload on code changes
- Admin panel auto-rebuild
- Hot module replacement
- Detailed logging

### Creating Content Types

**Via Admin Panel**:
1. Go to **Content-Type Builder**
2. Click **Create new collection type**
3. Define fields
4. Save
5. Restart server

**Via Code**:
Create `src/api/{name}/content-types/{name}/schema.json`:

```json
{
  "kind": "collectionType",
  "collectionName": "my_entities",
  "info": {
    "singularName": "my-entity",
    "pluralName": "my-entities",
    "displayName": "My Entity"
  },
  "attributes": {
    "name": {
      "type": "string"
    }
  }
}
```

### Seeding Database

**Script**: `scripts/seed.js`

```bash
npm run seed:example
```

The seed script:
1. Reads from `scripts/data.json`
2. Creates tenant
3. Creates departments and areas
4. Creates social programs
5. Creates profiles
6. Creates streets and neighborhoods

### Custom Controllers

Create custom logic in `src/api/{entity}/controllers/{entity}.ts`:

```typescript
export default {
  async find(ctx) {
    // Custom find logic
    const entries = await strapi.entityService.findMany(
      'api::profile.profile',
      ctx.query
    );
    return entries;
  }
};
```

### Debugging

Enable detailed logging:

```env
# .env
NODE_ENV=development
DEBUG=strapi:*
```

View logs:
```bash
npm run dev
# Logs will show all queries, requests, etc.
```

## Testing

### Unit Tests

Create tests in `tests/` directory:

```javascript
// tests/profile.test.js
const request = require('supertest');

describe('Profile API', () => {
  it('should return profiles', async () => {
    const response = await request(strapi.server.httpServer)
      .get('/api/profiles')
      .expect(200);

    expect(response.body.data).toBeDefined();
  });
});
```

Run tests:
```bash
npm test
```

### Integration Tests

Test with real database:

```bash
# Use test database
DATABASE_URL=postgresql://user:pass@localhost:5432/gobify_test npm test
```

### API Testing

Use Postman or curl:

```bash
# Test profile creation
curl -X POST http://localhost:1337/api/profiles \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer $TOKEN" \
  -d '{
    "data": {
      "name": "Test User",
      "curp": "TEST123456HJCRRN01"
    }
  }'
```

## Performance Optimization

### Database Optimization

1. **Use populate wisely**: Only populate needed relations
   ```
   /api/profiles?populate[tenant][fields][0]=name
   ```

2. **Limit pagination**: Keep pageSize reasonable (25-100)
   ```
   /api/profiles?pagination[pageSize]=25
   ```

3. **Add indexes**: For frequently queried fields
   ```json
   {
     "indexes": [
       {
         "columns": ["curp"],
         "type": "unique"
       }
     ]
   }
   ```

### Caching

Enable caching in `config/middlewares.ts`:

```typescript
{
  name: 'strapi::cache',
  config: {
    enabled: true,
    maxAge: 3600000, // 1 hour
  }
}
```

### Image Optimization

Firebase Storage automatically generates optimized breakpoints:
- xlarge: 1920px
- large: 1000px
- medium: 750px
- small: 500px
- xsmall: 64px

Use appropriate size in frontend:
```javascript
const imageUrl = profile.photo.formats.medium.url;
```

## Deployment

See [DEPLOYMENT.md](./DEPLOYMENT.md) for detailed deployment instructions.

**Quick Deploy with Docker**:

```bash
# Build image
docker build -t gobify-backend .

# Run container
docker run -d \
  -p 1337:1337 \
  -e DATABASE_URL="postgresql://..." \
  -e JWT_SECRET="..." \
  --name gobify-backend \
  gobify-backend
```

## Troubleshooting

### Common Issues

**Issue**: "Database connection failed"
- **Solution**: Verify DATABASE_URL is correct and PostgreSQL is running

**Issue**: "Meilisearch not responding"
- **Solution**: Start Meilisearch: `docker start meilisearch`

**Issue**: "Firebase Storage upload failed"
- **Solution**: Verify service account credentials in `config/plugins.ts`

**Issue**: "Port 1337 already in use"
- **Solution**: Change PORT in `.env` or kill process: `lsof -ti:1337 | xargs kill`

## Best Practices

1. **No Business Logic**: Keep controllers thin, move logic to frontend
2. **Use Relations**: Leverage Strapi's relational capabilities
3. **Validate Input**: Use Strapi's built-in validation
4. **Secure Secrets**: Never commit `.env` file
5. **Populate Wisely**: Only fetch needed relations
6. **Index Queries**: Add indexes for filtered fields
7. **Version Control**: Commit schema changes, not database
8. **Backup Database**: Regular PostgreSQL backups
9. **Monitor Logs**: Watch for errors and slow queries
10. **Update Regularly**: Keep Strapi and plugins updated

## Support

- **Strapi Documentation**: https://docs.strapi.io/
- **Strapi Discord**: https://discord.strapi.io/
- **GitHub Issues**: https://github.com/strapi/strapi/issues

---

**Document Version**: 1.0.0
**Last Updated**: December 2024
**Backend Version**: Strapi 5.15.0
