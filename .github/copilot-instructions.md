# Copilot Instructions

## Repository Overview

This repository is the planning and implementation home for an **Authorized Bug Bounty Reporting Website** — a platform that helps authorized bug bounty hunters and security teams:

- Plan and track testing engagements
- Capture findings in a structured way
- Generate remediation-focused reports
- Show evidence of a flaw without providing harmful exploitation guidance

## Repository State

This project is currently in a **documentation and planning phase**. The repository contains:

- `ReadMe.md` — Full roadmap and specification for the platform, including feature descriptions, data model, technical stack options, and a phased delivery plan.

There is currently **no build tooling, test infrastructure, or source code** in the repository. When implementing the project, follow the stack and architecture described in `ReadMe.md`.

## Recommended Technical Stack

Based on `ReadMe.md`, the preferred approach is:

- **Frontend**: React or Next.js
- **Backend**: Node.js with Express, or Next.js API routes
- **Database**: PostgreSQL (production) or SQLite (local/MVP development)
- **Auth**: Session-based auth or a trusted auth provider
- **ORM**: Prisma
- **Export**: Server-side HTML to PDF

## Project Architecture

The application is organized around five core modules:

1. **Project Dashboard** — Manage authorized targets and scope
2. **Findings Manager** — Structured records for each security finding
3. **Report Generator** — Professional PDF/HTML reports from saved findings
4. **Remediation Tracker** — Track findings through triage → patch → resolved lifecycle
5. **Evidence Library** — Store screenshots, request/response snippets, parameters, and timestamps

### Core Data Entities

- `User`, `Project`, `Asset`, `Finding`, `Evidence`, `Report`, `RemediationUpdate`
- One project → many findings
- One finding → many evidence items
- One report → many findings

## Key Pages

`Home` · `About / Methodology` · `Dashboard` · `Projects` · `Findings` · `Reports` · `Remediation Tracker` · `Settings`

## Quality and Safety Requirements

When writing code for this platform, always:

- Only support **authorized** testing engagements — never facilitate unauthorized access
- Clearly separate in-scope and out-of-scope assets
- Protect uploaded evidence (access controls, secure storage)
- Redact secrets from stored data
- Log access to reports and evidence for audit purposes
- Keep remediation guidance clear, actionable, and defensive in nature
- Do not generate or assist with exploit code; focus on patch recommendations and safe reproduction notes

## Getting Started (Once Code Exists)

When build tooling is added, this section should be updated with:

```
# Install dependencies
npm install

# Run development server
npm run dev

# Run tests
npm test

# Build for production
npm run build
```

Until then, use `ReadMe.md` as the authoritative specification for all implementation decisions.

## Guidance for the Coding Agent

- Trust the specification in `ReadMe.md` as the source of truth for features and data models.
- When creating new source files, follow the phased delivery plan (Phase 1 first: auth, project dashboard, findings CRUD, severity labels, basic export).
- Prefer Next.js full-stack with Prisma + SQLite for the MVP to keep the setup simple.
- Always validate user authorization before allowing access to any project, finding, or report.
- When no existing test infrastructure is present, add tests as part of any feature implementation.
