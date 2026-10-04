<!--
  Hi, you're reading the raw markdown. Nice.
  Everything here is hand-written: the SVGs in /assets are plain text, no build step, no third-party image services, no trackers.
  The rule for this page: if a claim can't link to a receipt, it doesn't go here.
-->

<p align="center">
  <img src="assets/hero.svg" width="100%" alt="Taha Saiyed, full-stack developer in Vancouver, BC. I build software for the things people forget, and make it trustworthy before I make it clever." />
</p>

<p align="center">
  <b>Full-stack developer</b> · TypeScript, React, Node, Next.js, Supabase · Studying Computer &amp; Information Systems at Douglas College<br/>
  Open to <b>co-op and internship</b> roles in software, QA, data and IT support<br/><br/>
  <a href="#01--lifeos">Flagship</a> &nbsp;·&nbsp;
  <a href="#03--receipts">Receipts</a> &nbsp;·&nbsp;
  <a href="#05--changelog">Changelog</a> &nbsp;·&nbsp;
  <a href="https://www.linkedin.com/in/TahaSaiyed">LinkedIn</a>
</p>

<br/>

## 01 · LifeOS

**Life admin, handled before it bites.** A privacy-first app that tracks renewals, expiries and bills, and tells you what needs you *before* it becomes a charge, a fine or a lapsed document.

**The problem.** Life admin fails silently. You find out a subscription renewed or a policy lapsed after it's too late.

**The thinking.** An app that reads your email has to earn trust before it earns features. So LifeOS uses read-only OAuth, extracts the fact it needs, and **discards the source**. Phase 1 alerts are **plain date math**: predictable and explainable, with no model in the loop. AI only gets added once code-level validators exist to check what it says.

<p align="center">
  <a href="https://github.com/smta08/lifeos/blob/main/docs/ARCHITECTURE.md">
    <img src="assets/lifeos-architecture.svg" width="100%" alt="LifeOS architecture. Features call domain, repositories and services. Repositories are the only database access. User paths use the Supabase client under the user's JWT so row-level security enforces tenancy, and Prisma is limited to migrations and webhooks. The Phase 2 AI pipeline runs SQL date pre-pass, model pre-filter, cross-reference model, Zod parse, code validators, then upsert. Validators in code are the security control, not prompts." />
  </a>
</p>

**Where it stands.** Phase 1 runs: facts, the deterministic alert engine, an in-browser PDF and OCR scanner (files never leave the browser), read-only Gmail scanning, and a dashboard. The Phase 2 AI life-scan is designed and documented, and its prompts are still stubs.

**What it taught me.** Prisma's default connection quietly **bypasses row-level security**. That changed the whole data-access design. Gmail's API returned 429s until I [batched fetches five at a time](https://github.com/smta08/lifeos/commit/e4323c5). A strict CSP broke hot reload, so `unsafe-eval` is allowed [in dev only](https://github.com/smta08/lifeos/commit/69c6a56).

<sub>Next.js 14 · TypeScript (strict) · Supabase (Postgres, Auth, RLS) · Prisma · Tailwind · shadcn/ui · Zod · TanStack Query · Inngest · Resend · pdf.js · Tesseract.js · Anthropic API</sub><br/>
<sub>→ [Repo](https://github.com/smta08/lifeos) · [Architecture](https://github.com/smta08/lifeos/blob/main/docs/ARCHITECTURE.md) · [Security model](https://github.com/smta08/lifeos/blob/main/docs/SECURITY.md) · [1,000-line spec](https://github.com/smta08/lifeos/blob/main/docs/TRD.md) · [Spec review](https://github.com/smta08/lifeos/blob/main/docs/TRD-review.md)</sub>

<br/>

## 02 · Also shipped

<p>
  <a href="https://github.com/smta08/ApplyFlow"><img src="assets/card-applyflow.svg" width="370" alt="ApplyFlow: offline Android job-application tracker with interview and follow-up reminders, stats and CSV export. Java, MVVM, Room, WorkManager. 19 unit tests and a real database migration." /></a>
  <a href="https://github.com/smta08/NutriGuard"><img src="assets/card-nutriguard.svg" width="370" alt="NutriGuard: early Android health-tracker prototype. Meals via the Open Food Facts API with a halal filter, plus water, sleep and mood." /></a>
</p>

<br/>

## 03 · Receipts

Principles are cheap. Each of these links to the place I actually did it.

| I believe… | Receipt |
|---|---|
| **Deterministic before intelligent.** If date math can answer it, a model shouldn't. | [`alerts/engine.ts`](https://github.com/smta08/lifeos/blob/main/src/features/alerts/engine.ts) |
| **Prompts aren't security controls. Validators in code are.** | [ARCHITECTURE.md → The AI pipeline](https://github.com/smta08/lifeos/blob/main/docs/ARCHITECTURE.md#the-ai-pipeline) |
| **Tenancy belongs to the database, not my memory.** RLS on every user table, and the service role never touches a user path. | [SECURITY.md → Tenancy isolation](https://github.com/smta08/lifeos/blob/main/docs/SECURITY.md#tenancy-isolation-rls) |
| **Keep the fact, discard the source.** | [`scan/gmail.ts`](https://github.com/smta08/lifeos/blob/main/src/features/scan/gmail.ts) |
| **Never lose a user's data on upgrade.** An explicit migration, not a destructive fallback. | [`AppDatabase.java`](https://github.com/smta08/ApplyFlow/blob/main/app/src/main/java/com/applyflow/data/db/AppDatabase.java) |
| **Test what's easy to get subtly wrong.** CSV escaping, stats bucketing, date handling. | [ApplyFlow tests](https://github.com/smta08/ApplyFlow/tree/main/app/src/test/java/com/applyflow) |
| **Write the spec, then argue with it.** | [TRD.md](https://github.com/smta08/lifeos/blob/main/docs/TRD.md) → [TRD-review.md](https://github.com/smta08/lifeos/blob/main/docs/TRD-review.md) |

<br/>

## 04 · Stack radar

<p align="center">
  <img src="assets/stack-radar.svg" width="100%" alt="Stack radar. Core: JavaScript, TypeScript, React, Node.js, Express, MongoDB. Building with: Next.js 14, Supabase and Postgres, Tailwind, Zod, Java for Android, Room, React Native with Expo. Learning: Docker, GitHub Actions, Linux, AWS, Terraform. Exploring: Anthropic API, LLM validation, Inngest, Ollama, Electron, Chrome MV3." />
</p>

<br/>

## 05 · Changelog

| When | What |
|---|---|
| `2026-09` | **3rd place, Vision2Reality Hackathon.** Led a 4-person team building a growth strategy for a startup. |
| `2026-06` | **LifeOS phase 1.** Next.js + Supabase with RLS tenancy, in-browser OCR and read-only Gmail scanning, documented end to end. |
| `2026-06` | **NutriGuard prototype.** Android app calling the Open Food Facts API, with a halal filter. |
| `2026-05` | **ApplyFlow v1.** Offline-first Android, Room migrations, WorkManager reminders, unit tests. |
| `2025` | Started a Post-Baccalaureate Diploma in Computer &amp; Information Systems (Emerging Technology) at Douglas College. |
| `2024` | Bachelor of Computer Application, Swarrnim University. |
| `2023` | [BILLINGSOFTWARE](https://github.com/smta08/BILLINGSOFTWARE), a team Angular project. My part was the header, navigation and invoice routing. |
| `earlier` | Internships: IT support &amp; web development at Kipling Media (Vancouver), and Web Nodes (Ahmedabad). |

<br/>

<details>
<summary><code>$ taha --help</code></summary>

<br/>

```text
USAGE
  Read 01 for how I think, 03 to check it, 05 for the timeline.

VERSION
  0.4.0-pre   Pre-1.0 on purpose: still a student, shipping anyway.
              The version bumps when something real ships.

NOT ON THIS PAGE
  A few projects are still private (a job-application automation
  system, a halal-investing research platform). They go public when
  they have a README I'd be happy for you to read.

KNOWN ISSUES
  LifeOS SECURITY.md describes a cross-user RLS isolation test.
  It isn't written yet. It's next, along with CI.

CONTACT
  linkedin.com/in/TahaSaiyed
```

</details>

<br/>

<p align="center">
  <a href="https://www.linkedin.com/in/TahaSaiyed">LinkedIn</a> &nbsp;·&nbsp; <a href="https://github.com/smta08?tab=repositories">All repositories</a><br/>
  <sub>Hand-built. No trackers, no stats widgets, no borrowed art.</sub>
</p>
