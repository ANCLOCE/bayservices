# Dryer Vent Pro Reports Application

## Overview

This is a full-stack web application for creating and managing professional dryer vent cleaning reports. The application allows technicians to document their work, attach photos, and generate PDF reports for clients. It features a modern React frontend with a dark mode UI, built with shadcn/ui components, and a Node.js backend with Express. Data is persisted using Drizzle ORM with PostgreSQL.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

The application follows a client-server architecture with a clear separation between frontend and backend:

### Frontend
- Built with React and TypeScript
- Uses shadcn/ui components based on Radix UI primitives
- State management with React Query for server state
- Form handling with React Hook Form and Zod validation
- Dark-themed UI with Tailwind CSS for styling
- Client-side routing with Wouter (lightweight alternative to React Router)

### Backend
- Node.js with Express for the API server
- TypeScript for type safety
- Drizzle ORM for database access
- RESTful API design
- Session-based authentication (currently partially implemented)
- File handling for photo uploads (base64 encoded)

### Database
- PostgreSQL for data storage
- Schema defined with Drizzle ORM schema builders
- Includes tables for users, properties, and reports

## Key Components

### Frontend Components

1. **Layout Components**
   - `Header`: App header with logo and user information
   - `Footer`: App footer with copyright and links

2. **Form Components**
   - `ReportForm`: Main form for creating new vent cleaning reports
   - Includes property selection, date, technician name, work description, and photo uploads

3. **Display Components**
   - `SavedReports`: Displays previously saved reports
   - Various UI components from shadcn/ui library

4. **Utility Components**
   - Comprehensive UI component library based on shadcn/ui
   - Toast notifications for user feedback

### Backend Components

1. **API Routes**
   - Property management routes (`/api/properties`)
   - Report management routes (`/api/reports`)
   - User authentication (partially implemented)

2. **Storage Layer**
   - `storage.ts`: Interface for data persistence
   - Currently using in-memory storage with plans to use PostgreSQL

3. **Schema Definitions**
   - Database schema defined in `shared/schema.ts`
   - Includes models for users, properties, and reports
   - Zod validation schemas for input validation

## Data Flow

1. **User Authentication**
   - User logs in (authentication flow not fully implemented)
   - Session is maintained for the logged-in technician

2. **Report Creation**
   - User selects a property from dropdown
   - Fills in report details (date, technician name, work description)
   - Optionally attaches photos with captions
   - Submits form which is validated with Zod
   - Data is sent to backend API and stored in database

3. **Report Retrieval**
   - Reports are fetched from backend API
   - Displayed in the SavedReports component
   - Can be filtered by property

4. **PDF Generation**
   - Reports can be exported to PDF using jsPDF
   - Includes all report details and photos

## External Dependencies

### Frontend Libraries
- React and React DOM for UI
- Tailwind CSS for styling
- shadcn/ui components (based on Radix UI)
- React Hook Form for form handling
- Zod for validation
- React Query for data fetching
- jsPDF for PDF generation
- Wouter for client-side routing

### Backend Libraries
- Express for API server
- Drizzle ORM for database access
- Zod for validation
- Various utility libraries

## Deployment Strategy

The application is configured for deployment on Replit:

1. **Development**
   - Run with `npm run dev` for local development
   - Vite handles frontend hot reloading
   - Server runs with tsx for TypeScript execution

2. **Production Build**
   - Frontend built with Vite (`npm run build`)
   - Backend compiled with esbuild
   - Combined into single deployment package

3. **Database**
   - Uses Postgres on Replit
   - Connection via environment variable (DATABASE_URL)
   - Schema migrations with Drizzle Kit

4. **Hosting**
   - Configured for Replit deployment
   - Uses Replit's autoscale deployment target
   - Exposes port 5000 internally, mapped to port 80 externally