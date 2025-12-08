# Gobify Platform - Deployment Architecture

This diagram illustrates the production deployment architecture for the Gobify platform, including infrastructure, services, and network topology.

## Production Deployment Architecture

```mermaid
graph TB
    subgraph "DNS & CDN Layer"
        DNS[DNS Provider<br/>Domain Management]
        CDN[CDN - Cloudflare/CloudFront<br/>Static Asset Distribution]
    end

    subgraph "Load Balancer & Gateway"
        LB[Load Balancer<br/>NGINX/HAProxy]
        WAF[Web Application Firewall<br/>Rate Limiting & Security]
    end

    subgraph "Frontend Tier - Next.js"
        direction TB
        NEXT1[Next.js Instance 1<br/>Node.js Runtime]
        NEXT2[Next.js Instance 2<br/>Node.js Runtime]
        NEXT3[Next.js Instance 3<br/>Node.js Runtime]

        subgraph "Next.js Features"
            SSR[Server-Side Rendering]
            SSG[Static Site Generation]
            ISR[Incremental Static Regeneration]
            API_ROUTES[API Routes]
        end

        NEXT1 --> SSR
        NEXT1 --> SSG
        NEXT2 --> ISR
        NEXT3 --> API_ROUTES
    end

    subgraph "Backend Tier - Strapi"
        direction TB
        STRAPI1[Strapi Instance 1<br/>Node.js Runtime]
        STRAPI2[Strapi Instance 2<br/>Node.js Runtime]

        subgraph "Strapi Services"
            ADMIN[Admin Panel]
            REST_API[REST API]
            UPLOAD_SVC[Upload Service]
            SEARCH_SVC[Search Service]
        end

        STRAPI1 --> ADMIN
        STRAPI1 --> REST_API
        STRAPI2 --> UPLOAD_SVC
        STRAPI2 --> SEARCH_SVC
    end

    subgraph "Database Tier"
        PG_PRIMARY[(PostgreSQL Primary<br/>Read/Write)]
        PG_REPLICA[(PostgreSQL Replica<br/>Read Only)]
        PG_BACKUP[(PostgreSQL Backup<br/>Daily Snapshots)]

        PG_PRIMARY -.->|Replication| PG_REPLICA
        PG_PRIMARY -.->|Backup| PG_BACKUP
    end

    subgraph "Cache & Queue Layer"
        REDIS_MASTER[(Redis Master<br/>Session & Cache)]
        REDIS_REPLICA[(Redis Replica<br/>Read Only)]
        QUEUE[Job Queue<br/>Bull/BullMQ]

        REDIS_MASTER -.->|Replication| REDIS_REPLICA
    end

    subgraph "Search Infrastructure"
        MEILISEARCH1[Meilisearch Instance 1<br/>Primary]
        MEILISEARCH2[Meilisearch Instance 2<br/>Replica]

        MEILISEARCH1 -.->|Sync| MEILISEARCH2
    end

    subgraph "Storage & Files"
        FIREBASE[Firebase Storage<br/>Cloud Storage]
        BACKUP_STORAGE[Backup Storage<br/>S3/GCS]
    end

    subgraph "Monitoring & Logging"
        METRICS[Metrics<br/>Prometheus]
        LOGS[Centralized Logging<br/>ELK Stack/Loki]
        APM[APM<br/>Application Performance]
        ALERTS[Alerting<br/>PagerDuty/Slack]
    end

    subgraph "CI/CD Pipeline"
        GIT[Git Repository<br/>GitHub/GitLab]
        CI[CI/CD<br/>GitHub Actions/GitLab CI]
        DOCKER_REG[Docker Registry<br/>Container Images]
        DEPLOY[Deployment<br/>Docker/Kubernetes]
    end

    subgraph "External Services"
        EMAIL[Email Service<br/>SendGrid/SES]
        SMS[SMS Service<br/>Twilio]
        MAPBOX_EXT[Mapbox API<br/>Geographic Services]
        ANALYTICS[Analytics<br/>Google Analytics]
    end

    %% User connections
    User([End Users]) --> DNS
    DNS --> CDN
    CDN --> WAF
    WAF --> LB

    %% Load balancer routing
    LB --> NEXT1
    LB --> NEXT2
    LB --> NEXT3
    LB --> STRAPI1
    LB --> STRAPI2

    %% Frontend to Backend
    NEXT1 --> LB
    NEXT2 --> LB
    NEXT3 --> LB

    %% Backend to Database
    STRAPI1 --> PG_PRIMARY
    STRAPI2 --> PG_PRIMARY
    NEXT1 -.->|Read| PG_REPLICA
    NEXT2 -.->|Read| PG_REPLICA
    NEXT3 -.->|Read| PG_REPLICA

    %% Cache connections
    STRAPI1 --> REDIS_MASTER
    STRAPI2 --> REDIS_MASTER
    NEXT1 --> REDIS_MASTER
    NEXT2 --> REDIS_REPLICA
    NEXT3 --> REDIS_REPLICA

    %% Search connections
    STRAPI1 --> MEILISEARCH1
    STRAPI2 --> MEILISEARCH2
    NEXT1 --> MEILISEARCH1

    %% Storage connections
    STRAPI1 --> FIREBASE
    STRAPI2 --> FIREBASE
    NEXT1 --> FIREBASE

    %% Queue connections
    STRAPI1 --> QUEUE
    QUEUE --> REDIS_MASTER

    %% External services
    STRAPI1 --> EMAIL
    STRAPI1 --> SMS
    NEXT1 --> MAPBOX_EXT
    CDN --> ANALYTICS

    %% Monitoring
    NEXT1 --> METRICS
    NEXT2 --> METRICS
    NEXT3 --> METRICS
    STRAPI1 --> METRICS
    STRAPI2 --> METRICS
    PG_PRIMARY --> METRICS
    REDIS_MASTER --> METRICS

    METRICS --> ALERTS
    LOGS --> ALERTS
    APM --> ALERTS

    %% CI/CD
    GIT --> CI
    CI --> DOCKER_REG
    DOCKER_REG --> DEPLOY
    DEPLOY --> NEXT1
    DEPLOY --> STRAPI1

    %% Backup
    PG_BACKUP --> BACKUP_STORAGE
    FIREBASE -.->|Backup| BACKUP_STORAGE

    style User fill:#64b5f6
    style DNS fill:#81c784
    style CDN fill:#81c784
    style LB fill:#ffb74d
    style WAF fill:#e57373
    style PG_PRIMARY fill:#9575cd
    style FIREBASE fill:#ffca28
    style METRICS fill:#4db6ac
    style LOGS fill:#4db6ac
```

## Container Architecture (Docker)

```mermaid
graph TB
    subgraph "Docker Host"
        subgraph "Frontend Containers"
            NEXT_CONTAINER[next-app<br/>Node:20-alpine<br/>Port: 3000]
        end

        subgraph "Backend Containers"
            STRAPI_CONTAINER[strapi-api<br/>Node:20-alpine<br/>Port: 1337]
        end

        subgraph "Database Containers"
            POSTGRES_CONTAINER[(postgres:16<br/>Port: 5432)]
            REDIS_CONTAINER[(redis:7-alpine<br/>Port: 6379)]
            MEILISEARCH_CONTAINER[meilisearch:v1.6<br/>Port: 7700]
        end

        subgraph "Utility Containers"
            NGINX_CONTAINER[nginx:alpine<br/>Reverse Proxy<br/>Port: 80, 443]
        end

        subgraph "Docker Network"
            NETWORK[gobify-network<br/>Bridge Network]
        end
    end

    NGINX_CONTAINER --> NEXT_CONTAINER
    NGINX_CONTAINER --> STRAPI_CONTAINER

    NEXT_CONTAINER --> NETWORK
    STRAPI_CONTAINER --> NETWORK
    POSTGRES_CONTAINER --> NETWORK
    REDIS_CONTAINER --> NETWORK
    MEILISEARCH_CONTAINER --> NETWORK

    STRAPI_CONTAINER --> POSTGRES_CONTAINER
    STRAPI_CONTAINER --> REDIS_CONTAINER
    STRAPI_CONTAINER --> MEILISEARCH_CONTAINER
    NEXT_CONTAINER --> REDIS_CONTAINER

    VOLUMES[(Docker Volumes<br/>postgres_data<br/>redis_data<br/>meilisearch_data<br/>uploads)]

    POSTGRES_CONTAINER -.-> VOLUMES
    REDIS_CONTAINER -.-> VOLUMES
    MEILISEARCH_CONTAINER -.-> VOLUMES
    STRAPI_CONTAINER -.-> VOLUMES
```

## Kubernetes Deployment (Alternative)

```mermaid
graph TB
    subgraph "Kubernetes Cluster"
        subgraph "Ingress Layer"
            INGRESS[Ingress Controller<br/>NGINX/Traefik]
            CERT[Cert Manager<br/>SSL/TLS]
        end

        subgraph "Frontend Namespace"
            NEXT_DEPLOY[Next.js Deployment<br/>Replicas: 3]
            NEXT_SVC[Next.js Service<br/>ClusterIP]
            NEXT_HPA[Horizontal Pod Autoscaler<br/>CPU: 70%]

            NEXT_DEPLOY --> NEXT_SVC
            NEXT_HPA -.-> NEXT_DEPLOY
        end

        subgraph "Backend Namespace"
            STRAPI_DEPLOY[Strapi Deployment<br/>Replicas: 2]
            STRAPI_SVC[Strapi Service<br/>ClusterIP]
            STRAPI_HPA[Horizontal Pod Autoscaler<br/>CPU: 70%]

            STRAPI_DEPLOY --> STRAPI_SVC
            STRAPI_HPA -.-> STRAPI_DEPLOY
        end

        subgraph "Data Namespace"
            PG_STATEFUL[PostgreSQL StatefulSet<br/>Replicas: 1]
            PG_SVC[PostgreSQL Service<br/>Headless]

            REDIS_STATEFUL[Redis StatefulSet<br/>Replicas: 1]
            REDIS_SVC[Redis Service<br/>ClusterIP]

            MEILI_STATEFUL[Meilisearch StatefulSet<br/>Replicas: 1]
            MEILI_SVC[Meilisearch Service<br/>ClusterIP]

            PG_STATEFUL --> PG_SVC
            REDIS_STATEFUL --> REDIS_SVC
            MEILI_STATEFUL --> MEILI_SVC
        end

        subgraph "Storage"
            PVC_PG[PersistentVolumeClaim<br/>postgres-data]
            PVC_REDIS[PersistentVolumeClaim<br/>redis-data]
            PVC_MEILI[PersistentVolumeClaim<br/>meili-data]

            PG_STATEFUL -.-> PVC_PG
            REDIS_STATEFUL -.-> PVC_REDIS
            MEILI_STATEFUL -.-> PVC_MEILI
        end

        subgraph "Config & Secrets"
            CONFIGMAP[ConfigMaps]
            SECRETS[Secrets]

            NEXT_DEPLOY -.-> CONFIGMAP
            NEXT_DEPLOY -.-> SECRETS
            STRAPI_DEPLOY -.-> CONFIGMAP
            STRAPI_DEPLOY -.-> SECRETS
        end
    end

    INGRESS --> NEXT_SVC
    INGRESS --> STRAPI_SVC
    CERT --> INGRESS

    NEXT_DEPLOY --> STRAPI_SVC
    STRAPI_DEPLOY --> PG_SVC
    STRAPI_DEPLOY --> REDIS_SVC
    STRAPI_DEPLOY --> MEILI_SVC
```

## Deployment Architecture Details

### 1. DNS & CDN Layer

**DNS Provider**
- Domain management for gobify.app
- DNS records: A, CNAME, MX, TXT
- TTL configuration for caching
- DNSSEC for security

**CDN (Cloudflare/CloudFront)**
- Global edge network for static assets
- Caches: Images, CSS, JavaScript, fonts
- SSL/TLS termination
- DDoS protection
- Geographic distribution

### 2. Load Balancer & Security

**Load Balancer (NGINX/HAProxy)**
- Round-robin distribution
- Health checks every 10 seconds
- Sticky sessions for user sessions
- SSL/TLS termination
- HTTP/2 support
- WebSocket proxy support

**Web Application Firewall (WAF)**
- OWASP Top 10 protection
- Rate limiting: 100 requests/minute per IP
- Bot detection and blocking
- SQL injection prevention
- XSS attack prevention
- Geographic blocking if needed

### 3. Frontend Tier - Next.js

**Deployment Configuration**
- **Instances**: 3 Node.js instances
- **Runtime**: Node.js 20 LTS
- **Build**: Turbopack for faster builds
- **Server**: Custom server or standalone output
- **Port**: 3000 (internal)

**Features**
- **SSR**: Server-Side Rendering for dynamic pages
- **SSG**: Static Site Generation for static pages
- **ISR**: Incremental Static Regeneration (revalidate: 60s)
- **API Routes**: Edge API routes for lightweight operations

**Environment Variables**
```env
NEXT_PUBLIC_API_URL=https://api.gobify.app
NEXT_PUBLIC_MAPBOX_TOKEN=pk.xxx
NODE_ENV=production
PORT=3000
```

**Resource Allocation**
- CPU: 2 cores per instance
- Memory: 4GB per instance
- Disk: 20GB per instance

### 4. Backend Tier - Strapi

**Deployment Configuration**
- **Instances**: 2 Node.js instances
- **Runtime**: Node.js 20 LTS
- **Port**: 1337 (internal)
- **Admin Panel**: Disabled in production (separate deployment)

**Environment Variables**
```env
DATABASE_URL=postgresql://user:pass@postgres:5432/gobify
REDIS_URL=redis://redis:6379
MEILISEARCH_HOST=http://meilisearch:7700
MEILISEARCH_API_KEY=xxx
JWT_SECRET=xxx
API_TOKEN_SALT=xxx
ADMIN_JWT_SECRET=xxx
```

**Resource Allocation**
- CPU: 4 cores per instance
- Memory: 8GB per instance
- Disk: 50GB per instance

### 5. Database Tier - PostgreSQL

**Primary Database**
- **Version**: PostgreSQL 16
- **Configuration**: Optimized for read-heavy workloads
- **Connections**: Max 200 connections
- **Shared Buffers**: 4GB
- **Work Memory**: 64MB
- **Maintenance Work Memory**: 512MB

**Read Replica**
- Asynchronous streaming replication
- Read-only queries
- Automatic failover with Patroni/repmgr

**Backup Strategy**
- Daily full backups at 2 AM UTC
- Point-in-time recovery (PITR) with WAL archiving
- Retention: 30 days
- Backup location: S3/GCS

**Resource Allocation**
- CPU: 8 cores
- Memory: 16GB
- Disk: 500GB SSD (auto-scaling)

### 6. Cache & Queue Layer

**Redis Master**
- **Version**: Redis 7
- **Use Cases**: Session storage, cache, pub/sub
- **Persistence**: RDB + AOF
- **Eviction Policy**: allkeys-lru
- **Max Memory**: 8GB

**Redis Replica**
- Read-only replica
- Automatic failover with Redis Sentinel

**Job Queue (Bull/BullMQ)**
- Email sending queue
- PDF generation queue
- Data export queue
- Search indexing queue
- Concurrency: 10 jobs per queue

### 7. Search Infrastructure - Meilisearch

**Configuration**
- **Version**: Meilisearch v1.6
- **Indexes**: Separate indexes for each entity
  - social_programs
  - articles
  - profiles
  - procedures
- **Synonyms**: Configured for Spanish language
- **Stop Words**: Spanish stop words

**Resource Allocation**
- CPU: 4 cores
- Memory: 8GB
- Disk: 100GB SSD

### 8. Storage & Files - Firebase Storage

**Configuration**
- **Bucket**: gobify-production
- **Access**: Signed URLs with expiration
- **File Types**: Images, PDFs, documents
- **Max File Size**: 10MB per file

**Organization**
```
/uploads/
  /social-programs/
  /articles/
  /profiles/
  /reports/
  /documents/
```

**Backup Strategy**
- Daily backups to S3/GCS
- Versioning enabled
- Lifecycle policies: Archive after 90 days

### 9. Monitoring & Logging

**Metrics (Prometheus)**
- Application metrics
- System metrics (CPU, memory, disk, network)
- Database metrics (connections, queries, slow queries)
- Cache hit/miss rates
- API response times

**Centralized Logging (ELK/Loki)**
- Application logs
- Access logs
- Error logs
- Audit logs
- Log retention: 90 days

**APM (Application Performance Monitoring)**
- Transaction tracing
- Error tracking
- Performance bottleneck identification
- User experience metrics

**Alerting**
- CPU usage > 80% for 5 minutes
- Memory usage > 90% for 5 minutes
- Disk usage > 85%
- Error rate > 1% for 10 minutes
- Response time > 1s for 5 minutes
- Database connection failures

### 10. CI/CD Pipeline

**Git Repository**
- GitHub or GitLab
- Branch strategy: main, staging, feature/*
- Protected branches with required reviews

**CI/CD Process**
```mermaid
graph LR
    CODE[Code Push] --> LINT[Lint & Format]
    LINT --> TEST[Run Tests]
    TEST --> BUILD[Build Docker Image]
    BUILD --> SCAN[Security Scan]
    SCAN --> PUSH[Push to Registry]
    PUSH --> DEPLOY[Deploy to Production]
    DEPLOY --> VERIFY[Health Check]
    VERIFY --> NOTIFY[Notify Team]
```

**GitHub Actions/GitLab CI**
- Automated testing on PR
- Build on merge to main
- Deploy to staging on merge to staging
- Deploy to production on tag

**Docker Registry**
- Private registry (Docker Hub, ECR, GCR)
- Image tagging: git commit SHA
- Image scanning for vulnerabilities

### 11. Deployment Process

**Zero-Downtime Deployment**
1. Build new Docker image
2. Push to registry
3. Update container with new image
4. Perform rolling update (1 instance at a time)
5. Health check after each update
6. Rollback on failure

**Rollback Strategy**
- Keep previous 3 images
- One-click rollback via CI/CD
- Database migrations handled separately

### 12. Disaster Recovery

**Recovery Time Objective (RTO)**: 4 hours
**Recovery Point Objective (RPO)**: 1 hour

**Disaster Recovery Plan**
1. Restore database from latest backup
2. Deploy application from latest stable image
3. Verify data integrity
4. Update DNS if needed
5. Monitor for issues

## Infrastructure as Code

**Terraform/Pulumi**
```hcl
# Example Terraform configuration
resource "aws_ecs_service" "next_app" {
  name            = "gobify-next"
  cluster         = aws_ecs_cluster.main.id
  task_definition = aws_ecs_task_definition.next_app.arn
  desired_count   = 3

  load_balancer {
    target_group_arn = aws_lb_target_group.next.arn
    container_name   = "next-app"
    container_port   = 3000
  }
}
```

**Docker Compose (Development)**
```yaml
version: '3.8'

services:
  next-app:
    build: ./gobify-admin-portal
    ports:
      - "3000:3000"
    environment:
      - NEXT_PUBLIC_API_URL=http://localhost:1337
    depends_on:
      - strapi-api

  strapi-api:
    build: ./strapi-backend
    ports:
      - "1337:1337"
    environment:
      - DATABASE_URL=postgresql://postgres:password@postgres:5432/gobify
    depends_on:
      - postgres

  postgres:
    image: postgres:16
    environment:
      - POSTGRES_DB=gobify
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=password
    volumes:
      - postgres_data:/var/lib/postgresql/data

  redis:
    image: redis:7-alpine
    ports:
      - "6379:6379"

  meilisearch:
    image: getmeili/meilisearch:v1.6
    ports:
      - "7700:7700"

volumes:
  postgres_data:
```

## Scaling Strategy

**Horizontal Scaling**
- Frontend: Scale to 5+ instances during peak hours
- Backend: Scale to 4+ instances during peak hours
- Auto-scaling based on CPU (70%) and memory (80%)

**Vertical Scaling**
- Database: Increase to 32GB RAM if needed
- Redis: Increase to 16GB RAM if needed

**Database Sharding** (Future)
- Shard by tenant_id for multi-tenant isolation
- Improves query performance at scale
