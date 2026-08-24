# Desiree Fisker

Personal academic website built with [al-folio](https://github.com/alshedivat/al-folio) and hosted with GitHub Pages.

## Local Preview

This repo is configured for the Docker workflow used by al-folio:

```bash
docker compose up
```

Then open <http://localhost:8080>.

## GitHub Pages

Create a public repository named `desifisker.github.io`, push this source to `main`, and set GitHub Pages to deploy from the `gh-pages` branch. The included GitHub Actions workflow builds the site and publishes `_site` to that branch.

Key files to personalize:

- `_config.yml` for site title, URL, author name, and feature toggles.
- `_pages/about.md` for the home-page bio and profile details.
- `_data/socials.yml` for email, GitHub, ORCID, Scholar, LinkedIn, and other links.
- `_bibliography/papers.bib` for publications.
- `_data/cv.yml` for the rendered CV page.
