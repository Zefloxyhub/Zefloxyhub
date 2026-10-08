# GitHub Profile Design Specification: `Zefloxyhub`

_Companion to `github-profile-audit.md`. Nothing here is implemented yet._

## 1. Design principle: honest and small, but premium

The audit found **two real projects**, **9 public contributions**, and **no name, bio or links**. A "dashboard" packed with widgets would expose that thinness. The design therefore:

- leads with **identity + work** (what you build), not with metrics;
- shows **two strong project cards with real screenshots** instead of a long list;
- uses **custom static SVGs** for structure (no third-party stats services);
- marks every project with an **evidence-based status**;
- leaves clear **slots** for information only you can provide (name, links, more work).

Target: a visitor understands who / what / how good / where to look in **under 15 seconds**, on a phone.

## 2. Information architecture (top to bottom)

```
┌──────────────────────────────────────────────┐
│ 1 HERO  (SVG banner, light+dark)             │  who + what, 1 line
│   links row (only verified links)            │
├──────────────────────────────────────────────┤
│ 2 WHAT I DO  (3 short plain-English lines)   │
├──────────────────────────────────────────────┤
│ 3 ENGINEERING DOMAINS  (SVG map, 4 blocks)   │
├──────────────────────────────────────────────┤
│ 4 FEATURED PROJECTS                          │
│   Vantia card  (screenshot + text + stack)   │
│   Loyalwise card                             │
├──────────────────────────────────────────────┤
│ 5 TECH STACK  (grouped, icons, no %)         │
├──────────────────────────────────────────────┤
│ 6 PROJECT STATUS BOARD (replaces "activity") │
├──────────────────────────────────────────────┤
│ 7 HOW I BUILD (optional, 3 evidence lines)   │
├──────────────────────────────────────────────┤
│ 8 CONTACT / CTA                              │
└──────────────────────────────────────────────┘
```

Sections from the brief that are **dropped or changed**, and why:

| Brief section | Decision | Reason |
|---|---|---|
| 6 GitHub activity widgets | **Replaced** by a static project status board | 9 lifetime contributions; streak/stats cards would hurt. Public `github-readme-stats` instances are also frequently rate-limited. Revisit once activity grows. |
| 7 Currently building | **Omitted** unless you confirm a project | No repo has commits in the last ~11 months. `echtjoot` is empty. |
| 8 Engineering philosophy | **Reduced** to an optional "How I build" with 3 code-backed lines | No stated philosophy exists; making one up is not allowed. |

## 3. Section-by-section content (draft copy)

All copy below uses only verified facts. `[[...]]` marks slots that need your input.

### 3.1 Hero (`assets/hero-dark.svg` / `assets/hero-light.svg`)
- Line 1 (large): `[[Your name or brand]]`, falling back to **Zefloxyhub**
- Line 2: **Full-stack web developer**
- Line 3: _Building commerce and small-business web apps: storefronts, payments, dashboards._
- Small monospace tag row inside the SVG: `Next.js · React · Node/Express · Flask · MongoDB`
- Below the SVG, an HTML link row with **only verified links**. Today that is just the GitHub profile; add `[[LinkedIn]]`, `[[Portfolio]]`, `[[Email]]` if you supply them.
- No stats badges, no visitor counter, no typing animation.

### 3.2 What I do (plain language, max 3 lines)
> I build web applications for selling and serving customers online: online stores with flexible payments, admin back-offices for owners, and simple tools that help small businesses keep customers coming back.

Followed by three icon bullets: **Storefronts & checkout** · **Admin dashboards** · **Customer-loyalty tools**.

### 3.3 Engineering domains (`assets/domains.svg`)
Four blocks, each listing sub-capabilities **and the project that proves it** (small grey caption). No percentages.

| Block | Items | Proof |
|---|---|---|
| FRONTEND | Next.js / React UIs · Tailwind design systems · Dashboards & charts · PWA / offline page | Vantia, Loyalwise |
| BACKEND & APIs | REST APIs (Express) · Flask apps · JWT auth · Data models | Vantia, Loyalwise |
| COMMERCE & PAYMENTS | Checkout flow · Stripe payments · Installment plans · Inventory & orders admin | Vantia |
| REAL-TIME & DATA | Socket.io live chat · MongoDB / Mongoose · SQLite / SQLAlchemy · QR generation | Vantia, Loyalwise |

Layout: 2×2 grid drawn at `viewBox` width **640** with a 16px minimum font size, so text stays about 9–10px on a 360px phone and is crisp on desktop (SVG scales with `width="100%"`). For accessibility and very small screens, the same content is repeated as text inside a collapsed `<details>` ("Read as text").

### 3.4 Featured projects (`assets/projects/vantia.png`, `assets/projects/loyalwise.png`)
One card per project, stacked vertically (no side-by-side table, so it reflows on mobile). Each card:

```
[ screenshot, rendered from the repo's own HTML, 1280×800 → shown at width 100% ]
VANTIA: Gold marketplace with installment payments            PROTOTYPE
An online shop for gold bars, coins and jewelry where buyers can pay over
several months instead of all at once, plus a back-office for the store owner.
Why it matters: makes a high-value purchase affordable and gives the owner
one place to manage products, orders, stock and support chats.
Stack: Next.js · React · Tailwind · Node/Express · MongoDB · Stripe · Socket.io
→ Repository   (no demo link: none exists)
```

```
LOYALWISE: QR-code loyalty cards for small businesses           EARLY MVP
A shop fills in a short form (points per purchase, reward, terms) and gets a
digital loyalty card with its own QR code and shareable page.
Why it matters: replaces paper stamp cards with something customers can't lose.
Stack: Python · Flask · SQLAlchemy/SQLite · qrcode/Pillow · Gunicorn
→ Repository
```

Honesty notes baked into the copy: Vantia's price feed and crypto checkout use demo data, so the card says **"live price channel (demo data)"** if it mentions pricing at all, and does not mention crypto. Loyalwise's auth pages are UI only, so the card does not claim accounts/login.

Screenshots: PNGs generated by Devin with headless Chrome from `Vantia-marketplace/preview/index.html` and `loyalwise/templates/index.html` (already captured during the audit, attached). Optionally a second, scrolled screenshot per project.

### 3.5 Tech stack (`assets/stack.svg`, or HTML icon rows)
Grouped, icon + label, no levels. Only technologies **used in code** (manifest-only entries excluded):

| Group | Items |
|---|---|
| Languages | JavaScript · Python · HTML/CSS |
| Frontend | Next.js · React · Tailwind CSS · Framer Motion · React Query · Chart.js / Recharts |
| Backend | Node.js · Express · Flask · Socket.io · JWT |
| Data | MongoDB (Mongoose) · SQLite (SQLAlchemy) · Redis (cache utility) |
| Payments | Stripe |
| Deploy / tooling | Netlify · Render · Gunicorn · autocannon (load testing) |

Excluded on purpose: TypeScript (devDependency, no `.ts` files), Jest (no tests), Cloudinary/Nodemailer/node-cron/Coinbase/SendGrid/TaxJar/Google Places (declared, not used), Flask-Login/WTF/Mail/Migrate (declared, not used).

Icons: drawn inside our own SVG (simple monochrome glyphs/labels), so there are **no external icon services**. Alternative, lighter option: `skillicons.dev` image row. It is an external dependency, so it is **not** the default.

### 3.6 Project status board (`assets/status.svg`), replacing activity widgets
A small static board, explicitly dated:

| Project | Status | Evidence |
|---|---|---|
| Vantia-marketplace | PROTOTYPE · not in active development | 1 commit, last update 2025-05-01 |
| Loyalwise | EARLY MVP · not in active development | 1 commit, last update 2025-01-02 |
| echtjoot | PLANNED (empty repo), shown **only if you confirm** what it is | created 2025-10-29 |

Status vocabulary: ACTIVE (commits in last 90 days) · IN PROGRESS · PROTOTYPE/MVP · COMPLETED · ARCHIVED. Today nothing qualifies as ACTIVE. GitHub's own contribution graph remains below the README, which is enough activity signal.

### 3.7 How I build (optional, 3 lines, each tied to code)
- **Secrets stay out of code.** Env-based config and a written API security guide (`API_SECURITY.md`).
- **Measure before scaling.** Load-testing script (autocannon) and a performance monitor in the API.
- **Owner tools, not just storefronts.** Admin dashboards for products, orders, inventory and support.

Shown only if you approve; otherwise omitted.

### 3.8 Contact / CTA
A centered closing line, _"Want to see the code? Start with Vantia."_, then the verified link row (same as hero). Only GitHub today; LinkedIn / portfolio / email are added only if you provide them.

## 4. Visual design

| Token | Value |
|---|---|
| Background (dark SVG) | `#0d1117` (GitHub dark), cards `#161b22`, border `#30363d` |
| Background (light SVG) | `#ffffff`, cards `#f6f8fa`, border `#d0d7de` |
| Accent | single accent, e.g. amber `#f5b942` (nods to Vantia's gold without copying its purple theme) |
| Text | `#e6edf3` / `#1f2328`; muted `#8b949e` / `#57606a` |
| Type | System stack: `-apple-system, Segoe UI, Helvetica, Arial, sans-serif`; mono `ui-monospace, SFMono-Regular, Consolas, monospace` |
| Shapes | 12px radius cards, 1px borders, thin accent rule under section titles |
| Motion | At most one subtle CSS fade-in on the hero accent line; no typing effects, no marquee |

Light/dark: `<picture>` with `<source media="(prefers-color-scheme: dark)">`, which GitHub supports. Every image gets meaningful `alt` text.

Section headers are plain Markdown `##` (keeps anchors, accessibility and mobile reflow) with a short muted subtitle. No emoji.

## 5. Proposed repository layout (`Zefloxyhub/Zefloxyhub`)

```
README.md
assets/
  hero-dark.svg   hero-light.svg
  domains-dark.svg domains-light.svg
  status-dark.svg  status-light.svg
  stack-dark.svg   stack-light.svg
  projects/vantia.png  projects/loyalwise.png
docs/
  github-profile-audit.md
  github-profile-design.md
```

No build tooling, no GitHub Actions, no dependencies.

## 6. GitHub compatibility considerations
- SVGs embedded via `<img>` are sandboxed: **no external fonts, no external images, no JavaScript**. Use system fonts and inline shapes only. CSS `@keyframes` inside the SVG works; keep it minimal.
- GitHub strips `style` attributes and `<style>` tags in README HTML, so layout uses only `align`, `width`, `<p>`, `<picture>`, `<details>`, `<br>`.
- Relative image paths (`assets/...`) are resolved by GitHub, so no hotlinking.
- Width: images use `width="100%"` (or a max of about 880px for the hero); no multi-column tables for core content, so it reflows on mobile.
- The GitHub mobile app ignores `prefers-color-scheme` in some versions, so both SVG variants must be legible on either background (sufficient contrast is tested).
- A profile README shows only if the repo is **public** and named exactly like the username.

## 7. Risks and limitations
1. **Thin evidence.** With two single-commit prototypes, the profile can look polished but not "senior". The design avoids overstating; real credibility will come from more public work and history.
2. **No identity data.** Without your name and links, the hero and CTA are weak. This needs input from you.
3. **Possibly incomplete view.** Devin sees only 5 repos. Private or other work is missing.
4. **Prototype caveats.** Mocked price/crypto data in Vantia and non-functional auth in Loyalwise limit what can be claimed.
5. **Profile repo missing.** `Zefloxyhub/Zefloxyhub` must be created by you (Devin cannot create repos), made public, and added to Devin's GitHub app access.
6. **Screenshots** are of static/preview pages, not of the full running apps (running them needs MongoDB/Stripe keys, which won't be requested).

## 8. Implementation plan (after approval)
1. You create the public repo `Zefloxyhub/Zefloxyhub` (with "Add a README" checked) and grant Devin access. Provide name/brand and links (optional).
2. Devin clones it and adds `docs/` (these two files).
3. Build SVG assets (hero, domains, status, stack; dark + light) by hand, no generators.
4. Add project screenshots (`assets/projects/*.png`, optimized to under ~300 KB each).
5. Write `README.md` following §2–§3.
6. Validate:
   - render with GitHub's Markdown API (`POST /markdown`, `mode=gfm`) and visually inspect at 1280px, 768px and 375px in Chrome (dark + light);
   - parse every SVG as XML and confirm no external references;
   - verify every relative image path exists and every link returns 200;
   - re-check every claim and technology against audit sections 2 and 3;
   - secret scan of the repo (no `.env`, tokens, keys).
7. Open a PR in `Zefloxyhub/Zefloxyhub` with before/after screenshots. You merge.
8. Optional owner follow-ups (not done by Devin unless asked): fix repo descriptions, archive `loyalwis`/`github-pages`, pin Vantia + Loyalwise, add repo topics, add screenshots to project READMEs.
