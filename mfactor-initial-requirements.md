# The (M) Factor Menopause Provider Directory - Initial Requirements

## Executive Summary

The (M) Factor is a specialized healthcare provider directory connecting women experiencing menopause with appropriate care providers. The platform facilitates discovery and connection without handling appointments or insurance claims, operating on a pay-per-match model for providers.

**Launch Target**: January 1st, 2026 (Soft Launch)  
**Geographic Scope**: United States (nationwide at launch)  
**Future Expansion**: UK, Australia, Canada by 2027  
**Success Metrics**: 7,000 providers, 100,000 searches/year  

## Core Requirements

### 1. User Types & Access

#### 1.1 Patients (Primary Users)
- **Registration**: Email/password with 2FA(Optional, but will keep provision for this)
- **Profile Features**:
  - Save favorite providers
  - Track search history
  - Manage contact preferences
  - Demographic information for matching
- **Access**: Free platform access

#### 1.2 Providers
- **Types**:
  - **Level 1**: Medical doctors (MDs, DOs) - "M Factor Vetted Clinicians"
  - **Level 2**: Allied health professionals (therapists, nurse practitioners)
  - **Level 3**: Non-medical practitioners (yoga instructors, nutritionists, coaches)
- **Registration**: Detailed application with credential upload
- **Access**: Free to list, pay-per-match model
- **Verification**: Manual review process with 2FA

#### 1.3 Administrators
- **Super Admin**: Full system control
- **Content Manager**: Pages, events, educational content
- **Provider Reviewer**: Application vetting, approvals, renewals
- **Admin Support**: Profile QA, support, refunds

### 2. Provider Management

#### 2.1 Provider Profiles
**Required Information**:
- Basic credentials and license status
- Specialties and treatment approaches
- Cultural backgrounds and languages spoken
- Insurance accepted (informational only)
- Telehealth availability
- Personal statement on menopause care philosophy
- Photos and optional video introductions
- Contact information (verified)
- Treatment protocols followed
- Menopause-specific certifications

#### 2.2 Verification Process
**Required Credentials**:
- Active medical license (verified every 2 years)
- Menopause-specific training:
  - CME courses
  - Menopause Training programs
  - Conference attendance (The Menopause Society)
  - Certifications (Menopause Society, Hey Perry)
- **Timeline**: 3-6 months typical for certification
- **External team** for license verification and certificate review

#### 2.3 Approval Workflow
**Status Types**:
- Pending
- Under Review
- Approved
- Rejected
- Needs Changes

**Features**:
- Automated email notifications for status changes
- Appeals process via resubmission
- Audit trail for all approval actions
- Manual intervention for disqualifications
- No automatic removal of inactive providers

### 3. Patient Search & Matching

#### 3.1 Search Criteria
- **Location**: State, city, zip code, proximity
- **Provider Type**: MD, naturopath, therapist, etc.
- **Treatment Approach**: Medical, holistic, integrative
- **Demographics**: Age, gender, ethnicity matching
- **Language**: Spoken languages
- **Specialties**: Specific symptoms/conditions
- **Insurance**: Accepted plans (informational)
- **Availability**: Telehealth, new patients
- **Certifications**: M Factor Vetted vs other menopause certifications

#### 3.2 Matching Algorithm
**Ranking Factors** (all confirmed important):
- Geographic proximity
- Exact specialty match
- Cultural/language alignment
- Insurance acceptance
- M Factor Vetted status (shown separately)
- Treatment protocol preference
- Provider boosting options

**Key Requirement**: Prevent same doctors from always appearing first

### 4. Business Model

#### 4.1 Revenue Structure
- **Patients**: Free access
- **Providers**: 
  - Free to list
  - Pay when matched with patients
  - No commission on appointments
- **Year 1**: Sponsor-funded
- **Year 2 Target**: $250K-$500K revenue

#### 4.2 Future Revenue Streams
- Advertising
- Partnerships
- Premium content
- Concierge service (Phase 2)

### 5. Platform Features

#### 5.1 Communication
- **Direct Contact**: Patients contact providers directly
- **No Appointment Booking**: Contact information only
- **Verified Numbers**: Ensure provider contact info is valid
- **No Insurance Integration**: Platform doesn't handle claims

#### 5.2 Feedback System
**Collection Points**:
- Post-inquiry (automated email)
- After initial visit (scheduled email)
- 3-6 month follow-up (optional)

**Feedback Types**:
- Overall satisfaction
- Wait times
- Treatment effectiveness
- Bedside manner

**Visibility**: Private initially, option for public later

**Management**: 
- Route negative feedback to admin dashboard
- Status flags for review
- Provider response/appeals internally

#### 5.3 Educational Content
**At Launch**:
- Blog-style articles on menopause topics
- Interactive quizzes and symptom checklists
- Lifestyle guides
- Link to M Factor Film coaching program

**Phase 2**:
- Provider-submitted content (paid feature)
- External tool integrations
- CMS-editable content

### 6. Technical Requirements

#### 6.1 Platform Specifications
- **Type**: Progressive Web App (PWA)
- **Responsive Design**: Mobile and desktop
- **Security**: 
  - 2FA for all users
  - Anti-crawling protection
  - No AI scraping allowed
  - HTTPS/SSL
  - Rate limiting

#### 6.2 Data Management
- **Import/Export**: Bulk provider data capabilities
- **Integration Ready**: 
  - Mailchimp (future)
  - Zapier (future)
  - Analytics dashboards
- **No PHI Collection**: Follow security best practices

#### 6.3 Compliance
- **HIPAA**: Not required (no PHI)
- **State Regulations**: Platform takes no liability
- **Data Security**: Access control, regional awareness
- **Audit Trails**: All provider actions logged

### 7. Content Sections

#### 7.1 Main Sections
- **Provider Directory**: Core search and profiles
- **Resources**: Educational content, guides
- **Events**: Landing page linking to TheMFactorfilm.com
- **Blog**: SEO-focused content
- **About**: Platform information

#### 7.2 Provider Categories
**Medical Providers**:
- OB/GYN
- Primary Care
- Endocrinologist
- Psychiatrist

**Non-Medical Providers** (with disclaimers):
- Certified coaches
- Yoga instructors
- Nutritionists
- Fitness trainers

### 8. Key Differentiators

1. **M Factor Seal of Approval**: Verified menopause-specific training
2. **Cultural Matching**: Emphasis on cultural competence
3. **Treatment Philosophy**: Clear about medical vs holistic approaches
4. **No Insurance Hassles**: Direct patient-provider connection
5. **Quality Over Quantity**: Manual verification process

### 9. Success Metrics

**Year 1 Goals**:
- 7,000 verified providers
- 100,000 annual searches
- Nationwide coverage (all 50 states)
- Diverse provider representation
- High-quality SEO traffic through blog

**Long-term Vision**:
- International expansion (2027)
- Sustainable revenue model
- Industry-leading provider directory

### 10. Phase 1 Deliverables

1. **Provider System**:
   - Registration and profile creation
   - Manual verification workflow
   - Approval process with audit trails
   - Basic profile management

2. **Patient Features**:
   - Search with all specified filters
   - Save favorites
   - Direct contact with providers
   - Basic account management

3. **Admin Panel**:
   - Provider approval workflow
   - Content management
   - Basic analytics
   - Audit trail viewing

4. **Content**:
   - Blog functionality
   - Educational resources
   - Events landing page

### 11. Out of Scope for Phase 1

- Appointment booking system
- Insurance claim processing
- Automated provider removal
- Multilingual support
- Concierge service (framework only)
- Provider-contributed content
- Public feedback display
- Mobile native apps

### 12. Critical Requirements

1. **Security**: 2FA mandatory for all users
2. **Verification**: Manual review of all providers
3. **Disclaimer**: Clear non-medical disclaimers for Level 3 providers
4. **Audit**: Complete trail of all approval actions
5. **Quality**: Minimum profile requirements enforced
6. **Performance**: Fast search results with intelligent ranking
7. **Scalability**: Architecture supporting 100K+ searches/year

### 13. Provider Journey

1. **Application**: Detailed form with credential upload
2. **Verification**: External team reviews licenses/certifications
3. **Approval**: Internal team makes final decision
4. **Onboarding**: Complete profile setup
5. **Maintenance**: Biennial reverification
6. **Matching**: Pay when connected with patients

### 14. Patient Journey

1. **Discovery**: Find platform via search/referral
2. **Search**: Use filters to find ideal provider
3. **Review**: Read profiles and credentials
4. **Save**: Add favorites for comparison
5. **Contact**: Reach out directly to provider
6. **Feedback**: Post-visit experience survey

### 15. Competitive Positioning

**Primary Competitor**: menopause.org
**Differentiation**:
- More comprehensive matching
- Cultural competence focus
- Broader provider types
- Modern user experience
- Pay-per-match model