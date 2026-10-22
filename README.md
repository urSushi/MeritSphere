# MeritSphere — Scholarship Discovery & Application Support System

[![Software Engineering](https://img.shields.io/badge/Architecture-Clean%20Layered-blue.svg)]()
[![Stack](https://img.shields.io/badge/Stack-React%20%2B%20TypeScript%20%2B%20Express%20%2B%20Prisma-indigo.svg)]()
[![Tests](https://img.shields.io/badge/Tests-Vitest%20Passed-emerald.svg)]()
[![Database](https://img.shields.io/badge/Database-SQLite%20(Prisma%20ORM)-amber.svg)]()

> **MeritSphere** is an end-to-end scholarship discovery, personalized matching, eligibility checking, application preparation, document management, and deadline tracking system built strictly according to academic Software Engineering principles.

---

## 1. Project Aim & Vision

Traditional scholarship hunting forces students to juggle scattered websites, disparate eligibility criteria, isolated document folders, and forgotten deadlines. 

**MeritSphere unites the complete student application lifecycle under one roof:**
1. **Universal Discovery**: Open public exploration without forced registration, multi-facet filtering (degree, country, university, field, CGPA), and side-by-side comparison matrix.
2. **Personalized Compatibility Engine**: Multi-factor scoring ($0$–$100\%$) correlating student CGPA, field of study, destination preferences, and language proficiency, paired with plain-English rationales.
3. **Automated Eligibility Checker**: Real-time evaluation against program prerequisites, clearly categorizing results into `Eligible`, `Partially Eligible`, or `Not Eligible`.
4. **Application Readiness System & Checklist**: An intelligent meter verifying profile completion, required document presence in the vault, and deadline safety margins before application submission.
5. **Secure Academic Document Vault**: Upload credentials (transcripts, CVs, SOPs, recommendation letters, test scorecards) once, and reuse them across unlimited applications.
6. **Smart Urgency & Deadline Timeline**: Live countdowns and color-coded alerts ($\le 7$ days Critical, $\le 14$ days Warning) with calendar views.
7. **Multi-Role Governance**: Dedicated, secured portals for **Students**, **Scholarship Providers** (posting opportunities & managing review pipelines), and **Administrators** (analytics, accreditation verification, and security audit logs).

---

## 2. Professional Technology Stack

| Layer | Technology | Rationale & Software Engineering Benefits |
|---|---|---|
| **Frontend Framework** | **React 18 + TypeScript + Vite** | Blazing-fast development, strict compile-time type safety, modular component architecture, and responsive state management. |
| **Styling & UI** | **Tailwind CSS + Lucide Icons** | Design system with consistent tokens, glassmorphic panels, accessible controls, and responsive layouts. |
| **Routing** | **React Router DOM (v6)** | Multi-page client-side routing with role-based route guards (`STUDENT`, `PROVIDER`, `ADMIN`). |
| **Backend & REST API** | **Node.js + Express.js + TypeScript** | Layered architecture (*Controllers, Services, Middlewares, Routes, Data Layer*) conforming directly to the high-level system architecture. |
| **Database & ORM** | **Prisma ORM with SQLite** | Zero-configuration local database requiring no standalone server installation, with strict relational schema matching the ER diagram, automatic migrations, foreign key cascades, and full PostgreSQL compatibility. |
| **Security & Auth** | **JWT (JSON Web Tokens) + BcryptJS** | Stateless authentication with Role-Based Access Control (RBAC), password hashing, and login-attempt tracking. |
| **File Management** | **Document Vault Engine** | Secure local storage with MIME verification, document categorization, and credential expiration tracking. |
| **Testing** | **Vitest** | Automated unit tests verifying matching algorithms, eligibility rules, and readiness calculations. |

---

## 3. High-Level System Architecture

```
┌────────────────────────────────────────────────────────────────────────┐
│                              CLIENT LAYER                              │
│   • Visitor Public Catalog & Compare     • Student Personal Dashboard  │
│   • Provider Opportunity Manager         • Administrator Command Center│
└───────────────────────────────────┬────────────────────────────────────┘
                                    │ HTTPS (REST API / JSON)
┌───────────────────────────────────▼────────────────────────────────────┐
│                           APPLICATION LAYER                            │
│   • Auth & RBAC (JWT/Bcrypt)             • Matching Service (0-100%)   │
│   • Eligibility Engine                   • Application Readiness Meter │
│   • Deadline & Urgency Parser            • Milestone Badges Engine     │
└───────────────────────────────────┬────────────────────────────────────┘
                                    │ Prisma ORM (Type-Safe Queries)
┌───────────────────────────────────▼────────────────────────────────────┐
│                              DATA LAYER                                │
│   • Users & Profiles (Student/Provider)  • Scholarships & Universities │
│   • 9-Stage Applications                 • Reusable Document Vault     │
│   • Notifications & Audit Logs           • Badges & Success Stories    │
└────────────────────────────────────────────────────────────────────────┘
```

---

## 4. Pre-Seeded Evaluation Accounts (1-Click Demo)

The system includes pre-seeded demo accounts with comprehensive realistic data. You can log in using the **"Demo Switch"** button on the navigation bar, the quick buttons on `/login`, or by entering the credentials:

| Role | Email | Password | Persona & Pre-Seeded Data |
|---|---|---|---|
| **Student** | `student@meritsphere.edu` | `password123` | **Alex Rivera** (CGPA: 3.82, CS, IELTS: 7.5, 4 vault documents, 3 active applications in Interview/Review, 4 badges unlocked) |
| **Scholarship Provider** | `provider@daad.de` | `password123` | **German Academic Exchange Service (DAAD)** (Accredited provider, 3 published scholarships, candidate review pipeline) |
| **Administrator** | `admin@meritsphere.edu` | `password123` | **Platform Director** (Full telemetry analytics, provider accreditation verifier, live security audit trail) |

---

## 5. Quick Start Guide

### Prerequisites
- Node.js (v18+ or v20+ or v24+)
- npm (v9+)

### Installation & Launch

Run the following commands in the `MeritSphere` directory:

```bash
# 1. Install root, server, and client dependencies
npm run install:all

# 2. Setup SQLite database with Prisma migrations & seed demo dataset
npm run setup:db

# 3. Launch both backend API and frontend client concurrently
npm run dev
```

The system will start:
- **Frontend Web App**: `http://localhost:5173`
- **Backend REST API**: `http://localhost:5000`
- **API Health Check**: `http://localhost:5000/api/health`

---

## 6. Running Automated Tests

To execute the unit and algorithmic test suites:

```bash
cd server
npm test
```

Test coverage includes:
- `matching.test.ts`: Personalized score computation, degree/GPA weighting, and rationale explanation generation.
- `eligibility.test.ts`: Prerequisite rules verification, cut-offs, and `Eligible`/`Partially Eligible`/`Not Eligible` classification.
- `readiness.test.ts`: Readiness score percentage, missing document detection, and checklist generation.

---

## 7. Key Features & Workflows

### 1. Public Explorer & Side-by-Side Comparison
- Explore scholarships without logging in.
- Filter by country, university, degree level, field, funding type, and GPA.
- Select up to 4 scholarships to generate a side-by-side comparison matrix.

### 2. Personalized Student Portal
- **Dashboard**: Track applications across 9 stages (`Saved`, `Preparing`, `Documents Ready`, `Applied`, `Under Review`, `Shortlisted`, `Interview`, `Selected`, `Rejected`).
- **Readiness Meter**: Real-time progress ring checking profile completeness, eligibility, and required document uploads.
- **7-Step Preparation Roadmap**: Interactive step-by-step guidance from profile completion to application submission.
- **Document Vault**: Upload transcripts, CVs, SOPs, and language scorecards with expiration alerts and document reuse.

### 3. Scholarship Provider Portal
- Post and update scholarship programs with custom eligibility criteria and deadlines.
- Review incoming candidate dossiers with attached documents and applicant CGPA.
- Make status decisions (`Under Review`, `Shortlisted`, `Interview`, `Selected`, `Rejected`) with interview feedback.

### 4. Administrator Command Center
- System analytics: Application conversion funnels, top countries, and popular fields.
- Provider accreditation verification toggles.
- Real-time security and administrative audit trail logging all system events with timestamps and IP addresses.
=======
# MeritSphere — Scholarship Discovery & Application Platform

**Discover Opportunities. Match Your Potential. Achieve Your Dreams.**

MeritSphere is a web-based scholarship discovery and application management platform designed to help students find suitable scholarship opportunities, evaluate their eligibility, organize application documents, and track their application progress in one centralized place.

The project aims to simplify the scholarship application journey by combining scholarship search, personalized recommendations, eligibility checking, deadline tracking, and application preparation tools.

## Table of Contents

- [Overview](#overview)
- [Problem Statement](#problem-statement)
- [Objectives](#objectives)
- [Key Features](#key-features)
- [User Roles](#user-roles)
- [Technology Stack](#technology-stack)
- [System Architecture](#system-architecture)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Project Scope](#project-scope)
- [Future Enhancements](#future-enhancements)
- [Contributors](#contributors)
- [Project Status](#project-status)
- [License](#license)

## Overview

Finding a suitable scholarship often requires students to visit multiple websites, compare eligibility criteria, prepare documents, monitor deadlines, and manage applications separately.

MeritSphere aims to bring these activities together in a single, student-friendly platform.

The system is designed to help students identify relevant opportunities based on their academic background, CGPA/GPA, preferred countries, universities, degree levels, fields of study, skills, and funding preferences.

It also provides scholarship providers with tools to publish opportunities and manage applicants, while administrators can oversee users, verify scholarships, and maintain platform information.

## Problem Statement

Scholarship information is often scattered across different platforms, making it difficult for students to identify relevant opportunities and manage the application process efficiently.

Common challenges include:

- Finding scholarships that match academic qualifications.
- Understanding eligibility criteria and funding options.
- Keeping track of application deadlines.
- Preparing and organizing required documents.
- Monitoring application progress and status updates.
- Identifying missing requirements before applying.

**MeritSphere addresses these challenges** by providing a centralized system for scholarship discovery, personalized matching, application preparation, and progress tracking.

## Objectives

- Create a centralized scholarship discovery platform.
- Provide personalized scholarship recommendations.
- Help students evaluate eligibility requirements.
- Organize scholarship applications and their progress.
- Simplify document management and application readiness checks.
- Provide deadline reminders and preparation roadmaps.
- Enable providers to manage scholarships and applicants.
- Support administrators with verification, moderation, and analytics.

## Key Features

### 1. Scholarship Discovery

- Browse scholarships without registering.
- Search by keyword.
- Filter by country, university, degree level, and field of study.
- Filter by scholarship type, funding type, and eligibility.
- View scholarship details, requirements, and deadlines.
- Compare multiple scholarship opportunities.

### 2. Student Profile & Personalization

- Student registration and login.
- Academic profile and education history.
- CGPA/GPA, skills, achievements, and language-test scores.
- Preferred countries, universities, degrees, and fields of study.
- Profile completion tracking.

### 3. Personalized Scholarship Matching

- Recommendations based on student profiles.
- Scholarship match percentages.
- Matching based on academic qualifications and preferences.
- Explanations of why a scholarship is recommended.

### 4. Eligibility Checker

- Compare student profiles with scholarship requirements.
- Identify matched and missing requirements.
- Display eligibility percentages.
- Categorize results as Eligible, Partially Eligible, or Not Eligible.

### 5. Application Tracking

- Save and bookmark scholarships.
- Organize scholarship lists.
- Track application progress.
- Maintain application history.

Supported application stages are designed to include:

`Saved → Preparing → Documents Ready → Applied → Under Review → Shortlisted → Interview → Selected / Rejected`

### 6. Document Vault & Application Readiness

- Organize transcripts, certificates, CVs, statements of purpose, and recommendation letters.
- Reuse documents across applications.
- Track document completion and expiry.
- Identify missing documents.
- Generate personalized application preparation checklists.

### 7. Deadline Management & Notifications

- Scholarship deadline countdowns.
- Upcoming deadline alerts.
- Calendar-based deadline tracking.
- Notifications for application updates and missing documents.
- Interview and scholarship-result notifications.

### 8. Preparation Roadmap & Achievements

- Step-by-step scholarship preparation guidance.
- Personalized application checklists.
- Progress tracking.
- Achievement badges for completing important milestones.

### 9. Provider & Administrator Management

- Publish and update scholarships.
- Define eligibility criteria and deadlines.
- Manage applicants and application statuses.
- Verify scholarships and providers.
- Manage users and platform content.
- Access administrative reports and analytics.

## User Roles

| Role | Main Responsibilities |
|---|---|
| Visitor | Browse, search, filter, and compare scholarships. |
| Student | Manage profiles, receive recommendations, check eligibility, organize documents, and track applications. |
| Scholarship Provider | Publish scholarships, define requirements, and manage applicants. |
| Administrator | Manage users, verify scholarships, oversee platform information, and access analytics. |

## Technology Stack

The following is the **proposed technology stack for the complete platform**, as outlined in the project proposal. The exact stack used by the current frontend prototype may differ.

| Component | Proposed Technology |
|---|---|
| Frontend | React.js, HTML5, CSS3, JavaScript |
| Backend | Node.js, Express.js |
| Database | PostgreSQL |
| API | RESTful API |
| Authentication | JWT-based or secure session-based authentication |
| File Storage | Protected server or object storage |
| Version Control | Git and GitHub |
| Testing | Jest, React Testing Library, API testing |
| Deployment | Cloud-hosted web application |

## System Architecture

MeritSphere is designed around four main layers:

1. **Client Layer:** Interfaces for visitors, students, scholarship providers, and administrators.
2. **Application Layer:** Authentication, scholarship search, matching, eligibility checking, application management, notifications, and analytics.
3. **Data Layer:** Structured storage for users, profiles, scholarships, applications, documents, and related information.
4. **External Services Layer:** Email notifications, official scholarship sources, and protected file storage.

The modular architecture is intended to make the platform easier to maintain and extend.

## Project Structure

The repository may contain the frontend prototype and its supporting assets. A typical static frontend structure looks like this:

```text
MeritSphere/
├── index.html
├── css/
│   └── style.css
├── js/
│   └── script.js
├── assets/
│   ├── images/
│   └── icons/
├── README.md
└── package.json
```

*Note: This is an illustrative structure. Actual filenames and folders may differ from the repository.*

## Getting Started

### Prerequisites

- A modern web browser.
- Git.
- Node.js and npm, if the project uses npm-based scripts.

### Installation

**1. Clone the repository**

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
```

**2. Navigate to the project directory**

```bash
cd MeritSphere
```

**3. Install dependencies, if applicable**

```bash
npm install
```

**4. Run the project**

For a static HTML/CSS/JavaScript prototype, open `index.html` in your browser or use a local development server.

If the repository defines an npm start script, use the command specified in `package.json`, for example:

```bash
npm run dev
```

The available commands depend on the project's actual configuration.

## Project Scope

The initial project scope focuses on the core scholarship discovery and application management experience.

The following features are planned for the core platform:

- Scholarship discovery and comparison.
- Student profiles and personalized matching.
- Eligibility checking.
- Application and deadline tracking.
- Document management and application readiness.
- Provider and administrator dashboards.
- Verification and security features.

Optional features, such as the interactive 3D opportunity globe, community discussions, and mentorship system, are reserved for potential future development.

## Future Enhancements

Potential future improvements include:

- Interactive global scholarship opportunity visualization.
- Global scholarship statistics and destination insights.
- Scholarship discussion communities.
- Mentorship from scholarship recipients.
- Expanded analytics and reporting.
- Additional integrations with external scholarship information sources.

## Contributors

MeritSphere is an academic software project developed collaboratively.

- **Karimun Nahar Karima**
- **Didar Ibn Firoz**
- **Syeda Tasmia Zaman**

Contributions, feedback, and suggestions are welcome as the project evolves.

## Project Status

**Status: In Development**

MeritSphere is being developed iteratively, beginning with interface design and core system planning, followed by implementation of the platform's major modules.

Features described in this README represent the project vision and proposed scope; availability depends on the current implementation.

## License

No license has been specified yet. Unless a license is added to the repository, the project should not be assumed to be open-source or freely reusable.

---

**MeritSphere — Making Scholarship Discovery and Application Preparation Simpler.**
>>>>>>> 684666064ec12cb21596d52a03841763079acecf
