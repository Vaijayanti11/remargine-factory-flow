# ReMargin — Complete Mock-First Product Plan

## Goal
Build the complete responsive ReMargin product in this React/TanStack application: a polished public website plus every requested authenticated workspace page. The visual direction will adapt Zephyra’s premium editorial composition for the public site and Spark Admin’s dense, practical chart structure for factory dashboards, using ReMargin’s navy, teal, green, white, and warm financial-impact accents.

The delivered version will be fully interactive with realistic, clearly labeled demonstration data. Authentication, OCR, persistence, scheduled work, and PDF generation will be represented behind typed service interfaces so a separate FastAPI/PostgreSQL/Redis/Celery backend can replace the mock adapter later without redesigning pages.

## Product surfaces

### Public experience
- Build `/` as a long-form, high-impact ReMargin website with sticky navigation, full-width manufacturing imagery, animated illustrative metrics, the three market gaps, factory-data workflow, feature grid, novelty comparison, three intelligence layers, calls to action, and professional footer.
- Build separate `/contact` and `/feedback` pages with validated forms.
- Build `/login` and `/register`; registration will be multi-step with all requested fields, inline validation, Indian mobile validation, password rules, and strength feedback.
- Add page-specific titles, descriptions, Open Graph metadata, and accessible navigation.

### Mock authentication and onboarding
- Create a browser-side mock session and typed repository scoped to one user and company, clearly isolated behind an API client contract.
- Implement registration → login → first-login setup → dashboard flow.
- Build `/setup` with editable company details and dynamic machine forms; completion marks onboarding complete.
- Guard all private pages in the client experience and redirect signed-out visitors to `/login`.
- Add sign-out, session-aware header controls, and a profile menu.
- Clearly document in code that the mock session is demonstration-only and must be replaced by FastAPI-issued secure cookies/JWTs before production.

### Authenticated application shell
- Create a shared top navigation and responsive sidebar system with desktop, tablet, and mobile behavior.
- Add dropdown navigation for Dashboard and Reports, active states, notifications, profile access, and logout.
- Default `/dashboard` to `/dashboard/carbon` and `/reports` to `/reports/esg`.
- Reuse standard KPI, chart, table, upload, machine, alert, report, result, recommendation, modal, confirmation, toast, date-range, and empty-state components.

### Dashboards
- Build Carbon Tracker, Sustainability Analytics, and Energy Monitoring pages using Chart.js.
- Include all requested KPI cards, date controls, trend/comparison charts, illustrative-data badges, last-updated labels, and polished no-data states.
- Keep the product relationship visible throughout: Energy → Waste → ₹ Loss → Cause → Action → Savings → Carbon Impact → Reporting.

### Data workflow
- Build `/upload` with meter, scrap/production, and electricity bill sections; drag/drop, previews, removal, mock OCR state, manual verification, calculations, and validation.
- Build `/result` with energy and scrap waste, assumptions, cost-impact breakdown, evidence-based possible causes, recommendations, and an interactive fix tracker.
- Build `/history` with search, filters, pagination, result detail access, and report actions.

### Machines and company profile
- Build `/tracker` with company-scoped machine status, maintenance alerts, service updates, maintenance records, notes, and completion flows.
- Build `/profile` with editable company/factory details and machine add/edit/remove management.
- Model each machine as its own entity linked to the active company.

### Reports
- Build a shared report shell and complete ESG, CBAM, Green Loan, and Solar Investment pages.
- Include previews, completeness/status, assumptions, generate/download states, and polished empty/error states.
- Implement the requested prototype CBAM rule (`machine count > 30`) as a replaceable strategy, with careful language that legal applicability depends on products and supply chains.
- Mock PDF downloads with a service boundary designed for a later ReportLab endpoint.

## Technical approach
- Use TanStack file routes and shared layouts; do not introduce another router.
- Use Tailwind v4 semantic tokens in `src/styles.css`; no hardcoded visual colors in page components.
- Add Chart.js with the React adapter and create reusable responsive chart wrappers.
- Use Zod for every user-entered form and calculated input boundary.
- Define typed domain entities matching the requested relational model: users, companies, machines, energy records, scrap records, bills, uploads, results, maintenance records, reports, history, and corrective actions.
- Build a `services` layer with mock implementations and REST-ready request/response DTOs. Every company-owned query will require an authenticated company context and filter by company ID.
- Keep OCR, report generation, alerts, and scheduling as asynchronous mock services with realistic loading, verification, success, and failure states.
- Use generated industrial imagery for the landing page rather than stock placeholders.

## Verification
- Check every route for unique metadata and working navigation.
- Exercise registration, login, first-time setup, machine creation, upload processing, result/fix tracking, history, reports, profile updates, and logout.
- Verify desktop and mobile layouts with browser screenshots, including charts, navigation, forms, and upload states.
- Confirm clear illustrative-data labeling and no unsupported statistics or universal CBAM claims.
- Check accessibility basics, form errors, empty states, runtime console errors, and the latest build status.

## Deferred integration boundary
The separate FastAPI/PostgreSQL/Redis/Celery/APScheduler/Google Vision/ReportLab service is not hosted inside this TanStack workspace. This delivery will include the frontend contracts and mock adapters for it, but not deploy that external Python service or provide real secure persistence, OCR, scheduled jobs, or PDF generation.
