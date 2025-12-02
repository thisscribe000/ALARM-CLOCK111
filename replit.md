# Overview

This is a mobile-first alarm clock application built with React and Express. The app allows users to create, manage, and respond to alarms with customizable settings including repeat schedules, snooze options, alarm sounds, and an optional Tic-Tac-Toe challenge for dismissal. The application features a modern, mobile-optimized interface following iOS/Material Design hybrid principles.

# User Preferences

Preferred communication style: Simple, everyday language.

# System Architecture

## Frontend Architecture

**Framework & Build System**
- **React 18** with TypeScript for type safety and modern React features
- **Vite** as the build tool and development server for fast HMR and optimized production builds
- **Wouter** for lightweight client-side routing (no React Router dependency)
- **TanStack Query** for server state management and data fetching

**UI Component Strategy**
- **shadcn/ui** component library built on Radix UI primitives for accessible, unstyled components
- **Tailwind CSS** for utility-first styling with custom design tokens
- Custom mobile-first design system with consistent spacing (2, 4, 6, 8, 12, 16, 24px units)
- Maximum container width of 428px (iPhone 14 Pro Max) to enforce mobile-first experience
- Responsive design that works on desktop but prioritizes mobile UX

**State Management Strategy**
- **Local Storage** for alarm data persistence (client-side only, no backend persistence)
- In-memory storage service (`MemStorage`) on server side for user data (ephemeral)
- Alarm scheduler runs client-side with interval-based checking (every 5 seconds)
- React hooks for component-level state management

**Client-Side Scheduling**
- `alarmScheduler` service continuously checks for alarms that need to trigger
- Computes next trigger times based on current time and alarm settings
- Handles snooze logic with configurable snooze counts and durations
- Manages alarm sound playback and device vibration through dedicated services

## Backend Architecture

**Server Framework**
- **Express.js** with TypeScript for type-safe API development
- Middleware setup for JSON parsing, logging, and request tracking
- Vite integration in development mode for HMR and asset serving
- Static file serving in production from built assets

**Database & ORM**
- **Drizzle ORM** configured for PostgreSQL with schema-first development
- Database schema defined in `shared/schema.ts` for type sharing between client and server
- **Neon Serverless** driver for PostgreSQL connectivity
- Current implementation uses in-memory storage (`MemStorage` class) - database integration is prepared but not actively used for alarm data

**Why PostgreSQL is Prepared but Not Used**
- The application stores alarm data in browser localStorage for simplicity and offline capability
- PostgreSQL setup (via Drizzle + Neon) is scaffolded for future features like user accounts, cloud sync, or multi-device support
- The `users` table schema is defined but the alarm functionality operates entirely client-side

**API Design**
- Routes prefixed with `/api` for clear separation from frontend routes
- Centralized error handling and response logging
- Storage interface pattern (`IStorage`) for potential database implementation switching

## Design System

**Color Palette**
- Primary: `#36454F` (charcoal blue-gray) for navigation and primary actions
- Background: White (`#FFFFFF`) for cards, Light gray (`#F5F5F5`) for page background
- Text: Near-black (`#1F2937`) for primary text, Medium gray (`#6B7280`) for secondary
- Accent colors derived from primary with hover state variations

**Typography**
- Primary font: **Inter** from Google Fonts for high legibility
- Heading scale: H1 (28px), H2 (24px), H3 (20px)
- Body text: 16px with 1.6 line-height
- Consistent font weights: 400 (regular), 600 (semibold), 700 (bold)

**Component Patterns**
- Card-based layout with rounded corners (rounded-2xl = 16px)
- Consistent padding and spacing using Tailwind's spacing scale
- Sticky header (64px height) with back navigation and actions
- Custom time picker with scroll-based selection
- Badge components for day-of-week selection
- Switch components for alarm toggle states

## External Dependencies

**UI Component Libraries**
- **@radix-ui/** suite: Accessible, unstyled component primitives (accordion, dialog, dropdown, select, switch, toast, etc.)
- **lucide-react**: Icon library for consistent iconography
- **class-variance-authority**: Component variant management
- **cmdk**: Command palette component
- **embla-carousel-react**: Carousel/slider functionality

**Database & Backend**
- **@neondatabase/serverless**: PostgreSQL driver for edge/serverless environments
- **drizzle-orm**: Type-safe SQL query builder and ORM
- **drizzle-zod**: Zod schema generation from Drizzle schemas
- **connect-pg-simple**: PostgreSQL session store for Express (prepared for future auth)

**Utilities & Tooling**
- **date-fns**: Date manipulation and formatting
- **zod**: Runtime type validation and schema definition
- **clsx** + **tailwind-merge**: Conditional className composition
- **nanoid**: Unique ID generation
- **wouter**: Lightweight routing library

**Development Tools**
- **tsx**: TypeScript execution for development server
- **esbuild**: Fast JavaScript bundler for production builds
- **Replit plugins**: Development banners, error overlays, and cartographer for Replit environment

**Browser APIs Used**
- **LocalStorage**: Persistent alarm data storage
- **Web Audio API**: Fallback beep sounds when audio files fail to load
- **Vibration API**: Device vibration for alarm alerts (mobile only)
- **Audio Element**: Playing custom alarm sounds