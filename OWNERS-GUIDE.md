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

## When you land: your first session (in order)

**The site is already live at doctorilana.com** — nothing below is urgent, and nothing
can break.

1. **Set up the laptop** (~15 min, with your husband). Install Claude Desktop if
   needed, open Claude Code, and paste this sentence:
   *"Set this computer up following
   https://github.com/doctorilana/doctorilana-site/blob/main/SETUP-NEW-COMPUTER.md"*
   Claude does the rest and proves it works with a test edit.
2. **Make one edit yourself.** Ask Claude to change something small in your own words.
   Watch it appear on doctorilana.com a minute later. Now it's your website.
3. **Google Search Console** (~3 min, any device): search-console.google.com → Add
   property → "Domain" → doctorilana.com. Google shows a TXT record — send it to
   Danny, he adds it at GoDaddy, you click Verify. Then submit the sitemap:
   https://doctorilana.com/sitemap.xml. This makes Google index the new site fast.
4. **Google Business Profile**: set your website field to https://doctorilana.com.
5. **Update your links elsewhere** (big for Google, easy for you): point your Open
   Wellness PDX provider page, LinkedIn, Turd Nerds bio, SIBO Doctor course bio, and
   Teachable school at doctorilana.com. Mention the new site in future podcast
   appearances.
6. **Your old Wix site ("thegutdoc")**: it still exists in your Wix account, with blog
   posts and Online Classes content. Export or copy anything you want to keep —
   **before** canceling any Wix subscription. Claude can help fold that content into
   the new site.

## Answers Claude is waiting on (tell any Claude session, it'll handle the rest)

- Which states you're licensed to see telehealth patients from (for an FAQ section).
- Whether "hundreds of clinicians trained" (Providers page) is accurate to your liking.
- The Flowdesk embed snippet, when marketing emails are ready — the newsletter signup
  is built and hidden, waiting for it.
- Real podcast cover art files, to replace the placeholder tiles.
