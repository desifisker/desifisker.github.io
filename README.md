# Desiree Fisker

Personal academic website built with [al-folio](https://github.com/alshedivat/al-folio) and hosted with GitHub Pages.

- Live website: <https://desifisker.github.io/>
- GitHub repository: <https://github.com/desifisker/desifisker.github.io>
- Local folder on this computer: `/home/desiree/Personal/website`

## What Stays Live

The live website is served by GitHub Pages, not by VS Code or Docker on this computer.

That means:

- Closing VS Code does not take the website offline.
- Stopping Docker does not take the website offline.
- Turning off this computer does not take the website offline.
- The live site keeps serving the most recent successfully deployed version from GitHub Pages.

Docker is only for previewing edits on your own computer before publishing them.

## Coming Back Months Later

Use this section when you have forgotten everything. Start here.

### 1. Open the Repo

Open a terminal and go to the website folder:

```bash
cd /home/desiree/Personal/website
```

Open the folder in VS Code:

```bash
code .
```

If `code .` does not work, open VS Code manually and choose:

```text
File -> Open Folder -> /home/desiree/Personal/website
```

### 2. Check the Current State

Before editing, see whether there are local changes:

```bash
git status
```

If the working tree is clean, update the folder from GitHub:

```bash
git pull origin main
```

If `git status` shows files you do not recognize, stop and inspect them before pulling or committing.

### 3. Start a Local Preview

Start the local website server:

```bash
docker compose up
```

Then open:

```text
http://localhost:8080
```

Leave that terminal open while editing. Most page/content edits will refresh automatically.

To stop the preview:

```text
Ctrl+C
```

If Docker was left running in the background, stop it with:

```bash
docker compose down
```

### 4. Edit Files

Most website edits are plain Markdown, YAML, BibTeX, or image files. Do not edit `_site/`; that folder is generated output.

Common files:

- `_pages/about.md` - home/about page text and headshot settings.
- `assets/img/desiree-fisker-headshot.jpg` - current about-page headshot.
- `_data/socials.yml` - email, GitHub, LinkedIn, ORCID, Google Scholar, and other profile links.
- `_data/cv.yml` - rendered CV content.
- `_bibliography/papers.bib` - publications page entries.
- `_projects/*.md` - project pages.
- `_pages/blog.md` and `_posts/` - blog listing and blog posts. A few default al-folio sample posts are kept as examples.
- `_news/*.md` - news items on the home page.
- `_pages/cv.md` - CV page settings. `cv_pdf:` is intentionally blank so the CV tab renders as webpage sections.
- `_pages/dropdown.md` - the `extras` dropdown in the top navigation.
- `_pages/repositories.md` - visible top navigation page for selected GitHub repositories.
- `_pages/teaching.md` - currently set to `nav: false`, so it is hidden from the top navigation.

Private/source documents that should not be published:

- `_private_documents/`
- `Final_Edited_For_Website/`

Those folders are intentionally ignored by git.

### 5. Preview and Check

After editing, refresh <http://localhost:8080> and click through the pages you changed.

Useful checks:

```bash
git status
git diff --check
```

For a full Jekyll build check, run this while Docker is already running:

```bash
docker compose exec jekyll sh -lc 'bundle exec jekyll build'
```

If you changed formatting-sensitive files and have Node installed, run:

```bash
npm run lint:prettier
```

If local `npm` is not installed, GitHub Actions will still run the Prettier check after you push.

### 6. Publish Changes

Stage the files you edited:

```bash
git add path/to/file1 path/to/file2
```

Example:

```bash
git add _data/cv.yml _pages/about.md assets/img/desiree-fisker-headshot.jpg
```

Commit:

```bash
git commit -m "Describe the website update"
```

Push:

```bash
git push origin main
```

GitHub Actions will build and deploy the site automatically. After a few minutes, check:

- <https://github.com/desifisker/desifisker.github.io/actions>
- <https://desifisker.github.io/>

## Editing Specific Sections

### About Page

Edit:

```text
_pages/about.md
```

To change the headshot, put the new image in:

```text
assets/img/
```

Then update this line in `_pages/about.md`:

```yaml
image: desiree-fisker-headshot.jpg
```

### CV Page

Edit:

```text
_data/cv.yml
```

The CV page is rendered from this YAML file. A public CV PDF is also linked from the social icons at the bottom of the About page.

Keep this blank in `_pages/cv.md`:

```yaml
cv_pdf:
```

The About-page CV icon is controlled in `_data/socials.yml`:

```yaml
cv_pdf: /assets/pdf/desiree-fisker-cv.pdf
```

### Publications

Edit:

```text
_bibliography/papers.bib
```

Current publication setup:

- IROS paper has a local PDF in `assets/pdf/fisker-uav-see-ugv-do-iros-2025.pdf`.
- MASc thesis links to the public Scholaris page instead of publishing a local thesis PDF.
- Publication preview images live in `assets/img/publication_preview/`.
- Publication videos live in `assets/video/`. Keep individual files under GitHub's 100 MB limit.

### Projects

Add or edit Markdown files in:

```text
_projects/
```

Each project page starts with front matter like:

```yaml
---
layout: page
title: Project Title
description: Short one-line description.
importance: 2
category: research
permalink: /projects/project-slug/
---
```

Lower `importance` values appear earlier.

### Photography Landing Page

Edit:

```text
_projects/photography.md
```

The rotating header images are controlled by this front matter:

```yaml
hero_images:
  - image: /assets/img/photography/events/dropout-august-2026/cover.jpg
    alt: DropOut event skydiving scene
```

To choose different rotating header photos:

1. Put the images somewhere under `assets/img/photography/events/`.
2. Add or replace entries under `hero_images`.
3. Keep the paths starting with `/assets/...`.
4. Add useful `alt` text for each image.

### Photography Event Galleries

The current DropOut event gallery is:

```text
_pages/photography/dropout-august-2026.md
```

Its photos are in:

```text
assets/img/photography/events/dropout-august-2026/
```

The gallery page automatically displays `.jpg` files in that folder except `cover.jpg`.

The photography landing page gets its event cards from:

```text
_data/photo_events.yml
```

To add a new event gallery:

1. Make a new image folder, for example:

   ```text
   assets/img/photography/events/my-event-2027/
   ```

2. Add `cover.jpg` and the event photos to that folder.
3. Copy `_pages/photography/dropout-august-2026.md` to a new file, for example:

   ```text
   _pages/photography/my-event-2027.md
   ```

4. Update the new page's `title`, `permalink`, `description`, `event_date_label`, `event_location`, `event_slug`, `event_cover`,
   `gallery_dir`, and `og_image`.
5. Add a matching entry to `_data/photo_events.yml`.

## Navigation

The current top navigation is:

```text
about, blog, publications, projects, CV, repositories, extras
```

The `extras` dropdown is controlled by:

```text
_pages/dropdown.md
```

The repositories tab is populated from:

```text
_data/repositories.yml
```

To hide a page from the top navigation, set:

```yaml
nav: false
```

To show it, set:

```yaml
nav: true
```

## Search Engines

The site is public and set up for crawling:

- `robots.txt` allows crawlers.
- `robots.txt` points to `https://desifisker.github.io/sitemap.xml`.
- `jekyll-sitemap` generates the sitemap.

Google indexing is not instant and cannot be guaranteed by the repo alone. To help Google find updates faster, use Google Search Console and submit:

```text
https://desifisker.github.io/sitemap.xml
```

You can check whether Google has indexed the site by searching:

```text
site:desifisker.github.io Desiree Fisker
```

## Working With AI Agents

This repo includes instructions for multiple coding agents.

Before asking an AI agent to edit the site, tell it:

```text
Please read AGENTS.md first and follow the al-folio v1 instructions in this repo.
```

Important agent files:

- `AGENTS.md` - shared instructions for Codex and other agents.
- `CLAUDE.md` - Claude Code entry point; it imports `AGENTS.md`.
- `.github/copilot-instructions.md` - GitHub Copilot coding agent instructions.
- `.agents/skills/al-folio-bootstrap/SKILL.md` - setup/customization workflow.
- `.agents/skills/al-folio-v1-migration/SKILL.md` - migration workflow.
- `.codex/skills` and `.claude/skills` - symlinks to the shared `.agents/skills` folder.

The most important rule: keep normal website content in `_pages`, `_projects`, `_data`, `_bibliography`, `_posts`, `_news`, and `assets`.
Avoid copying al-folio runtime internals into this repo unless you intentionally want to maintain a local override.

## Troubleshooting

### Port 8080 Is Already in Use

Something else is already using the preview port. Stop any old Docker preview:

```bash
docker compose down
```

Then try again:

```bash
docker compose up
```

### Docker Build or Preview Is Acting Weird

Try:

```bash
docker compose down
docker compose up --build
```

### The Live Site Did Not Change After Pushing

Check GitHub Actions:

```text
https://github.com/desifisker/desifisker.github.io/actions
```

If the deploy failed, open the failed run and read the red error section. The live site usually keeps serving the last successful deployment
until a new deployment succeeds.

### I Accidentally Edited `_site`

Do not commit `_site`. It is generated output. Move your real changes into the source files listed above, then rebuild.

### I Want to Publish a PDF

Put public PDFs in:

```text
assets/pdf/
```

Do not put private CV/thesis/source documents there unless you want them publicly downloadable.

## Current Published Files to Remember

- Public IROS paper PDF: `assets/pdf/fisker-uav-see-ugv-do-iros-2025.pdf`
- Public CV PDF: `assets/pdf/desiree-fisker-cv.pdf`
- Public thesis link: <https://utoronto.scholaris.ca/items/f8efadbf-afb8-46e9-97be-72551ae875c0>
- About-page headshot: `assets/img/desiree-fisker-headshot.jpg`
- Publication previews: `assets/img/publication_preview/`
- Publication videos: `assets/video/`
- Selected repository list: `_data/repositories.yml`
- Rendered CV source: `_data/cv.yml`
- Photography landing page: `_projects/photography.md`
- DropOut gallery page: `_pages/photography/dropout-august-2026.md`
