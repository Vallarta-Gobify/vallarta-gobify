# Installation Guide

Complete step-by-step guide to install and configure the Gobify platform on your local development environment.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Backend Installation](#backend-installation)
- [Frontend Installation](#frontend-installation)
- [Database Setup](#database-setup)
- [Environment Configuration](#environment-configuration)
- [First Run](#first-run)
- [Verification](#verification)
- [Troubleshooting](#troubleshooting)

## Prerequisites

Ensure you have the following software installed on your system:

### Required Software

| Software | Minimum Version | Recommended | Download |
|----------|----------------|-------------|----------|
| Node.js | 18.0.0 | 18.x LTS | https://nodejs.org/ |
| npm | 9.8.1 | Latest | Included with Node.js |
| PostgreSQL | 14.0 | 15.x | https://www.postgresql.org/ |
| Git | 2.x | Latest | https://git-scm.com/ |

### Optional Software

| Software | Purpose | Download |
|----------|---------|----------|
| Docker | Containerized deployment | https://www.docker.com/ |
| pgAdmin | PostgreSQL GUI | https://www.pgadmin.org/ |
| Postman | API testing | https://www.postman.com/ |

### Verify Installation

Check that prerequisites are correctly installed:

```bash
# Check Node.js version (should be 18+)
node --version

# Check npm version
npm --version

# Check PostgreSQL
psql --version

# Check Git
git --version
```

## Backend Installation

### 1. Clone the Repository

```bash
# Clone the repository
git clone <repository-url>
cd Vallarta-Gobify
```

### 2. Navigate to Backend Directory

```bash
cd gobify-backend
```

### 3. Install Dependencies

```bash
# Install all npm packages
npm install
```

This will install:
- Strapi 5.15.0 and core plugins
- PostgreSQL driver (pg)
- Meilisearch plugin
- Firebase Storage provider
- All other dependencies

**Expected installation time**: 2-5 minutes depending on your connection.

### 4. Configure Environment Variables

Create a `.env` file in the `gobify-backend` directory:

```bash
# Copy the example file
cp .env.example .env

# Edit the file with your preferred editor
nano .env
# or
vim .env
```

**Required environment variables:**

```env
# Server Configuration
HOST=0.0.0.0
PORT=1337

# Security Keys (IMPORTANT: Change these in production!)
APP_KEYS="generate-random-key-1,generate-random-key-2"
API_TOKEN_SALT=generate-random-salt
ADMIN_JWT_SECRET=generate-random-secret
TRANSFER_TOKEN_SALT=generate-random-salt
JWT_SECRET=generate-random-secret

# Database Connection
DATABASE_URL=postgresql://postgres:password@localhost:5432/gobify

# Alternative database configuration (if not using DATABASE_URL)
DATABASE_CLIENT=postgres
DATABASE_HOST=localhost
DATABASE_PORT=5432
DATABASE_NAME=gobify
DATABASE_USERNAME=postgres
DATABASE_PASSWORD=password
DATABASE_SSL=false

# Meilisearch Configuration
MEILISEARCH_HOST=http://localhost:7700
MEILISEARCH_API_KEY=your-master-key

# Firebase Storage
STORAGE_BUCKET_URL=gobify-app.appspot.com

# Environment
NODE_ENV=development
```

**Generate secure random keys:**

```bash
# Generate random strings for secrets (Linux/Mac)
openssl rand -base64 32

# Or use Node.js
node -e "console.log(require('crypto').randomBytes(32).toString('base64'))"
```

### 5. Setup PostgreSQL Database

Create the database for Gobify:

```bash
# Connect to PostgreSQL
psql -U postgres

# Create database
CREATE DATABASE gobify;

# Create user (optional, if not using default postgres user)
CREATE USER gobify_user WITH PASSWORD 'secure_password';
GRANT ALL PRIVILEGES ON DATABASE gobify TO gobify_user;

# Exit
\q
```

Or using command line:

```bash
# Create database directly
createdb -U postgres gobify
```

### 6. Install and Configure Meilisearch (Optional but Recommended)

Meilisearch provides fast full-text search for social program requests.

**Using Docker:**
```bash
docker run -d \
  --name meilisearch \
  -p 7700:7700 \
  -e MEILI_MASTER_KEY=your-master-key \
  -v $(pwd)/meili_data:/meili_data \
  getmeili/meilisearch:latest
```

**Or download binary:**
```bash
# Download for your OS from https://www.meilisearch.com/docs/learn/getting_started/installation
# Then run:
./meilisearch --master-key=your-master-key
```

### 7. Build and Start Backend

```bash
# Build the Strapi admin panel
npm run build

# Start in development mode
npm run dev
```

The backend will be available at:
- **API**: http://localhost:1337
- **Admin Panel**: http://localhost:1337/admin

### 8. Create Admin User

On first run, Strapi will prompt you to create an admin user:

1. Open http://localhost:1337/admin
2. Fill in the registration form:
   - First name
   - Last name
   - Email (will be your username)
   - Password (minimum 8 characters)
3. Click "Let's start"

## Frontend Installation

### 1. Navigate to Frontend Directory

```bash
# From the project root
cd gobify-portals
```

### 2. Install Dependencies

```bash
# Install all workspace dependencies
npm install
```

This installs dependencies for:
- Root workspace
- `apps/gobify-admin-portal`
- All shared packages in `packages/`

**Expected installation time**: 3-7 minutes depending on your connection.

### 3. Configure Environment Variables

The frontend uses environment variables for API connection and external services.

**Note**: Check if `apps/gobify-admin-portal/.env.local` exists. If not, create it:

```bash
cd apps/gobify-admin-portal
touch .env.local
```

Add the following variables:

```env
# API Configuration
NEXT_PUBLIC_API_URL=http://localhost:1337/api
NEXT_PUBLIC_STRAPI_URL=http://localhost:1337

# Mapbox Configuration (required for maps)
NEXT_PUBLIC_MAPBOX_TOKEN=your-mapbox-public-token

# Meilisearch Configuration (for search)
NEXT_PUBLIC_MEILISEARCH_HOST=http://localhost:7700
NEXT_PUBLIC_MEILISEARCH_API_KEY=your-search-key

# Authentication
NEXT_PUBLIC_JWT_EXPIRATION=7d

# Environment
NODE_ENV=development
```

**Get a Mapbox token:**
1. Create account at https://account.mapbox.com/
2. Go to https://account.mapbox.com/access-tokens/
3. Copy your default public token or create a new one

### 4. Build Shared Packages

Before running the admin portal, build the shared packages:

```bash
# From gobify-portals root
npm run build
```

This builds:
- `@repo/strapi-client` - API client
- `@repo/pdf-generator` - PDF generation utilities
- Other shared packages

### 5. Start Frontend

```bash
# Start all apps in development mode
npm run dev
```

Or start only the admin portal:

```bash
cd apps/gobify-admin-portal
npm run dev
```

The frontend will be available at:
- **Admin Portal**: http://localhost:3000

## Database Setup

### Initial Migration

Strapi automatically creates database tables on first run. If you need to manually run migrations:

```bash
cd gobify-backend
npm run strapi db:migrate
```

### Seed Sample Data

Populate the database with example data:

```bash
cd gobify-backend
npm run seed:example
```

This creates:
- Sample tenant
- Test departments and areas
- Example social programs
- Sample streets and neighborhoods
- Test citizen profiles

The seed script reads from `scripts/data.json` and populates all content types.

## Environment Configuration

### Backend Environment Variables Reference

```env
# ============================================
# Server Configuration
# ============================================
HOST=0.0.0.0                              # Server host
PORT=1337                                  # Server port

# ============================================
# Security (CHANGE IN PRODUCTION!)
# ============================================
APP_KEYS="key1,key2,key3,key4"            # Comma-separated keys
API_TOKEN_SALT=random-string               # API token salt
ADMIN_JWT_SECRET=random-string             # Admin JWT secret
TRANSFER_TOKEN_SALT=random-string          # Transfer token salt
JWT_SECRET=random-string                   # Public JWT secret

# ============================================
# Database
# ============================================
DATABASE_URL=postgresql://user:pass@host:5432/dbname
# OR individual parameters:
DATABASE_CLIENT=postgres
DATABASE_HOST=localhost
DATABASE_PORT=5432
DATABASE_NAME=gobify
DATABASE_USERNAME=postgres
DATABASE_PASSWORD=your-password
DATABASE_SSL=false

# ============================================
# Meilisearch (Optional but Recommended)
# ============================================
MEILISEARCH_HOST=http://localhost:7700
MEILISEARCH_API_KEY=your-master-key

# ============================================
# Firebase Storage (Required for file uploads)
# ============================================
STORAGE_BUCKET_URL=gobify-app.appspot.com
# Note: Firebase service account is configured in config/plugins.ts

# ============================================
# Other
# ============================================
NODE_ENV=development                       # development | production
```

### Frontend Environment Variables Reference

```env
# ============================================
# API Configuration
# ============================================
NEXT_PUBLIC_API_URL=http://localhost:1337/api
NEXT_PUBLIC_STRAPI_URL=http://localhost:1337

# ============================================
# External Services
# ============================================
NEXT_PUBLIC_MAPBOX_TOKEN=pk.xxxxx...       # Mapbox public token
NEXT_PUBLIC_MEILISEARCH_HOST=http://localhost:7700
NEXT_PUBLIC_MEILISEARCH_API_KEY=search-key

# ============================================
# Authentication
# ============================================
NEXT_PUBLIC_JWT_EXPIRATION=7d              # Token expiration

# ============================================
# Features (Optional)
# ============================================
NEXT_PUBLIC_ENABLE_ANALYTICS=false
NEXT_PUBLIC_ENABLE_ERROR_REPORTING=false

# ============================================
# Environment
# ============================================
NODE_ENV=development                        # development | production
```

## First Run

### 1. Start Backend

```bash
cd gobify-backend
npm run dev
```

**Expected output:**
```
[2024-12-08 10:00:00.000] info: Starting Strapi application...
[2024-12-08 10:00:05.000] info: Database connection established
[2024-12-08 10:00:10.000] info: Server listening on http://0.0.0.0:1337
```

### 2. Create Admin User

1. Visit http://localhost:1337/admin
2. Complete the registration form
3. Log in with your credentials

### 3. Configure API Permissions

Set up public access for the API (if needed):

1. In Strapi admin, go to **Settings** → **Users & Permissions** → **Roles**
2. Click on **Public** role
3. Expand each content type and enable permissions:
   - For **Profile**, **Social-Program**, etc., enable `find` and `findOne`
   - For **Auth**, enable all methods
4. Click **Save**

### 4. Seed Database (Optional)

```bash
npm run seed:example
```

### 5. Start Frontend

```bash
cd gobify-portals
npm run dev
```

**Expected output:**
```
> turbo run dev

• Packages in scope: gobify-admin-portal, @repo/strapi-client, ...
• Running dev in 1 packages
gobify-admin-portal:dev: ready - started server on 0.0.0.0:3000
```

### 6. Access the Application

- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:1337/api
- **Strapi Admin**: http://localhost:1337/admin

## Verification

Verify that everything is working correctly:

### 1. Backend Health Check

```bash
# Test API connection
curl http://localhost:1337/api/tenants

# Expected response: JSON array of tenants or empty array
```

### 2. Frontend Health Check

1. Open http://localhost:3000
2. You should see the login page
3. Try logging in (if you created test users via seed)

### 3. Database Connection

```bash
# Connect to database and verify tables
psql -U postgres -d gobify -c "\dt"

# Should list tables like: profiles, social_programs, etc.
```

### 4. Check Logs

**Backend logs:**
```bash
# Terminal where you ran npm run dev should show:
# - Database connection successful
# - Server started
# - No error messages
```

**Frontend logs:**
```bash
# Terminal should show:
# - Compiled successfully
# - ready - started server on 0.0.0.0:3000
# - No compilation errors
```

## Troubleshooting

### Backend Issues

#### Problem: "Database connection failed"

**Solution:**
1. Verify PostgreSQL is running:
   ```bash
   # Check PostgreSQL status
   pg_ctl status
   # or
   systemctl status postgresql
   ```
2. Verify connection string in `.env`:
   ```env
   DATABASE_URL=postgresql://postgres:password@localhost:5432/gobify
   ```
3. Test connection manually:
   ```bash
   psql -U postgres -d gobify
   ```

#### Problem: "Port 1337 already in use"

**Solution:**
1. Find process using port:
   ```bash
   lsof -i :1337
   ```
2. Kill the process:
   ```bash
   kill -9 <PID>
   ```
3. Or change port in `.env`:
   ```env
   PORT=1338
   ```

#### Problem: "Meilisearch connection failed"

**Solution:**
1. Verify Meilisearch is running:
   ```bash
   curl http://localhost:7700/health
   ```
2. If not running, start it:
   ```bash
   docker start meilisearch
   # or
   ./meilisearch --master-key=your-key
   ```
3. Update `MEILISEARCH_HOST` in `.env` if needed

#### Problem: "Firebase Storage upload failed"

**Solution:**
1. Verify Firebase configuration in `config/plugins.ts`
2. Check service account credentials
3. Verify bucket exists and is accessible
4. Check Firebase Storage rules

### Frontend Issues

#### Problem: "Cannot connect to API"

**Solution:**
1. Verify backend is running at http://localhost:1337
2. Check `NEXT_PUBLIC_API_URL` in `.env.local`
3. Open browser console and check for CORS errors
4. Verify Strapi API permissions are configured

#### Problem: "Mapbox token invalid"

**Solution:**
1. Get new token from https://account.mapbox.com/
2. Update `NEXT_PUBLIC_MAPBOX_TOKEN` in `.env.local`
3. Restart the Next.js dev server

#### Problem: "Module not found errors"

**Solution:**
1. Delete node_modules and reinstall:
   ```bash
   rm -rf node_modules package-lock.json
   npm install
   ```
2. If in monorepo, do this in both root and app directory:
   ```bash
   cd gobify-portals
   rm -rf node_modules package-lock.json
   cd apps/gobify-admin-portal
   rm -rf node_modules
   cd ../..
   npm install
   ```

#### Problem: "Build failed - TypeScript errors"

**Solution:**
1. Check TypeScript version:
   ```bash
   npm list typescript
   ```
2. Verify `tsconfig.json` extends the shared config
3. Run type check:
   ```bash
   npm run type-check
   ```
4. Fix reported errors

### Database Issues

#### Problem: "Database migration failed"

**Solution:**
1. Drop and recreate database:
   ```bash
   dropdb -U postgres gobify
   createdb -U postgres gobify
   ```
2. Restart Strapi:
   ```bash
   npm run dev
   ```

#### Problem: "Permission denied for database"

**Solution:**
```sql
-- Grant all privileges to user
GRANT ALL PRIVILEGES ON DATABASE gobify TO your_user;
GRANT ALL ON SCHEMA public TO your_user;
```

### Common Errors

#### Error: "node: command not found"

Install Node.js 18+ from https://nodejs.org/

#### Error: "pg: command not found"

Install PostgreSQL from https://www.postgresql.org/download/

#### Error: "EADDRINUSE: address already in use"

Port is already in use. Kill the process or use a different port.

#### Error: "Maximum call stack size exceeded"

Usually caused by circular dependencies. Check recent code changes.

## Next Steps

After successful installation:

1. **Read the documentation**:
   - [BACKEND.md](./BACKEND.md) - Backend architecture and content types
   - [FRONTEND.md](./FRONTEND.md) - Frontend structure and components
   - [API-REFERENCE.md](./API-REFERENCE.md) - API endpoints documentation

2. **Explore the admin panel**:
   - Create content types in Strapi admin
   - Set up permissions and roles
   - Upload test data

3. **Test the frontend**:
   - Navigate through different pages
   - Create test citizens and programs
   - Generate PDFs and exports

4. **Customize the platform**:
   - Modify content types in Strapi
   - Customize frontend components
   - Add new features

## Support

If you encounter issues not covered in this guide:

1. Check the [Troubleshooting](#troubleshooting) section
2. Review logs for error messages
3. Search the Strapi documentation: https://docs.strapi.io/
4. Search the Next.js documentation: https://nextjs.org/docs
5. Contact the development team

---

**Document Version**: 1.0.0
**Last Updated**: December 2024
