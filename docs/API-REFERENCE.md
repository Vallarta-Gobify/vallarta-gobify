# API Reference

Complete reference for the Gobify REST API powered by Strapi 5.

## Table of Contents

- [Introduction](#introduction)
- [Base URL](#base-url)
- [Authentication](#authentication)
- [Request Format](#request-format)
- [Response Format](#response-format)
- [Error Handling](#error-handling)
- [Query Parameters](#query-parameters)
- [Endpoints](#endpoints)
  - [Authentication](#authentication-endpoints)
  - [Profiles](#profiles-endpoints)
  - [Social Programs](#social-programs-endpoints)
  - [Social Program Requests](#social-program-requests-endpoints)
  - [Departments & Areas](#departments--areas-endpoints)
  - [Streets & Neighborhoods](#streets--neighborhoods-endpoints)
  - [Reports](#reports-endpoints)
  - [Articles](#articles-endpoints)
  - [Procedures](#procedures-endpoints)
  - [Tenants](#tenants-endpoints)
- [Rate Limiting](#rate-limiting)
- [Versioning](#versioning)

## Introduction

The Gobify API is a RESTful API built with Strapi 5 that provides endpoints for managing government civic administration data. All responses are in JSON format.

### API Characteristics

- **RESTful**: Follows REST principles
- **JSON**: All data exchanged in JSON format
- **JWT Authentication**: Secure token-based auth
- **Pagination**: All list endpoints support pagination
- **Filtering**: Advanced filtering capabilities
- **Population**: Control related data fetching
- **Sorting**: Flexible sorting options

## Base URL

```
https://api.gobify.app/api
```

**Development**:
```
http://localhost:1337/api
```

All endpoints are relative to this base URL.

## Authentication

### JWT Token Authentication

The API uses JWT (JSON Web Tokens) for authentication. Include the token in the `Authorization` header.

**Header Format**:
```
Authorization: Bearer <your-jwt-token>
```

### Obtaining a Token

**Endpoint**: `POST /auth/local`

**Request**:
```json
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
    "blocked": false,
    "createdAt": "2024-01-15T10:30:00.000Z",
    "updatedAt": "2024-01-15T10:30:00.000Z"
  }
}
```

### Using the Token

**cURL Example**:
```bash
curl -X GET https://api.gobify.app/api/profiles \
  -H "Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
```

**JavaScript Example**:
```javascript
const response = await fetch('https://api.gobify.app/api/profiles', {
  headers: {
    'Authorization': `Bearer ${token}`,
    'Content-Type': 'application/json'
  }
});
```

### Token Expiration

Tokens expire after a configurable period (default: 30 days). When a token expires, you'll receive a `401 Unauthorized` response. Request a new token using the login endpoint.

## Request Format

### Headers

**Required Headers**:
```
Content-Type: application/json
Authorization: Bearer <token>
```

### Body Format

For POST and PUT requests, send data in JSON format with a `data` wrapper:

```json
{
  "data": {
    "name": "Juan Pérez",
    "curp": "JUAP850101HJCRRN01",
    "phone": "3331234567"
  }
}
```

## Response Format

### Success Response

All successful responses follow this structure:

**Single Entity**:
```json
{
  "data": {
    "id": 1,
    "documentId": "abc123xyz",
    "attributes": {
      "name": "Juan Pérez",
      "curp": "JUAP850101HJCRRN01",
      "createdAt": "2024-01-15T10:30:00.000Z",
      "updatedAt": "2024-01-15T10:30:00.000Z"
    }
  },
  "meta": {}
}
```

**Collection (List)**:
```json
{
  "data": [
    {
      "id": 1,
      "documentId": "abc123xyz",
      "attributes": {
        "name": "Juan Pérez",
        "curp": "JUAP850101HJCRRN01"
      }
    },
    {
      "id": 2,
      "documentId": "def456uvw",
      "attributes": {
        "name": "María García",
        "curp": "MAGA900215MJCRRL02"
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

### HTTP Status Codes

| Code | Meaning | Description |
|------|---------|-------------|
| `200` | OK | Request succeeded |
| `201` | Created | Resource created successfully |
| `204` | No Content | Request succeeded (no content returned) |
| `400` | Bad Request | Invalid request format or parameters |
| `401` | Unauthorized | Missing or invalid authentication token |
| `403` | Forbidden | Insufficient permissions |
| `404` | Not Found | Resource not found |
| `429` | Too Many Requests | Rate limit exceeded |
| `500` | Internal Server Error | Server error |

## Error Handling

### Error Response Format

```json
{
  "error": {
    "status": 400,
    "name": "ValidationError",
    "message": "Invalid data provided",
    "details": {
      "errors": [
        {
          "path": ["name"],
          "message": "name must be at least 2 characters"
        }
      ]
    }
  }
}
```

### Common Errors

**Validation Error (400)**:
```json
{
  "error": {
    "status": 400,
    "name": "ValidationError",
    "message": "name is a required field"
  }
}
```

**Authentication Error (401)**:
```json
{
  "error": {
    "status": 401,
    "name": "UnauthorizedError",
    "message": "Invalid token"
  }
}
```

**Not Found (404)**:
```json
{
  "error": {
    "status": 404,
    "name": "NotFoundError",
    "message": "Profile not found"
  }
}
```

## Query Parameters

### Pagination

Control the number of results and which page to return.

**Parameters**:
- `pagination[page]` - Page number (default: 1)
- `pagination[pageSize]` - Items per page (default: 25, max: 100)
- `pagination[withCount]` - Include total count (default: true)

**Example**:
```
GET /api/profiles?pagination[page]=2&pagination[pageSize]=50
```

**Response**:
```json
{
  "data": [...],
  "meta": {
    "pagination": {
      "page": 2,
      "pageSize": 50,
      "pageCount": 5,
      "total": 250
    }
  }
}
```

### Filtering

Filter results based on field values.

**Operators**:
- `$eq` - Equal to
- `$ne` - Not equal to
- `$lt` - Less than
- `$lte` - Less than or equal
- `$gt` - Greater than
- `$gte` - Greater than or equal
- `$in` - In array
- `$notIn` - Not in array
- `$contains` - Contains (case-sensitive)
- `$notContains` - Does not contain
- `$containsi` - Contains (case-insensitive)
- `$notContainsi` - Does not contain (case-insensitive)
- `$null` - Is null
- `$notNull` - Is not null
- `$between` - Between two values
- `$startsWith` - Starts with
- `$endsWith` - Ends with

**Examples**:

Equal:
```
GET /api/profiles?filters[name][$eq]=Juan Pérez
```

Case-insensitive contains:
```
GET /api/profiles?filters[name][$containsi]=juan
```

Greater than:
```
GET /api/social-program-requests?filters[folio][$gt]=1000
```

In array:
```
GET /api/social-programs?filters[type][$in][0]=federal&filters[type][$in][1]=local
```

Multiple filters (AND):
```
GET /api/profiles?filters[name][$containsi]=juan&filters[sector][$eq]=Norte
```

OR operator:
```
GET /api/profiles?filters[$or][0][name][$containsi]=juan&filters[$or][1][curp][$containsi]=juan
```

### Population

Control which relations to include in the response.

**Populate all relations**:
```
GET /api/social-program-requests?populate=*
```

**Populate specific relation**:
```
GET /api/social-program-requests?populate[user]=*
```

**Populate nested relations**:
```
GET /api/social-program-requests?populate[user][populate][0]=tenant
```

**Populate with field selection**:
```
GET /api/social-program-requests?populate[user][fields][0]=name&populate[user][fields][1]=curp
```

### Sorting

Sort results by one or more fields.

**Ascending**:
```
GET /api/profiles?sort=name:asc
```

**Descending**:
```
GET /api/profiles?sort=createdAt:desc
```

**Multiple fields**:
```
GET /api/calles?sort[0]=tipo:asc&sort[1]=nombre:asc
```

### Field Selection

Limit which fields are returned.

**Select specific fields**:
```
GET /api/profiles?fields[0]=name&fields[1]=curp&fields[2]=phone
```

**Example Response**:
```json
{
  "data": [
    {
      "id": 1,
      "documentId": "abc123",
      "attributes": {
        "name": "Juan Pérez",
        "curp": "JUAP850101HJCRRN01",
        "phone": "3331234567"
      }
    }
  ]
}
```

## Endpoints

### Authentication Endpoints

#### Login

Authenticate and receive JWT token.

**Endpoint**: `POST /auth/local`

**Request**:
```json
{
  "identifier": "user@example.com",
  "password": "SecurePassword123"
}
```

**Response**: `200 OK`
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

**cURL**:
```bash
curl -X POST https://api.gobify.app/api/auth/local \
  -H "Content-Type: application/json" \
  -d '{
    "identifier": "user@example.com",
    "password": "SecurePassword123"
  }'
```

---

#### Register

Create new user account.

**Endpoint**: `POST /auth/local/register`

**Request**:
```json
{
  "username": "newuser",
  "email": "newuser@example.com",
  "password": "SecurePassword123"
}
```

**Response**: `200 OK`
```json
{
  "jwt": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": {
    "id": 2,
    "username": "newuser",
    "email": "newuser@example.com",
    "confirmed": false,
    "blocked": false
  }
}
```

---

#### Forgot Password

Request password reset.

**Endpoint**: `POST /auth/forgot-password`

**Request**:
```json
{
  "email": "user@example.com"
}
```

**Response**: `200 OK`
```json
{
  "ok": true
}
```

---

#### Reset Password

Reset password with code.

**Endpoint**: `POST /auth/reset-password`

**Request**:
```json
{
  "code": "reset-code-from-email",
  "password": "NewSecurePassword123",
  "passwordConfirmation": "NewSecurePassword123"
}
```

**Response**: `200 OK`
```json
{
  "jwt": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "user": { /* user object */ }
}
```

---

### Profiles Endpoints

Manage citizen profiles.

#### List Profiles

**Endpoint**: `GET /profiles`

**Query Parameters**:
- `pagination[page]` - Page number
- `pagination[pageSize]` - Items per page
- `filters[name][$containsi]` - Search by name
- `filters[curp][$containsi]` - Search by CURP
- `filters[sector][$eq]` - Filter by sector
- `populate` - Include relations
- `sort` - Sort order

**Response**: `200 OK`
```json
{
  "data": [
    {
      "id": 1,
      "documentId": "abc123xyz",
      "attributes": {
        "name": "Juan",
        "first_last_name": "Pérez",
        "second_last_name": "García",
        "curp": "JUAP850101HJCRRN01",
        "birthdate": "1985-01-01",
        "phone": "3331234567",
        "phone2": "3339876543",
        "sector": "Norte",
        "address": "Av. Principal #123",
        "lat": 20.6534,
        "lng": -105.2253,
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

**cURL**:
```bash
curl -X GET "https://api.gobify.app/api/profiles?pagination[page]=1&pagination[pageSize]=25&filters[name][\$containsi]=juan" \
  -H "Authorization: Bearer YOUR_TOKEN"
```

**JavaScript**:
```javascript
const response = await fetch(
  'https://api.gobify.app/api/profiles?pagination[page]=1&pagination[pageSize]=25',
  {
    headers: {
      'Authorization': `Bearer ${token}`
    }
  }
);
const data = await response.json();
```

---

#### Get Profile

**Endpoint**: `GET /profiles/:id`

**Parameters**:
- `id` - Profile ID or documentId

**Query Parameters**:
- `populate` - Include relations

**Response**: `200 OK`
```json
{
  "data": {
    "id": 1,
    "documentId": "abc123xyz",
    "attributes": {
      "name": "Juan",
      "first_last_name": "Pérez",
      "second_last_name": "García",
      "curp": "JUAP850101HJCRRN01",
      "birthdate": "1985-01-01",
      "phone": "3331234567",
      "phone2": "3339876543",
      "sector": "Norte",
      "address": "Av. Principal #123",
      "lat": 20.6534,
      "lng": -105.2253
    }
  }
}
```

**cURL**:
```bash
curl -X GET https://api.gobify.app/api/profiles/1 \
  -H "Authorization: Bearer YOUR_TOKEN"
```

---

#### Create Profile

**Endpoint**: `POST /profiles`

**Request**:
```json
{
  "data": {
    "name": "Juan",
    "first_last_name": "Pérez",
    "second_last_name": "García",
    "curp": "JUAP850101HJCRRN01",
    "birthdate": "1985-01-01",
    "phone": "3331234567",
    "sector": "Norte",
    "address": "Av. Principal #123",
    "lat": 20.6534,
    "lng": -105.2253,
    "tenant": 1
  }
}
```

**Response**: `201 Created`
```json
{
  "data": {
    "id": 2,
    "documentId": "def456uvw",
    "attributes": {
      "name": "Juan",
      "first_last_name": "Pérez",
      /* ... */
    }
  }
}
```

**cURL**:
```bash
curl -X POST https://api.gobify.app/api/profiles \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{
    "data": {
      "name": "Juan",
      "first_last_name": "Pérez",
      "curp": "JUAP850101HJCRRN01",
      "phone": "3331234567"
    }
  }'
```

---

#### Update Profile

**Endpoint**: `PUT /profiles/:id`

**Parameters**:
- `id` - Profile ID or documentId

**Request**:
```json
{
  "data": {
    "phone": "3339999999",
    "address": "Nueva Dirección #456"
  }
}
```

**Response**: `200 OK`
```json
{
  "data": {
    "id": 1,
    "documentId": "abc123xyz",
    "attributes": {
      "name": "Juan",
      "phone": "3339999999",
      "address": "Nueva Dirección #456",
      /* ... */
    }
  }
}
```

---

#### Delete Profile

**Endpoint**: `DELETE /profiles/:id`

**Parameters**:
- `id` - Profile ID or documentId

**Response**: `200 OK`
```json
{
  "data": {
    "id": 1,
    "documentId": "abc123xyz",
    "attributes": { /* deleted profile data */ }
  }
}
```

---

### Social Programs Endpoints

Manage social assistance programs.

#### List Social Programs

**Endpoint**: `GET /social-programs`

**Query Parameters**:
- `filters[type][$eq]` - Filter by type (federal/local)
- `filters[name][$containsi]` - Search by name
- `populate[department]=*` - Include department
- `populate[area]=*` - Include area

**Response**: `200 OK`
```json
{
  "data": [
    {
      "id": 1,
      "documentId": "prog123abc",
      "attributes": {
        "name": "Apoyo Alimentario",
        "type": "local",
        "target_audience": "Familias de escasos recursos",
        "createdAt": "2024-01-15T10:30:00.000Z",
        "updatedAt": "2024-01-15T10:30:00.000Z"
      }
    }
  ],
  "meta": {
    "pagination": {
      "page": 1,
      "pageSize": 25,
      "pageCount": 2,
      "total": 50
    }
  }
}
```

---

#### Get Social Program

**Endpoint**: `GET /social-programs/:id`

**Parameters**:
- `id` - Program ID or documentId

**Response**: `200 OK`
```json
{
  "data": {
    "id": 1,
    "documentId": "prog123abc",
    "attributes": {
      "name": "Apoyo Alimentario",
      "type": "local",
      "target_audience": "Familias de escasos recursos",
      "description": [
        {
          "__component": "shared.rich-text",
          "body": "Programa de apoyo..."
        }
      ]
    }
  }
}
```

---

#### Create Social Program

**Endpoint**: `POST /social-programs`

**Request**:
```json
{
  "data": {
    "name": "Nuevo Programa",
    "type": "local",
    "target_audience": "Adultos mayores",
    "department": 1,
    "area": 2,
    "tenant": 1
  }
}
```

**Response**: `201 Created`

---

#### Update Social Program

**Endpoint**: `PUT /social-programs/:id`

**Request**:
```json
{
  "data": {
    "name": "Programa Actualizado",
    "target_audience": "Nueva audiencia"
  }
}
```

**Response**: `200 OK`

---

#### Delete Social Program

**Endpoint**: `DELETE /social-programs/:id`

**Response**: `200 OK`

---

### Social Program Requests Endpoints

Manage program applications and deliveries.

#### List Social Program Requests

**Endpoint**: `GET /social-program-requests`

**Query Parameters**:
- `filters[folio][$eq]` - Filter by folio number
- `filters[request_status][$eq]` - Filter by status
- `filters[social_program][documentId][$eq]` - Filter by program
- `populate[user]=*` - Include beneficiary
- `populate[social_program]=*` - Include program

**Response**: `200 OK`
```json
{
  "data": [
    {
      "id": 1,
      "documentId": "req123xyz",
      "attributes": {
        "folio": 12345,
        "type": "local",
        "request_status": "Validado",
        "calle": "Av. Juárez",
        "numero_exterior": "123",
        "colonia": "Centro",
        "material": "Despensa básica",
        "createdAt": "2024-01-15T10:30:00.000Z",
        "updatedAt": "2024-01-15T10:30:00.000Z"
      }
    }
  ],
  "meta": {
    "pagination": {
      "page": 1,
      "pageSize": 25,
      "pageCount": 100,
      "total": 2500
    }
  }
}
```

**cURL**:
```bash
curl -X GET "https://api.gobify.app/api/social-program-requests?filters[request_status][\$eq]=Validado&populate=*" \
  -H "Authorization: Bearer YOUR_TOKEN"
```

---

#### Get Social Program Request

**Endpoint**: `GET /social-program-requests/:id`

**Parameters**:
- `id` - Request ID or documentId

**Query Parameters**:
- `populate=*` - Include all relations

**Response**: `200 OK`
```json
{
  "data": {
    "id": 1,
    "documentId": "req123xyz",
    "attributes": {
      "folio": 12345,
      "type": "local",
      "request_status": "Validado",
      "calle": "Av. Juárez",
      "numero_exterior": "123",
      "numero_interior": "A",
      "entre_calle": "Calle 1",
      "y_calle": "Calle 2",
      "colonia": "Centro",
      "material": "Despensa básica",
      "telefono": "3331234567",
      "telefono_secundario": "3339876543",
      "foto_vivienda": {
        "url": "https://storage.googleapis.com/..."
      },
      "foto_entrega": {
        "url": "https://storage.googleapis.com/..."
      }
    }
  }
}
```

---

#### Create Social Program Request

**Endpoint**: `POST /social-program-requests`

**Request (Basic)**:
```json
{
  "data": {
    "user": 1,
    "social_program": 1,
    "type": "local",
    "request_status": "En proceso",
    "calle": "Av. Juárez",
    "numero_exterior": "123",
    "colonia": "Centro",
    "material": "Despensa básica",
    "telefono": "3331234567"
  }
}
```

**Request (School Program)**:
```json
{
  "data": {
    "user": 1,
    "social_program": 2,
    "type": "local",
    "request_status": "En proceso",
    "codigo_escuela": "ESC001",
    "grado": "3",
    "grupo": "A",
    "alumno_nombre": "Pedro",
    "alumno_primer_apellido": "López",
    "alumno_segundo_apellido": "Martínez",
    "alumno_curp": "LOMP100515HJCRRD01",
    "sexo": "MASCULINO",
    "talla_uniforme": "10",
    "talla_zapato": "22",
    "tutor_nombre": "María",
    "tutor_primer_apellido": "López",
    "tutor_segundo_apellido": "García",
    "telefono": "3331234567"
  }
}
```

**Response**: `201 Created`

---

#### Update Social Program Request

**Endpoint**: `PUT /social-program-requests/:id`

**Request**:
```json
{
  "data": {
    "request_status": "Entregado",
    "foto_entrega": 123
  }
}
```

**Response**: `200 OK`

---

#### Delete Social Program Request

**Endpoint**: `DELETE /social-program-requests/:id`

**Response**: `200 OK`

---

### Departments & Areas Endpoints

Manage organizational structure.

#### List Departments

**Endpoint**: `GET /departments`

**Response**: `200 OK`
```json
{
  "data": [
    {
      "id": 1,
      "documentId": "dept123",
      "attributes": {
        "name": "Desarrollo Social",
        "description": "Departamento encargado de...",
        "createdAt": "2024-01-15T10:30:00.000Z"
      }
    }
  ]
}
```

---

#### List Areas

**Endpoint**: `GET /areas`

**Query Parameters**:
- `filters[department][documentId][$eq]` - Filter by department

**Response**: `200 OK`
```json
{
  "data": [
    {
      "id": 1,
      "documentId": "area123",
      "attributes": {
        "name": "Programas Alimentarios",
        "description": "Área responsable de...",
        "createdAt": "2024-01-15T10:30:00.000Z"
      }
    }
  ]
}
```

---

### Streets & Neighborhoods Endpoints

Manage geographic catalogs.

#### List Streets

**Endpoint**: `GET /calles`

**Query Parameters**:
- `filters[tipo][$containsi]` - Search by type
- `filters[nombre][$containsi]` - Search by name
- `sort[0]=tipo:asc&sort[1]=nombre:asc` - Sort by type and name

**Response**: `200 OK`
```json
{
  "data": [
    {
      "id": 1,
      "documentId": "calle123",
      "attributes": {
        "tipo": "Avenida",
        "nombre": "Juárez",
        "municipio": "Puerto Vallarta",
        "createdAt": "2024-01-15T10:30:00.000Z"
      }
    },
    {
      "id": 2,
      "documentId": "calle456",
      "attributes": {
        "tipo": "Calle",
        "nombre": "Morelos",
        "municipio": "Puerto Vallarta",
        "createdAt": "2024-01-15T10:30:00.000Z"
      }
    }
  ],
  "meta": {
    "pagination": {
      "page": 1,
      "pageSize": 25,
      "pageCount": 50,
      "total": 1250
    }
  }
}
```

**cURL**:
```bash
curl -X GET "https://api.gobify.app/api/calles?filters[nombre][\$containsi]=juarez&sort=nombre:asc" \
  -H "Authorization: Bearer YOUR_TOKEN"
```

---

#### List Neighborhoods

**Endpoint**: `GET /colonias`

**Query Parameters**:
- `filters[nombre][$containsi]` - Search by name
- `filters[codigo_postal][$eq]` - Filter by postal code

**Response**: `200 OK`
```json
{
  "data": [
    {
      "id": 1,
      "documentId": "colonia123",
      "attributes": {
        "nombre": "Centro",
        "codigo_postal": "48300",
        "municipio": "Puerto Vallarta",
        "createdAt": "2024-01-15T10:30:00.000Z"
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

---

### Reports Endpoints

Manage citizen reports.

#### List Reports

**Endpoint**: `GET /reports`

**Query Parameters**:
- `filters[status][$eq]` - Filter by status
- `filters[report_type][documentId][$eq]` - Filter by type
- `populate[user]=*` - Include reporter
- `populate[photos]=*` - Include photos

**Response**: `200 OK`
```json
{
  "data": [
    {
      "id": 1,
      "documentId": "report123",
      "attributes": {
        "title": "Bache en calle",
        "description": "Hay un bache grande...",
        "status": "En proceso",
        "address": "Av. Principal #123",
        "lat": 20.6534,
        "lng": -105.2253,
        "createdAt": "2024-01-15T10:30:00.000Z"
      }
    }
  ]
}
```

---

### Articles Endpoints

Manage content and news.

#### List Articles

**Endpoint**: `GET /articles`

**Query Parameters**:
- `filters[title][$containsi]` - Search by title
- `filters[article_category][documentId][$eq]` - Filter by category
- `populate[cover_image]=*` - Include cover image
- `sort=published_at:desc` - Sort by date

**Response**: `200 OK`
```json
{
  "data": [
    {
      "id": 1,
      "documentId": "article123",
      "attributes": {
        "title": "Nuevo programa social",
        "slug": "nuevo-programa-social",
        "excerpt": "Se anuncia nuevo programa...",
        "content": "El gobierno municipal anuncia...",
        "published_at": "2024-01-15T10:30:00.000Z",
        "createdAt": "2024-01-15T10:30:00.000Z"
      }
    }
  ]
}
```

---

### Procedures Endpoints

Manage administrative procedures.

#### List Procedures

**Endpoint**: `GET /procedures`

**Query Parameters**:
- `filters[name][$containsi]` - Search by name
- `filters[department][documentId][$eq]` - Filter by department
- `populate[department]=*` - Include department

**Response**: `200 OK`
```json
{
  "data": [
    {
      "id": 1,
      "documentId": "proc123",
      "attributes": {
        "name": "Solicitud de apoyo",
        "description": "Trámite para solicitar...",
        "requirements": "1. Identificación oficial\n2. Comprobante de domicilio",
        "cost": 0,
        "duration": "5 días hábiles",
        "createdAt": "2024-01-15T10:30:00.000Z"
      }
    }
  ]
}
```

---

### Tenants Endpoints

Manage multi-tenant organizations.

#### List Tenants

**Endpoint**: `GET /tenants`

**Response**: `200 OK`
```json
{
  "data": [
    {
      "id": 1,
      "documentId": "tenant123",
      "attributes": {
        "name": "Gobierno Municipal",
        "slug": "gobierno-municipal",
        "createdAt": "2024-01-15T10:30:00.000Z"
      }
    }
  ]
}
```

---

## Rate Limiting

The API implements rate limiting to prevent abuse.

**Limits**:
- Authenticated: 1000 requests per hour
- Unauthenticated: 100 requests per hour

**Headers**:
```
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 995
X-RateLimit-Reset: 1641024000
```

**Rate Limit Exceeded (429)**:
```json
{
  "error": {
    "status": 429,
    "name": "RateLimitError",
    "message": "Too many requests, please try again later"
  }
}
```

## Versioning

The API is currently at version 1. Future versions will be indicated in the URL path.

**Current**: `/api/*`
**Future**: `/api/v2/*` (when released)

Breaking changes will be introduced in new versions while maintaining backward compatibility for existing versions.

## Best Practices

1. **Use Pagination**: Always paginate large collections
2. **Populate Wisely**: Only populate relations you need
3. **Cache Responses**: Cache GET requests to reduce API calls
4. **Handle Errors**: Implement proper error handling
5. **Use HTTPS**: Always use HTTPS in production
6. **Store Tokens Securely**: Never expose JWT tokens in client code
7. **Validate Input**: Validate data before sending to API
8. **Use Field Selection**: Request only needed fields
9. **Implement Retries**: Add retry logic for transient errors
10. **Monitor Rate Limits**: Track rate limit headers

## Support

For API issues or questions:
- Documentation: https://api.gobify.app/documentation
- Support: support@gobify.app

---

**API Version**: 1.0
**Last Updated**: December 2024
**Powered by**: Strapi 5.15.0
