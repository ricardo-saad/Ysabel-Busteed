# Ysabel Busteed portfolio

This is a static portfolio website for Ysabel Busteed. It has no framework, package manager, build command, database, or environment variables: the browser reads the HTML, CSS, JavaScript, images, and video directly. That keeps it ideal for small content changes made through Claude Code and previewed before a Git push.

The live site's source of truth is this repository. `index.html` is the home page and each project has its own HTML page. All pages use the same `styles.css` and `site.js` files.

## Repository guidance files

| File | Purpose |
| --- | --- |
| `README.md` | This human-friendly site map, editing guide, and media inventory. |
| `AGENTS.md` | Canonical instructions for coding agents working in this repository. It defines the direct-edit, preview, commit, and push workflow. |
| `CLAUDE.md` | Claude Code entry point. It points to `AGENTS.md`, so the rules live in one place. |

## Everyday editing

For most requests, describe the desired outcome to Claude Code in plain English, for example:

> Update the Meats & Cuts project description, replace its Saudi launch image, keep the current layout, update the image alt text and social-sharing image if needed, then show me the changed files.

Before pushing, preview the changes and check:

1. The desktop and mobile layouts look right.
2. Every project-card link opens the intended page.
3. New images load and have useful alt text.
4. The page title, description, and social-sharing image match the new content.

Useful guardrails:

- Keep file names lowercase, with hyphens rather than spaces.
- Do not move or rename `styles.css` or `site.js` without updating every HTML page.
- Add images to `images/` and keep the source filename and the HTML `src` in sync.
- Preserve the shared header, footer, skip link, stylesheet link, and deferred script tag when editing a page.
- Use `target="_blank" rel="noopener"` together on links that open another website.
- The URLs in canonical and Open Graph meta tags are currently written for `https://ysabelbusteed.com/`. Update the domain everywhere if the site moves.

To run a simple local preview without installing anything, from this folder run `python3 -m http.server 8000`, then visit `http://localhost:8000`. Stop it with `Ctrl+C`.

## Site map

| File | Purpose | Notes |
| --- | --- | --- |
| `index.html` | Home / work index | Hero, category filters, and 15 project cards. This is the main place to add, reorder, remove, or recategorise projects. |
| `about.html` | Biography and credentials | Intro, services, experience, skills/toolkit, and education. |
| `contact.html` | Contact page | Email link, copy-email button, CV link, and work link. |
| `404.html` | Missing-page fallback | Shows a short return-to-work message; configure the host to serve it as the 404 page if that is not already done. |
| `beauty-candy.html` | Beauty & Candy Week case study | Event branding for Galeries Lafayette × Museum of Candy; includes a passport flipbook link. |
| `head-of-the-class.html` | Head of the Class case study | Galeries Lafayette back-to-school campaign; includes the only project-page video. |
| `christmas.html` | Christmas Campaign case study | Galeries Lafayette festive menswear campaign. |
| `gl-panels.html` | Galeries Lafayette panels case study | Dubai Mall exterior / large-format panel design. |
| `fashion-forever.html` | Fashion Forever case study | Galeries Lafayette campaign production and key visuals. |
| `mc-diner.html` | M&C Diner case study | Brand identity, packaging, menus, illustration, and social work. |
| `blu.html` | Blu case study | Café/barber-shop logo and packaging. |
| `sumwon.html` | Sumwon case study | Menswear multibuy banner-ad formats. |
| `missguided.html` | Missguided case study | Womenswear multibuy banner-ad formats. |
| `mode-dubai.html` | Mode Dubai case study | Fashion-event content and social media. |
| `brothhaus.html` | Brothhaus case study | Restaurant production and social media. |
| `terra-solis.html` | Terra Solis case study | Wayfinding, map, signage, and poster work. |
| `meats-cuts.html` | Meats & Cuts case study | Rebrand, marketing, and Dubai/Saudi social content. |
| `the-drop.html` | The Drop case study | Galeries Lafayette sale campaign identity and social ads. |
| `styles.css` | Shared visual system and responsive layout | Controls colours, typography, navigation, cards, project galleries, lightbox, and accessibility/motion preferences. |
| `site.js` | Shared browser behaviour | Adds crayon strokes, home filtering, reduced-motion behaviour, project lightbox, scroll reset, and copy-email interaction. |
| `favicon.svg` | Browser tab icon | A vector icon referenced by every HTML page. |

## How pages are put together

Every page has the same basic shell: SEO metadata in `<head>`, a sticky navigation bar, a `<main>` section, footer contact details, `styles.css`, and `site.js` loaded with `defer`.

Project pages are intentionally consistent. Each contains:

1. The project title and discipline.
2. A left-hand summary with category, description, and client fact.
3. A media gallery. Still images are buttons so the shared lightbox can enlarge them; video is displayed directly.
4. Previous/next project links.
5. A lightbox dialog with close, previous, and next controls.

When creating a new project, copy an existing project page, replace every piece of project-specific content, add its card to `index.html`, set its `data-cats` to the right filter categories, and connect it into the previous/next links. Also add a suitable `og:image` (a full URL under `/images/`) and ensure each media item's `alt` text describes what is visible.

### Home-page filters

The buttons on `index.html` filter cards using the `data-cats` attribute. Their values must match the chip's `data-cat` value exactly. Current categories are `all`, `campaigns`, `branding`, `social`, `ads`, `print`, and `events`. More than one category may be separated with spaces, for example `data-cats="social branding"`.

`site.js` also writes the selected category into the URL hash (such as `#branding`), so that filtered view can be linked to directly.

### Shared design and interaction files

`styles.css` is organised in sections: colour/font variables and global rules; navigation; hero; filters; home grid; project pages; about; contact; lightbox; skills; and the animated crayon/card refinements. It supports automatic dark mode and respects `prefers-reduced-motion`. Prefer changing an existing CSS variable or rule rather than adding page-specific inline styles, unless an image needs a unique aspect ratio or crop.

`site.js` is plain, dependency-free JavaScript. It:

- draws decorative SVG crayon marks around selected elements;
- filters home-page projects and restores filters from the URL hash;
- pauses autoplay videos for visitors who prefer reduced motion;
- resets project-page scroll position when appropriate;
- powers the image lightbox, including keyboard left/right navigation; and
- copies the contact email, with a text-selection fallback when clipboard access is unavailable.

## Media inventory

All supplied media lives in `images/`. The table documents every asset and where it is used. Images marked **card** also appear on the home-page work grid.

| Asset | Content / usage |
| --- | --- |
| `bc-logo.jpg` | Beauty & Candy logo, colourways, and palette. |
| `bc-passport-cover.jpg` | Beauty & Candy passport cover; **card** image. |
| `bc-invite.jpg` | Beauty & Candy press-day invitation. |
| `bc-passport-spreads.jpg` | Beauty & Candy passport cover and inside spreads. |
| `bc-tickets.jpg` | Beauty & Candy ticket fronts and backs. |
| `bc-bag-1.jpg` | Beauty & Candy tote bag in use. |
| `bc-bag-2.jpg` | Beauty & Candy tote bag, front. |
| `bc-bag-3.jpg` | Beauty & Candy tote bag, back. |
| `bc-masterclass.jpg` | Beauty & Candy masterclass announcements. |
| `blu-packaging.jpg` | Blu packaging system. |
| `blu-cup.jpg` | Blu logo on cup; **card** image. |
| `brothhaus-grid.jpg` | Brothhaus Instagram grid; **card** image. |
| `drop-logo.jpg` | The Drop campaign logo. |
| `drop-sky-1.jpg` | The Drop “Just landed. Just reduced.” story ad. |
| `drop-sky-2.jpg` | The Drop “Just landed. Just reduced.” story ad; **card** image. |
| `drop-dune-1.jpg` | The Drop “Glide into new season savings” story ad. |
| `drop-dune-2.jpg` | The Drop “Glide into new season savings” story ad. |
| `drop-drive-1.jpg` | The Drop “Full speed into the savings” story ad. |
| `drop-drive-2.jpg` | The Drop “Full speed into the savings” story ad. |
| `ff-1.jpg` | Fashion Forever, look 1. |
| `ff-2.jpg` | Fashion Forever, look 2. |
| `ff-3.jpg` | Fashion Forever, look 3. |
| `gl-campaign-hero.jpg` | Fashion Forever campaign key image; **card** image. |
| `gl-panels-1.jpg` | Galeries Lafayette Dubai Mall exterior panels. |
| `gl-panels-2.jpg` | Galeries Lafayette “The French Department Store” billboard; **card** image. |
| `hotc-key-anim.mp4` | Head of the Class looping animated key visual; **card** video. |
| `hotc-key-anim.jpg` | Poster/first-frame fallback for the Head of the Class video. |
| `hotc-key-1.jpg` | Head of the Class static key visual. |
| `hotc-1.jpg` | Head of the Class campaign image. |
| `hotc-2.jpg` | Head of the Class tote bag. |
| `hotc-3.jpg` | Head of the Class campaign image. |
| `mc-sign.jpg` | M&C Diner signage; **card** image. |
| `mc-packaging.jpg` | M&C Diner packaging. |
| `mc-menu.jpg` | M&C Diner menus and bags. |
| `mc-icons.jpg` | M&C Diner illustration set. |
| `mc-social-1.jpg` | M&C Diner social creative. |
| `mc-social-2.jpg` | M&C Diner social creative. |
| `meats-grid.jpg` | Meats & Cuts Dubai Instagram grid; **card** image. |
| `meats-saudi.jpg` | Meats & Cuts Saudi launch content. |
| `missguided-homepage.jpg` | Missguided homepage banner placement. |
| `missguided-square.jpg` | Missguided square (1:1) banner. |
| `missguided-portrait.jpg` | Missguided portrait (4:5) banner. |
| `missguided-landscape.jpg` | Missguided landscape (3:2) banner. |
| `missguided-main.jpg` | Missguided card/preview image. |
| `mode-grid.jpg` | Mode Dubai Instagram grid; **card** image. |
| `sumwon-homepage.jpg` | Sumwon homepage banner placement. |
| `sumwon-square.jpg` | Sumwon square (1:1) banner. |
| `sumwon-portrait.jpg` | Sumwon portrait (4:5) banner. |
| `sumwon-landscape.jpg` | Sumwon landscape (3:2) banner. |
| `sumwon-main.jpg` | Sumwon card/preview image. |
| `terra-map.jpg` | Terra Solis venue map and folded map card. |
| `terra-poster.jpg` | Terra Solis season poster; **card** image. |
| `xmas-1.jpg` | Christmas Campaign image; **card** image. |
| `xmas-2.jpg` | Christmas Campaign image. |
| `xmas-3.jpg` | Christmas Campaign image. |

## SEO, accessibility, and external links

Each page has a title, meta description, canonical URL, Open Graph basics, Twitter-card declaration, viewport setting, and favicon. Project pages also set an Open Graph image. Keep those in step with the visible project content when editing.

The site includes a skip-to-content link, semantic headings, descriptive image alternatives, visible keyboard focus, labelled navigation, and a native `<dialog>` for the lightbox. Do not remove these when simplifying a page. Decorative elements use `aria-hidden` where appropriate.

External destinations currently include the Canva CV and, on Beauty & Candy, a FlipHTML5 passport. Their links are deliberately opened in a new tab. Verify them after changing or republishing them.

## Deployment and Git handoff

There is no repository-side deployment configuration in this checkout. The site is expected to be published by the existing GitHub-to-Amplify connection: ask Claude Code to make the requested change, inspect the preview, then ask it to commit and push. The Amplify pipeline should build/deploy the static files as configured outside this repository.

Suggested final prompt after approving a preview:

> Commit only the files for this approved portfolio change with a clear message, push them to the connected branch, and show me the commit hash and changed-file summary.

Because there are no automated checks here, the visual preview and the short manual checklist above are the release check. Avoid manually editing generated content in Amplify; make changes in Git so the history remains recoverable.
