# The (M) Factor Technical Documentation

This directory contains the complete technical documentation for The (M) Factor Menopause Provider Directory platform. The documentation has been organized into focused sections for easier navigation and maintenance.

## Document Structure

### 1. [Overview & Architecture](01-overview-architecture.md)
- Project overview and goals
- Technology stack decisions
- System architecture diagrams
- Component architecture
- Frontend framework options
- Laravel 12 benefits and support timeline

### 2. [Database & Matching Algorithm](02-database-matching-algorithm.md)
- Database schema design
- Provider approval workflow
- Comprehensive matching algorithm
- Menopause-specific matching criteria
- Provider rotation and fair distribution
- Performance optimization strategies

### 3. [Implementation Estimation](03-implementation-estimation.md)
- Detailed man-hour estimates (439 total hours)
- Complete task breakdown with subtasks
- Enhanced matching algorithm (96 hours)
- Analytics & touchpoint tracking (64 hours)
- Blog & SEO system (8 hours using Lara Zeus Sky)
- Audit trails with proper logging (8 hours using Laravel Auditing + log service)
- Approval workflows (6 hours using Laravel Process Approval)
- Laravel Cloud deployment (12 hours - saves 20 hours)
- Package R&D and learning (10 hours)
- Social login with reCAPTCHA (no MFA)
- Risk factors and mitigation
- MVP-focused delivery

### 4. [Infrastructure & Costs](04-infrastructure-costs.md)
- Service stack recommendations
- Cost optimization strategy
- Infrastructure scaling plan
- Laravel Cloud configuration
- Package compatibility notes
- Backup and disaster recovery

### 5. [Security & Analytics](05-security-analytics.md)
- Security implementation details
- Anti-crawling protection
- HIPAA compliance checklist
- Analytics architecture
- Key metrics tracking
- Compliance requirements

### 6. [Code Snippets & Examples](code-snippets.md)
- All code examples from the documentation
- Database queries and schemas
- Configuration files
- Implementation examples
- Quick start commands

## Quick Reference

**Total Estimated Hours**: 439 hours (including 15% buffer)  
**Tech Stack**: Laravel 12 + Filament 3 + Inertia 2 + PostgreSQL + Cloudflare  
**Launch Target**: January 1st, 2026  
**Budget**: $31-40/month* (MVP), scaling to $260/month  
*Pending Laravel Cloud pricing verification, includes HIPAA-compliant logging  
**Team Size**: Single developer  

## Key Features

- **Multi-role system** (Patients, Providers, Reviewers, Admins)
- **Sophisticated matching algorithm** with fair provider rotation
- **Manual verification process** with audit trails
- **Pay-per-match business model**
- **HIPAA-compliant** security measures
- **Real-time analytics** and dashboards
- **Blog system** for SEO traffic generation

## Getting Started

1. Review the [Overview & Architecture](01-overview-architecture.md) document first
2. Understand the [Database & Matching Algorithm](02-database-matching-algorithm.md)
3. Review the [Implementation Estimation](03-implementation-estimation.md) for detailed hour breakdowns
4. Plan infrastructure using [Infrastructure & Costs](04-infrastructure-costs.md)
5. Implement security following [Security & Analytics](05-security-analytics.md)

## Related Documents

- [Initial Requirements](../mfactor-initial-requirements.md) - Client requirements and clarifications
- [CLAUDE.md](../CLAUDE.md) - AI assistant guidance for development

## Support

For questions or clarifications about the technical implementation, please refer to the specific document section or contact the development team.