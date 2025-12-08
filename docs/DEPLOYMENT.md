# Deployment Guide

Complete guide for deploying the Gobify platform to production environments.

## Table of Contents

- [Overview](#overview)
- [Pre-deployment Checklist](#pre-deployment-checklist)
- [Backend Deployment](#backend-deployment)
  - [Docker Deployment](#docker-deployment)
  - [Traditional Deployment](#traditional-deployment)
  - [Database Setup](#database-setup)
- [Frontend Deployment](#frontend-deployment)
  - [Vercel Deployment](#vercel-deployment)
  - [Custom Server Deployment](#custom-server-deployment)
- [Environment Configuration](#environment-configuration)
- [SSL/HTTPS Setup](#sslhttps-setup)
- [Domain Configuration](#domain-configuration)
- [Monitoring & Logging](#monitoring--logging)
- [Backup Strategy](#backup-strategy)
- [Performance Optimization](#performance-optimization)
- [Security Hardening](#security-hardening)
- [Continuous Deployment](#continuous-deployment)
- [Rollback Procedures](#rollback-procedures)
- [Troubleshooting](#troubleshooting)

## Overview

The Gobify platform consists of two main components that can be deployed independently:

1. **Backend (Strapi)**: API server that can be deployed via Docker or traditional Node.js hosting
2. **Frontend (Next.js)**: Web application that can be deployed to Vercel, custom servers, or Docker

### Deployment Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                      Load Balancer / CDN                     │
│                    (Cloudflare, AWS CloudFront)              │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│                      Frontend (Next.js)                      │
│                    Vercel / Custom Server                    │
│                    https://gobify.app                        │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌─────────────────────────────────────────────────────────────┐
│                      Backend (Strapi)                        │
│                    Docker / VPS / Cloud                      │
│                https://api.gobify.app/api                    │
└─────────────────────────────────────────────────────────────┘
                            ↓
┌──────────────┬──────────────┬──────────────┬──────────────┐
│  PostgreSQL  │ Meilisearch  │   Firebase   │    Redis     │
│   Database   │    Search    │   Storage    │    Cache     │
└──────────────┴──────────────┴──────────────┴──────────────┘
```

## Pre-deployment Checklist

Before deploying to production, ensure you've completed:

### Backend Checklist

- [ ] Generate secure random keys for all secrets
- [ ] Configure production database (PostgreSQL)
- [ ] Set up Meilisearch instance
- [ ] Configure Firebase Storage with production credentials
- [ ] Enable CORS for frontend domain
- [ ] Configure rate limiting
- [ ] Set up database backups
- [ ] Test all API endpoints
- [ ] Review and configure user roles/permissions
- [ ] Enable SSL/TLS
- [ ] Set NODE_ENV=production

### Frontend Checklist

- [ ] Update API URL to production backend
- [ ] Configure Mapbox production token
- [ ] Set up analytics (if applicable)
- [ ] Configure error tracking (Sentry, etc.)
- [ ] Test all pages and features
- [ ] Run production build locally
- [ ] Optimize images and assets
- [ ] Configure CDN for static assets
- [ ] Set up monitoring
- [ ] Enable HTTPS

### Security Checklist

- [ ] Change all default passwords
- [ ] Rotate JWT secrets
- [ ] Configure firewall rules
- [ ] Enable rate limiting
- [ ] Set up intrusion detection
- [ ] Configure backup retention
- [ ] Review API permissions
- [ ] Enable audit logging
- [ ] Set up SSL certificates
- [ ] Configure CSP headers

## Backend Deployment

### Docker Deployment

Docker is the recommended deployment method for the backend.

#### 1. Build Docker Image

The backend includes a Dockerfile at `/Users/manny/Projects/agilgob/Vallarta-Gobify/gobify-backend/Dockerfile`.

```bash
cd gobify-backend

# Build the image
docker build -t gobify-backend:latest .
```

**Dockerfile**:
```dockerfile
# Use Node.js 18 Alpine
FROM node:18-alpine

# Set working directory
WORKDIR /usr/src/app

# Copy package files
COPY package.json ./

# Install dependencies
RUN npm install

# Copy application code
COPY . .

# Build admin panel
RUN npm run build

# Expose port
EXPOSE 1337

# Start application
CMD ["npm", "start"]
```

#### 2. Create docker-compose.yml

For a complete stack including database and search:

```yaml
version: '3.8'

services:
  # PostgreSQL Database
  postgres:
    image: postgres:15-alpine
    container_name: gobify-postgres
    environment:
      POSTGRES_DB: gobify
      POSTGRES_USER: gobify_user
      POSTGRES_PASSWORD: ${DB_PASSWORD}
    volumes:
      - postgres_data:/var/lib/postgresql/data
    ports:
      - "5432:5432"
    restart: unless-stopped
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U gobify_user"]
      interval: 10s
      timeout: 5s
      retries: 5

  # Meilisearch
  meilisearch:
    image: getmeili/meilisearch:latest
    container_name: gobify-meilisearch
    environment:
      MEILI_MASTER_KEY: ${MEILISEARCH_MASTER_KEY}
      MEILI_ENV: production
    volumes:
      - meilisearch_data:/meili_data
    ports:
      - "7700:7700"
    restart: unless-stopped

  # Strapi Backend
  strapi:
    image: gobify-backend:latest
    container_name: gobify-backend
    environment:
      HOST: 0.0.0.0
      PORT: 1337
      NODE_ENV: production
      DATABASE_URL: postgresql://gobify_user:${DB_PASSWORD}@postgres:5432/gobify
      JWT_SECRET: ${JWT_SECRET}
      ADMIN_JWT_SECRET: ${ADMIN_JWT_SECRET}
      API_TOKEN_SALT: ${API_TOKEN_SALT}
      TRANSFER_TOKEN_SALT: ${TRANSFER_TOKEN_SALT}
      APP_KEYS: ${APP_KEYS}
      MEILISEARCH_HOST: http://meilisearch:7700
      MEILISEARCH_API_KEY: ${MEILISEARCH_MASTER_KEY}
      STORAGE_BUCKET_URL: ${STORAGE_BUCKET_URL}
    ports:
      - "1337:1337"
    depends_on:
      postgres:
        condition: service_healthy
      meilisearch:
        condition: service_started
    restart: unless-stopped
    volumes:
      - strapi_uploads:/usr/src/app/public/uploads

volumes:
  postgres_data:
  meilisearch_data:
  strapi_uploads:
```

#### 3. Create .env File

```bash
# Create production .env
cat > .env.production << 'EOF'
# Database
DB_PASSWORD=your-secure-db-password

# Strapi Secrets (generate with: openssl rand -base64 32)
JWT_SECRET=your-jwt-secret-here
ADMIN_JWT_SECRET=your-admin-jwt-secret
API_TOKEN_SALT=your-api-token-salt
TRANSFER_TOKEN_SALT=your-transfer-token-salt
APP_KEYS=key1,key2,key3,key4

# Meilisearch
MEILISEARCH_MASTER_KEY=your-meili-master-key

# Firebase Storage
STORAGE_BUCKET_URL=gobify-app.appspot.com
EOF
```

#### 4. Deploy with Docker Compose

```bash
# Start all services
docker-compose --env-file .env.production up -d

# Check logs
docker-compose logs -f strapi

# Check status
docker-compose ps
```

#### 5. Create Admin User

After deployment, create the first admin user:

1. Open browser: https://api.gobify.app/admin
2. Complete registration form
3. Configure API permissions

### Traditional Deployment

For deployment without Docker (VPS, dedicated server):

#### 1. Server Requirements

- Ubuntu 22.04 LTS or similar
- Node.js 18+
- PostgreSQL 15+
- Nginx (reverse proxy)
- PM2 (process manager)

#### 2. Install Dependencies

```bash
# Update system
sudo apt update && sudo apt upgrade -y

# Install Node.js 18
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs

# Install PostgreSQL
sudo apt install -y postgresql postgresql-contrib

# Install Nginx
sudo apt install -y nginx

# Install PM2 globally
sudo npm install -g pm2
```

#### 3. Setup PostgreSQL

```bash
# Switch to postgres user
sudo -u postgres psql

# Create database and user
CREATE DATABASE gobify;
CREATE USER gobify_user WITH PASSWORD 'secure-password';
GRANT ALL PRIVILEGES ON DATABASE gobify TO gobify_user;
\q
```

#### 4. Deploy Application

```bash
# Clone repository
cd /var/www
git clone <repository-url> gobify
cd gobify/gobify-backend

# Install dependencies
npm install --production

# Create .env file
nano .env
# Add all production environment variables

# Build admin panel
npm run build

# Start with PM2
pm2 start npm --name "gobify-backend" -- start
pm2 save
pm2 startup
```

#### 5. Configure Nginx

```bash
# Create Nginx configuration
sudo nano /etc/nginx/sites-available/gobify-api
```

```nginx
server {
    listen 80;
    server_name api.gobify.app;

    location / {
        proxy_pass http://localhost:1337;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_cache_bypass $http_upgrade;

        # Increase timeouts for large uploads
        proxy_connect_timeout 600;
        proxy_send_timeout 600;
        proxy_read_timeout 600;
        send_timeout 600;
    }

    # Increase client body size for file uploads
    client_max_body_size 50M;
}
```

```bash
# Enable site
sudo ln -s /etc/nginx/sites-available/gobify-api /etc/nginx/sites-enabled/

# Test configuration
sudo nginx -t

# Reload Nginx
sudo systemctl reload nginx
```

### Database Setup

#### PostgreSQL Configuration

**Production settings** (`/etc/postgresql/15/main/postgresql.conf`):

```conf
# Connection Settings
max_connections = 100
shared_buffers = 256MB

# Performance
effective_cache_size = 1GB
maintenance_work_mem = 64MB
checkpoint_completion_target = 0.9
wal_buffers = 16MB
default_statistics_target = 100
random_page_cost = 1.1
effective_io_concurrency = 200

# Logging
log_min_duration_statement = 1000
log_line_prefix = '%t [%p]: [%l-1] user=%u,db=%d,app=%a,client=%h '

# Security
ssl = on
ssl_cert_file = '/etc/ssl/certs/ssl-cert-snakeoil.pem'
ssl_key_file = '/etc/ssl/private/ssl-cert-snakeoil.key'
```

#### Create Backup User

```sql
CREATE USER backup_user WITH PASSWORD 'backup-password';
GRANT CONNECT ON DATABASE gobify TO backup_user;
GRANT USAGE ON SCHEMA public TO backup_user;
GRANT SELECT ON ALL TABLES IN SCHEMA public TO backup_user;
```

## Frontend Deployment

### Vercel Deployment

Vercel is the recommended platform for Next.js applications.

#### 1. Install Vercel CLI

```bash
npm install -g vercel
```

#### 2. Login to Vercel

```bash
vercel login
```

#### 3. Configure Project

Create `vercel.json` in `gobify-portals/apps/gobify-admin-portal/`:

```json
{
  "buildCommand": "npm run build",
  "outputDirectory": ".next",
  "devCommand": "npm run dev",
  "installCommand": "npm install",
  "framework": "nextjs",
  "regions": ["iad1"],
  "env": {
    "NEXT_PUBLIC_API_URL": "https://api.gobify.app/api",
    "NEXT_PUBLIC_MAPBOX_TOKEN": "@mapbox-token"
  }
}
```

#### 4. Deploy

```bash
cd gobify-portals/apps/gobify-admin-portal

# First deployment (creates project)
vercel

# Production deployment
vercel --prod
```

#### 5. Configure Environment Variables

In Vercel Dashboard:
1. Go to Project Settings → Environment Variables
2. Add all required variables:
   - `NEXT_PUBLIC_API_URL`
   - `NEXT_PUBLIC_MAPBOX_TOKEN`
   - `NEXT_PUBLIC_MEILISEARCH_HOST`
   - `NEXT_PUBLIC_MEILISEARCH_API_KEY`

#### 6. Configure Domain

1. Go to Project Settings → Domains
2. Add custom domain: `gobify.app`
3. Add DNS records as instructed
4. Wait for SSL certificate provisioning

### Custom Server Deployment

For deployment on your own infrastructure:

#### 1. Build Application

```bash
cd gobify-portals/apps/gobify-admin-portal

# Install dependencies
npm install

# Build for production
npm run build
```

#### 2. Start with PM2

```bash
# Start application
pm2 start npm --name "gobify-frontend" -- start

# Save PM2 configuration
pm2 save

# Enable startup script
pm2 startup
```

#### 3. Configure Nginx

```nginx
server {
    listen 80;
    server_name gobify.app www.gobify.app;

    location / {
        proxy_pass http://localhost:3000;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_cache_bypass $http_upgrade;
    }

    # Cache static assets
    location /_next/static {
        proxy_pass http://localhost:3000;
        proxy_cache_valid 200 1y;
        add_header Cache-Control "public, immutable";
    }
}
```

## Environment Configuration

### Production Environment Variables

#### Backend (.env)

```env
# Server
HOST=0.0.0.0
PORT=1337
NODE_ENV=production

# Database
DATABASE_URL=postgresql://user:password@host:5432/gobify
DATABASE_SSL=true

# Security (generate with: openssl rand -base64 32)
JWT_SECRET=CHANGE_ME_IN_PRODUCTION
ADMIN_JWT_SECRET=CHANGE_ME_IN_PRODUCTION
API_TOKEN_SALT=CHANGE_ME_IN_PRODUCTION
TRANSFER_TOKEN_SALT=CHANGE_ME_IN_PRODUCTION
APP_KEYS="key1,key2,key3,key4"

# Meilisearch
MEILISEARCH_HOST=https://search.gobify.app
MEILISEARCH_API_KEY=production-master-key

# Firebase Storage
STORAGE_BUCKET_URL=gobify-app.appspot.com

# CORS
CLIENT_URL=https://gobify.app

# Rate Limiting
RATE_LIMIT_ENABLED=true
RATE_LIMIT_MAX_REQUESTS=1000
RATE_LIMIT_DURATION=3600000
```

#### Frontend (.env.production)

```env
# API Configuration
NEXT_PUBLIC_API_URL=https://api.gobify.app/api
NEXT_PUBLIC_STRAPI_URL=https://api.gobify.app

# Mapbox
NEXT_PUBLIC_MAPBOX_TOKEN=pk.production.token.here

# Meilisearch
NEXT_PUBLIC_MEILISEARCH_HOST=https://search.gobify.app
NEXT_PUBLIC_MEILISEARCH_API_KEY=public-search-key

# Analytics (optional)
NEXT_PUBLIC_GA_ID=G-XXXXXXXXXX
NEXT_PUBLIC_ENABLE_ANALYTICS=true

# Error Tracking (optional)
SENTRY_DSN=https://xxx@sentry.io/xxx
NEXT_PUBLIC_SENTRY_DSN=https://xxx@sentry.io/xxx

# Environment
NODE_ENV=production
```

## SSL/HTTPS Setup

### Using Certbot (Let's Encrypt)

Free SSL certificates from Let's Encrypt:

```bash
# Install Certbot
sudo apt install -y certbot python3-certbot-nginx

# Obtain certificate for backend
sudo certbot --nginx -d api.gobify.app

# Obtain certificate for frontend (if self-hosted)
sudo certbot --nginx -d gobify.app -d www.gobify.app

# Auto-renewal is enabled by default
# Test renewal:
sudo certbot renew --dry-run
```

### Using Cloudflare

1. Add domain to Cloudflare
2. Update nameservers at domain registrar
3. Enable "Full (strict)" SSL mode
4. Enable "Always Use HTTPS"
5. Configure Page Rules for caching

## Domain Configuration

### DNS Records

Configure the following DNS records:

```
# Backend API
api.gobify.app.    A    123.456.789.10

# Frontend (if self-hosted)
gobify.app.        A    123.456.789.11
www.gobify.app.    CNAME gobify.app.

# Vercel deployment
gobify.app.        CNAME cname.vercel-dns.com.
www.gobify.app.    CNAME cname.vercel-dns.com.

# Meilisearch (if separate server)
search.gobify.app. A    123.456.789.12
```

### CORS Configuration

Update backend CORS settings in `config/middlewares.ts`:

```typescript
export default [
  // ...
  {
    name: 'strapi::cors',
    config: {
      origin: [
        'https://gobify.app',
        'https://www.gobify.app',
        // Add development URLs if needed
      ],
      methods: ['GET', 'POST', 'PUT', 'DELETE', 'OPTIONS'],
      headers: ['Content-Type', 'Authorization'],
      credentials: true,
    },
  },
  // ...
];
```

## Monitoring & Logging

### Backend Monitoring

#### PM2 Monitoring

```bash
# View logs
pm2 logs gobify-backend

# Monitor resources
pm2 monit

# Generate status report
pm2 report
```

#### Application Logs

Configure logging in `config/server.ts`:

```typescript
export default ({ env }) => ({
  // ...
  app: {
    logger: {
      level: 'info',
      format: 'json',
      transports: [
        {
          type: 'console',
        },
        {
          type: 'file',
          filename: 'logs/app.log',
          maxFiles: 7,
        },
      ],
    },
  },
});
```

#### Database Monitoring

```bash
# PostgreSQL query stats
sudo -u postgres psql -d gobify -c "
  SELECT query, calls, total_time, mean_time
  FROM pg_stat_statements
  ORDER BY total_time DESC
  LIMIT 10;
"

# Active connections
sudo -u postgres psql -d gobify -c "
  SELECT count(*) FROM pg_stat_activity;
"
```

### Frontend Monitoring

#### Vercel Analytics

Enable in Vercel Dashboard:
1. Go to Analytics
2. Enable Web Analytics
3. View real-time metrics

#### Error Tracking with Sentry

```bash
# Install Sentry
npm install @sentry/nextjs

# Initialize
npx @sentry/wizard -i nextjs
```

**Configuration** (`sentry.client.config.js`):
```javascript
import * as Sentry from '@sentry/nextjs';

Sentry.init({
  dsn: process.env.NEXT_PUBLIC_SENTRY_DSN,
  environment: process.env.NODE_ENV,
  tracesSampleRate: 0.1,
  beforeSend(event) {
    // Filter sensitive data
    return event;
  },
});
```

### Uptime Monitoring

Use services like:
- **UptimeRobot**: Free uptime monitoring
- **Pingdom**: Advanced monitoring
- **StatusCake**: Multi-location checks

Configure monitors for:
- Backend API: `https://api.gobify.app/api`
- Frontend: `https://gobify.app`
- Database port (if exposed)
- Meilisearch: `https://search.gobify.app/health`

## Backup Strategy

### Database Backups

#### Automated Backup Script

```bash
#!/bin/bash
# /usr/local/bin/backup-gobify-db.sh

DATE=$(date +%Y%m%d_%H%M%S)
BACKUP_DIR="/backups/gobify"
DB_NAME="gobify"
DB_USER="gobify_user"

# Create backup directory
mkdir -p $BACKUP_DIR

# Create backup
pg_dump -U $DB_USER -F c -b -v -f "$BACKUP_DIR/gobify_$DATE.backup" $DB_NAME

# Compress backup
gzip "$BACKUP_DIR/gobify_$DATE.backup"

# Delete backups older than 30 days
find $BACKUP_DIR -name "*.backup.gz" -mtime +30 -delete

# Upload to S3 (optional)
aws s3 cp "$BACKUP_DIR/gobify_$DATE.backup.gz" s3://my-backups/gobify/
```

#### Schedule with Cron

```bash
# Edit crontab
crontab -e

# Add daily backup at 2 AM
0 2 * * * /usr/local/bin/backup-gobify-db.sh >> /var/log/gobify-backup.log 2>&1
```

#### Restore from Backup

```bash
# Decompress
gunzip gobify_20241208_020000.backup.gz

# Restore
pg_restore -U gobify_user -d gobify -c gobify_20241208_020000.backup
```

### File Backups

#### Firebase Storage

Firebase automatically replicates data. For additional backup:

```bash
# Install Firebase CLI
npm install -g firebase-tools

# Login
firebase login

# Download files
gsutil -m cp -r gs://gobify-app.appspot.com/uploads ./backup/uploads
```

### Configuration Backups

```bash
# Backup environment files
tar -czf config-backup-$(date +%Y%m%d).tar.gz \
  gobify-backend/.env \
  gobify-portals/.env.production

# Store securely (encrypted)
gpg --encrypt --recipient admin@gobify.app config-backup-*.tar.gz
```

## Performance Optimization

### Backend Optimization

#### Database Indexing

```sql
-- Add indexes for frequently queried fields
CREATE INDEX idx_profiles_curp ON profiles(curp);
CREATE INDEX idx_profiles_tenant ON profiles(tenant_id);
CREATE INDEX idx_requests_folio ON social_program_requests(folio);
CREATE INDEX idx_requests_status ON social_program_requests(request_status);
CREATE INDEX idx_requests_program ON social_program_requests(social_program_id);
```

#### Enable Caching

```typescript
// config/middlewares.ts
export default [
  // ...
  {
    name: 'strapi::cache',
    config: {
      enabled: true,
      type: 'redis',
      maxAge: 3600000, // 1 hour
      redis: {
        host: 'localhost',
        port: 6379,
      },
    },
  },
];
```

#### Connection Pooling

```typescript
// config/database.ts
export default ({ env }) => ({
  connection: {
    client: 'postgres',
    connection: {
      connectionString: env('DATABASE_URL'),
      ssl: { rejectUnauthorized: false },
    },
    pool: {
      min: 2,
      max: 10,
      acquireTimeoutMillis: 30000,
      idleTimeoutMillis: 30000,
    },
  },
});
```

### Frontend Optimization

#### Enable Compression

```javascript
// next.config.js
module.exports = {
  compress: true,
  // ...
};
```

#### Image Optimization

```javascript
// next.config.js
module.exports = {
  images: {
    domains: ['storage.googleapis.com', 'api.gobify.app'],
    formats: ['image/avif', 'image/webp'],
    minimumCacheTTL: 86400, // 1 day
  },
};
```

#### CDN Configuration

Use Cloudflare or similar CDN:
1. Enable CDN caching for static assets
2. Set cache TTL: 1 year for `/_next/static/*`
3. Enable Brotli compression
4. Enable HTTP/3
5. Enable Auto Minify (CSS, JS)

## Security Hardening

### Backend Security

#### Firewall Rules

```bash
# Install UFW
sudo apt install ufw

# Allow SSH
sudo ufw allow 22/tcp

# Allow HTTP/HTTPS
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp

# Allow PostgreSQL (only from app server)
sudo ufw allow from 10.0.0.5 to any port 5432

# Enable firewall
sudo ufw enable
```

#### Security Headers

```typescript
// config/middlewares.ts
export default [
  // ...
  {
    name: 'strapi::security',
    config: {
      contentSecurityPolicy: {
        directives: {
          'default-src': ["'self'"],
          'img-src': ["'self'", 'data:', 'https://storage.googleapis.com'],
        },
      },
      frameguard: {
        action: 'deny',
      },
      hsts: {
        maxAge: 31536000,
        includeSubDomains: true,
      },
    },
  },
];
```

#### Rate Limiting

```typescript
// config/middlewares.ts
export default [
  // ...
  {
    name: 'strapi::ratelimit',
    config: {
      interval: 60000, // 1 minute
      max: 100, // 100 requests per minute
      prefixKey: 'rl_',
      whitelist: ['127.0.0.1'],
    },
  },
];
```

### Frontend Security

#### Security Headers (Vercel)

Create `vercel.json`:
```json
{
  "headers": [
    {
      "source": "/(.*)",
      "headers": [
        {
          "key": "X-Content-Type-Options",
          "value": "nosniff"
        },
        {
          "key": "X-Frame-Options",
          "value": "DENY"
        },
        {
          "key": "X-XSS-Protection",
          "value": "1; mode=block"
        },
        {
          "key": "Referrer-Policy",
          "value": "strict-origin-when-cross-origin"
        }
      ]
    }
  ]
}
```

#### Environment Variable Security

Never expose secrets in client code:
- Use `NEXT_PUBLIC_` prefix only for public variables
- Store sensitive keys server-side
- Use API routes for sensitive operations

## Continuous Deployment

### GitHub Actions (Backend)

Create `.github/workflows/deploy-backend.yml`:

```yaml
name: Deploy Backend

on:
  push:
    branches:
      - main
    paths:
      - 'gobify-backend/**'

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Build and push Docker image
        run: |
          cd gobify-backend
          docker build -t gobify-backend:latest .
          docker tag gobify-backend:latest registry.example.com/gobify-backend:latest
          docker push registry.example.com/gobify-backend:latest

      - name: Deploy to server
        uses: appleboy/ssh-action@master
        with:
          host: ${{ secrets.SERVER_HOST }}
          username: ${{ secrets.SERVER_USER }}
          key: ${{ secrets.SSH_PRIVATE_KEY }}
          script: |
            cd /var/www/gobify
            docker-compose pull strapi
            docker-compose up -d strapi
```

### Vercel Auto-Deploy (Frontend)

Vercel automatically deploys on git push:
1. Connect GitHub repository
2. Configure build settings
3. Set environment variables
4. Push to main branch → auto-deploy

### Manual Deploy Script

```bash
#!/bin/bash
# deploy.sh

echo "Starting deployment..."

# Backend
echo "Deploying backend..."
cd gobify-backend
git pull origin main
npm install --production
npm run build
pm2 restart gobify-backend

# Frontend
echo "Deploying frontend..."
cd ../gobify-portals/apps/gobify-admin-portal
git pull origin main
npm install
npm run build
pm2 restart gobify-frontend

echo "Deployment complete!"
```

## Rollback Procedures

### Backend Rollback

#### Docker Rollback

```bash
# Tag before deploy
docker tag gobify-backend:latest gobify-backend:backup-$(date +%Y%m%d)

# Rollback
docker-compose stop strapi
docker tag gobify-backend:backup-20241208 gobify-backend:latest
docker-compose up -d strapi
```

#### Database Rollback

```bash
# Restore from backup
pg_restore -U gobify_user -d gobify -c gobify_backup.dump

# Or restore to new database and switch
createdb gobify_rollback
pg_restore -U gobify_user -d gobify_rollback gobify_backup.dump

# Update connection string
# Restart application
```

### Frontend Rollback

#### Vercel Rollback

1. Go to Vercel Dashboard
2. Select project
3. Go to Deployments
4. Click "..." on previous deployment
5. Select "Promote to Production"

#### PM2 Rollback

```bash
# Keep git history
git log --oneline
git checkout <commit-hash>
npm run build
pm2 restart gobify-frontend
```

## Troubleshooting

### Common Production Issues

#### Issue: 502 Bad Gateway

**Cause**: Backend not responding

**Solution**:
```bash
# Check if backend is running
pm2 status
# or
docker-compose ps

# Check logs
pm2 logs gobify-backend
# or
docker-compose logs strapi

# Restart if needed
pm2 restart gobify-backend
# or
docker-compose restart strapi
```

#### Issue: Database Connection Failed

**Cause**: Database not accessible or wrong credentials

**Solution**:
```bash
# Test database connection
psql -U gobify_user -h localhost -d gobify

# Check PostgreSQL status
sudo systemctl status postgresql

# Check connection limit
sudo -u postgres psql -c "SELECT count(*) FROM pg_stat_activity;"

# Restart PostgreSQL
sudo systemctl restart postgresql
```

#### Issue: Out of Memory

**Cause**: Insufficient server resources

**Solution**:
```bash
# Check memory usage
free -h

# Check process memory
pm2 monit

# Increase Node.js memory
NODE_OPTIONS=--max-old-space-size=4096 pm2 restart gobify-backend

# Or in docker-compose.yml:
services:
  strapi:
    environment:
      NODE_OPTIONS: --max-old-space-size=4096
```

#### Issue: Slow API Response

**Cause**: Database queries, missing indexes

**Solution**:
```bash
# Enable query logging
# In postgresql.conf:
log_min_duration_statement = 100

# Analyze slow queries
sudo -u postgres psql -d gobify -c "
  SELECT query, mean_time, calls
  FROM pg_stat_statements
  ORDER BY mean_time DESC
  LIMIT 10;
"

# Add indexes as needed
```

### Health Checks

#### Backend Health

```bash
# API health check
curl https://api.gobify.app/api

# Database health
psql -U gobify_user -d gobify -c "SELECT 1;"

# Meilisearch health
curl https://search.gobify.app/health
```

#### Frontend Health

```bash
# Check frontend
curl https://gobify.app

# Check build logs (Vercel)
vercel logs
```

## Support & Maintenance

### Regular Maintenance Tasks

**Daily**:
- Check error logs
- Monitor server resources
- Verify backups completed

**Weekly**:
- Review security logs
- Check disk space
- Update dependencies (if needed)

**Monthly**:
- Review and optimize database
- Rotate logs
- Test backup restoration
- Review and update SSL certificates

**Quarterly**:
- Security audit
- Performance review
- Capacity planning
- Update documentation

---

**Document Version**: 1.0.0
**Last Updated**: December 2024
**Deployment Target**: Production
