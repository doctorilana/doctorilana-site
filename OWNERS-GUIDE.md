# Your Website — Owner's Guide

*For Ilana (and anyone helping her). No technical knowledge assumed.
Justin: start with `HANDOFF.md` — it has the setup steps and explains the moving
parts. This guide is the day-to-day reference.*

## What you have

Your website — **doctorilana.com** — is a set of simple files that live in three places:

1. **GitHub** (github.com/doctorilana/doctorilana-site) — the master copy and its full
   edit history. Think of it as the filing cabinet.
2. **Netlify** — the company that puts those files on the internet. Whenever the master
   copy changes, Netlify updates the live site automatically within about a minute.
   You never need to touch it.
3. **A folder on the laptop** — a working copy where edits are made.

All logins are in the shared 1Password vault. Hosting costs: **$0/month**. The only
bill is the annual domain renewal at GoDaddy.

The site's #1 job (your call, August 2026): **growing your audience and email list**
around the free "Rebuild Your Microbiome" cookbook. Everything about that loop is
live — signup forms and a timed popup on the site, and Flodesk automatically emails
new subscribers the cookbook. Patient and clinic content stays, but list growth is
the point.

## How you edit your site

Open Claude Code on the laptop, in the website folder, and say what you want in plain
English. Examples that work verbatim:

- "Change my Saturday hours to 9–4."
- "Add this episode to the podcasts page: [paste title + link]"
- "Add a testimonial from a patient — here's the quote…"
- "Reword the second paragraph on the About page to mention my new certification."
- "Undo whatever we changed yesterday."
- "What's on the open items list?"

Claude edits the files, saves the change to GitHub with a note describing it, and the
live site updates in about a minute. **Every change is reversible** — the filing
cabinet keeps every version ever, so nothing you ask for can permanently break the
site.

## Four rules

1. **One voice rule:** never describe yourself as a "gastroenterologist" on the site —
   Claude knows this rule and will phrase around it ("naturopathic physician
   specializing in gastrointestinal disorders").
2. **No secrets in the site files.** Passwords and API keys never go in this folder —
   the folder is publicly visible by design. Claude knows this too.
3. **Flodesk's account-wide branding belongs to the clinic.** Your one Flodesk
   account serves both Open Wellness and doctorilana.com; don't change global
   settings there. Claude knows the workaround for your newsletters.
4. **When in doubt, just ask Claude** — including "explain what you just did" or
   "show me before you publish."

## When something seems wrong

- **Site looks broken?** Tell Claude: "the site looks broken, roll back to the last
  good version." That's a real command; it works.
- **Site is down?** It almost never will be (Netlify is very reliable). Check
  netlify.com status, or ask Claude to investigate.
- **Locked out of something?** All credentials are in 1Password: GitHub, Netlify,
  GoDaddy, Flodesk.
- **Human help:** Danny set this up and can always be called.

## What's still to do

The full list lives in `OPEN-ITEMS.md` (ask Claude: "what's on the open items
list?"). The highlights, in rough priority order:

1. **Email at doctorilana.com** — Google Workspace, so newsletters come from
   ilana@doctorilana.com instead of the clinic address. Decided; needs your card to
   finish. The DNS steps have traps — coordinate with Danny.
2. **Your old Wix site ("thegutdoc")** — export the blog posts and Online Classes
   content you want to keep **before** canceling any Wix subscription.
3. **Google Search Console + Business Profile + your bios** — quick one-time steps
   that make Google find the new site: submit the sitemap, set your Business Profile
   website, and point your Open Wellness page, LinkedIn, Turd Nerds bio, SIBO
   Doctor, and Teachable links at doctorilana.com.
4. **Real podcast cover art** — the current tiles are placeholders.
5. **Copy you haven't signed off on** — "Hundreds of clinicians trained"
   (Providers page) and the About pull-quote.
