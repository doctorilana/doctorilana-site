# Open items

*The running to-do list for doctorilana.com. Anyone (human or Claude) can start a
session with "what's on the open items list?" — keep this file updated as things
finish: delete done items or mark them DONE with the date.*

Last updated: 2026-08-29 (handoff from Danny).

## 1. Email at doctorilana.com — Google Workspace (IN PROGRESS)

**Status at handoff:** decided and possibly partially executed — check with Danny
what state this is in before touching it. The plan was fully researched; the
decision record below is the source of truth.

- **Provider:** Google Workspace Business Starter, $7/user/mo annual, 1 seat, bought
  **direct from Google** (not GoDaddy's reseller bundle). Ilana = super admin +
  billing owner (her card), Danny = second admin. Was waiting on Ilana's card details.
- **Addresses:** `ilana@doctorilana.com` is the primary mailbox; `hello@` is a free
  alias to it (for the contact form). Aliases cost nothing — `dmarc@`, `press@` etc.
  can be added freely.
- **Two clocks start at Google signup:** 14-day trial, and the domain must be
  verified within 9 days.
- **⚠️ DNS gotchas (this is the footgun zone — read before changing anything at GoDaddy):**
  - Website records must not be disturbed: A `@` = 75.2.60.5, CNAME `www` =
    doctorilana.netlify.app.
  - GoDaddy auto-provisioned a DMARC record
    (`v=DMARC1; p=quarantine; ... rua=mailto:dmarc_rua@onsecureserver.net`). It must
    be **replaced, not added to** — a domain gets exactly one DMARC record. Plan:
    run `p=none` with `rua=mailto:dmarc@doctorilana.com` for 2–3 weeks, confirm
    Google and Flodesk both align in the reports, then tighten back to `p=quarantine`.
    Skipping this risks her first newsletter sends silently landing in spam.
  - Google's SPF TXT and Flodesk's SPF do NOT conflict (Flodesk uses a CNAME
    return-path, not a TXT). DKIM selectors don't collide either. DMARC is the only
    shared record.
- **Follow-on once the mailbox exists:**
  - Authenticate doctorilana.com in Flodesk as its 2nd sending domain (the clinic
    keeps the 1st) so newsletters come from her domain.
  - Decide contact routing on the site: currently everything points at
    info@openwellnesspdx.com. Likely split: patients → clinic; providers /
    companies / media → her new address. Small site edit.

## 2. Contact form replacement (blocked on item 1)

`contact.html` still uses a **mailto composer** — no backend, and it fails silently
for people who use Gmail in a browser. Researched fix: **Web3Forms** (free,
forward-only, stores nothing — preferred over Netlify Forms, which stores
submissions indefinitely with no BAA, a bad fit for a medical practice). The Web3Forms
access key must be generated from whichever inbox will receive inquiries — so do
this AFTER the email project lands. The key is public-by-design and safe to commit.

## 3. Old Wix site ("thegutdoc")

Still in Ilana's Wix account, with blog posts and Online Classes content. **Export or
copy anything worth keeping BEFORE canceling any Wix subscription.** Claude can help
fold the good content into the new site afterward (old blog posts are SEO fuel).

## 4. Search presence (quick wins, mostly one-time)

- Google Search Console: add property → Domain → doctorilana.com; it gives a TXT
  record to add at GoDaddy; then submit https://doctorilana.com/sitemap.xml.
- Bing Webmaster Tools (imports from Search Console in one click).
- Google Business Profile: set the website field to https://doctorilana.com.
- Backlinks from her own profiles: Open Wellness provider page, LinkedIn, Turd Nerds
  bio, SIBO Doctor, Teachable. Each one helps Google trust the new domain.

## 5. Podcast cover art

The gold/teal tiles on index and podcasts pages are typographic placeholders. Get the
real cover art for Turd Nerds and Point of Medicine and swap them in.

## 6. Copy sign-offs Ilana still owes

- "Hundreds of clinicians trained" stat (providers.html) — accurate to her liking?
- The About page pull-quote ("I devoted my practice to digestive disease…").
- Six voice/copy flags from Aug 10 (booking headline, reviews CTA, "lived one" hero
  line, etc.) — ask Danny for the list if she wants to review them.

## 7. Minor / someday

- Flodesk popup's thank-you message is the default — a custom one resisted
  automation; can be set by hand in the Flodesk form editor if desired.
- Telehealth FAQ: which states Ilana is licensed to see telehealth patients from —
  answer enables an FAQ section that was planned but never written.
