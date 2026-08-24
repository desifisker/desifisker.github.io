---
layout: page
title: "Personal Season Edits"
permalink: /projects/photography/personal-season-edits/
description: "Short skydiving season edits and the stories behind them."
nav: false
cover: /assets/img/photography/header/pic2.jpg
og_image: /assets/img/photography/header/pic2.jpg
---

{% assign season_edits = site.data.season_edits %}

<script>
  (() => {
    const photographyPath = "{{ '/projects/photography/' | relative_url }}";
    const modeKey = "desireePhotographyNavMode";
    let referrerPath = "";

    try {
      if (document.referrer) {
        const referrer = new URL(document.referrer);
        if (referrer.origin === window.location.origin) {
          referrerPath = referrer.pathname;
        }
      }
    } catch (error) {
      referrerPath = "";
    }

    const cameFromPhotography = referrerPath.startsWith(photographyPath);
    const cameFromAcademicSite = referrerPath && !cameFromPhotography;

    if (cameFromAcademicSite) {
      sessionStorage.setItem(modeKey, "full");
    } else if (!cameFromPhotography) {
      sessionStorage.setItem(modeKey, "compact");
    }

    if ((sessionStorage.getItem(modeKey) || "compact") === "compact") {
      document.body.classList.add("photography-section");
    }
  })();
</script>

<style>
  body {
    overflow-x: hidden;
  }

  .post-header {
    display: none;
  }

  .season-page {
    --season-ink: #111111;
    --season-muted: #6d6862;
    --season-line: rgba(17, 17, 17, 0.14);
    --season-warm: #f7f2ea;
    margin-top: -0.75rem;
  }

  html[data-theme="dark"] .season-page {
    --season-ink: #f5f1ea;
    --season-muted: #c8c0b8;
    --season-line: rgba(255, 255, 255, 0.2);
    --season-warm: #201f1d;
  }

  .season-hero {
    min-height: clamp(340px, 56vh, 600px);
    display: grid;
    align-items: end;
    padding: clamp(2rem, 5vw, 4.5rem);
    margin: 0 calc(50% - 50vw) 3rem;
    background-image: linear-gradient(180deg, rgba(0, 0, 0, 0.08), rgba(0, 0, 0, 0.7)), url("{{ page.cover | relative_url }}");
    background-position: center;
    background-size: cover;
    color: #ffffff;
  }

  .season-back,
  .season-kicker,
  .season-entry__meta {
    text-transform: uppercase;
    font-size: 0.72rem;
    letter-spacing: 0;
    font-weight: 700;
  }

  .season-back {
    color: rgba(255, 255, 255, 0.84);
    text-decoration: none;
  }

  .season-back:hover {
    color: #ffffff;
  }

  .season-hero h2 {
    max-width: 800px;
    margin: 0.75rem 0 0.7rem;
    font-size: clamp(2.15rem, 6vw, 5rem);
    line-height: 1;
    color: #ffffff;
  }

  .season-hero p {
    max-width: 620px;
    color: rgba(255, 255, 255, 0.88);
    font-size: clamp(1rem, 2vw, 1.16rem);
  }

  .season-intro {
    max-width: 820px;
    margin-bottom: 2.5rem;
  }

  .season-intro p {
    color: var(--season-muted);
    font-size: 1.03rem;
  }

  .season-grid {
    display: grid;
    gap: 1.5rem;
  }

  .season-entry {
    border-top: 1px solid var(--season-line);
    display: grid;
    grid-template-columns: minmax(0, 1.15fr) minmax(240px, 0.85fr);
    gap: clamp(1rem, 3vw, 2rem);
    padding-top: 1.5rem;
  }

  .season-entry h3 {
    margin-top: 0.35rem;
    color: var(--season-ink);
  }

  .season-entry p {
    color: var(--season-muted);
  }

  .season-entry__meta {
    color: var(--global-theme-color);
    margin-bottom: 0;
  }

  .season-entry__details {
    border-top: 1px solid var(--season-line);
    padding-top: 0.8rem;
  }

  .season-entry__details div {
    display: flex;
    justify-content: space-between;
    gap: 1rem;
    padding: 0.28rem 0;
    color: var(--season-muted);
  }

  .season-entry__details strong {
    color: var(--season-ink);
  }

  .season-video,
  .season-placeholder {
    aspect-ratio: 16 / 9;
    border-radius: 8px;
    overflow: hidden;
    background: var(--season-warm);
    border: 1px solid var(--season-line);
  }

  .season-video iframe,
  .season-video video {
    width: 100%;
    height: 100%;
    display: block;
    border: 0;
  }

  .season-placeholder {
    display: grid;
    place-items: center;
    padding: 1.5rem;
    color: var(--season-muted);
    text-align: center;
  }

  .season-empty {
    background: var(--season-warm);
    border: 1px solid var(--season-line);
    border-radius: 8px;
    padding: clamp(1.25rem, 3vw, 2rem);
    color: var(--season-muted);
  }

  @media (max-width: 760px) {
    .season-hero {
      min-height: 430px;
      padding: 2rem 1.25rem;
    }

    .season-entry {
      grid-template-columns: 1fr;
    }
  }
</style>

<div class="season-page">
  <section class="season-hero" aria-label="Personal season edits header">
    <div>
      <a class="season-back" href="{{ '/projects/photography/' | relative_url }}">Photography</a>
      <h2>Personal Season Edits</h2>
      <p>Short skydiving edits from different seasons, with notes on where they happened and what each one meant.</p>
    </div>
  </section>

  <section class="season-intro">
    <p class="season-kicker">season videos</p>
    <p>
      A home for 2-3 minute edits from different skydiving seasons: the DZs, jumps, friends, goals, ratings, camera experiments, and milestones
      that made each stretch of the sport feel special.
    </p>
  </section>

{% if season_edits.size > 0 %}
<section class="season-grid" aria-label="Personal skydiving season edit videos">
{% for edit in season_edits %}
<article class="season-entry">
<div>
<p class="season-entry__meta">{{ edit.season | default: "Season edit" }}</p>
<h3>{{ edit.title }}</h3>
<p>{{ edit.description }}</p>
<div class="season-entry__details" aria-label="{{ edit.title | escape }} details">
{% if edit.location %}
<div><strong>Location</strong><span>{{ edit.location }}</span></div>
{% endif %}
{% if edit.achievement %}
<div><strong>Highlights</strong><span>{{ edit.achievement }}</span></div>
{% endif %}
</div>
</div>
{% if edit.youtube %}
<div class="season-video">
<iframe
src="{{ edit.youtube }}"
title="{{ edit.title | escape }}"
loading="lazy"
allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
allowfullscreen
></iframe>
</div>
{% elsif edit.video %}
<div class="season-video">
{% if edit.poster %}
<video controls preload="metadata" poster="{{ edit.poster | relative_url }}">
{% else %}
<video controls preload="metadata">
{% endif %}
<source src="{{ edit.video | relative_url }}" type="video/mp4">
</video>
</div>
{% else %}
<div class="season-placeholder">{{ edit.placeholder | default: "Video coming soon." }}</div>
{% endif %}
</article>
{% endfor %}
</section>
{% else %}
<div class="season-empty">Personal season edits will appear here once the videos are ready to share.</div>
{% endif %}
</div>
