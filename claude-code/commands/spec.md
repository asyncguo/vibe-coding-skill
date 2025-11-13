---
description: Requirements specification mode - defines WHAT to build from product and user perspective
argument-hint: <feature or requirement to specify>
---

# Requirements Specification Mode

You are now in **requirements specification mode**. Your role is to define WHAT needs to be built, not HOW to build it. Think like a Product Manager, not an Engineer.

**Specification Target**: $ARGUMENTS

## Usage Guidelines

Choose the appropriate level of detail based on feature complexity:

**For Simple Features** (< 2 day development):
- Use sections 1, 2.2 (Must Have only), 7, 9

**For Standard Features** (2-10 days):
- Use sections 1, 2, 3, 7, 8, 9

**For Complex Features** (> 10 days or cross-team):
- Use all sections

## Core Principles

- **DEFINE REQUIREMENTS, NOT SOLUTIONS**: Describe behaviors and outcomes, not implementations
- **USER-CENTRIC**: Focus on user needs, use cases, and acceptance criteria
- **BALANCED ABSTRACTION**:
  - Focus on outcomes and behaviors, not implementation patterns
  - DO specify technical constraints when they're business requirements (performance SLAs, compliance, compatibility)
  - DON'T prescribe specific technologies, libraries, or architectures unless mandated
- **TESTABLE**: Every requirement should be verifiable
- **TRACEABLE**: Every requirement should have a unique ID and source attribution
- **CLEAR CONTRACT**: This document is the "contract" between stakeholders and engineers

## Specification Framework

### 1. **Overview & Context**
- **Brief description**: One-paragraph summary of the feature/requirement
- **Business objective**: Why are we building this? What problem does it solve?
- **Target users**: Who will use this feature?
- **Success metrics**: How do we measure success? (KPIs, usage metrics)
- **Requirement source**: User feedback, data analysis, competitive analysis, regulatory requirement, etc.

### 2. **Functional Requirements**

#### 2.1 User Stories
Format: "As a [user type], I want to [action], so that [benefit]"

**Example**:
- As a registered user, I want to reset my password via email, so that I can regain access if I forget my credentials

#### 2.2 Detailed Requirements (MoSCoW Priority)

Use unique IDs for traceability (format: REQ-###)

**Must Have** (Critical):
- [ ] [REQ-001] Requirement: Description with clear, testable acceptance criteria
  - _Source: [User feedback / Business requirement / Compliance]_

**Should Have** (Important):
- [ ] [REQ-002] Requirement: Description
  - _Source: [...]_

**Could Have** (Nice to have):
- [ ] [REQ-003] Requirement: Description
  - _Source: [...]_

**Won't Have** (Out of scope):
- Explicitly list what this feature will NOT do in this iteration
- State if these are deferred to future releases or permanently excluded

### 3. **User Flows & Scenarios**

#### Happy Path (Primary Flow)
Step-by-step description of the ideal user journey:
1. User action
2. System response
3. ...

#### Alternative Flows
- What happens when exceptions occur?
- What happens when validation fails?
- What happens when service is unavailable?
- What happens when user cancels midway?

#### Edge Cases
- Boundary conditions (empty data, max limits, etc.)
- Unusual but valid scenarios
- Error conditions
- Race conditions or concurrent operations

### 4. **Interface Requirements**

#### 4.1 API/Interface Contracts
Define inputs and outputs (technology-agnostic):

**Operation**: [Operation Name]
- **Input**: What data is provided (fields, types, constraints)
- **Output**: What is returned (format, structure)
- **Errors**: Expected error cases and codes
- **Side effects**: What changes in the system

#### 4.2 Data Requirements
What data needs to be captured and stored?
- **[REQ-ID]** Field name (data type, constraints, validation rules, required/optional)
- **Data retention**: How long must this data be kept?
- **Data privacy**: Is this PII/sensitive data? What protections are needed?

#### 4.3 UI/UX Requirements (if applicable)
- What must be displayed to users?
- What actions must be available?
- What feedback must be provided?
- Response time expectations for user actions
- Accessibility requirements (WCAG level, screen reader support)
- Responsive design requirements (mobile, tablet, desktop)

### 5. **Business Rules & Constraints**

List all business logic and rules with unique IDs:
- **[BUS-001]** Validation rules (format, range, dependencies)
- **[BUS-002]** Business constraints (time windows, quantity limits, eligibility)
- **[BUS-003]** Workflow rules (approval chains, state transitions)
- **[BUS-004]** Data integrity rules (uniqueness, referential integrity)
- **[BUS-005]** Calculation formulas or algorithms (describe outcomes, not implementations)

### 6. **Non-Functional Requirements**

#### Performance
- **Response time**: P50 < Xms, P95 < Yms, P99 < Zms (specify for each operation type)
- **Throughput**: Support N concurrent users / M requests per second
- **Scalability**: Handle Xx current load with <Y% latency increase
- **Resource limits**: Max memory, CPU, storage per operation

#### Security & Privacy
- **Authentication**: What level of authentication is required?
- **Authorization**: Who can perform what actions? (role-based access control)
- **Data protection**: Encryption requirements (at rest, in transit)
- **Compliance**: GDPR, HIPAA, SOC2, PCI-DSS, etc.
- **Data residency**: Geographic restrictions on data storage
- **Privacy**: User rights (access, deletion, portability)
- **Audit**: What actions must be logged for compliance?

#### Reliability
- **Uptime**: Target availability (e.g., 99.9% = ~8.7 hours downtime/year)
- **Data durability**: Acceptable data loss tolerance (RPO - Recovery Point Objective)
- **Recovery time**: Maximum acceptable downtime (RTO - Recovery Time Objective)
- **Backup requirements**: Frequency, retention period, restore testing
- **Fault tolerance**: Graceful degradation expectations

#### Usability
- **Accessibility**: WCAG 2.1 Level AA compliance (or specific standard)
- **Internationalization**:
  - Languages to support
  - Time zone handling requirements
  - Currency and number formatting
  - Date/time format localization
  - Text directionality (LTR/RTL)
  - Cultural adaptations (colors, icons, imagery)
- **Device compatibility**: Browser versions, mobile OS versions, screen sizes
- **Learning curve**: Expected time for user proficiency

#### Observability
- **Logging**: What events and data must be logged?
- **Metrics**: What must be measured? (latency, throughput, error rates, business metrics)
- **Alerts**: What conditions require immediate notification?
- **Debugging**: What information is needed to troubleshoot issues?

### 7. **Acceptance Criteria**

Clear, testable conditions for accepting the feature as complete.

Format:
```
[REQ-ID] Scenario: [Brief description]
Given: [Initial context/state]
When: [Action taken]
Then: [Expected outcomes]
```

**Example**:
```
[REQ-001] Scenario: Successful password reset
Given: User has a registered email address
When: User requests password reset and clicks the email link
Then:
  - User is redirected to password reset page
  - New password is accepted if it meets complexity requirements
  - User can log in with new password
  - Old password no longer works
  - Password reset link expires after use
```

### 8. **Dependencies & Assumptions**

#### Dependencies
- What other systems/features must exist first?
- What external services are required? (APIs, third-party tools)
- What data must be available?
- What infrastructure is required?
- What team/resource dependencies exist?

#### Assumptions
- Explicit assumptions being made
- What we're assuming about users, systems, or environment
- Volume/scale assumptions
- Technology/platform assumptions

### 9. **Out of Scope**

Explicitly state what is NOT included:
- Features that might be expected but aren't part of this spec
- Future enhancements (with potential timeline if known)
- Related but separate concerns
- Limitations that are acceptable for this release

### 10. **Requirement Conflicts & Trade-offs**

Document and resolve conflicting requirements:

**[CONFLICT-001]**
- **Conflict**: [Description of contradiction]
- **Stakeholders**: Who is affected / Who has conflicting needs
- **Options considered**: [Option A, Option B, Option C]
- **Resolution**: Decision made
- **Rationale**: Why this decision was made
- **Trade-off**: What was sacrificed / What's the downside

### 11. **Open Questions**

Track unresolved questions that need stakeholder input:
- [ ] **[Q-001]** Question requiring decision - _Owner: [Name], Due: [Date]_
- [ ] **[Q-002]** Question requiring research - _Owner: [Name], Due: [Date]_

### 12. **Version History & Change Log**

| Version | Date | Changes | Author | Reason |
|---------|------|---------|--------|--------|
| 1.0 | YYYY-MM-DD | Initial specification | [Name] | - |
| 1.1 | YYYY-MM-DD | Updated REQ-005 based on legal review | [Name] | Compliance requirement |

## Output Guidelines

✅ **DO**:
- Use clear, unambiguous language
- Write testable requirements
- Focus on user value and behaviors
- Use examples and scenarios
- Define explicit acceptance criteria
- Assign unique IDs to requirements
- Specify quantitative metrics for non-functional requirements
- Document the source and rationale for requirements
- Explicitly state what's out of scope

🚫 **DO NOT**:
- Prescribe specific technical solutions or architectures
- Include implementation details (class names, database schemas, etc.)
- Use vague terms without definition ("fast", "scalable", "user-friendly")
- Mix requirements with design decisions
- Leave conflicts unresolved
- Skip quantification on performance/reliability requirements

## Quality Checklist

Before finalizing the spec, verify:
- [ ] Every requirement has a unique ID
- [ ] Every "Must Have" requirement has acceptance criteria
- [ ] Non-functional requirements are quantified with specific numbers
- [ ] All conflicts have documented resolutions
- [ ] "Out of Scope" section is explicit
- [ ] Assumptions are stated clearly
- [ ] Success metrics are measurable
- [ ] Acceptance criteria use Given-When-Then format
- [ ] Open questions have assigned owners

---

Now, create a comprehensive requirements specification for the target provided above. Remember: Define WHAT needs to be built, not HOW to build it.
