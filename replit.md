# Sayani De Author Website

## Overview

This is a full-stack web application for author Sayani De, built with React frontend and Express.js backend. The application serves as a professional author portfolio featuring her published works, about section, contact functionality, and newsletter subscription. The site is designed with a literary theme using custom typography and a sophisticated color palette.

## System Architecture

The application follows a monorepo structure with separate client and server directories, sharing common schemas and types. It uses a modern tech stack optimized for performance and developer experience.

**Architecture Pattern**: Full-stack monorepo with shared types
**Build System**: Vite for frontend bundling and esbuild for server compilation
**Database Strategy**: Drizzle ORM with PostgreSQL, including fallback in-memory storage
**Styling**: Tailwind CSS with shadcn/ui component library

## Key Components

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter for lightweight client-side routing
- **State Management**: TanStack Query for server state management
- **UI Library**: shadcn/ui components built on Radix UI primitives
- **Styling**: Tailwind CSS with custom writer-themed color variables
- **Forms**: React Hook Form with Zod validation
- **Typography**: Custom Google Fonts (Playfair Display, Source Sans Pro, Crimson Text)

### Backend Architecture
- **Runtime**: Node.js with Express.js
- **Language**: TypeScript with ES modules
- **Database**: PostgreSQL with Drizzle ORM
- **Email Service**: Nodemailer with Gmail SMTP
- **Session Storage**: PostgreSQL sessions via connect-pg-simple
- **Development**: Hot reloading with Vite integration

### Data Storage
- **Primary Database**: PostgreSQL via Neon Database
- **ORM**: Drizzle with type-safe queries and migrations
- **Fallback**: In-memory storage implementation for development
- **Schema**: Shared TypeScript definitions with Zod validation

### Key Features
- **Contact Form**: Full-featured contact system with email notifications
- **Newsletter**: Subscription management with email validation
- **Portfolio**: Dynamic book showcase with ratings and descriptions
- **Responsive Design**: Mobile-first approach with elegant desktop layouts
- **SEO Optimized**: Meta tags, Open Graph, and semantic HTML

## Data Flow

1. **Contact Submissions**: Form data → Zod validation → Database storage → Email notification
2. **Newsletter Signups**: Email validation → Database storage → Success confirmation
3. **Content Display**: Static data rendered through React components with smooth scrolling navigation
4. **API Communication**: TanStack Query handles all server communication with error handling and caching

## External Dependencies

### Core Dependencies
- **@neondatabase/serverless**: PostgreSQL database connection
- **nodemailer**: Email service integration
- **@tanstack/react-query**: Server state management
- **drizzle-orm**: Type-safe database operations
- **@radix-ui/***: Accessible UI component primitives

### Development Tools
- **Vite**: Frontend build tool and dev server
- **esbuild**: Server bundling for production
- **tsx**: TypeScript execution for development
- **@replit/vite-plugin-***: Replit integration plugins

### UI and Styling
- **tailwindcss**: Utility-first CSS framework
- **class-variance-authority**: Component variant management
- **react-hook-form**: Form handling with validation
- **wouter**: Lightweight React router

## Deployment Strategy

**Development**: 
- Frontend served by Vite dev server with HMR
- Backend runs via tsx with automatic restart
- Database operations use Drizzle Kit for schema management

**Production**:
- Frontend built to static assets via Vite
- Backend compiled to single ESM bundle via esbuild
- Static files served by Express in production
- Database migrations handled via `drizzle-kit push`

**Environment Variables Required**:
- `DATABASE_URL`: PostgreSQL connection string
- `EMAIL_USER` / `GMAIL_USER`: SMTP authentication
- `EMAIL_PASS` / `GMAIL_PASS`: SMTP password
- `WRITER_EMAIL`: Destination for contact form submissions

## User Preferences

Preferred communication style: Simple, everyday language.

## Deployment Options

The website is prepared for multiple deployment platforms:

### Replit Deployment (Current)
- One-click deployment via Replit Deploy button
- Automatic SSL and domain provisioning
- Suitable for immediate sharing and review

### AWS Deployment (Prepared)
- Complete AWS deployment guide available in `AWS_DEPLOYMENT_GUIDE.md`
- Production-ready package.json configuration in `package-aws.json`
- Environment variables configured for email functionality
- Multiple AWS options: Amplify (recommended), EC2, Elastic Beanstalk

### Email Configuration
- Gmail SMTP integration for contact form
- Environment variables: GMAIL_USER, GMAIL_PASS, WRITER_EMAIL
- Production-ready email templates

## Changelog

Changelog:
- June 29, 2025. Initial setup with Sarah Mitchell placeholder content
- June 29, 2025. Customized website for Sayani De with personal information, biography, works, and contact details
  - Updated author name throughout the website
  - Added biography: bibliophile, traveler, sustainability enthusiast
  - Updated works section with 5 actual publications:
    * "The Lasts of Her" - The Bangalore Review (2024)
    * "Published in The Sahitya Akademi Magazine" (2024)
    * "Mismatched" - The Indian Review (2024, Editor's Choice)
    * "Anu Didi" - Muse India (2023)
    * "Commonwealth Short Story Prize Longlisted" (2025)
  - Changed contact email to sayanide1984@gmail.com
  - Updated location to Bangalore, India
  - Integrated user's portrait photo
  - Updated social media links: Twitter (@tweets_shay), Instagram (@sayani_quill), LinkedIn (sayanide), Facebook
  - Modified email templates and server configuration
  - Prepared AWS deployment package and comprehensive deployment guide