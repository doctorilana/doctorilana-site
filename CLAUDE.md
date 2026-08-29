# doctorilana.com — site guide for Claude sessions

Static HTML site for Dr. Ilana Gurevich, ND, LAc, FABNG — naturopathic physician
specializing in gastrointestinal disorders, Portland, OR. No build step, no framework:
edit the HTML/CSS directly and push to `main`; the host deploys automatically.

## ⚠️ Title compliance — non-negotiable

NEVER describe Ilana as a "gastroenterologist" (including "naturopathic
gastroenterologist" or "gastroenterology specialist") — she cannot legally use
that title. Approved: "naturopathic physician specializing in gastrointestinal
disorders" and shortenings that avoid the banned noun. Field terms and proper
nouns are fine: "naturopathic gastroenterology" (the discipline), FABNG,
"Gastroenterology Association of Naturopathic Physicians". Calling her MD
colleagues "your gastroenterologist" is fine — they hold that title.

## ⚠️ Current strategic priority (confirmed by Ilana, Aug 29, 2026)

The site's #1 job is **building Ilana's personal brand, audience, and email list.**
She does NOT need help generating clinic business. Patient/clinic content stays, but
earlier design decisions that prioritized patient booking over email capture are
superseded — re-evaluate them rather than preserving them.

The capture flow is built around the lead magnet (Aug 29, 2026): every signup
section offers the free "Rebuild Your Microbiome" cookbook, the homepage hero's
primary CTA is "Get the Free Cookbook" (#newsletter), and the site-wide footer
link reads "Free Cookbook". Delivery: `downloads/rebuild-your-microbiome-cookbook.pdf`
(compressed to 2.6MB) is linked from `cookbook.html`; both are noindexed via
`_headers` and the page's robots meta, and deliberately absent from `sitemap.xml` —
the Flodesk welcome email is the intended way in. Don't add them to the sitemap.

The owners are non-technical: the site is managed by Ilana and her husband Justin
(as of the Aug 2026 handoff from Danny, who built it). When they ask for a change,
make it, verify the affected page still renders sensibly, commit with a
plain-English message, and push. Don't introduce build tools, frameworks, or
dependencies. Explain what you did in plain English — assume no knowledge of git,
GitHub, or web tooling.

## Companion docs

- `HANDOFF.md` — orientation for Justin/Ilana: what the pieces are, how to work
- `OWNERS-GUIDE.md` — human-facing guide for Ilana (plain English)
- `OPEN-ITEMS.md` — the live to-do list; keep it updated as items finish
- `SETUP-NEW-COMPUTER.md` — runbook for Claude to set up a new editing machine

## Accounts and access

- GitHub repo owner: the `doctorilana` account (Ilana's; login in the shared
  1Password vault, item "Ilana Github"). Justin edits using this account.
  `robotdanny` (Danny) remains a collaborator as the break-glass option.
- The repo must stay **public** — Netlify's free tier blocks collaborator pushes on
  private repos. Never suggest making it private.
- Netlify, GoDaddy, and Flodesk logins are all in the shared 1Password vault.
  Claude never needs these credentials and secrets never go in this repo.

## Flodesk (email list) — shared-account rules

Ilana has ONE Flodesk account (legacy $38/mo unlimited plan, renews Mar 2027 —
**never cancel or downgrade it**, that pricing is discontinued) serving TWO brands:
Open Wellness PDX (the clinic, ~14k patient list, the account's primary tenant) and
doctorilana.com.

- **Global branding belongs to the CLINIC** (logo, colors, footer address,
  double-opt-in email). Changing global settings retroactively rewrites existing
  clinic emails/forms — don't.
- doctorilana emails override per-email: delete the logo block, insert an image
  block with the doctor-ilana logo, duplicate a past doctorilana email as the
  template for new sends.
- Website signups → segment "doctorilana.com signups" (form ID
  6a7a2a99f57159891f9b371d, double opt-in ON). Keep this segment separate from the
  clinic's patient-derived segments.
- Cookbook delivery workflow "Cookbook delivery — doctorilana.com signups" is
  published and handles fulfillment automatically.
- Popup form "Cookbook popup — doctorilana.com" shows after 30s. Gotcha: Flodesk's
  universal header script alone does NOT display popups on a hand-coded site — every
  page needs a `window.fd('form', {formId})` call (present site-wide except
  cookbook.html). Keep that call when creating new pages.

## Email at doctorilana.com

Google Workspace (ilana@doctorilana.com + hello@ alias) was decided Aug 2026 and may
or may not be fully set up — see `OPEN-ITEMS.md` for the full decision record and
the DNS/DMARC gotchas. Any DNS change at GoDaddy must preserve the website records
(A @ = 75.2.60.5, CNAME www = doctorilana.netlify.app), and the domain can hold only
ONE DMARC record shared between Google and Flodesk.

## Structure

- `index.html` — homepage: hero ("The gut can heal."), three audience doors
  (Patients / Providers / Companies), featured testimonial, "gut·in·stinct"
  definition block with portrait, podcasts section
- `patients.html` — conditions grid (cards open a detail dialog), approach,
  what-to-expect steps, testimonials (#stories), booking box (#book)
- `providers.html` — courses, mentorship, clinician endorsements, speaking
- `consulting.html` — six services for companies + credibility panel
- `podcasts.html` — both shows, latest episodes, guest interviews (#interviews)
- `reviews.html` — all patient + clinician quotes, rating stats
- `about.html` — bio + credentials
- `contact.html` — routing form (patient/provider/company/media → mailto)
- `press.html` — press kit (bios, headshot, talk topics)
- `conditions/*.html` — 9 SEO condition pages, one per condition
- `assets/styles.css` — the design system (colors/typography as CSS variables)
- `assets/main.js` — mobile nav toggle + active-link marking
- `sitemap.xml`, `robots.txt`

## Conventions

- Palette and fonts live in `:root` variables in `assets/styles.css`; don't hardcode
  new colors.
- Header/footer are duplicated in every page (no templating). A nav or footer change
  must be applied to ALL html files, including `conditions/*` (which use `../` paths).
- Condition data appears twice: the dialog data in `patients.html` (JS `CONDITIONS`
  array) and the standalone pages in `conditions/`. Keep both in sync when editing
  condition content.
- Episode lists on `podcasts.html` are a static snapshot. To refresh, fetch the RSS
  feeds and update the "Latest episodes" section:
  - Turd Nerds: https://anchor.fm/s/7d912314/podcast/rss
  - Point of Medicine: https://anchor.fm/s/fb0a6418/podcast/rss
- Contact email everywhere: info@openwellnesspdx.com
- Clinic facts: Open Wellness PDX, 1901 N Killingsworth St, Portland OR 97217,
  503-770-0670, Mon–Fri 8–6 / Sat 9–6.

## Pending TODOs

- **Newsletter is LIVE** (not a TODO): Flodesk form ID 6a7a2a99f57159891f9b371d,
  segment "doctorilana.com signups", double opt-in ON. Loader script in every page's
  <head>; form embedded on index, podcasts, providers, and all 9 condition pages, plus
  a footer link site-wide. Deliberately NOT on patients/consulting/about/reviews/
  contact — those pages have a single competing action. Fields/colors/button are edited
  in Flodesk; only the surrounding headline/subtext live in the HTML.
- **Contact form still uses a mailto composer** (contact.html) — planned replacement
  is Web3Forms; details and sequencing in `OPEN-ITEMS.md`.
- Everything else lives in `OPEN-ITEMS.md` — read it when asked "what's next" and
  keep it current as items complete.
- Structured data + sitemap assume https://doctorilana.com.

## Deploy budget

Netlify free credit plan: 300 credits/month, ~15 per production deploy (~20 deploys).
Forms are free/unmetered. During heavy work sessions, batch changes into fewer pushes.
