# Gobify Platform - Architecture Overview

This diagram provides a high-level view of the Gobify platform architecture, showing how the frontend, backend, databases, and external services interact.

## System Architecture

```mermaid
graph TB
    subgraph "Client Layer"
        WEB[Web Browser]
        MOBILE[Mobile Browser]
    end

    subgraph "Frontend - Next.js 15"
        NEXTJS[Next.js App Router<br/>Turborepo Monorepo]
        ADMIN[gobify-admin-portal]
        NEXTJS --> ADMIN

        subgraph "Key Libraries"
            TANSTACK[TanStack Query<br/>Server State]
            MAPBOX[Mapbox GL<br/>Maps]
            NEXTUI[NextUI<br/>Components]
        end

        ADMIN --> TANSTACK
        ADMIN --> MAPBOX
        ADMIN --> NEXTUI
    end

    subgraph "Backend - Strapi 5"
        STRAPI[Strapi 5 Headless CMS]

        subgraph "Core Services"
            AUTH[JWT Authentication]
            REST[REST API Layer]
            SEARCH[Search Service]
            UPLOAD[Upload Service]
        end

        STRAPI --> AUTH
        STRAPI --> REST
        STRAPI --> SEARCH
        STRAPI --> UPLOAD

        subgraph "Content Types"
            TENANT[Multi-Tenant System]
            PROFILES[Profiles]
            PROGRAMS[Social Programs]
            REPORTS[Reports]
            ARTICLES[Articles]
            PROCEDURES[Procedures]
            GEO[Geographic Data]
        end

        REST --> TENANT
        REST --> PROFILES
        REST --> PROGRAMS
        REST --> REPORTS
        REST --> ARTICLES
        REST --> PROCEDURES
        REST --> GEO
    end

    subgraph "Data Layer"
        POSTGRES[(PostgreSQL<br/>Main Database)]
        MEILISEARCH[(Meilisearch<br/>Search Engine)]
        FIREBASE[Firebase Storage<br/>File Storage]
    end

    subgraph "External Services"
        MAPS_API[Mapbox API]
        EMAIL[Email Service]
        SMS[SMS Service]
    end

    %% Client connections
    WEB --> NEXTJS
    MOBILE --> NEXTJS

    %% Frontend to Backend
    NEXTJS -->|HTTPS/REST| STRAPI
    NEXTJS -->|api.gobify.app| REST

    %% Backend to Data Layer
    STRAPI --> POSTGRES
    SEARCH --> MEILISEARCH
    UPLOAD --> FIREBASE

    %% Backend to External Services
    STRAPI --> MAPS_API
    STRAPI --> EMAIL
    STRAPI --> SMS

    %% Frontend to External Services
    MAPBOX --> MAPS_API

    style NEXTJS fill:#0070f3
    style STRAPI fill:#8e75ff
    style POSTGRES fill:#336791
    style MEILISEARCH fill:#ff5caa
    style FIREBASE fill:#ffca28
```

## Architecture Components

### Frontend Layer (Next.js 15)
- **Framework**: Next.js 15 with App Router for modern React patterns
- **Build System**: Turborepo for efficient monorepo management
- **State Management**: TanStack Query for server state synchronization
- **UI Components**: NextUI for consistent design system
- **Maps**: Mapbox GL for geographic visualizations
- **Deployment**: Optimized for edge runtime and static generation

### Backend Layer (Strapi 5)
- **CMS**: Strapi 5 Headless CMS for content management
- **API**: RESTful API at api.gobify.app
- **Authentication**: JWT-based authentication and authorization
- **Multi-tenancy**: Tenant-based data isolation
- **Content Types**: 17 main entities managing government services

### Data Layer
- **PostgreSQL**: Primary relational database for structured data
- **Meilisearch**: Fast, typo-tolerant search engine for content discovery
- **Firebase Storage**: Scalable file storage for documents and media

### External Services
- **Mapbox API**: Geographic data and mapping services
- **Email Service**: Notifications and communications
- **SMS Service**: Mobile notifications for citizens

## Key Features

1. **Multi-tenant Architecture**: Supports multiple government departments and services
2. **Real-time Search**: Meilisearch integration for instant search results
3. **Geographic Capabilities**: Street and neighborhood mapping with Mapbox
4. **Social Program Management**: Complete workflow from application to delivery
5. **Report System**: Citizen reports with categorization and tracking
6. **Content Management**: Articles and procedures for public information
7. **Scalable Storage**: Firebase for unlimited file and media storage

## API Communication

All frontend-to-backend communication occurs via:
- **Protocol**: HTTPS/REST
- **Domain**: api.gobify.app
- **Authentication**: JWT tokens in Authorization header
- **Format**: JSON request/response payloads

## Security Considerations

- JWT tokens with configurable expiration
- Multi-tenant data isolation at database level
- Role-based access control (RBAC)
- HTTPS encryption for all communications
- Secure file uploads with validation
- API rate limiting and request validation
