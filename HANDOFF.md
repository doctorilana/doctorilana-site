# Handoff guide — running doctorilana.com

*For Justin (and Ilana). Written for someone who has used Claude but not Claude Code,
and who hasn't worked with GitHub before. Read this once; after that, Claude handles
the details.*

The site is live at **https://doctorilana.com**, it costs $0/month to host, and
nothing you do while learning can permanently break it — every change ever made is
saved and reversible.

---

## The five pieces, in plain English

**GitHub** — an online filing cabinet for the site's files, with a complete history
of every version of every file. The site lives at
github.com/doctorilana/doctorilana-site. Because the full history is kept, any change
can be undone. Login: the "Ilana Github" item in the shared 1Password vault (it has a
passkey — 1Password will offer to sign in automatically).

**Netlify** — the company that takes the files from GitHub and puts them on the
internet. It watches the filing cabinet: about a minute after any change lands in
GitHub, the live site updates automatically. You never operate Netlify directly; it
just works. (Login is in 1Password if you ever need to look at it.)

**GoDaddy** — where the domain name `doctorilana.com` is registered, and where the
"address book" (DNS) that points the name at Netlify lives. The only recurring bill
is the annual domain renewal here. Don't change anything at GoDaddy without checking
with Danny — DNS mistakes are the one thing that can take the site (or email) down.

**Flodesk** — Ilana's email-newsletter service. The signup forms on the site feed it,
and it automatically sends new subscribers the free cookbook. Important: it's ONE
Flodesk account serving TWO brands (the Open Wellness clinic and doctorilana.com),
and the account-wide branding belongs to the clinic. Claude knows the rules for
working around this — see `CLAUDE.md`.

**Claude Code** — the version of Claude you'll use to edit the site. The Claude
you've used is a chat window; Claude Code is Claude with hands: it runs on the Mac,
works inside the site's folder, edits the actual files, and publishes the changes.
You still just talk to it in plain English.

## How a change actually happens

You tell Claude what you want → Claude edits the files in the folder on your Mac →
Claude saves the change to GitHub with a plain-English note (this is called a
"commit" and "push" — you'll see those words go by) → Netlify notices and updates
the live site ~1 minute later. That's the whole pipeline. No build tools, no
publishing dashboard, no FTP.

## One-time setup (~20 minutes)

1. **Install Claude Code** on the Mac: download the Claude desktop app from
   claude.ai/download and sign in with your Claude account, or install the terminal
   version (instructions at docs.anthropic.com/claude-code). The desktop app is the
   gentler start.
2. **Have 1Password unlocked** — you'll need the "Ilana Github" login during setup.
3. **Paste this to Claude Code:**

   > Set this computer up following
   > https://github.com/doctorilana/doctorilana-site/blob/main/SETUP-NEW-COMPUTER.md

   Claude will walk through it with you: it gets the site's folder onto the Mac,
   connects it to GitHub using Ilana's account (a browser window will open — sign in
   with 1Password), and proves everything works by making a harmless test edit and
   watching it go live.
4. **Make one real edit.** Ask Claude for something small in your own words and watch
   it appear on doctorilana.com a minute later.

After setup, every session is just: open Claude Code in the site folder and say what
you want.

## Things to say to Claude (verbatim examples that work)

- "Add this episode to the podcasts page: [paste title + link]"
- "Add a testimonial — here's the quote…"
- "Reword the second paragraph on the About page to mention Ilana's new certification."
- "Show me the change before you publish it."
- "Explain what you just did."
- "Undo whatever we changed yesterday."
- "The site looks broken — roll back to the last good version."
- "What's on the open items list?" (Claude will read `OPEN-ITEMS.md` and catch you up.)

## The rules (Claude knows these too, but you should know they exist)

1. **Never describe Ilana as a "gastroenterologist"** anywhere on the site — she
   cannot legally use that title. Claude enforces the approved phrasings
   (see `CLAUDE.md`).
2. **The GitHub repo is public, on purpose** (Netlify's free plan requires it) —
   which is fine, because everything in it is the public website anyway. The
   corollary: **no passwords, no API keys, no private files ever go in the site
   folder.** They live in 1Password.
3. **Don't make it private.** If the repo is ever switched to private, publishing
   breaks. Leave that setting alone.
4. **Batch changes.** Each publish uses ~15 of Netlify's 300 free monthly credits
   (~20 publishes/month). Claude knows to group a session's edits into one publish
   rather than pushing after every tweak.
5. **DNS at GoDaddy and Flodesk's account-wide branding are "measure twice" zones** —
   loop in Danny before touching either.

## What's where

- `HANDOFF.md` — this file.
- `OWNERS-GUIDE.md` — Ilana's plain-English guide to the site.
- `OPEN-ITEMS.md` — the to-do list being handed over; start any work session by
  asking Claude about it.
- `CLAUDE.md` — instructions Claude reads automatically every session (site
  structure, conventions, the title rule, Flodesk details). You never need to read
  it, but it's why Claude "already knows" things.
- `SETUP-NEW-COMPUTER.md` — the setup runbook from step 3 above.

## Files Danny is sending separately (keep them somewhere safe, NOT in the site folder)

- `Rebuild your microbiome cookbook.pdf` — the original full-quality cookbook
  (the site serves a compressed copy).
- `New Doctor ilana logo.png` — the doctor-ilana brand logo (used in Flodesk emails).
- Headshots (Open Wellness portrait + two stylized versions).
- Open Wellness clinic logo.

## If something goes wrong

- **Site looks wrong:** tell Claude to roll back. Real command, works.
- **Site is down:** almost certainly Netlify (rare) — ask Claude to investigate, or
  check netlifystatus.com.
- **Locked out:** everything is in the shared 1Password vault: GitHub, Netlify,
  GoDaddy, Flodesk.
- **Stuck:** call Danny. He keeps a backup GitHub login (`robotdanny`) and can fix
  anything remotely.
