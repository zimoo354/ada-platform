# Product Requirements Document (PRD)

## Product Name (Working)
Accessibly / ClearAccess / ProofOfAccess  
*(Name TBD)*

---

## 1. Problem Statement

Businesses with legacy websites face ongoing legal risk from ADA / WCAG-related lawsuits. Existing solutions are expensive, opaque, and often provide one-time audits without remediation, monitoring, or clear documentation of ongoing compliance efforts.

There is no practical, affordable tool that:
- Continuously monitors accessibility issues
- Explains issues clearly to engineers and non-engineers
- Provides a verifiable record of good-faith compliance efforts
- Offers human expertise when automated tools fall short

---

## 2. Goals & Success Criteria

### Primary Goals
- Reduce ADA lawsuit risk for customers
- Provide clear, actionable accessibility findings
- Maintain auditability and historical evidence
- Discourage opportunistic lawsuits through visible compliance effort

### Success Metrics
- First paying customer onboarded
- Audit report used in a real legal or settlement context
- Automated scans running without manual intervention
- Customer renews after initial term

---

## 3. Non-Goals

- Guarantee 100% ADA or WCAG compliance
- Provide legal advice
- Act as an insurance provider
- Replace accessibility consultants entirely

---

## 4. Target Users

### Primary Users
- Agency owners
- Technical leads / engineers
- Small and mid-sized business owners

### Secondary Users
- Legal counsel (read-only access)
- Accessibility consultants

---

## 5. Core Use Cases

### UC1 – Register a Website
Users can register a website by providing:
- Website URL
- Tech stack (WordPress, Divi, Shopify, Custom, etc.)
- Primary contact
- Optional staging URL

---

### UC2 – Run Automated Accessibility Scans
The system:
- Runs axe-core, Pa11y, and Lighthouse scans
- Crawls a configurable number of pages
- Stores raw scan results for auditability

---

### UC3 – AI Interpretation Layer
AI processes scan results to:
- Group issues by category (contrast, keyboard navigation, alt text, ARIA, etc.)
- Explain why each issue matters in plain language
- Assign severity levels:
  - Critical (high lawsuit risk)
  - Medium
  - Low / cosmetic
- Propose actionable fixes
  - CMS-specific guidance (e.g. WordPress / Divi)
  - Code snippets where applicable

---

### UC4 – Human Review & Verification
WCAG-certified reviewers:
- Review automated findings
- Mark false positives
- Add contextual notes
- Flag issues automation may miss

---

### UC5 – Compliance Evidence & History
The platform stores:
- Scan timestamps
- Issue findings per scan
- Reviewer notes
- Remediation history

This data serves as evidence of good-faith compliance efforts.

---

### UC6 – Public Compliance Badge
Optional feature:
- Embeddable badge for customer websites
- Badge links to a public summary page showing:
  - Last audit date
  - Monitoring status
  - Clear disclaimer (no certification claims)

---

### UC7 – Ongoing Monitoring
- Scheduled scans (monthly or quarterly)
- Delta reports showing new or resolved issues
- Alerts for newly detected critical issues

---

## 6. Feature Requirements

### Must Have (V1)
- Website registration
- Automated accessibility scans
- Issue dashboard
- AI explanations and fix suggestions
- Manual reviewer notes
- Scan and issue history
- Exportable PDF report
- Simple embeddable badge

### Nice to Have (V1.5)
- Page-level filtering
- Issue assignment and status tracking
- Email or Slack alerts
- Staging vs production comparisons

---

## 7. User Experience (High Level)

### Dashboard
- Overall risk indicator (non-absolute)
- Last scan status
- Count of critical issues
- Historical trend view

### Issue Detail View
- Plain-language description
- Technical details
- Impact explanation
- Suggested fix
- Reviewer notes
- Status (open, fixed, ignored)

---

## 8. Data Model (Conceptual)

### Website
- Unique ID
- URL
- Technology stack
- Owner or account reference

### Scan
- Unique ID
- Associated website
- Scan date and time
- Tool versions used

### Issue
- Unique ID
- Associated scan
- Issue type/category
- Severity level
- Raw tool output
- AI-generated summary
- Suggested remediation

### Reviewer Note
- Unique ID
- Associated issue
- Reviewer identity
- Notes and context

### Badge
- Unique ID
- Associated website
- Last verification date

---

## 9. Technical Approach

### Stack
- Frontend: Next.js, React, Tailwind
- Backend: Next.js API routes / Edge where applicable
- Database: PostgreSQL (Prisma or Drizzle)
- Scanning Tools:
  - axe-core
  - Pa11y
  - Lighthouse (Headless Chrome)
- AI Layer: LLM for interpretation and explanation
- Authentication: Email magic links (initial)
- Infrastructure: Vercel + background jobs (cron / Trigger.dev)

---

## 10. Security & Legal Considerations

- Explicit disclaimers in UI and reports
- Avoid language implying certification or legal protection
- Immutable audit logs
- Reviewer identity and timestamps tracked

---

## 11. Pricing (Initial Hypothesis)

### Pilot Customer
- One-time setup: $2,000–$5,000
- Monthly monitoring: $250–$500
- Human review bundled initially

### Future Pricing
- Tiered by page count
- Agency and white-label plans

---

## 12. Rollout Plan

1. Build MVP for one real client
2. Run in parallel with existing consultant audits
3. Compare outputs and effectiveness
4. Use pilot as a reference case
5. Expand to additional agencies and SMBs

---

## 13. Open Questions

- Crawl depth limits
- Human review SLAs
- White-label branding options
- Legal copy review for reports and badges
