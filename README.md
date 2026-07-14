# AERA Digital Platform Ecosystem (Web & Mobile) — 2026 Overhaul

## 1. Overview
This repository houses the core codebase for AERA Skincare's unified digital platform ecosystem, encompassing both the web storefront and cross-platform mobile application. In line with AERA's core ethos of prioritizing utility and data over cosmetic presentation, this platform is engineered to be exceptionally lightweight, performant, and secure[cite: 1, 3]. It features a streamlined, zero-friction e-commerce funnel integrated directly with localized regional distribution APIs, alongside a dedicated, uncompressed media streaming engine for dermatological and scientific research education[cite: 1].

## 2. Core Architecture
The platform is built on an decoupled, headless architecture designed to maximize uptime, localized rendering speeds, and global scalability.

*   **Frontend (Web & App):** Built using a unified JavaScript framework utilizing pre-rendered static generation (SSG) for fast page loading. Total asset overhead is strictly capped at <1.5MB by excluding ornamental tracking scripts, third-party marketing pixels, and heavy animation libraries.
*   **Backend & APIs:** A cloud-native microservices mesh written in a high-concurrency language. It handles multi-currency transactions, localized regional taxes, and live warehouse inventory streaming via secure RESTful endpoints[cite: 1].
*   **Media & Video Infrastructure:** Content Delivery Network (CDN) utilizing geo-distributed edge servers to stream uncompressed, high-definition educational skin biology videos directly to users in Europe and APAC with zero buffer latency.

## 3. Repository Directory Structure
```text
├── .github/                 # GitHub actions, workflows, and CI/CD pipelines
├── apps/
│   ├── web/                 # Web platform source code
│   └── mobile/              # Cross-platform mobile app source code
├── packages/
│   ├── api-client/          # Shared API integration layers (Supply Chain & Finance sync)
│   ├── ui-core/             # Minimalist, high-contrast design system components
│   └── video-player/        # Custom raw HTML5 video player component (no-filter mandate)
├── docs/
│   ├── ARCHITECTURE.md      # Detailed system topology and CDN caching schemas
│   ├── API_DOCS.md          # Endpoint specifications for inventory and checkout systems
│   └── SECURITY.md          # GDPR compliance and data encryption configurations
├── CHANGELOG.md             # Version release history tracking
└── README.md                # This root directory documentation

```

## 4. Setup & Local Installation

To spin up the development environment locally, follow these instructions.

### Prerequisites

* Node.js (v20 LTS or higher required)
* Package Manager: `pnpm` (v8.x or higher)
* Docker (Optional, for local database container virtualization)

### Steps

1. **Clone the Repository:**
```bash
git clone [https://github.com/aera-skincare/digital-platform-2026.git](https://github.com/aera-skincare/digital-platform-2026.git)
cd digital-platform-2026

```


2. **Configure Environment Variables:**
Copy the example environment file and populate it with your local development keys:
```bash
cp .env.example .env.local

```


*Note: Ensure local endpoints for the regional Supply Chain and Finance mock APIs are verified.*
3. **Install Dependencies:**
```bash
pnpm install

```


4. **Launch the Local Development Server:**
```bash
pnpm dev

```


*The local web app will boot at `http://localhost:3000` and the mobile packager will initialize on port `8081`.*

## 5. Testing & Quality Assurance

All additions to the main branch must clear mandatory automated testing criteria enforced via the CI/CD pipeline.

* **Unit & Component Testing:** Run the core test suite locally before pushing code:

```bash
pnpm test

```

* **Accessibility & Performance Auditing:** Every UI component must hit a 100/100 performance and Web Content Accessibility Guidelines (WCAG) 2.1 Level AA ranking in automated headless engine logs.

## 6. Contribution & Branching Policy

The DEP department operates on standard 2-week agile sprint iterations managed via GitHub Projects.

* **Branch Naming Convention:** `feature/DEP-[Issue_Number]-short-description` or `bugfix/DEP-[Issue_Number]-short-description`.
* **Pull Requests (PR):** All PRs require a linked Confluence Product Requirements Document (PRD) reference, passing CI/CD checks, and approval from at least two software engineers before being eligible for staging merges.
* **Deployment Notification:** Successful code updates automatically trigger webhooks piping confirmation data directly into the AERA Mattermost `#dep-alerts` operational channel.

```

```
