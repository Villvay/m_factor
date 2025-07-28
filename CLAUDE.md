# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

MFactor is a healthcare provider directory platform for menopause care, built with Laravel 12, Filament 3, and Inertia 2. The project emphasizes HIPAA compliance, security, modern development practices, and features a sophisticated matching algorithm to connect patients with the most suitable providers while ensuring fair distribution.

## Tech Stack

- **Backend**: Laravel 12, PHP 8.4, PostgreSQL 16 with PostGIS 3.4
- **Admin**: Filament 3 for admin panel
- **Frontend**: Inertia 2 with React 18 or Vue 3, TypeScript 5, shadcn/ui, Tailwind CSS 3
- **API**: Laravel Orion for REST API generation
- **Infrastructure**: Laravel Cloud hosting, Cloudflare CDN, Redis 7 for caching

## Common Commands

```bash
# Development
npm run dev          # Start Vite dev server
php artisan serve    # Start Laravel dev server

# Building
npm run build        # Build frontend assets  
php artisan optimize # Optimize Laravel for production

# Testing
php artisan test     # Run Pest tests
npm run type-check   # TypeScript type checking

# Code Quality
./vendor/bin/pint    # Laravel Pint for PHP formatting
npm run lint         # ESLint for JavaScript/TypeScript

# Database
php artisan migrate  # Run database migrations
php artisan db:seed  # Seed database with test data
```

## Architecture Overview

### Multi-Role System
- **Patients**: Search providers, save favorites, manage profiles
- **Providers**: Self-service portal for profile management
- **Reviewers**: Approve/reject provider applications  
- **Admins**: Full system access via Filament

### Key Components
1. **Provider Management**: Approval workflows with states (pending, under_review, approved, rejected)
2. **Matching Algorithm**: Sophisticated ranking system considering menopause-specific factors with fair provider rotation
3. **Search System**: PostgreSQL full-text search with PostGIS for location-based queries
4. **Analytics**: Event tracking system with matching algorithm metrics and dashboards
5. **Security**: Audit trails, rate limiting, anti-crawling measures

### Database Design
- Uses PostgreSQL with PostGIS for spatial queries
- Provider profiles use JSONB for flexible medical attributes
- Comprehensive audit logging for HIPAA compliance
- Event-driven analytics storage

## Development Guidelines

1. **Security First**: All features must consider HIPAA compliance and include audit logging
2. **Use TypeScript**: All frontend code should be fully typed
3. **Test Coverage**: Write Pest tests for all critical backend functionality, especially matching algorithm
4. **API Design**: Use Laravel Orion conventions for REST endpoints
5. **Frontend Components**: Leverage shadcn/ui components for consistency
6. **Algorithm Testing**: A/B test matching algorithm variations with proper metrics
7. **Fair Distribution**: Ensure provider rotation prevents monopolization of search results

## Important Considerations

- **Healthcare Compliance**: No PHI collected, but follow security best practices
- **Provider Verification**: Manual review process with external team for license verification
- **Payment Model**: Providers pay per match, not for listing
- **Provider Levels**: Three tiers (medical, allied health, non-medical) with appropriate disclaimers
- **Location Services**: Use PostGIS for all location-based queries
- **Performance**: Implement caching strategies using Redis
- **Security**: 2FA required, rate limiting, anti-crawling/AI scraping protection
- **No Insurance Integration**: Platform only connects patients and providers