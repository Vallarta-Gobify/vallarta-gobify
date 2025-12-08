# Frontend Documentation

Comprehensive documentation for the Gobify frontend - a Next.js 15 monorepo with Turborepo.

## Table of Contents

- [Overview](#overview)
- [Technology Stack](#technology-stack)
- [Monorepo Structure](#monorepo-structure)
- [App Router Architecture](#app-router-architecture)
- [Pages & Features](#pages--features)
- [State Management](#state-management)
- [API Integration](#api-integration)
- [Components](#components)
- [Forms & Validation](#forms--validation)
- [Maps Integration](#maps-integration)
- [Document Generation](#document-generation)
- [Styling](#styling)
- [Development](#development)
- [Testing](#testing)

## Overview

The Gobify frontend is a modern web application built with Next.js 15 using the App Router pattern. It's organized as a Turborepo monorepo with shared packages for code reusability.

### Key Features

- **Modern Stack**: Next.js 15, React 18, TypeScript 5.7
- **Server Actions**: Native Next.js data mutations
- **Server Components**: Optimized initial page loads
- **Interactive Maps**: Mapbox GL with clustering
- **Advanced Tables**: AG Grid for complex data tables
- **PDF Generation**: Custom PDF receipts with progress tracking
- **Excel Export**: ExcelJS for data exports
- **QR Integration**: Generation and scanning
- **Form Management**: Formik + Yup validation
- **State Management**: TanStack Query for server state
- **Design System**: NextUI components with Tailwind CSS

### Architecture Philosophy

The frontend follows these principles:
1. **Server-first**: Use Server Components by default
2. **Progressive Enhancement**: Add interactivity only when needed
3. **Type Safety**: Comprehensive TypeScript coverage
4. **Code Reuse**: Shared packages for common functionality
5. **Performance**: Optimized bundle size and lazy loading

## Technology Stack

### Core Framework

| Technology | Version | Purpose |
|-----------|---------|---------|
| **Next.js** | 15.3.2 | React framework with App Router |
| **React** | 18.3.1 | UI library |
| **TypeScript** | 5.7.2 | Type safety |
| **Turborepo** | 2.3.3 | Monorepo build system |

### UI & Styling

| Technology | Version | Purpose |
|-----------|---------|---------|
| **NextUI** | 2.6.10 | Component library |
| **Tailwind CSS** | 3.4.17 | Utility-first CSS |
| **Framer Motion** | 11.15.0 | Animations |
| **Tabler Icons** | 3.34.1 | Icon set |

### Data & State

| Technology | Version | Purpose |
|-----------|---------|---------|
| **TanStack Query** | 5.62.11 | Server state management |
| **Axios** | 1.7.9 | HTTP client |
| **Formik** | 2.4.6 | Form management |
| **Yup** | 1.6.1 | Schema validation |

### Maps & Geo

| Technology | Version | Purpose |
|-----------|---------|---------|
| **Mapbox GL** | 3.9.3 | Interactive maps |
| **react-map-gl** | 7.1.8 | React wrapper for Mapbox |
| **Supercluster** | 8.0.1 | Point clustering |

### Tables & Data

| Technology | Version | Purpose |
|-----------|---------|---------|
| **AG Grid** | 33.0.3 | Advanced data tables |
| **ExcelJS** | 4.4.0 | Excel generation |

### Documents & QR

| Technology | Version | Purpose |
|-----------|---------|---------|
| **pdf-lib** | 1.17.1 | PDF manipulation |
| **QRCode** | 1.5.4 | QR generation |
| **qr-scanner** | 1.4.2 | QR scanning |

### Search

| Technology | Version | Purpose |
|-----------|---------|---------|
| **Meilisearch** | 0.49.0 | Client for search |

### Testing

| Technology | Version | Purpose |
|-----------|---------|---------|
| **Jest** | 29.7.0 | Test framework |
| **Testing Library** | Latest | Component testing |

## Monorepo Structure

```
gobify-portals/
├── apps/
│   └── gobify-admin-portal/          # Main admin application
│       ├── app/                       # Next.js App Router
│       │   ├── (private)/            # Protected routes
│       │   ├── (public)/             # Public routes
│       │   ├── api/                  # API route handlers
│       │   ├── layout.tsx            # Root layout
│       │   └── page.tsx              # Landing page
│       ├── components/                # React components
│       ├── hooks/                     # Custom hooks
│       ├── lib/                       # Utilities
│       ├── public/                    # Static assets
│       ├── styles/                    # Global styles
│       ├── types/                     # TypeScript types
│       ├── next.config.js             # Next.js config
│       ├── tailwind.config.js         # Tailwind config
│       ├── tsconfig.json              # TypeScript config
│       └── package.json               # Dependencies
├── packages/
│   ├── strapi-client/                 # API client package
│   │   ├── index.ts                  # Axios client
│   │   └── package.json
│   ├── pdf-generator/                 # PDF generation
│   │   ├── src/
│   │   │   ├── generator.ts          # PDF generator
│   │   │   ├── database.ts           # DB client
│   │   │   └── cli.ts                # CLI tool
│   │   ├── templates/                # PDF templates
│   │   └── package.json
│   ├── ui/                            # Shared components
│   │   ├── src/
│   │   └── package.json
│   ├── eslint-config/                 # ESLint configuration
│   │   ├── base.js                   # Base config
│   │   └── package.json
│   └── typescript-config/             # TypeScript configs
│       ├── base.json                 # Base config
│       ├── nextjs.json               # Next.js config
│       └── package.json
├── turbo.json                         # Turborepo config
├── package.json                       # Root package.json
└── tsconfig.json                      # Root TypeScript config
```

### Workspace Configuration

**Root `package.json`**:
```json
{
  "workspaces": [
    "apps/*",
    "packages/*"
  ],
  "engines": {
    "node": ">=18"
  },
  "packageManager": "npm@9.8.1"
}
```

## App Router Architecture

The admin portal uses Next.js 15 App Router with route groups for authentication boundaries.

### Route Structure

```
app/
├── layout.tsx                         # Root layout (providers)
├── page.tsx                           # Landing page
├── (private)/                         # Protected routes group
│   ├── layout.tsx                    # Private layout (navbar, sidebar)
│   ├── dashboard/                    # KPI dashboard
│   │   ├── page.tsx                 # Server Component
│   │   └── client.tsx               # Client Component
│   ├── ciudadanos/                   # Citizens management
│   │   ├── page.tsx
│   │   ├── actions.ts               # Server Actions
│   │   └── [id]/                    # Dynamic route
│   │       ├── page.tsx
│   │       └── edit/
│   │           └── page.tsx
│   ├── programas-sociales/           # Social programs
│   │   ├── page.tsx                 # Programs overview
│   │   ├── header.tsx               # Section header
│   │   ├── {program-id}/            # Program-specific routes
│   │   │   ├── page.tsx            # Request listing
│   │   │   ├── actions.ts          # Program actions
│   │   │   ├── cols.ts             # Column definitions
│   │   │   ├── header.tsx          # Program header
│   │   │   ├── new/                # New request
│   │   │   │   └── page.tsx
│   │   │   └── [socialProgramRequestId]/  # Request detail
│   │   │       ├── page.tsx
│   │   │       └── edit/
│   │   │           └── page.tsx
│   │   └── [documentId]/            # Document viewer
│   │       └── page.tsx
│   ├── calles/                       # Streets management
│   │   ├── page.tsx
│   │   └── actions.ts
│   ├── colonias/                     # Neighborhoods
│   │   ├── page.tsx
│   │   └── actions.ts
│   ├── reportes/                     # Reports
│   │   └── page.tsx
│   ├── demografico/                  # Demographics
│   │   └── page.tsx
│   ├── qr/                           # QR scanner
│   │   └── page.tsx
│   └── team/                         # Team management
│       └── page.tsx
├── (public)/                          # Public routes group
│   ├── login/                        # Login page
│   │   └── page.tsx
│   └── logout/                       # Logout handler
│       └── page.tsx
└── api/                               # API routes
    └── v1/                           # API v1
        ├── areas/
        │   └── route.ts
        ├── departments/
        │   └── route.ts
        ├── pdf-export/
        │   └── route.ts
        ├── pdf-export-progress/
        │   └── route.ts
        ├── social-programs/
        │   └── route.ts
        └── tenant/
            └── route.ts
```

### Route Groups

**`(private)`**: Protected routes requiring authentication
- Layout includes navbar and sidebar
- Middleware checks for valid session
- Redirects to login if unauthenticated

**`(public)`**: Public routes (login, logout)
- Minimal layout
- No authentication required
- Redirects to dashboard if already authenticated

### Server Actions Pattern

Each feature follows this pattern:

**`page.tsx`** - Server Component:
```typescript
// app/(private)/ciudadanos/page.tsx
import { getCiudadanos } from './actions';

export default async function CiudadanosPage() {
  const initialData = await getCiudadanos({ page: 1, pageSize: 25 });

  return <CiudadanosClient initialData={initialData} />;
}
```

**`actions.ts`** - Server Actions:
```typescript
// app/(private)/ciudadanos/actions.ts
"use server";

import strapi from "@repo/strapi-client";

export async function getCiudadanos(params: {
  page?: number;
  pageSize?: number;
  search?: string;
}) {
  const response = await strapi.get('/profiles', {
    params: {
      'pagination[page]': params.page || 1,
      'pagination[pageSize]': params.pageSize || 25,
      'filters[name][$containsi]': params.search,
      'populate': '*'
    }
  });

  return response.data;
}
```

**`client.tsx`** - Client Component (when needed):
```typescript
// app/(private)/ciudadanos/client.tsx
"use client";

import { useQuery } from '@tanstack/react-query';

export default function CiudadanosClient({ initialData }) {
  const { data } = useQuery({
    queryKey: ['ciudadanos'],
    queryFn: () => fetch('/api/v1/profiles').then(r => r.json()),
    initialData
  });

  return <div>{/* Interactive UI */}</div>;
}
```

## Pages & Features

### 1. Dashboard

**Route**: `/dashboard`

**Features**:
- KPI cards (total citizens, active programs, pending deliveries)
- Recent activity feed
- Charts and statistics with Recharts
- Quick actions

**Components**:
- `KPICard` - Metric display
- `ActivityFeed` - Recent events
- `StatChart` - Data visualization

---

### 2. Citizens Management (Ciudadanos)

**Route**: `/ciudadanos`

**Features**:
- AG Grid table with sorting, filtering, pagination
- Search by name, CURP, phone
- CRUD operations (Create, Read, Update, Delete)
- Address with geolocation
- Phone number management
- View request history

**Data Flow**:
1. Server Component fetches initial data
2. Client Component renders AG Grid
3. User interactions trigger Server Actions
4. TanStack Query manages cache invalidation

**Key Files**:
- `/Users/manny/Projects/agilgob/Vallarta-Gobify/gobify-portals/apps/gobify-admin-portal/app/(private)/ciudadanos/page.tsx`
- `/Users/manny/Projects/agilgob/Vallarta-Gobify/gobify-portals/apps/gobify-admin-portal/app/(private)/ciudadanos/actions.ts`

---

### 3. Social Programs (Programas Sociales)

**Route**: `/programas-sociales`

**Features**:
- Programs overview with KPIs per program
- Program-specific request management
- Map view with Mapbox clustering
- Status workflow (En proceso → Validado → Entregado → Negado)
- Photo uploads (home, delivery)
- School program support (student info, uniforms)
- Material delivery tracking
- PDF receipt generation
- Excel export with progress tracking

**Program Structure**:

Each program has a unique directory (e.g., `o6mwurdk8xs6l4lp3kxud97j/`) containing:

```
programas-sociales/{program-id}/
├── page.tsx                  # Request listing with map
├── actions.ts                # CRUD operations
├── cols.ts                   # AG Grid column definitions
├── header.tsx                # Program header
├── new/                      # New request form
│   └── page.tsx
└── [socialProgramRequestId]/ # Request detail/edit
    ├── page.tsx
    └── edit/
        └── page.tsx
```

**Column Definitions** (`cols.ts`):
```typescript
export const coloniaMapping = {
  "5 de Diciembre": "5 de Diciembre",
  "Agua Azul": "Agua Azul",
  // ... neighborhood mappings
};

export const cols = [
  { field: 'folio', headerName: 'Folio', sortable: true },
  { field: 'alumno_nombre', headerName: 'Nombre' },
  { field: 'colonia', headerName: 'Colonia', valueGetter: (params) =>
      coloniaMapping[params.data.colonia] || params.data.colonia
  },
  // ...
];
```

**Map Integration**:
```typescript
<Map
  initialViewState={{
    latitude: 20.6534,
    longitude: -105.2253,
    zoom: 12
  }}
>
  <Source
    type="geojson"
    data={geoJsonData}
    cluster={true}
    clusterMaxZoom={14}
    clusterRadius={50}
  >
    <Layer {...clusterLayer} />
    <Layer {...pointLayer} />
  </Source>
</Map>
```

**Status Workflow**:
1. **En proceso**: Initial state, pending validation
2. **Validado**: Approved, ready for delivery
3. **Entregado**: Delivered to beneficiary
4. **Negado**: Rejected with reason

**Key Files**:
- `/Users/manny/Projects/agilgob/Vallarta-Gobify/gobify-portals/apps/gobify-admin-portal/app/(private)/programas-sociales/page.tsx`
- `/Users/manny/Projects/agilgob/Vallarta-Gobify/gobify-portals/apps/gobify-admin-portal/app/(private)/programas-sociales/{program-id}/page.tsx`

---

### 4. Streets Management (Calles)

**Route**: `/calles`

**Features**:
- List all streets with type and name
- Search by type or name
- CRUD operations
- Street type filter (Avenida, Calle, Privada, etc.)

**Search Pattern**:
```typescript
// Multi-field search with $or operator
const params = {
  'filters[$or][0][tipo][$containsi]': searchTerm,
  'filters[$or][1][nombre][$containsi]': searchTerm,
};
```

**Key Files**:
- `/Users/manny/Projects/agilgob/Vallarta-Gobify/gobify-portals/apps/gobify-admin-portal/app/(private)/calles/page.tsx`
- `/Users/manny/Projects/agilgob/Vallarta-Gobify/gobify-portals/apps/gobify-admin-portal/app/(private)/calles/actions.ts`

---

### 5. Neighborhoods (Colonias)

**Route**: `/colonias`

**Features**:
- List neighborhoods with postal codes
- Search by name or postal code
- CRUD operations
- Municipality organization

**Key Files**:
- `/Users/manny/Projects/agilgob/Vallarta-Gobify/gobify-portals/apps/gobify-admin-portal/app/(private)/colonias/page.tsx`
- `/Users/manny/Projects/agilgob/Vallarta-Gobify/gobify-portals/apps/gobify-admin-portal/app/(private)/colonias/actions.ts`

---

### 6. QR Scanner

**Route**: `/qr`

**Features**:
- Scan QR codes from camera or uploaded image
- Generate QR codes for verification
- Display scanned data
- Integration with qr-scanner library

**Implementation**:
```typescript
import QrScanner from 'qr-scanner';

const scanner = new QrScanner(
  videoElement,
  result => {
    console.log('Decoded:', result.data);
  },
  { /* options */ }
);

scanner.start();
```

**Key Files**:
- `/Users/manny/Projects/agilgob/Vallarta-Gobify/gobify-portals/apps/gobify-admin-portal/app/(private)/qr/page.tsx`

---

### 7. Reports (Reportes)

**Route**: `/reportes`

**Features**:
- View citizen-submitted reports
- Filter by type and status
- View photos and location
- Status management

---

### 8. Demographics (Demográfico)

**Route**: `/demografico`

**Features**:
- Citizen demographic statistics
- Age distribution
- Gender breakdown
- Geographic distribution

## State Management

### TanStack Query (React Query)

Used for server state management and caching.

**Configuration** (`app/layout.tsx`):
```typescript
import { QueryClient, QueryClientProvider } from '@tanstack/react-query';

const queryClient = new QueryClient({
  defaultOptions: {
    queries: {
      staleTime: 5 * 60 * 1000, // 5 minutes
      cacheTime: 10 * 60 * 1000, // 10 minutes
      refetchOnWindowFocus: false,
    },
  },
});

export default function RootLayout({ children }) {
  return (
    <QueryClientProvider client={queryClient}>
      {children}
    </QueryClientProvider>
  );
}
```

**Usage Example**:
```typescript
"use client";

import { useQuery, useMutation, useQueryClient } from '@tanstack/react-query';

export function ProfileList() {
  const queryClient = useQueryClient();

  // Fetch data
  const { data, isLoading, error } = useQuery({
    queryKey: ['profiles', { page: 1 }],
    queryFn: () => fetch('/api/v1/profiles').then(r => r.json()),
  });

  // Mutation
  const createMutation = useMutation({
    mutationFn: (newProfile) =>
      fetch('/api/v1/profiles', {
        method: 'POST',
        body: JSON.stringify(newProfile),
      }),
    onSuccess: () => {
      // Invalidate and refetch
      queryClient.invalidateQueries({ queryKey: ['profiles'] });
    },
  });

  if (isLoading) return <Loading />;
  if (error) return <Error />;

  return <div>{/* Render data */}</div>;
}
```

**Key Patterns**:
- Automatic caching and deduplication
- Background refetching
- Optimistic updates
- Cache invalidation on mutations

### Local State

For component-specific state, use React hooks:

```typescript
const [isOpen, setIsOpen] = useState(false);
const [selectedItems, setSelectedItems] = useState<string[]>([]);
```

### Form State

Managed by Formik (see Forms & Validation section).

## API Integration

### Strapi Client Package

**Package**: `@repo/strapi-client`

**Location**: `/Users/manny/Projects/agilgob/Vallarta-Gobify/gobify-portals/packages/strapi-client/index.ts`

**Configuration**:
```typescript
import axios from 'axios';

const strapi = axios.create({
  baseURL: 'https://api.gobify.app/api',
  headers: {
    'Content-Type': 'application/json',
  },
});

// Add auth token interceptor
strapi.interceptors.request.use((config) => {
  const token = localStorage.getItem('token');
  if (token) {
    config.headers.Authorization = `Bearer ${token}`;
  }
  // Add cache buster
  config.params = {
    ...config.params,
    _t: Date.now(),
  };
  return config;
});

export default strapi;
```

**Usage in Server Actions**:
```typescript
"use server";

import strapi from "@repo/strapi-client";

export async function getProfiles(params) {
  const response = await strapi.get('/profiles', { params });
  return response.data;
}

export async function createProfile(data) {
  const response = await strapi.post('/profiles', { data });
  return response.data;
}

export async function updateProfile(id, data) {
  const response = await strapi.put(`/profiles/${id}`, { data });
  return response.data;
}

export async function deleteProfile(id) {
  await strapi.delete(`/profiles/${id}`);
}
```

### API Routes

Next.js API routes for custom logic.

**Example** (`app/api/v1/pdf-export/route.ts`):
```typescript
import { NextRequest, NextResponse } from 'next/server';
import { generatePDF } from '@repo/pdf-generator';

export async function POST(request: NextRequest) {
  try {
    const body = await request.json();
    const { requestIds } = body;

    const pdf = await generatePDF(requestIds);

    return new NextResponse(pdf, {
      headers: {
        'Content-Type': 'application/pdf',
        'Content-Disposition': 'attachment; filename="receipts.pdf"',
      },
    });
  } catch (error) {
    return NextResponse.json(
      { error: error.message },
      { status: 500 }
    );
  }
}
```

### Response Format

All Strapi responses follow this structure:

```typescript
interface StrapiResponse<T> {
  data: T[];
  meta: {
    pagination: {
      page: number;
      pageSize: number;
      pageCount: number;
      total: number;
    };
  };
}

interface StrapiEntity<T> {
  id: number;
  documentId: string;
  attributes: T;
}
```

### Error Handling

```typescript
try {
  const response = await strapi.get('/profiles');
  return response.data;
} catch (error) {
  if (axios.isAxiosError(error)) {
    console.error('API Error:', error.response?.data);
    throw new Error(error.response?.data?.error?.message || 'API Error');
  }
  throw error;
}
```

## Components

### Component Organization

```
components/
├── layout/                    # Layout components
│   ├── Navbar.tsx
│   ├── Sidebar.tsx
│   └── Footer.tsx
├── forms/                     # Form components
│   ├── ProfileForm.tsx
│   ├── ProgramRequestForm.tsx
│   └── AddressForm.tsx
├── tables/                    # Table components
│   ├── ProfileTable.tsx
│   └── RequestTable.tsx
├── maps/                      # Map components
│   ├── RequestMap.tsx
│   └── ClusterMap.tsx
├── ui/                        # UI primitives
│   ├── Button.tsx
│   ├── Card.tsx
│   ├── Modal.tsx
│   └── Input.tsx
└── features/                  # Feature-specific
    ├── dashboard/
    │   ├── KPICard.tsx
    │   └── ActivityFeed.tsx
    └── programs/
        ├── ProgramCard.tsx
        └── StatusBadge.tsx
```

### Component Patterns

**Server Component** (default):
```typescript
// No "use client" directive
export default async function ProfilePage() {
  const profiles = await getProfiles();
  return <div>{/* Render */}</div>;
}
```

**Client Component** (interactive):
```typescript
"use client";

import { useState } from 'react';

export default function InteractiveComponent() {
  const [state, setState] = useState('');
  return <button onClick={() => setState('clicked')}>Click</button>;
}
```

**Shared Component** (reusable):
```typescript
// components/ui/Button.tsx
import { Button as NextUIButton } from '@nextui-org/react';

interface ButtonProps {
  children: React.ReactNode;
  onClick?: () => void;
  variant?: 'solid' | 'bordered' | 'light';
  color?: 'primary' | 'secondary' | 'success' | 'danger';
}

export function Button({ children, ...props }: ButtonProps) {
  return <NextUIButton {...props}>{children}</NextUIButton>;
}
```

### NextUI Components

Common NextUI components used:

- `<Button>` - Buttons with variants
- `<Input>` - Text inputs
- `<Card>` - Content containers
- `<Modal>` - Dialogs and overlays
- `<Table>` - Simple tables
- `<Dropdown>` - Dropdown menus
- `<Tabs>` - Tab navigation
- `<Chip>` - Status badges
- `<Spinner>` - Loading indicators
- `<Avatar>` - User avatars

**Example**:
```typescript
import { Card, CardHeader, CardBody, Button } from '@nextui-org/react';

export function ProfileCard({ profile }) {
  return (
    <Card>
      <CardHeader>
        <h3>{profile.name}</h3>
      </CardHeader>
      <CardBody>
        <p>{profile.curp}</p>
        <Button color="primary">Edit</Button>
      </CardBody>
    </Card>
  );
}
```

## Forms & Validation

### Formik + Yup Pattern

All forms use Formik for state management and Yup for validation.

**Form Component**:
```typescript
"use client";

import { Formik, Form, Field } from 'formik';
import * as Yup from 'yup';
import { Input, Button } from '@nextui-org/react';

const ProfileSchema = Yup.object().shape({
  name: Yup.string()
    .min(2, 'Muy corto')
    .max(50, 'Muy largo')
    .required('Requerido'),
  curp: Yup.string()
    .length(18, 'CURP debe tener 18 caracteres')
    .required('Requerido'),
  phone: Yup.string()
    .matches(/^[0-9]{10}$/, 'Teléfono debe tener 10 dígitos')
    .required('Requerido'),
  email: Yup.string()
    .email('Email inválido')
    .required('Requerido'),
});

export function ProfileForm({ initialValues, onSubmit }) {
  return (
    <Formik
      initialValues={initialValues}
      validationSchema={ProfileSchema}
      onSubmit={onSubmit}
    >
      {({ errors, touched, isSubmitting }) => (
        <Form>
          <Field name="name">
            {({ field }) => (
              <Input
                {...field}
                label="Nombre"
                isInvalid={touched.name && !!errors.name}
                errorMessage={touched.name && errors.name}
              />
            )}
          </Field>

          <Field name="curp">
            {({ field }) => (
              <Input
                {...field}
                label="CURP"
                isInvalid={touched.curp && !!errors.curp}
                errorMessage={touched.curp && errors.curp}
              />
            )}
          </Field>

          <Button
            type="submit"
            isLoading={isSubmitting}
            color="primary"
          >
            Guardar
          </Button>
        </Form>
      )}
    </Formik>
  );
}
```

### Custom Validation Rules

```typescript
// Validate Mexican CURP
const curpRegex = /^[A-Z]{4}[0-9]{6}[HM][A-Z]{5}[0-9]{2}$/;

const CURPValidation = Yup.string()
  .matches(curpRegex, 'CURP inválido')
  .required('CURP es requerido');

// Validate phone number
const PhoneValidation = Yup.string()
  .matches(/^[0-9]{10}$/, 'Teléfono debe tener 10 dígitos')
  .required('Teléfono es requerido');

// Conditional validation
const ConditionalSchema = Yup.object().shape({
  type: Yup.string().required(),
  schoolCode: Yup.string().when('type', {
    is: 'school',
    then: Yup.string().required('Código de escuela requerido'),
    otherwise: Yup.string(),
  }),
});
```

## Maps Integration

### Mapbox GL Implementation

**Setup**:
```typescript
"use client";

import Map, { Source, Layer, Marker } from 'react-map-gl';
import 'mapbox-gl/dist/mapbox-gl.css';

const MAPBOX_TOKEN = process.env.NEXT_PUBLIC_MAPBOX_TOKEN;

export function RequestMap({ requests }) {
  return (
    <Map
      mapboxAccessToken={MAPBOX_TOKEN}
      initialViewState={{
        latitude: 20.6534,
        longitude: -105.2253,
        zoom: 12,
      }}
      style={{ width: '100%', height: '600px' }}
      mapStyle="mapbox://styles/mapbox/streets-v12"
    >
      {requests.map((request) => (
        <Marker
          key={request.id}
          latitude={request.lat}
          longitude={request.lng}
        >
          <div className="marker">📍</div>
        </Marker>
      ))}
    </Map>
  );
}
```

### Clustering with Supercluster

**Implementation**:
```typescript
import Supercluster from 'supercluster';
import { Source, Layer } from 'react-map-gl';

function ClusterMap({ points }) {
  const supercluster = new Supercluster({
    radius: 50,
    maxZoom: 16,
  });

  supercluster.load(
    points.map(p => ({
      type: 'Feature',
      geometry: {
        type: 'Point',
        coordinates: [p.lng, p.lat],
      },
      properties: p,
    }))
  );

  const clusters = supercluster.getClusters(bounds, zoom);

  return (
    <Map>
      <Source
        type="geojson"
        data={{
          type: 'FeatureCollection',
          features: clusters,
        }}
      >
        <Layer
          id="clusters"
          type="circle"
          paint={{
            'circle-color': [
              'step',
              ['get', 'point_count'],
              '#51bbd6',
              10,
              '#f1f075',
              50,
              '#f28cb1',
            ],
            'circle-radius': [
              'step',
              ['get', 'point_count'],
              20,
              10,
              30,
              50,
              40,
            ],
          }}
        />
      </Source>
    </Map>
  );
}
```

### Map Controls

```typescript
import { NavigationControl, GeolocateControl } from 'react-map-gl';

<Map>
  <NavigationControl position="top-right" />
  <GeolocateControl
    position="top-right"
    trackUserLocation
  />
</Map>
```

## Document Generation

### PDF Generation

**Package**: `@repo/pdf-generator`

**Location**: `/Users/manny/Projects/agilgob/Vallarta-Gobify/gobify-portals/packages/pdf-generator/`

**Features**:
- Template-based PDF generation
- Batch processing with progress tracking
- Database integration
- Custom styling

**Usage**:
```typescript
import { PDFGenerator } from '@repo/pdf-generator';

// Generate single PDF
const generator = new PDFGenerator();
const pdf = await generator.generate({
  template: 'delivery-receipt',
  data: {
    folio: '12345',
    beneficiary: 'Juan Pérez',
    program: 'Apoyo Alimentario',
    date: new Date(),
  },
});

// Save PDF
fs.writeFileSync('receipt.pdf', pdf);
```

**Batch Generation with Progress**:
```typescript
const requestIds = [1, 2, 3, 4, 5];

await generator.generateBatch(requestIds, {
  onProgress: (current, total) => {
    console.log(`Progress: ${current}/${total}`);
  },
  onComplete: (pdf) => {
    console.log('Generation complete');
  },
  onError: (error) => {
    console.error('Error:', error);
  },
});
```

**API Route** (`app/api/v1/pdf-export/route.ts`):
```typescript
export async function POST(request: NextRequest) {
  const { requestIds } = await request.json();
  const progressId = crypto.randomUUID();

  // Store progress
  progressStore.set(progressId, { current: 0, total: requestIds.length });

  // Generate in background
  generatePDFs(requestIds, (current, total) => {
    progressStore.set(progressId, { current, total });
  });

  return NextResponse.json({ progressId });
}
```

**Progress Tracking** (`app/api/v1/pdf-export-progress/route.ts`):
```typescript
export async function GET(request: NextRequest) {
  const progressId = request.nextUrl.searchParams.get('id');
  const progress = progressStore.get(progressId);

  return NextResponse.json(progress || { current: 0, total: 0 });
}
```

### Excel Export

**Using ExcelJS**:
```typescript
import ExcelJS from 'exceljs';

async function exportToExcel(data: any[]) {
  const workbook = new ExcelJS.Workbook();
  const worksheet = workbook.addWorksheet('Datos');

  // Add headers
  worksheet.columns = [
    { header: 'Folio', key: 'folio', width: 10 },
    { header: 'Nombre', key: 'name', width: 30 },
    { header: 'CURP', key: 'curp', width: 20 },
    { header: 'Teléfono', key: 'phone', width: 15 },
  ];

  // Add rows
  data.forEach(item => {
    worksheet.addRow(item);
  });

  // Style header
  worksheet.getRow(1).font = { bold: true };
  worksheet.getRow(1).fill = {
    type: 'pattern',
    pattern: 'solid',
    fgColor: { argb: 'FF2C8B85' },
  };

  // Generate buffer
  const buffer = await workbook.xlsx.writeBuffer();
  return buffer;
}
```

**Download in Browser**:
```typescript
"use client";

async function handleExport() {
  const buffer = await exportToExcel(data);
  const blob = new Blob([buffer], {
    type: 'application/vnd.openxmlformats-officedocument.spreadsheetml.sheet'
  });
  const url = URL.createObjectURL(blob);
  const link = document.createElement('a');
  link.href = url;
  link.download = 'export.xlsx';
  link.click();
  URL.revokeObjectURL(url);
}
```

## Styling

### Tailwind CSS

**Configuration** (`tailwind.config.js`):
```javascript
const { nextui } = require("@nextui-org/react");

module.exports = {
  content: [
    "./app/**/*.{js,ts,jsx,tsx}",
    "./components/**/*.{js,ts,jsx,tsx}",
    "./node_modules/@nextui-org/theme/dist/**/*.{js,ts,jsx,tsx}",
  ],
  theme: {
    extend: {
      colors: {
        primary: {
          DEFAULT: '#2C8B85',
          50: '#E6F7F5',
          100: '#CCF0EB',
          500: '#2C8B85',
          900: '#1A5250',
        },
        secondary: {
          DEFAULT: '#B79905',
          50: '#FDF8E6',
          500: '#B79905',
        },
      },
    },
  },
  darkMode: "class",
  plugins: [nextui()],
};
```

**Usage**:
```typescript
<div className="bg-primary text-white p-4 rounded-lg shadow-md">
  <h1 className="text-2xl font-bold">Title</h1>
  <p className="text-sm text-gray-100">Description</p>
</div>
```

### Custom CSS

**Global Styles** (`app/globals.css`):
```css
@tailwind base;
@tailwind components;
@tailwind utilities;

@layer base {
  :root {
    --primary: 44 139 133;
    --secondary: 183 153 5;
  }
}

@layer components {
  .btn-primary {
    @apply bg-primary text-white px-4 py-2 rounded-lg hover:bg-primary-600;
  }

  .card {
    @apply bg-white rounded-lg shadow-md p-6;
  }
}
```

### Responsive Design

```typescript
<div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
  {/* Responsive grid */}
</div>

<div className="hidden md:block">
  {/* Show only on medium screens and up */}
</div>

<div className="md:hidden">
  {/* Show only on small screens */}
</div>
```

## Development

### Running Development Server

```bash
# From monorepo root
npm run dev

# Or specific app
cd apps/gobify-admin-portal
npm run dev
```

### Building for Production

```bash
# Build all apps and packages
npm run build

# Or specific app
cd apps/gobify-admin-portal
npm run build
```

### Linting and Formatting

```bash
# Lint all code
npm run lint

# Format with Prettier
npm run format
```

### Type Checking

```bash
# Check types across all packages
turbo check-types
```

### Adding Dependencies

```bash
# Add to specific workspace
npm install <package> -w apps/gobify-admin-portal

# Add to all workspaces
npm install <package> -ws
```

## Testing

### Jest Configuration

**File**: `apps/gobify-admin-portal/jest.config.js`

```javascript
module.exports = {
  preset: 'ts-jest',
  testEnvironment: 'jsdom',
  setupFilesAfterEnv: ['<rootDir>/jest.setup.js'],
  moduleNameMapper: {
    '^@/(.*)$': '<rootDir>/$1',
  },
};
```

### Writing Tests

**Component Test**:
```typescript
// __tests__/ProfileCard.test.tsx
import { render, screen } from '@testing-library/react';
import { ProfileCard } from '@/components/ProfileCard';

describe('ProfileCard', () => {
  it('renders profile information', () => {
    const profile = {
      name: 'Juan Pérez',
      curp: 'JUAP850101HJCRRN01',
    };

    render(<ProfileCard profile={profile} />);

    expect(screen.getByText('Juan Pérez')).toBeInTheDocument();
    expect(screen.getByText('JUAP850101HJCRRN01')).toBeInTheDocument();
  });
});
```

**Hook Test**:
```typescript
// __tests__/useDebounce.test.ts
import { renderHook } from '@testing-library/react-hooks';
import { useDebounce } from '@/hooks/useDebounce';

describe('useDebounce', () => {
  it('debounces value', async () => {
    const { result, rerender, waitForNextUpdate } = renderHook(
      ({ value }) => useDebounce(value, 500),
      { initialProps: { value: 'initial' } }
    );

    expect(result.current).toBe('initial');

    rerender({ value: 'updated' });
    expect(result.current).toBe('initial'); // Still old value

    await waitForNextUpdate();
    expect(result.current).toBe('updated'); // New value after delay
  });
});
```

### Running Tests

```bash
# Run all tests
npm test

# Watch mode
npm run test:watch

# Coverage report
npm run test:coverage
```

## Best Practices

1. **Use Server Components by Default**: Only add "use client" when needed
2. **Colocate Server Actions**: Keep actions.ts near the component using them
3. **Type Everything**: Use TypeScript for all files
4. **Validate Forms**: Always use Yup schemas
5. **Handle Errors**: Use try-catch and display user-friendly messages
6. **Optimize Images**: Use Next.js Image component
7. **Lazy Load**: Use dynamic imports for heavy components
8. **Cache Wisely**: Configure TanStack Query cache times appropriately
9. **Test Components**: Write tests for critical functionality
10. **Follow Conventions**: Maintain consistent file structure

## Performance Optimization

### Code Splitting

```typescript
// Dynamic import for heavy component
import dynamic from 'next/dynamic';

const HeavyMap = dynamic(() => import('@/components/HeavyMap'), {
  loading: () => <p>Loading map...</p>,
  ssr: false, // Disable server-side rendering
});
```

### Image Optimization

```typescript
import Image from 'next/image';

<Image
  src="/photo.jpg"
  alt="Description"
  width={500}
  height={300}
  priority // For above-fold images
  placeholder="blur" // Show blur placeholder
/>
```

### Bundle Analysis

```bash
# Install bundle analyzer
npm install @next/bundle-analyzer

# Add to next.config.js
const withBundleAnalyzer = require('@next/bundle-analyzer')({
  enabled: process.env.ANALYZE === 'true',
});

module.exports = withBundleAnalyzer(config);

# Run analysis
ANALYZE=true npm run build
```

## Troubleshooting

### Common Issues

**Issue**: "Hydration mismatch"
- **Cause**: Server and client rendering different content
- **Solution**: Ensure consistent data between server and client

**Issue**: "Cannot use client component in server component"
- **Solution**: Add "use client" directive to client component

**Issue**: "TanStack Query not updating"
- **Solution**: Check queryKey and invalidateQueries calls

**Issue**: "Mapbox not rendering"
- **Solution**: Verify MAPBOX_TOKEN and import CSS

## Documentation

- **Next.js**: https://nextjs.org/docs
- **React**: https://react.dev/
- **TanStack Query**: https://tanstack.com/query/latest/docs/react/overview
- **NextUI**: https://nextui.org/docs
- **Tailwind CSS**: https://tailwindcss.com/docs
- **Formik**: https://formik.org/docs
- **Mapbox**: https://docs.mapbox.com/

---

**Document Version**: 1.0.0
**Last Updated**: December 2024
**Frontend Version**: Next.js 15.3.2
