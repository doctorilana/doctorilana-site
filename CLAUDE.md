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

The owner is non-technical. When she asks for a change, make it, verify the affected
page still renders sensibly, commit with a plain-English message, and push. Don't
introduce build tools, frameworks, or dependencies.

## Companion docs

- `OWNERS-GUIDE.md` — human-facing guide for Ilana (plain English)
- `SETUP-NEW-COMPUTER.md` — runbook for Claude to set up a new editing machine

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

- NEWSLETTER: hidden sections on `index.html` and `podcasts.html` (search
  "NEWSLETTER — HIDDEN"). When Flowdesk is connected, replace the form with the
  Flowdesk embed snippet and remove the `hidden` attribute. Do NOT re-enable the
  placeholder form as-is (fake success message, stores nothing).
- Podcast cover art: the gold/teal tiles on index/podcasts are typographic
  placeholders — swap for real show artwork when provided.
- Two claims awaiting Ilana's confirmation: the About pull-quote ("I became a
  gastroenterology specialist because I had to…") and "100s of clinicians trained"
  (providers.html stat strip).
- Structured data + sitemap assume https://doctorilana.com — keep if that's the
  live domain.
