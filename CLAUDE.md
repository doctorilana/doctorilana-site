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

- **Newsletter is LIVE** (not a TODO): Flodesk form ID 6a7a2a99f57159891f9b371d,
  segment "doctorilana.com signups", double opt-in ON. Loader script in every page's
  <head>; form embedded on index, podcasts, providers, and all 9 condition pages, plus
  a footer link site-wide. Deliberately NOT on patients/consulting/about/reviews/
  contact — those pages have a single competing action. Fields/colors/button are edited
  in Flodesk; only the surrounding headline/subtext live in the HTML.
- **Contact form still uses a mailto composer** (contact.html) — no backend, and it
  fails silently for desktop webmail users. Researched replacement: Web3Forms
  (forward-only, stores nothing, free; access key is public-by-design so it's safe in
  this public repo). Needs an access key generated from the receiving inbox. Netlify
  Forms is the alternative — unlimited/free on our plan but stores submissions
  indefinitely with no BAA, which is why Web3Forms is preferred for a medical practice.
- **Flodesk welcome email not yet created** — the site now promises the cookbook at
  signup, but Flodesk must actually send the link. Needed (in the Flodesk UI): a
  workflow on segment "doctorilana.com signups" whose first email links to
  https://doctorilana.com/cookbook.html, with "include existing subscribers" enabled
  so anyone who signed up before the workflow existed still gets it. Also worth
  changing the form's button text in Flodesk from "Join the List" to
  "Send Me the Cookbook".
- Podcast cover art: gold/teal tiles on index/podcasts are typographic placeholders.
- Awaiting Ilana's confirmation: "Hundreds of clinicians trained" (providers.html stat
  strip) and the About pull-quote ("I devoted my practice to digestive disease…").
- Email domain: she wants an address at doctorilana.com. Any DNS work must preserve the
  Netlify website records, and Flodesk domain authentication needs to share one DMARC
  record with the email provider.
- Structured data + sitemap assume https://doctorilana.com.

## Deploy budget

Netlify free credit plan: 300 credits/month, ~15 per production deploy (~20 deploys).
Forms are free/unmetered. During heavy work sessions, batch changes into fewer pushes.
