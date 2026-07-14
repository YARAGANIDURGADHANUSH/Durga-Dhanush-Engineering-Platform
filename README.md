# Durga Dhanush Engineering Platform

**Live:** [https://durga-dhanush-engineering-platform.vercel.app/](https://durga-dhanush-engineering-platform.vercel.app/)

A single-file, self-contained engineering portfolio for **Durga Dhanush Yaragani** — AI Engineer, Backend Developer, and Cloud & DevOps practitioner. Built as a documentation-style platform rather than a traditional resume site: every project, role, and credential is a first-class page with its own architecture notes, decisions, and supporting evidence.

---

## What this is

Not a static "about me" page. This is an engineering workspace that documents:

- **18 shipped projects** — each with problem statement, architecture diagram, design decisions and trade-offs, engineering challenges, testing strategy, lessons learned, and a future roadmap
- **5 professional experiences** — presented as a vibrant timeline, with certificates and letters embedded directly on each dedicated page
- **Honest skill levels** — separated into Confident / Working Knowledge / Learning, never overstated
- **An AI Guide** — a portfolio-grounded assistant that answers questions about any project, decision, or credential in Recruiter, Technical, or Engineering Manager mode
- **A Resume Hub** — four role-tailored resume downloads (AI, Python, Cloud/DevOps, Master)

---

## Features

| Feature | Details |
|---|---|
| **Dark / Light mode** | Toggle in the sidebar, persisted via `localStorage` |
| **Command palette** | `⌘K` / `Ctrl+K` — fuzzy search across pages, projects, experience, and skills |
| **Project explorer** | Filterable by domain (AI, Backend, Cloud, DevOps, Full Stack, Automation); click any project to open a full case study |
| **Experience timeline** | Click any role title to open a dedicated page — includes embedded certificates, letters of recommendation/promotion, and award documents |
| **AI Guide** | Ask questions in General, Recruiter, Technical, or EM mode; grounded strictly in the portfolio's own data (no hallucinated claims) |
| **Responsive layout** | Collapsible sidebar on mobile, single-column reflow for all grids |
| **Print-friendly** | Sidebar/topbar hidden in print view for clean PDF export |
| **Reading progress bar** | Subtle scroll indicator at the top of the viewport |
| **Zero build step** | Single `.html` file — no bundler, no server, no dependencies to install |

---

## Tech stack

- **Structure & logic:** Vanilla HTML5 + CSS3 + JavaScript (ES6+) — no frameworks
- **Fonts:** Inter (UI text), JetBrains Mono (code, labels, timestamps)
- **AI Guide backend:** Calls a configurable API endpoint (see [Configuration](#configuration)) — designed to route through a `.env`-backed proxy rather than exposing any API key client-side
- **Assets:** Certificates and award documents are embedded as base64-encoded JPEGs directly in the HTML, so the file remains fully portable with no external asset folder required

---

## Project structure

This repository is intentionally minimal:

```
.
├── index.html      # The entire platform — markup, styles, data, and logic
└── README.md        # This file
```

All project data, experience records, skills, and certifications live in JavaScript objects near the bottom of `index.html` (`PROJECTS`, `EXPERIENCES`, `SKILLS`, `CERT_IMAGES`). Update these arrays to change content — no templating engine or build step required.

---

## Running locally

No installation needed:

```bash
# Clone or download index.html, then simply open it
open index.html        # macOS
start index.html        # Windows
xdg-open index.html     # Linux
```

Or serve it with any static file server:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

---

## Configuration

### AI Guide API endpoint

The AI Guide calls a configurable endpoint defined near the top of the `<script>` block:

```js
const API_URL = 'https://api.anthropic.com/v1/messages';
const API_MODEL = 'claude-sonnet-4-6';
```

**Recommended setup:** route this through your own lightweight backend proxy that reads the API key from a `.env` file, rather than calling the provider directly from the browser. Example:

```js
const API_URL = 'https://your-proxy-domain.com/api/guide';
```

Your proxy server should:
1. Accept the same request shape (`{ model, max_tokens, system, messages }`)
2. Attach your API key server-side (from `process.env.CLOUD_API_KEY` or similar)
3. Forward the request to your LLM provider and return the response unchanged

This keeps the API key out of client-side code entirely.

### Resume Hub downloads

The Resume Hub page expects four PDFs in a `resumes/` folder alongside `index.html`:

```
resumes/
├── resume_ai.pdf
├── resume_python.pdf
├── resume_cloud.pdf
└── resume_master.pdf
```

Drop your PDFs in with these exact filenames and the download buttons work immediately — no code changes needed.

---

## Deployment

This project deploys as a static site with zero configuration. Currently live on **Vercel**:

```bash
# Vercel (recommended — zero config for a single HTML file)
vercel deploy

# Netlify
netlify deploy --prod

# GitHub Pages
# Push to a repo, enable Pages on the main branch, done.
```

---

## Content overview

- **6 certifications:** Oracle OCI Architect Associate, Aviatrix Multicloud Network Associate, Zscaler Zero Trust Cyber Associate, Automation Anywhere RPA Essentials, Deloitte Data Analytics (Forage), Software Engineering (Forage)
- **5 professional experiences:** Scrum Master and AI Intern (The Entrepreneurship Network), AI & ML with Python Internship (Venura), IoT Cloud Engineer Virtual Internship (AICTE/EduSkills, Grade O), and a ServiceNow System Administrator Virtual Internship (ServiceNow University/AICTE/SmartBridge)
- **18 projects** spanning AI/LLM applications, backend systems, full-stack platforms, cloud infrastructure (AWS), and DevSecOps pipelines

---

## License

Personal portfolio content © Durga Dhanush Yaragani. Code structure and patterns may be referenced for learning purposes.

---

## Contact

- **Email:** ydurgadhanush@gmail.com
- **GitHub:** [github.com/YARAGANIDURGADHANUSH](https://github.com/YARAGANIDURGADHANUSH)
- **LinkedIn:** [linkedin.com/in/yaragani-durga-dhanush-16300a38b](https://www.linkedin.com/in/yaragani-durga-dhanush-16300a38b)
