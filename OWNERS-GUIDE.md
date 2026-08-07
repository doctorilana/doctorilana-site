# Your Website — Owner's Guide

*For Ilana (and anyone helping her). No technical knowledge assumed.*

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

## How you edit your site

Open Claude Code on the laptop, in the website folder, and say what you want in plain
English. Examples that work verbatim:

- "Change my Saturday hours to 9–4."
- "Add this episode to the podcasts page: [paste title + link]"
- "Add a testimonial from a patient — here's the quote…"
- "Reword the second paragraph on the About page to mention my new certification."
- "Undo whatever we changed yesterday."

Claude edits the files, saves the change to GitHub with a note describing it, and the
live site updates in about a minute. **Every change is reversible** — the filing
cabinet keeps every version ever, so nothing you ask for can permanently break the
site.

## Three rules

1. **One voice rule:** never describe yourself as a "gastroenterologist" on the site —
   Claude knows this rule and will phrase around it ("naturopathic physician
   specializing in gastrointestinal disorders").
2. **No secrets in the site files.** Passwords and API keys never go in this folder.
   Claude knows this too.
3. **When in doubt, just ask Claude** — including "explain what you just did" or
   "show me before you publish."

## When something seems wrong

- **Site looks broken?** Tell Claude: "the site looks broken, roll back to the last
  good version." That's a real command; it works.
- **Site is down?** It almost never will be (Netlify is very reliable). Check
  netlify.com status, or ask Claude to investigate.
- **Locked out of something?** All credentials are in 1Password: GitHub, Netlify,
  GoDaddy.
- **Human help:** Danny set this up and can always be called.

## Still to do (as of Aug 2026)

- Newsletter signup is built but hidden — it turns on when Flowdesk is connected.
- Podcast artwork on the site is a placeholder — real cover art can be swapped in.
- Your old Wix site ("thegutdoc") still exists in your Wix account with blog and
  online-class content — export anything you want before canceling Wix.
