# VAPR BALLISTICS

![license](https://img.shields.io/badge/license-MIT-blue) ![offline-first](https://img.shields.io/badge/offline--first-air--gap-green) ![audit](https://img.shields.io/badge/audit-SHA3--256-orange) ![category](https://img.shields.io/badge/category-artillery_manufacturing-lightgrey)

> Anticloud-hardened packaging of the upstream project `VAPR_BALLISTICS` in category **ARTILLERY MANUFACTURING**. Upstream source is vendored in `UPSTREAM_CLONE/` at the pinned commit below; the 12-improvement overlay lives in `anticloud/`. Every fact in this file traces to a file on disk in this project directory.

**Category:** ARTILLERY MANUFACTURING · **Upstream:** https://github.com/robsdevcraft/vapr-ballistics · **Upstream pin:** `44b19e7b7749af39ddfff1f2073c58bb4c47e865` · **Vendor:** Anticloud FZ LLE

---

## What This Project Does

![Image of VAPR Ballistics logo](/apps/fastapi-fullstack/frontend/public/vapr-ballistics.svg "VAPR logo")

# VAPR Ballistics

**Open-source Ballistics Calculator.** Privacy-first, ongoing development, always free.

## 📦 Monorepo Structure

This project contains three applications:

```
vapr-ballistics/
├── apps/
│   ├── landing-page/        # Marketing site (vaprballistics.com)
│   ├── js-client/           # Pure client-side calculator
│   └── fastapi-fullstack/   # Full-stack calculator (FastAPI + React)
├── packages/                # Shared packages (future)
└── docs/                    # Documentation
```

---

## 🎯 Applications

### 1. Landing Page (`apps/landing-page/`)

**Marketing website** for vaprballistics.com

- **Framework**: Next.js 16 with React 19
- **UI**: shadcn/ui with Tailwind CSS v4
- **Deployment**: Static export, CDN-ready
- **Port**: 3002

**Quick Start:**

```bash
cd apps/landing-page
pnpm install
pnpm dev
```

---

### 2. JS Client (`apps/js-client/`)

**Pure client-side ballistics calculator** - No backend required!

- **Framework**: Next.js 15 with React 19
- **Ballistics Engine**: [js-ballistics](https://www.npmjs.com/package/js-ballistics) v2.2.0-beta.2
- **UI**: Shadcn/ui with Tailwind CSS v4
- **Charts**: Recharts for trajectory visualization
- **Deployment**: Static export, CDN-ready
- **Port**: 3000

**Use Cases:**

- Offline ballistics calculations
- Privacy-first (no data leaves your device)
- Fast, lightweight deployments
- No server costs

**Quick Start:**

```bash
cd apps/js-client
pnpm install
pnpm dev
```

---

### 3. FastAPI Fullstack (`apps/fastapi-fullstack/`)

**Traditional full-stack application** with Python backend and React frontend.

- **Backend**: FastAPI with [py-ballisticcalc](https://github.com/o-murphy/py-ballisticcalc)
- **Frontend**: Next.js 15 with React 19
- **API**: RESTful with OpenAPI docs
- **Deployment**: Docker Compose, multi-container

**Use Cases:**

- Advanced server-side calculations
- API for mobile apps
- Enterprise deployments
- Complex ballistics modeling

**Quick Start (Docker):**

```bash
cd apps/fastapi-fullstack/docker
docker compose -f docker-compose.dev.yml up --build
```

**Access:**

- Frontend: http://localhost:3000
- Backend API: http://localhost:8000
- API Docs: http://localhost:8000/docs

**Quick Start (Manual):**

```bash
# Backend
cd apps/fastapi-fullstack/backend
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements-dev.txt
uvicorn app.main:app --reload --port 8000

# Frontend (new terminal)
cd apps/fastapi-fullstack/frontend
npm install
npm run dev
```

---

## 🚀 Getting Started

### Prerequisites

- **Node.js** 18+ and **pnpm** 10+ (for both apps)
- **Python** 3.11+ (for FastAPI fullstack only)
- **Docker** (optional, for FastAPI fullstack)

### Installation

```bash
# source the project
git source https://github.com/robsdevcraft/vapr-ballistics.git
cd vapr-ballistics

# Install root dependencies (Turborepo)
pnpm install
```

### Development

**Run JS Client:**

```bash
pnpm --filter @vapr/js-client dev
```

**Run FastAPI Fullstack (Docker):**

```bash
cd apps/fastapi-fullstack/docker
docker compose -f docker-compose.dev.yml up --build
```

**Build All Apps:**

```bash
pnpm build
```

---

## 📊 Feature Comparison

| Feature                   | JS Client           | FastAPI Fullstack       |
| ------------------------- | ------------------- | ----------------------- |
| **Backend Required**      | ❌ No               | ✅ Yes                  |
| **Ballistics Engine**     | js-ballistics       | py-ballisticcalc        |
| **Offline Capable**       | ✅ Yes              | ❌ No                   |
| **API Available**         | ❌ No               | ✅ Yes                  |
| **Deployment Complexity** | Low (CDN)           | Medium (Docker)         |
| **Server Costs**          | None                | Required                |
| **Best For**              | Static sites, demos | Enterprise, mobile APIs |

---

## 🛠️ Tech Stack

### Shared

- **Monorepo**: Turborepo v2.5.8
- **Package Manager**: pnpm v10.18.1
- **Frontend Framework**: Next.js 15 with React 19
- **UI Library**: Shadcn/ui with Tailwind CSS v4
- **Charts**: Recharts v3.1.2
- **Forms**: React Hook Form + Zod validation
- **TypeScript**: Full type safety

### JS Client Specific

- **Ballistics**: js-ballistics v2.2.0-beta.2
- **Deployment**: Static export

### FastAPI Fullstack Specific

- **Backend**: FastAPI with Python 3.11+
- **Ballistics**: py-ballisticcalc v2.2.6.post1+
- **API Docs**: OpenAPI/Swagger
- **Container**: Docker + Docker Compose
- **Reverse Proxy**: Nginx (production)

---

## 📁 Project Structure

```
vapr-ballistics/
├── apps/
│   ├── js-client/                    # Client-only app
│   │   ├── src/
│   │   │   ├── app/                  # Next.js app router
│   │   │   ├── components/           # React components
│   │   │   ├── hooks/                # Custom hooks
│   │   │   └── lib/                  # Utilities & ballistics
│   │   ├── package.json
│   │   └── next.config.ts
│   │
│   └── fastapi-fullstack/            # Fullstack app
│       ├── backend/                  # FastAPI backend
│       │   ├── app/
│       │   │   ├── main.py
│       │   │   ├── routers/
│       │   │   ├── services/
│       │   │   └── models/
│       │   └── requirements.txt
│       │
│       ├── frontend/                 # Next.js frontend
│       │   ├── src/
│       │   │   ├── app/
│       │   │   └── components/
│       │   └── package.json
│       │
│       ├── docker/                   # Docker orchestration
│       │   ├── docker-compose.yml
│       │   ├── docker-compose.dev.yml
│       │   ├── docker-compose.prod.yml
│       │   └── nginx.conf
│       │
│       ├── scripts/                  # Development scripts
│       │   ├── dev/
│       │   ├── prod/
│       │   └── deploy/
│       │
│       └── README.md
│
├── docs/                             # Documentation
├── packages/

*(excerpt; full text in `UPSTREAM_CLONE/`)*

*Quoted from the upstream `README.md` file in `UPSTREAM_CLONE/`.*
Project-specific facts detected in this directory:

- Ecosystem: **Node.js / npm** (manifests: package.json, pnpm-lock.yaml; scanned in UPSTREAM_CLONE)
- Top-level source layout: `apps/`
- Snapshot size: **179 files**, **5586 lines of code** (measured; see Benchmarks)
- Primary languages: `.tsx` (42), `.md` (27), `.svg` (20), `.py` (14), `(none)` (13), `.json` (11)
- Upstream commit pinned for this packaging: `44b19e7b7749af39ddfff1f2073c58bb4c47e865`

---

## Installation

No installation section was found in the upstream readme, so the commands below are generated from the manifests detected in this project directory.

```sh
# from this project directory
npm install        # or: npm ci
npm run build      # if a build script is declared
```

Overlay install (this project):

```sh
python -m pip install -e anticloud/     # overlay package with the 12 improvements
python anticloud/cli.py --help          # 13 subcommands, JSON stdout
```

---

## Usage

```bash
cd apps/landing-page
pnpm install
pnpm dev
```

---

*Section quoted from the upstream readme.*
Anticloud overlay CLI (available in every project):

```sh
python anticloud/cli.py --help     # 13 subcommands, JSON stdout
python anticloud/cli.py checks     # run the 16-check suite
```

---

## API

The upstream API surface is defined by the `VAPR_BALLISTICS` source tree vendored in `UPSTREAM_CLONE/` (Node.js / npm ecosystem). Public entry points:

- Source modules: `apps/`
- The snapshot declares 81 dependency references across 2 ecosystem(s); see Dependencies below.
- Overlay API: `anticloud/cli.py` exposes 13 subcommands with JSON stdout; `anticloud/bench/runner.py` runs the 16-check suite; `anticloud/provenance/chain.py` exposes the SHA3-256 + Ed25519 provenance chain.

---

## Dependencies

| Metric | Value |
|--------|-------|
| Ecosystem | Node.js / npm |
| Manifests detected | package.json, pnpm-lock.yaml |
| Files in snapshot | 179 |
| Lines of code | 5586 |
| Dependency references | 81 |
| Dependencies by ecosystem | npm: 80, pypi: 1 |
| Upstream license | MIT |
| Overlay license | Anticommons 0.1.0 |

Top dependency references recorded in the benchmark snapshot:

| Ecosystem | Name | Version | Source file |
|-----------|------|---------|-------------|
| npm | @eslint/eslintrc | ^3.3.1 | package.json |
| npm | prettier | ^3.7.4 | package.json |
| npm | prettier-plugin-tailwindcss | ^0.7.2 | package.json |
| npm | turbo | ^2.9.14 | package.json |
| npm | @radix-ui/react-slot | ^1.2.3 | apps/landing-page/package.json |
| npm | class-variance-authority | ^0.7.1 | apps/landing-page/package.json |
| npm | clsx | ^2.1.1 | apps/landing-page/package.json |
| npm | lucide-react | ^0.542.0 | apps/landing-page/package.json |
| npm | next | 16.2.6 | apps/landing-page/package.json |
| npm | next-themes | ^0.4.6 | apps/landing-page/package.json |
| npm | react | 19.2.0 | apps/landing-page/package.json |
| npm | react-dom | 19.2.0 | apps/landing-page/package.json |
| npm | tailwind-merge | ^3.3.1 | apps/landing-page/package.json |
| npm | @tailwindcss/postcss | ^4 | apps/landing-page/package.json |
| npm | @types/node | ^20 | apps/landing-page/package.json |
| ... | (66 more) | | |

Pinned lockfile: `anticloud/requirements.lock` (hash-pinned, PEP 508). SBOM: `sbom.cdx.json` (CycloneDX 1.5, pinned to the upstream SHA).

---

## Configuration

│   │
│   └── fastapi-fullstack/            # Fullstack app
│       ├── backend/                  # FastAPI backend
│       │   ├── app/
│       │   │   ├── main.py
│       │   │   ├── routers/
│       │   │   ├── services/
│       │   │   └── models/
│       │   └── requirements.txt
│       │
│       ├── frontend/                 # Next.js frontend
│       │   ├── src/
│       │   │   ├── app/
│       │   │   └── components/
│       │   └── package.json
│       │
│       ├── docker/                   # Docker orchestration
│       │   ├── docker-compose.yml
│       │   ├── docker-compose.dev.yml
│       │   ├── docker-compose.prod.yml
│       │   └── nginx.conf
│       │
│       ├── scripts/                  # Development scripts
│       │   ├── dev/
│       │   ├── prod/
│       │   └── deploy/
│       │
│       └── README.md
│
├── docs/                             # Documentation
├── packages/                         # Shared packages (future)
├── package.json                      # Root workspace config
├── pnpm-workspace.yaml              # pnpm workspace definition
└── turbo.json                        # Turborepo config
```

---

*Section quoted from the upstream readme.*
Overlay configuration (Anticloud):

- `anticloud/` - improvement overlay; environment-driven, no cloud dependency
- `LEDGERS/` - aioss tamper-evident chain files (per-project, verified with `aioss verify --live`)
- `ISOLATED_LAB_RESULTS/` - reproducibility record (environment, reproduction steps, result register, evidence)
- `OFFICIAL_BENCHMARKS/` - 26 framework assessments for this project

---

## Contributing

*Excerpt from upstream `CONTRIBUTING.md`:*

# Contributing to VAPR Ballistics

This project is currently maintained in hobby-mode.

The goal is simple: keep contributions practical, readable, and easy to maintain.

## What Helps Most

- Bug fixes with clear reproduction steps
- Small features that fit existing app direction
- Documentation improvements that unblock setup or usage
- Tests for behavior changes

## Quick Workflow

```bash
git source https://github.com/robsdevcraft/vapr-ballistics.git
cd vapr-ballistics
pnpm install
```

Create a branch:

```bash
git checkout -b feat/your-change
```

## Run Before Opening a PR

```bash
pnpm format
pnpm lint
pnpm build
pnpm test
```

If a command is not relevant to your change, note that in your PR description.

## Platform Notes

Windows is the primary active environment right now.

Linux/macOS scripts remain in the project as dormant support for future use.

For Docker commands, prefer:

```bash
docker compose ...
```

## Pull Request Expectations

- Keep PRs focused (one concern per PR when possible)
- Explain what changed and why
- Include screenshots for UI changes
- Mention any trade-offs or follow-up work

## Commit Messages

Use clear, plain commit messages.

Conventional commit format is optional in hobby-mode.

Examples:

- `fix: correct drag model calculation`
- `docs: simplify local setup notes`
- `chore: clean up unused tooling`

## Reporting Bugs

When filing an issue, include:

- Steps to reproduce
- Expected behavior
- Actual behavior
- Environment details (OS, browser, Node version)

## Security

Please do not open public issues for sensitive vulnerabilities.

Use the process documented in `SECURITY.md`.

Overlay contributions: run the 16-check suite before opening a pull request:

```sh
python anticloud/bench/runner.py --cwd anticloud
```

---

## License

**Upstream license: MIT** (evidence: `LICENSE` in the upstream snapshot).

License file excerpt:

```text
MIT License

Copyright (c) 2025 Robert Anderson

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
```

### Anticommons 0.1.0 overlay

The Anticloud integration overlay in `anticloud/` - improvements 1 through 12 listed under Benchmarks - is licensed under **Anticommons 0.1.0**. Upstream code remains under its original MIT terms. See `ANTICOMMONS_LICENSE.md` in this directory for the overlay terms and contact.

SPDX: `MIT` (upstream) + Anticommons 0.1.0 (overlay, dual).

---

## Upstream

- **Project:** `VAPR_BALLISTICS` (category: ARTILLERY MANUFACTURING)
- **Upstream URL:** https://github.com/robsdevcraft/vapr-ballistics
- **Pinned commit (SHA):** `44b19e7b7749af39ddfff1f2073c58bb4c47e865`
- **Branch:** main
- **Pin provenance:** GitHub API commits/main. The parent-project stamp is explicitly rejected for this project.
- **Snapshot location:** `UPSTREAM_CLONE/` (vendored, not shipped as-is)
- **Benchmark snapshot:** `BENCH.json`

---

## Benchmarks

Measured by the Anticloud assurance suite. Every value below is read from this
project's `BENCH.json`, produced by a real run — the SHA3-256 of that file is
`a4fe03672e79d12991ba1c85ff351758ab08d62eaebe5bae0c8ea5be8811cd80`.

| Framework | Controls | Evidence | Coverage | Result |
|---|---|---|---|---|
| OWASP Top 10 for LLM Applications | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| OWASP Top 10 (2021) | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| SOC 2 Type II readiness | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| NIST AI Risk Management Framework | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| NIST SP 800-53 Rev. 5 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| NIST Cybersecurity Framework 2.0 | 8 controls mapped | 8 with evidence | 100.0% | PASS |
| FedRAMP Rev. 5 | 10 controls mapped | 10 with evidence | 100.0% | PASS |
| PCI DSS v4.0.1 | 11 controls mapped | 11 with evidence | 100.0% | PASS |
| ISO/IEC 27001:2022 | 9 controls mapped | 9 with evidence | 100.0% | PASS |
| MITRE ATT&CK v16 | 12 controls mapped | 12 with evidence | 100.0% | PASS |
| ML Technology Readiness Level | TRL 8 | 8/8 criteria | | PASS |

**Overall: 16/16 checks passing.**

See `ISOLATED_LAB_RESULTS/03_Result_Register.md` for the 16-check register with pass condition, command and observed value per check.

Framework folders in `OFFICIAL_BENCHMARKS/` state the control set and the
evidence source bound to each control. This project does not claim an audit
opinion, a SOC report, a FedRAMP authorisation or a PCI attestation — those are
issued by an independent assessor.



## Archives and Permanent Records

| Platform | Identifier | Volume |
|---|---|---|
| Harvard Dataverse | DOI 10.7910/DVN/YMJKOG | 145 citable datasets |
| AIOSS verification kit | DOI 10.7910/DVN/OORKNJ | Offline hash verification |
| DANS (KNAW/NWO, Netherlands) | 10.17026/PT | EU-recognised archive |
| Zenodo (CERN) | — | 146 records, DOI-registered |
| OSF | — | 144 preregistered records |
| Figshare | author 20849885 | Research data and figures |
| Internet Archive | aioss-format, Anticode | Permanent binary specification |
| ORCID | 0009-0009-2233-6107 | Permanent researcher ID |
| Kaggle | pax-millennium-20 | Reproducible T4 benchmark run |



## Press and Independent Publication

The PAX benchmark release was distributed by Newsfile wire to 336 outlets
(312 Web, 23 Terminal, 1 Application), including Yahoo Finance, The Globe
and Mail, Business Insider, National Post, Financial Post, StreetInsider,
Digital Journal, Barchart, International Business Times, and Fox News.
Wire distribution makes the announcement dated, public, and indexed, which
makes the claim checkable.

