# Setting up a new computer to edit this site

*This document is written for Claude. Human: open Claude Code, point it at this file
(or paste it), and say "set this computer up following these instructions."*

## Goal

A local clone of `doctorilana/doctorilana-site` that can push to `main`. A push to
`main` auto-deploys to https://doctorilana.com via Netlify (~1 minute). That's the
entire pipeline — there is no build step, no staging, no other moving parts.

## Steps

1. **Check git exists**: `git --version`. On a fresh Mac this triggers the Xcode
   Command Line Tools install prompt — let the human click through it (~5 min).

2. **GitHub access.** Preferred: the human has their own GitHub account, added as a
   collaborator on `doctorilana/doctorilana-site` (repo Settings → Collaborators,
   done by the `doctorilana` account — credentials in the family 1Password).
   Then authenticate this machine, whichever is easiest:
   - `gh auth login` (install GitHub CLI via Homebrew if present; web-browser flow), or
   - SSH key: `ssh-keygen -t ed25519`, add the public key at github.com → Settings →
     SSH keys, clone via SSH remote.
   The repo is public, so cloning works without auth — only pushing needs it.

3. **Clone** into Documents:
   `git clone https://github.com/doctorilana/doctorilana-site.git ~/Documents/doctorilana-site`
   (or SSH URL if using keys).

4. **Set git identity** (repo-local is fine):
   `git config user.name "<human's name>"` and `git config user.email "<their email>"`.

5. **Read `CLAUDE.md`** in the repo root — it has the site structure, editing
   conventions, and a non-negotiable title-compliance rule.

6. **Verification edit** (do this — it proves the whole pipeline):
   - Make a trivial change (e.g., fix nothing — add a blank line to this file).
   - `git add -A && git commit -m "Test edit from new computer" && git push`
   - Within ~90 seconds, confirm the deploy: `curl -sI https://doctorilana.com/ | head -1`
     should be HTTP/2 200, and the Netlify Deploys page (login in 1Password) shows the
     new commit as Published. If the deploy fails with a "contributor" error, the repo
     was made private — it must stay public on Netlify's free tier.

7. Tell the human they're done, and that from now on they just open Claude Code in
   `~/Documents/doctorilana-site` and describe changes in plain English.

## Ongoing editing rules (also in CLAUDE.md)

- Push directly to `main` for routine edits; write plain-English commit messages.
- NEVER call Ilana a "gastroenterologist" — see CLAUDE.md for approved phrasing.
- Never commit secrets/API keys. Flowdesk embed snippets are fine (public by design).
- Header/footer are duplicated per page — apply nav/footer changes to ALL html files,
  including `conditions/*`.
