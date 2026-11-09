# Agent instructions — Ysabel Busteed portfolio

This is a small static portfolio for a non-technical owner. Treat plain-English requests as content/design changes to be made directly in this repository.

`CLAUDE.md` is intentionally only an entry point to this document. Keep this file as the single source of truth for agent instructions.

## Working model

- This is a static HTML/CSS/JavaScript site. There is no package manager, build step, test suite, database, secrets, or environment configuration in the repository.
- The existing GitHub-to-Amplify connection is already set up. Do not create, modify, or deploy Amplify/AWS infrastructure unless the owner explicitly asks.
- Make the smallest change that fulfils the request. Preserve the existing visual language and responsive behaviour unless the request calls for a redesign.
- Do not introduce a framework, build tooling, dependencies, analytics, or a CMS for ordinary portfolio changes.

## Required workflow

1. Read `README.md` before making a content or structural change. It documents every page, asset, and shared behaviour.
2. Inspect the relevant HTML page(s), `styles.css`, `site.js`, and media files before editing.
3. Make the requested change directly on the current branch. Do not create or switch branches.
4. Preview the site before pushing. Use the available Claude Code preview, or run `python3 -m http.server 8000` from the repository and visit `http://localhost:8000`.
5. Check the affected page at desktop and mobile widths. Confirm images load, links work, text is correct, and the layout has not regressed.
6. Clearly report the files changed and the preview/checks completed. Wait for approval if the owner has asked to review the preview.
7. When the owner asks to push (or has already approved the change and asked for the whole change-and-push workflow), commit the relevant files with a concise message and push directly to the current connected branch.

## Git rules

- Work directly on the existing branch; do not create branches.
- Do not create pull requests, draft pull requests, review requests, or branch-protection rules.
- Do not wait for CI, request approvals, configure security scanners, or add Trivy/other checks.
- Do not force-push, rewrite history, reset, or discard unrelated user changes.
- Before committing, inspect `git status` and commit only the files belonging to the approved request.
- A direct `git push` is the expected publishing handoff after the owner approves it. Do not require an additional release process.

## Site-specific editing rules

- Keep the header, footer, skip link, stylesheet link, and deferred `site.js` tag on every HTML page.
- Keep `styles.css` and `site.js` in the repository root and update references everywhere if an explicit request ever requires moving them.
- Add new media under `images/`, use lowercase hyphenated filenames, and update every relevant `src`, `alt`, and Open Graph image reference.
- For a new project: create a project page from an existing one; add its card to `index.html`; set correct `data-cats`; connect previous/next links; set title, description, canonical URL, Open Graph metadata, and image alternatives.
- Keep the home filter values aligned with their buttons: `all`, `campaigns`, `branding`, `social`, `ads`, `print`, and `events`.
- Preserve accessibility: meaningful image `alt` text, semantic headings, keyboard-accessible controls, focus styles, and reduced-motion support.
- Do not silently delete portfolio work or replace high-resolution assets with lower-quality versions. Ask if the target media or desired crop is unclear.

## Boundaries

- Do not change DNS, domains, GitHub repository settings, Amplify settings, access controls, billing, or external links unless explicitly requested.
- Do not expose, log, or add credentials or tokens to this repository.
- Do not modify unrelated files. If unrelated changes are already present, preserve them and mention them before committing.
