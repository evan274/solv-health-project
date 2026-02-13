# Product Requirements Document (PRD)
## AI-Powered Smart Queue Management System

**Product:** Solv Health Platform
**Feature:** Smart Queue Management with Predictive Wait Times
**Version:** 1.0
**Author:** Product Team
**Date:** February 2026
**Status:** Draft

---

## 1. Executive Summary

### Problem Statement
Urgent care facilities face unpredictable patient flow, leading to operational inefficiencies, poor patient experiences, and lost revenue. Current challenges include:
- Patients frustrated by long, unpredictable wait times
- Front desk staff overwhelmed managing walk-ins vs. scheduled appointments
- Providers unable to optimize staffing based on predicted demand
- 15-20% no-show rates creating schedule gaps that can't be filled efficiently
- Lost revenue when facilities are understaffed during surges or overstaffed during lulls

### Proposed Solution
An AI-powered Smart Queue Management System that:
- Dynamically predicts wait times based on real-time and historical data
- Intelligently sequences walk-ins and scheduled appointments
- Provides patients with accurate wait time estimates before and during visits
- Enables providers to adjust capacity in real-time
- Automatically fills gaps from no-shows or cancellations
- Optimizes patient throughput while maintaining care quality

### Success Metrics
- **Patient Satisfaction:** Increase NPS by 15 points within 6 months
- **Wait Time Accuracy:** 90%+ accuracy in predicted vs. actual wait times
- **Patient Throughput:** Increase daily patient volume by 10-15%
- **No-Show Impact:** Fill 60%+ of no-show slots within 30 minutes
- **Operational Efficiency:** Reduce front desk scheduling time by 40%
- **Revenue Impact:** Increase revenue per location by 12-18%

---

## 2. Background & Context

### Market Opportunity
- 210M+ Americans live within 5 miles of Solv network providers
- Urgent care industry growing 8% annually
- Patients increasingly expect on-demand, transparent healthcare experiences
- Providers seek competitive differentiation beyond clinical quality

### Current State
Solv currently offers:
- Online appointment booking
- Basic queue visibility for patients
- Check-in notifications
- Static wait time estimates

**Limitations:**
- Wait times are manually updated or based on simple averages
- No intelligent prioritization of walk-ins vs. appointments
- Limited ability to dynamically adjust capacity
- Providers lack predictive insights for staffing decisions

### Competitive Landscape
- **Zocdoc:** Offers booking but limited queue management
- **GoHealth:** Proprietary system for owned facilities only
- **Traditional EHRs:** Basic scheduling, no smart queue features
- **Solv Advantage:** Two-sided marketplace with data across hundreds of facilities

---

## 3. Goals & Objectives

### Business Goals
1. **Increase Patient Volume:** Enable providers to see 10-15% more patients without adding staff
2. **Improve Retention:** Reduce patient churn due to wait time dissatisfaction
3. **Provider Differentiation:** Make Solv's queue management a key competitive advantage
4. **Expand Market:** Attract larger health systems requiring enterprise queue solutions

### User Goals

**Patients (Sarah):**
- Know accurate wait times before leaving home
- Receive updates if wait time changes
- Feel confident their appointment time will be honored
- Minimize time in waiting room

**Providers (Dr. Rodriguez):**
- Maximize patient throughput and revenue
- Reduce staff time managing queues manually
- Make data-driven staffing decisions
- Maintain high patient satisfaction

**Front Desk Staff (Jennifer):**
- Automatic queue prioritization (less decision-making stress)
- Fewer complaints about wait times
- Proactive alerts to fill schedule gaps
- Less time on phone managing expectations

---

## 4. User Stories & Use Cases

### Epic 1: Predictive Wait Time Engine

**User Story 1.1:** As a patient, I want to see accurate wait times before booking so I can plan my day.
- **Acceptance Criteria:**
  - Wait time prediction displayed before booking confirmation
  - Prediction accuracy within ±10 minutes for 90% of appointments
  - Real-time updates as conditions change
  - Historical accuracy tracking and continuous improvement

**User Story 1.2:** As a patient in queue, I want to receive updates if my wait time changes so I'm not surprised.
- **Acceptance Criteria:**
  - Push notification if wait time increases by >15 minutes
  - SMS option for patients without app
  - Updated wait time visible in app dashboard
  - Option to reschedule if wait becomes too long

### Epic 2: Intelligent Queue Sequencing

**User Story 2.1:** As a front desk coordinator, I want the system to automatically prioritize patients so I don't have to make difficult decisions.
- **Acceptance Criteria:**
  - AI algorithm considers: appointment time, check-in time, visit type, historical wait time
  - Override capability for urgent cases
  - Visual queue dashboard showing next 10 patients
  - Provider-specific queues for multi-provider facilities

**User Story 2.2:** As a provider, I want to balance walk-ins and appointments to maximize volume without disappointing scheduled patients.
- **Acceptance Criteria:**
  - Configurable walk-in acceptance rules (e.g., "accept walk-ins if appointments are >30 min apart")
  - Automatic walk-in slot generation during gaps
  - "Hold" slots that convert to walk-in availability if not filled 2 hours before
  - Dashboard showing real-time capacity utilization

### Epic 3: Dynamic Capacity Optimization

**User Story 3.1:** As a provider, I want to see predicted patient volume for upcoming hours/days so I can adjust staffing.
- **Acceptance Criteria:**
  - Hourly predictions for next 48 hours
  - Weekly patterns with confidence intervals
  - Alerts when predicted volume exceeds optimal capacity
  - Historical accuracy tracking
  - Integration with staff scheduling tools

**User Story 3.2:** As a patient, I want to be offered alternative appointment times if my preferred time has a long wait.
- **Acceptance Criteria:**
  - Suggest times with shorter predicted waits
  - Option to book at different nearby Solv location
  - Smart suggestions based on historical patient acceptance rates
  - One-click rebooking

### Epic 4: No-Show Recovery

**User Story 4.1:** As a provider, I want to automatically fill no-show slots to minimize lost revenue.
- **Acceptance Criteria:**
  - Automatic detection of no-shows (patient not checked in 10 min after appointment)
  - Immediate push notifications to nearby patients in Solv network
  - "Last-minute availability" badge in patient app
  - Prioritize patients who previously wanted but couldn't get appointments
  - Track fill rate and time-to-fill metrics

---

## 5. Functional Requirements

### 5.1 AI/ML Wait Time Prediction Model

**Inputs:**
- Current queue length and composition (visit types)
- Historical visit duration data by visit type and provider
- Time of day, day of week, seasonality
- Provider capacity (number of providers, rooms available)
- Real-time check-in rate
- External factors (weather, local events, flu season indicators)

**Outputs:**
- Predicted wait time for new patient booking now
- Predicted wait time for specific future time slots
- Confidence interval for predictions
- Predicted queue clearing time

**Requirements:**
- Model retrains weekly using past 90 days of data
- Facility-specific models (not one-size-fits-all)
- A/B testing framework for model improvements
- Fallback to statistical averages if ML model confidence is low

### 5.2 Queue Sequencing Algorithm

**Prioritization Factors:**
- Scheduled appointment time (high weight)
- Check-in timestamp for walk-ins
- Visit type urgency/complexity
- Historical visit duration
- Patient wait time tolerance (learned from past behavior)
- Provider preferences (configurable rules)

**Business Rules:**
- Scheduled patients seen within 15 minutes of appointment time (90% target)
- Walk-ins see estimated wait time upon check-in
- Ability to "bump" less urgent walk-ins if appointments are at risk
- VIP/membership tier considerations (if applicable)

### 5.3 Patient Communication System

**Pre-Appointment:**
- Predicted wait time shown during booking flow
- Confirmation message includes wait time estimate
- Reminder 2 hours before with updated wait time
- Offer to reschedule if wait time increased significantly

**During Visit:**
- Check-in confirmation with current position in queue
- Push notification when "next in line" (5-10 min warning)
- Update if provider is running behind

**Post-Visit:**
- Feedback survey including wait time experience
- Feed data back into model training

### 5.4 Provider Dashboard

**Real-Time View:**
- Current queue visualization (ordered list with visit types)
- Current wait time for new walk-ins
- Capacity utilization percentage
- Alerts (over capacity, long wait times, no-shows)

**Predictive View:**
- Next 4 hours: predicted arrivals vs. capacity
- Next 7 days: daily volume predictions
- Recommended actions (open walk-in slots, add provider capacity)

**Historical Analytics:**
- Wait time trends
- Throughput metrics (patients/hour)
- No-show rates and recovery
- Prediction accuracy over time

### 5.5 Integration Requirements

**EHR Integration:**
- Bi-directional sync of appointment data
- Visit start/end timestamps for duration tracking
- Visit type/chief complaint for prediction model
- Patient check-in status

**Supported EHRs (Priority Order):**
1. Epic
2. athenaOne
3. eClinicalWorks
4. NextGen
5. DrChrono

**Solv Platform Integration:**
- Booking engine shows predicted wait times
- Patient app displays queue position and wait time
- SMS notifications for non-app users
- Provider mobile app for queue management on-the-go

---

## 6. Non-Functional Requirements

### 6.1 Performance
- Wait time predictions calculated in <500ms
- Dashboard updates in real-time (<5 second latency)
- System handles 10,000 concurrent facilities
- 99.9% uptime SLA

### 6.2 Scalability
- Support for health systems with 100+ locations
- Handle 1M+ daily appointments across platform
- Model training completes within 4-hour overnight window

### 6.3 Security & Compliance
- HIPAA compliant data handling
- PHI encryption at rest and in transit
- Audit logs for all queue modifications
- Role-based access control for provider dashboards

### 6.4 Usability
- Dashboard usable on mobile devices (responsive design)
- Minimal training required (intuitive UI)
- Accessible (WCAG 2.1 AA compliance)
- Available in English and Spanish

---

## 7. Design & User Experience

### 7.1 Patient App Experience

**Booking Flow:**
1. Patient searches for "urgent care near me"
2. List shows facilities with availability and wait times
3. Patient selects facility and time
4. Confirmation screen shows: appointment time, predicted wait time, address
5. Option to add to calendar

**In-Queue Experience:**
1. Patient checks in via app upon arrival (or auto-check-in via geofence)
2. Home screen shows: "You're #3 in line. Estimated wait: 18 minutes"
3. Progress bar updates as queue moves
4. Notification when "You're next! Please head to the front desk"

**Design Principles:**
- Large, readable text for wait times (primary information)
- Calm color palette (reduce anxiety)
- Clear visual progress indicator
- Minimal taps required (3 or fewer to complete actions)

### 7.2 Provider Dashboard

**Layout:**
- Left panel: Current queue (scrollable list)
- Center: Real-time metrics cards (current wait time, patients/hour, capacity %)
- Right panel: Predictive insights (next 4 hours graph)

**Queue List Item:**
- Patient name (last name, first initial for privacy)
- Visit type icon
- Checked-in timestamp / appointment time
- Predicted duration
- Drag-to-reorder capability

**Color Coding:**
- Green: On track (<10 min behind schedule)
- Yellow: Moderate delay (10-20 min behind)
- Red: Significant delay (>20 min behind)

---

## 8. Technical Architecture

### 8.1 System Components

**Frontend:**
- React Native (mobile apps)
- React (web dashboard)
- Real-time updates via WebSockets

**Backend:**
- Node.js microservices architecture
- GraphQL API layer
- PostgreSQL (transactional data)
- Redis (real-time queue state)

**ML/AI Pipeline:**
- Python (TensorFlow/PyTorch for models)
- Airflow (orchestration)
- S3 (training data storage)
- SageMaker (model hosting)

**Infrastructure:**
- AWS (primary cloud)
- CloudFront (CDN)
- DataDog (monitoring)

### 8.2 Data Model

**Queue Entry:**
```
{
  id: uuid
  facility_id: uuid
  patient_id: uuid
  appointment_time: datetime (null for walk-ins)
  check_in_time: datetime
  visit_type: enum
  predicted_duration: int (minutes)
  predicted_start_time: datetime
  actual_start_time: datetime (null until started)
  actual_end_time: datetime (null until completed)
  status: enum (waiting, in_progress, completed, no_show)
  priority_score: float (calculated by algorithm)
}
```

**Prediction Log:**
```
{
  id: uuid
  facility_id: uuid
  prediction_time: datetime
  predicted_wait_time: int
  actual_wait_time: int (backfilled after visit)
  prediction_accuracy: float
  model_version: string
  confidence_score: float
}
```

---

## 9. Success Metrics & KPIs

### 9.1 Product Metrics

**Prediction Accuracy:**
- Target: 90% of predictions within ±10 minutes of actual
- Measure: MAPE (Mean Absolute Percentage Error)
- Track by: facility, time of day, visit type

**Patient Throughput:**
- Target: 10-15% increase in patients seen per day
- Baseline: Average from prior 90 days
- Track by: facility, month-over-month

**Wait Time Reduction:**
- Target: 15-20% reduction in average actual wait time
- Measure: Median wait time (check-in to visit start)
- Track by: facility, patient type (walk-in vs. scheduled)

### 9.2 Business Metrics

**Patient Satisfaction:**
- Target: NPS increase of 15 points
- Survey question: "How satisfied were you with your wait time?"
- Track: weekly rolling average

**No-Show Recovery:**
- Target: Fill 60% of no-show slots within 30 minutes
- Measure: Time from no-show detection to slot filled
- Revenue impact: Calculate recovered revenue

**Provider Adoption:**
- Target: 80% of facilities actively using queue dashboard within 3 months
- Measure: Weekly active users, time spent in dashboard
- Qualitative: Provider feedback surveys

**Revenue Impact:**
- Target: 12-18% revenue increase per location
- Attribution: Compare facilities using Smart Queue vs. control group
- Track: Revenue per facility per day

### 9.3 Operational Metrics

**System Performance:**
- API response time: <500ms (p95)
- Dashboard load time: <2 seconds
- Uptime: 99.9%

**Staff Efficiency:**
- Target: 40% reduction in front desk time on scheduling
- Measure: Time-tracking before/after implementation
- Track: Staff satisfaction scores

---

## 10. Launch Plan & Rollout

### Phase 1: Closed Beta (Months 1-2)
**Scope:**
- 5 select facilities (diverse sizes, geographies)
- Full feature set with enhanced logging
- Weekly feedback sessions with providers and staff

**Goals:**
- Validate prediction model accuracy in real-world conditions
- Identify UX friction points
- Establish baseline metrics

**Success Criteria:**
- 85%+ prediction accuracy achieved
- No critical bugs
- Positive feedback from beta providers (4/5 stars average)

### Phase 2: Limited Release (Months 3-4)
**Scope:**
- Expand to 50 facilities
- Facilities with existing high Solv engagement
- Geographic diversity across US

**Goals:**
- Scale testing (handle 50x concurrent load)
- Refine model with diverse facility data
- Provider training and support process validation

**Success Criteria:**
- Maintain 85%+ prediction accuracy at scale
- 70%+ provider adoption (weekly dashboard usage)
- System performance within SLA targets

### Phase 3: General Availability (Month 5+)
**Scope:**
- Rollout to all Solv network facilities
- Marketing campaign to providers and patients
- Integration into standard onboarding

**Goals:**
- Platform-wide availability
- Drive patient awareness and adoption
- Achieve target business metrics

**Success Criteria:**
- 80% facility adoption within 6 months
- Target KPIs achieved (NPS, throughput, revenue)
- Competitive differentiation established

---

## 11. Risks & Mitigations

### Risk 1: Model Prediction Inaccuracy
**Impact:** High - Erodes patient trust, poor user experience
**Likelihood:** Medium
**Mitigation:**
- Conservative estimates (slightly overestimate wait times)
- Confidence thresholds (fall back to averages if low confidence)
- Continuous monitoring and weekly model retraining
- Facility-specific models vs. one-size-fits-all

### Risk 2: Provider Resistance to Change
**Impact:** High - Low adoption undermines value proposition
**Likelihood:** Medium
**Mitigation:**
- Early involvement of providers in beta testing
- Clear ROI communication (revenue increase, efficiency gains)
- Minimal workflow changes (automate, don't add work)
- Dedicated customer success team for onboarding
- Testimonials and case studies from beta providers

### Risk 3: Technical Complexity/Integration Issues
**Impact:** Medium - Delays launch, increases costs
**Likelihood:** Medium
**Mitigation:**
- Prioritize top 5 EHR integrations
- Robust API abstraction layer
- Early technical validation with EHR partners
- Fallback manual data entry option
- Comprehensive testing in beta phase

### Risk 4: Patient Privacy Concerns
**Impact:** High - Regulatory violations, trust loss
**Likelihood:** Low
**Mitigation:**
- HIPAA compliance review by legal team
- Minimal PHI exposure (last name + first initial only in queues)
- Regular security audits
- Staff training on privacy best practices
- Encrypted data transmission and storage

### Risk 5: Over-Reliance on AI Causing Issues
**Impact:** Medium - System fails without human oversight
**Likelihood:** Low
**Mitigation:**
- Always allow manual override by front desk staff
- Clear "AI-predicted" labeling so users understand
- Human-in-the-loop for edge cases
- Escalation protocols when predictions are uncertain

---

## 12. Dependencies & Requirements

### Internal Dependencies
- **Engineering:** ML team, backend team, mobile team, integration team
- **Design:** UX research, UI design, user testing
- **Product:** Spec refinement, prioritization, stakeholder management
- **Data Science:** Model development, validation, monitoring
- **Customer Success:** Beta partner management, training materials

### External Dependencies
- **EHR Vendors:** API access, documentation, technical support (Epic, athena, etc.)
- **Beta Partners:** Commitment to testing, timely feedback
- **Legal/Compliance:** HIPAA review, terms of service updates

### Resource Requirements
- **Engineering:** 2 ML engineers, 3 backend engineers, 2 mobile engineers, 1 QA engineer
- **Design:** 1 product designer, 1 UX researcher
- **Product:** 1 product manager (owner), 1 technical PM
- **Data Science:** 1 data scientist (full-time), 1 analytics engineer
- **Customer Success:** 2 CSMs for beta phase

**Timeline:** 9 months from kickoff to general availability

---

## 13. Open Questions

1. **Pricing Model:** Should Smart Queue be included in base platform or premium tier?
2. **Multi-Provider Facilities:** How to handle facilities with multiple providers with different specialties/speed?
3. **Telemedicine Integration:** Should virtual visits be included in same queue or separate?
4. **Patient Incentives:** Should we offer incentives (discounts, priority) for accepting off-peak times?
5. **White-Label Option:** Do health systems want to brand the patient-facing experience?

---

## 14. Appendix

### A. Competitive Analysis

| Feature | Solv Smart Queue | Zocdoc | Traditional EHR |
|---------|------------------|--------|-----------------|
| AI Prediction | ✅ | ❌ | ❌ |
| Real-time Updates | ✅ | Limited | ❌ |
| Walk-in Management | ✅ | ❌ | Basic |
| No-Show Recovery | ✅ | ❌ | ❌ |
| Multi-facility Support | ✅ | ✅ | Limited |
| Predictive Staffing | ✅ | ❌ | ❌ |

### B. Research References

- Patient Wait Time Tolerance Study (Healthcare Management Review, 2024)
- Urgent Care Industry Benchmarks (Urgent Care Association, 2025)
- AI in Healthcare Operations (McKinsey, 2025)
- Internal Solv user research (2025-2026)

### C. Glossary

- **MAPE:** Mean Absolute Percentage Error - measure of prediction accuracy
- **NPS:** Net Promoter Score - patient satisfaction metric
- **Throughput:** Number of patients seen per unit of time
- **Queue:** Ordered list of patients waiting to be seen
- **No-show:** Patient with scheduled appointment who doesn't check in

---

## Approvals

| Role | Name | Approval Date |
|------|------|---------------|
| Product Lead | [TBD] | |
| Engineering Lead | [TBD] | |
| Design Lead | [TBD] | |
| Data Science Lead | [TBD] | |
| VP Product | [TBD] | |
