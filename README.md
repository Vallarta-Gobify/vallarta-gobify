# Vallarta-Gobify Platform

Plataforma de administración cívica gubernamental para gestión de ciudadanos, programas sociales, reportes y datos geográficos.

## 📂 Estructura del Repositorio

```
Vallarta-Gobify/
├── gobify-backend/          # Strapi 5 Headless CMS - API Backend
├── gobify-portals/          # Next.js 15 Monorepo - Frontend Applications
├── docs/                    # 📖 Documentación Técnica Completa
└── user-manual/            # 👤 Manual de Usuario
```

## 🚀 Quick Start

### Backend (Strapi 5)
```bash
cd gobify-backend
npm install
cp .env.example .env
# Configurar variables de entorno en .env
npm run dev
# Admin Panel: http://localhost:1337/admin
# API: http://localhost:1337/api
```

### Frontend (Next.js 15)
```bash
cd gobify-portals
npm install
# Configurar STRAPI_API_URL en packages/strapi-client/index.ts
npm run dev
# Application: http://localhost:3000
```

## 📖 Documentación Técnica

### Diagramas de Arquitectura (Mermaid)
- **[Architecture Overview](./docs/architecture-overview.md)** - Arquitectura general del sistema
- **[Database Schema](./docs/database-schema.md)** - Diagrama entidad-relación de la base de datos
- **[Authentication Flow](./docs/authentication-flow.md)** - Flujo de autenticación JWT
- **[Social Program Workflow](./docs/social-program-workflow.md)** - Flujo de trabajo de programas sociales
- **[Deployment Architecture](./docs/deployment-architecture.md)** - Arquitectura de despliegue

### Guías Técnicas
- **[README](./docs/README.md)** - Descripción general del proyecto
- **[Installation Guide](./docs/INSTALLATION.md)** - Guía completa de instalación
- **[Backend Documentation](./docs/BACKEND.md)** - Documentación completa del backend (Strapi 5)
- **[Frontend Documentation](./docs/FRONTEND.md)** - Documentación completa del frontend (Next.js 15)
- **[API Reference](./docs/API-REFERENCE.md)** - Referencia completa de la API REST
- **[Deployment Guide](./docs/DEPLOYMENT.md)** - Guía de despliegue en producción

## 👤 Manual de Usuario

Manual completo para administradores gubernamentales:

- **[Introduction](./user-manual/README.md)** - Índice del manual de usuario
- **[01 - Getting Started](./user-manual/01-getting-started.md)** - Primeros pasos e interfaz
- **[02 - Dashboard](./user-manual/02-dashboard.md)** - Panel de control y KPIs
- **[03 - Managing Citizens](./user-manual/03-managing-citizens.md)** - Gestión de ciudadanos
- **[04 - Social Programs](./user-manual/04-social-programs.md)** - Administración de programas sociales
- **[05 - Geographic Data](./user-manual/05-geographic-data.md)** - Calles y colonias
- **[06 - QR Scanner](./user-manual/06-qr-scanner.md)** - Escaneo de códigos QR
- **[07 - Reports](./user-manual/07-reports.md)** - Gestión de reportes
- **[08 - Tips & Tricks](./user-manual/08-tips-and-tricks.md)** - Consejos y mejores prácticas

## 🏗️ Arquitectura

### Backend (gobify-backend)
- **Framework**: Strapi 5.15.0
- **Database**: PostgreSQL
- **Search**: Meilisearch
- **Storage**: Firebase Storage
- **Auth**: JWT (Users & Permissions plugin)
- **API**: REST at `https://api.gobify.app/api`

**17 Entidades Principales**:
- Multi-tenant: `tenant`
- Ciudadanos: `profile`
- Programas Sociales: `social-program`, `social-program-request`, `social-program-log`
- Organización: `department`, `area`
- Reportes: `report`, `report-type`
- Contenido: `article`, `article-category`, `comment`
- Trámites: `procedure`
- Geografía: `calle`, `colonia`
- Configuración: `global`, `about`

### Frontend (gobify-portals)
- **Framework**: Next.js 15 con App Router
- **Monorepo**: Turborepo
- **UI**: NextUI + Tailwind CSS
- **State**: TanStack Query
- **Forms**: Formik + Yup
- **Maps**: Mapbox GL con clustering
- **Exports**: PDF (con progreso) + Excel

**Aplicación Principal**: `gobify-admin-portal`

**Páginas**:
- Dashboard - KPIs y estadísticas
- Ciudadanos - Gestión con tabla AG Grid (10,000+ registros)
- Programas Sociales - Mapas interactivos, búsqueda, exportación
- Calles - Catálogo de vialidades
- Colonias - Catálogo de colonias
- QR - Escaneo de códigos QR
- Reportes - Gestión de reportes ciudadanos
- Demográfico - Análisis demográfico

## 🔑 Características Principales

### Para Administradores
- ✅ Gestión completa de ciudadanos con búsqueda avanzada
- ✅ Administración de programas sociales federales y locales
- ✅ Mapas interactivos con clustering de beneficiarios
- ✅ Exportación a PDF con tracking de progreso
- ✅ Exportación a Excel
- ✅ Gestión de solicitudes con cambio de estados
- ✅ Catálogos de calles y colonias con edición inline
- ✅ Escaneo de códigos QR
- ✅ Dashboard con KPIs y tendencias
- ✅ Control de acceso basado en roles

### Para Ciudadanos (Próximamente)
- 📱 Portal ciudadano
- 📝 Solicitud de programas sociales
- 📍 Reportes geo-referenciados
- 📄 Seguimiento de trámites

## 🛠️ Stack Tecnológico

### Backend
- Strapi 5.15.0
- PostgreSQL
- Meilisearch 0.13.2
- Firebase Storage
- Node.js 18+

### Frontend
- Next.js 15.3.2
- React 18.3.1
- TypeScript 5.7
- TanStack Query 5.62
- Mapbox GL 3.9
- NextUI 2.6
- Tailwind CSS 3.4
- Turborepo

### Herramientas
- Docker
- npm workspaces
- ESLint + Prettier
- Jest para testing

## 📝 Comandos Importantes

### Backend
```bash
npm run dev              # Desarrollo
npm run build           # Build producción
npm run start           # Servidor producción
npm run seed:example    # Poblar datos de ejemplo
npm run strapi -- admin:reset-user-password  # Reset password
```

### Frontend
```bash
npm run dev             # Desarrollo
npm run dev:turbo       # Desarrollo con Turbo
npm run build           # Build producción
npm run start           # Servidor producción
npm run lint            # Linting
npm test                # Tests
turbo check-types       # Validar tipos
```

## 🔐 Variables de Entorno

Ver guías de instalación para configuración completa:
- [Backend Environment Variables](./docs/INSTALLATION.md#backend-environment-variables)
- [Frontend Environment Variables](./docs/INSTALLATION.md#frontend-environment-variables)

## 📊 Estado del Proyecto

- ✅ Backend: Producción (Strapi 5)
- ✅ Frontend Admin: Producción (Next.js 15)
- 🚧 Portal Ciudadano: En desarrollo
- 🚧 Aplicación Móvil: Planeado

## 🤝 Contribución

1. Clonar repositorio
2. Crear rama feature: `git checkout -b feature/nueva-caracteristica`
3. Commit cambios: `git commit -m "Add nueva característica"`
4. Push a la rama: `git push origin feature/nueva-caracteristica`
5. Crear Pull Request

## 📄 Licencia

Propiedad de Vallarta-Gobify

## 🔗 Enlaces

- **Backend API**: https://api.gobify.app
- **Repositorio Backend**: https://github.com/Vallarta-Gobify/gobify-backend
- **Repositorio Frontend**: https://github.com/Vallarta-Gobify/gobify-portals

## 📞 Soporte

Para soporte técnico o preguntas, contactar al equipo de desarrollo.

---

**Documentación generada automáticamente** - Última actualización: 2025-12-08
