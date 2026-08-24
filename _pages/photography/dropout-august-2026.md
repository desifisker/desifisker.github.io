---
layout: page
title: "DropOut, August 2026"
permalink: /projects/photography/dropout-august-2026/
description: "A skydiving event gallery from DropOut, August 12-20, 2026."
nav: false
event_date_label: "August 12-20, 2026"
event_location: "Parachute Montreal"
event_slug: dropout-august-2026
event_cover: /assets/img/photography/events/dropout-august-2026/cover.jpg
gallery_dir: /assets/img/photography/events/dropout-august-2026/
og_image: /assets/img/photography/events/dropout-august-2026/cover.jpg
images:
  lightbox2: true
---

{% assign gallery_files = site.static_files | where_exp: "file", "file.path contains page.gallery_dir and file.path contains '.jpg'" | sort: "path" %}
{% assign photo_count = gallery_files | size | minus: 1 %}

<style>
  body {
    overflow-x: hidden;
  }

  .post-header {
    display: none;
  }

  .event-page {
    --event-ink: #111111;
    --event-muted: #6d6862;
    --event-line: rgba(17, 17, 17, 0.14);
    margin-top: -0.75rem;
  }

  html[data-theme="dark"] .event-page {
    --event-ink: #f5f1ea;
    --event-muted: #c8c0b8;
    --event-line: rgba(255, 255, 255, 0.2);
  }

  .event-hero {
    min-height: clamp(360px, 62vh, 640px);
    display: grid;
    align-items: end;
    padding: clamp(2rem, 5vw, 4.5rem);
    margin: 0 calc(50% - 50vw) 3rem;
    background-image: linear-gradient(180deg, rgba(0, 0, 0, 0.08), rgba(0, 0, 0, 0.78)), url("{{ page.event_cover | relative_url }}");
    background-position: center;
    background-size: cover;
    color: #ffffff;
  }

  .event-back,
  .event-meta,
  .event-kicker {
    text-transform: uppercase;
    font-size: 0.72rem;
    letter-spacing: 0;
    font-weight: 700;
  }

  .event-back {
    color: rgba(255, 255, 255, 0.84);
    text-decoration: none;
  }

  .event-back:hover {
    color: #ffffff;
  }

  .event-hero h2 {
    max-width: 880px;
    margin: 0.75rem 0 0.7rem;
    font-size: clamp(2.25rem, 6.5vw, 5.4rem);
    line-height: 0.98;
    color: #ffffff;
  }

  .event-hero p {
    max-width: 650px;
    color: rgba(255, 255, 255, 0.88);
    font-size: clamp(1rem, 2vw, 1.18rem);
  }

  .event-summary {
    display: grid;
    grid-template-columns: minmax(0, 1fr) minmax(220px, 0.36fr);
    gap: clamp(1.5rem, 4vw, 3rem);
    align-items: start;
    margin-bottom: 3rem;
  }

  .event-summary p {
    color: var(--event-muted);
    font-size: 1.03rem;
  }

  .event-facts {
    border-top: 1px solid var(--event-line);
    border-bottom: 1px solid var(--event-line);
    padding: 1rem 0;
  }

  .event-facts div {
    display: flex;
    justify-content: space-between;
    gap: 1rem;
    padding: 0.35rem 0;
    color: var(--event-muted);
  }

  .event-facts strong {
    color: var(--event-ink);
  }

  .event-gallery {
    columns: 3 240px;
    column-gap: 1rem;
  }

  .event-gallery a {
    display: block;
    break-inside: avoid;
    margin: 0 0 1rem;
  }

  .event-gallery img {
    width: 100%;
    display: block;
    border-radius: 8px;
    object-fit: cover;
    transition:
      transform 180ms ease,
      filter 180ms ease;
  }

  .event-gallery a:hover img {
    transform: translateY(-2px);
    filter: contrast(1.04);
  }

  @media (max-width: 720px) {
    .event-hero {
      min-height: 440px;
      padding: 2rem 1.25rem;
    }

    .event-summary {
      grid-template-columns: 1fr;
    }
  }
</style>

<div class="event-page">
  <section class="event-hero" aria-label="{{ page.title | escape }} gallery header">
    <div>
      <a class="event-back" href="{{ '/projects/photography/' | relative_url }}">Photography</a>
      <h2>{{ page.title }}</h2>
      <p>{{ page.description }}</p>
      <div class="event-meta">
        {{ page.event_date_label }}
        {% if page.event_location %} &middot; {{ page.event_location }}{% endif %}
      </div>
    </div>
  </section>

  <section class="event-summary">
    <div>
      <p class="event-kicker">event notes</p>
      <p>
        A visual record from DropOut, following skydivers through preparations on the ground, aircraft moments, freefall formations, canopy returns,
        and the quieter details around the drop zone.
      </p>
    </div>
    <div class="event-facts" aria-label="Event details">
      <div><strong>Date</strong><span>{{ page.event_date_label }}</span></div>
      <div><strong>Location</strong><span>{{ page.event_location }}</span></div>
      <div><strong>Photos</strong><span>{{ photo_count }}</span></div>
    </div>
  </section>

  <section aria-label="{{ page.title | escape }} photo gallery">
    <div class="event-gallery">
      {% assign visible_index = 0 %}
      {% for photo in gallery_files %}
        {% unless photo.name == "cover.jpg" %}
          {% assign visible_index = visible_index | plus: 1 %}
          <a href="{{ photo.path | relative_url }}" data-lightbox="{{ page.event_slug }}" data-title="{{ page.title | escape }} - photo {{ visible_index }}">
            <img src="{{ photo.path | relative_url }}" alt="{{ page.title | escape }} photo {{ visible_index }}" loading="lazy">
          </a>
        {% endunless %}
      {% endfor %}
    </div>
  </section>
</div>
