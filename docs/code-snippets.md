# The (M) Factor - Code Snippets & Examples

This document contains all code snippets and examples referenced in the technical documentation.

## Table of Contents

1. [Frontend Migration Commands](#frontend-migration-commands)
2. [Matching Algorithm Implementation](#matching-algorithm-implementation)
3. [Database Queries & Schema](#database-queries--schema)
4. [Security Implementation](#security-implementation)
5. [Analytics Implementation](#analytics-implementation)
6. [Laravel Configuration](#laravel-configuration)
7. [Quick Start Commands](#quick-start-commands)

---

## Frontend Migration Commands

### Switching Between React and Vue

```bash
php artisan install:vue  # Switch from React to Vue
php artisan install:react # Switch from Vue to React
```

## Matching Algorithm Implementation

### Provider Matching Service

```php
class ProviderMatchingService
{
    private const WEIGHTS = [
        'specialization' => 0.20,
        'treatment_match' => 0.15,
        'insurance' => 0.15,
        'distance' => 0.10,
        'availability' => 0.10,
        'reviews' => 0.10,
        'experience' => 0.05,
        'language' => 0.05,
        'rotation' => 0.10,
    ];
    
    public function rankProviders($patient, $providers)
    {
        $scoredProviders = [];
        
        foreach ($providers as $provider) {
            $score = $this->calculateMatchScore($patient, $provider);
            $scoredProviders[] = [
                'provider' => $provider,
                'score' => $score,
                'breakdown' => $this->getScoreBreakdown($patient, $provider)
            ];
        }
        
        // Apply rotation factor to prevent same providers always first
        $this->applyRotationFactor($scoredProviders);
        
        // Sort by score but introduce controlled randomness
        return $this->smartSort($scoredProviders);
    }
}
```

## Database Queries & Schema

### Provider Rotation Tracking

```sql
-- Provider rotation tracking
CREATE TABLE provider_rotations (
    provider_id UUID,
    appearance_date DATE,
    position INTEGER,
    search_count INTEGER,
    PRIMARY KEY (provider_id, appearance_date)
);

-- Calculate rotation penalty
SELECT 
    provider_id,
    COUNT(*) as recent_appearances,
    AVG(position) as avg_position,
    CASE 
        WHEN COUNT(*) > 20 THEN 0.7  -- Heavy penalty
        WHEN COUNT(*) > 10 THEN 0.85 -- Medium penalty
        WHEN COUNT(*) > 5 THEN 0.95  -- Light penalty
        ELSE 1.0                      -- No penalty
    END as rotation_multiplier
FROM provider_rotations
WHERE appearance_date >= CURRENT_DATE - INTERVAL '7 days'
GROUP BY provider_id;
```

### Optimized Matching Query

```sql
-- Optimized matching query with CTEs
WITH provider_scores AS (
    SELECT 
        p.id,
        -- Base matching scores
        CASE 
            WHEN ps.name = :patient_need THEN 1.0
            WHEN ps.category = :patient_category THEN 0.7
            ELSE 0.3
        END * :weight_specialization as spec_score,
        
        -- Distance score with telehealth consideration
        CASE 
            WHEN p.offers_telehealth THEN 1.0
            ELSE (1 - (ST_Distance(p.location, :patient_location) / 50000))
        END * :weight_distance as distance_score,
        
        -- Other scores...
    FROM providers p
    JOIN provider_specialties ps ON p.id = ps.provider_id
    WHERE p.status = 'approved'
),
rotation_penalties AS (
    SELECT provider_id, rotation_multiplier
    FROM provider_rotation_scores
    WHERE week = DATE_TRUNC('week', CURRENT_DATE)
)
SELECT 
    ps.*,
    COALESCE(rp.rotation_multiplier, 1.0) as rotation_factor,
    (spec_score + distance_score + ...) * COALESCE(rp.rotation_multiplier, 1.0) as final_score
FROM provider_scores ps
LEFT JOIN rotation_penalties rp ON ps.id = rp.provider_id
ORDER BY final_score DESC
LIMIT 20;
```

### Analytics Tables Schema

```sql
-- Real-time events (partitioned by month)
CREATE TABLE analytics_events (
    id BIGSERIAL PRIMARY KEY,
    user_id UUID,
    session_id VARCHAR(255),
    event_type VARCHAR(50),
    event_data JSONB,
    created_at TIMESTAMP
) PARTITION BY RANGE (created_at);

-- Aggregated daily metrics
CREATE TABLE analytics_daily (
    date DATE PRIMARY KEY,
    total_searches INTEGER,
    unique_users INTEGER,
    provider_views INTEGER,
    contact_clicks INTEGER,
    top_searches JSONB,
    conversion_rate DECIMAL(5,2)
);

-- Provider performance metrics
CREATE TABLE provider_analytics (
    provider_id UUID,
    date DATE,
    search_appearances INTEGER,
    profile_views INTEGER,
    contact_clicks INTEGER,
    PRIMARY KEY (provider_id, date)
);
```

## Security Implementation

### Rate Limiting Configuration

```php
// routes/api.php
Route::middleware(['auth:sanctum', 'throttle:60,1'])->group(function () {
    Route::get('/providers/search', [ProviderController::class, 'search']);
    Route::get('/providers/{id}', [ProviderController::class, 'show']);
});
```

### Event Tracking Implementation

```php
// Event listener example
class TrackSearchEvent
{
    public function handle(SearchPerformed $event)
    {
        AnalyticsJob::dispatch([
            'event_type' => 'search',
            'user_id' => auth()->id(),
            'session_id' => session()->getId(),
            'event_data' => [
                'query' => $event->query,
                'filters' => $event->filters,
                'result_count' => $event->resultCount,
            ]
        ])->onQueue('analytics');
    }
}
```

## Analytics Implementation

### Analytics Event Listener

```php
// Event listener example
class TrackSearchEvent
{
    public function handle(SearchPerformed $event)
    {
        AnalyticsJob::dispatch([
            'event_type' => 'search',
            'user_id' => auth()->id(),
            'session_id' => session()->getId(),
            'event_data' => [
                'query' => $event->query,
                'filters' => $event->filters,
                'result_count' => $event->resultCount,
            ]
        ])->onQueue('analytics');
    }
}
```

## Laravel Configuration

### Laravel Cloud Configuration

```yaml
# laravel-cloud.yml
services:
  - type: app
    name: m-factor
    memory: 1GB
    cpu: 1
    
databases:
  - type: postgresql
    name: m-factor-db
    version: 16
    extensions:
      - postgis
      
cache:
  - type: redis
  
storage:
  - type: r2
    name: m-factor-storage
    
queues:
  - default
  - emails
  - analytics
```

### Laravel Package Dependencies

```json
{
  "laravel/framework": "^12.0",
  "filament/filament": "^3.2",
  "laravel/sanctum": "^4.0",
  "laravel/horizon": "^5.24",
  "spatie/laravel-permission": "^6.7",
  "owen-it/laravel-auditing": "^13.6",
  "ringlesoft/laravel-process-approval": "^2.0"
}
```

## Quick Start Commands

### Project Setup

```bash
# Create Laravel 12 project with React starter kit
composer create-project laravel/laravel:^12.0 m-factor
cd m-factor

# Install the React starter kit (includes Inertia 2, TypeScript, shadcn/ui)
php artisan install:react

# Or install Vue starter kit if preferred
# php artisan install:vue

# IMPORTANT: Verify package compatibility with Laravel 12
# Some packages may need updates for Laravel 12 compatibility

# Install core packages
composer require filament/filament
composer require laravel/horizon
composer require spatie/laravel-permission
composer require owen-it/laravel-auditing
composer require ringlesoft/laravel-process-approval

# Filament plugins
composer require tapp/filament-auditing
composer require eightynine/filament-approvals

# Development tools
composer require --dev pestphp/pest
composer require --dev phpstan/phpstan

# Setup
php artisan filament:install --panels
npm install
npm run dev

# Create admin user
php artisan make:filament-user
```

### Common Development Commands

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

---

**Note**: As Laravel 12 was just released (February 2025), some packages may need updates. Check package compatibility and consider using `composer require --dev` to test packages first.