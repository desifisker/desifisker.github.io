---
layout: page
title: photography
description: Event photography galleries and visual storytelling.
img: assets/img/photography/events/dropout-august-2026/cover.jpg
importance: 1
category: creative
permalink: /projects/photography/
images:
  lightbox2: true
---

<style>
  body {
    overflow-x: hidden;
  }

  .post-header {
    display: none;
  }

  .photo-page {
    --photo-ink: #111111;
    --photo-muted: #686868;
    --photo-line: rgba(17, 17, 17, 0.14);
    --photo-warm: #f7f2ea;
    --photo-accent: #8a5a44;
    margin-top: -0.75rem;
  }

  html[data-theme="dark"] .photo-page {
    --photo-ink: #f3f1ec;
    --photo-muted: #c8c1b8;
    --photo-line: rgba(255, 255, 255, 0.2);
    --photo-warm: #201f1d;
    --photo-accent: #d6a77f;
  }

  .photo-hero {
    min-height: clamp(340px, 58vh, 620px);
    display: grid;
    align-items: end;
    padding: clamp(2rem, 5vw, 4.5rem);
    margin: 0 calc(50% - 50vw) 3rem;
    background-image: linear-gradient(180deg, rgba(0, 0, 0, 0.14), rgba(0, 0, 0, 0.72)), url("{{ '/assets/img/photography/events/dropout-august-2026/cover.jpg' | relative_url }}");
    background-position: center;
    background-size: cover;
    color: #ffffff;
  }

  .photo-hero__label,
  .photo-kicker,
  .photo-event-card__meta {
    text-transform: uppercase;
    font-size: 0.72rem;
    letter-spacing: 0;
    font-weight: 700;
  }

  .photo-hero h2 {
    max-width: 880px;
    margin: 0.6rem 0 0;
    font-size: clamp(2.4rem, 7vw, 5.6rem);
    line-height: 0.98;
    color: #ffffff;
  }

  .photo-hero p {
    max-width: 680px;
    margin: 1rem 0 0;
    color: rgba(255, 255, 255, 0.88);
    font-size: clamp(1rem, 2vw, 1.25rem);
  }

  .photo-intro {
    display: grid;
    grid-template-columns: minmax(0, 1fr) minmax(240px, 0.42fr);
    gap: clamp(1.5rem, 4vw, 3rem);
    align-items: start;
    margin-bottom: 3rem;
  }

  .photo-intro h3,
  .photo-section h3 {
    margin-top: 0;
    color: var(--photo-ink);
  }

  .photo-intro p {
    color: var(--photo-muted);
    font-size: 1.03rem;
  }

  .photo-details {
    border-top: 1px solid var(--photo-line);
    border-bottom: 1px solid var(--photo-line);
    padding: 1rem 0;
  }

  .photo-details div {
    display: flex;
    justify-content: space-between;
    gap: 1rem;
    padding: 0.35rem 0;
    color: var(--photo-muted);
  }

  .photo-details strong {
    color: var(--photo-ink);
    font-weight: 700;
  }

  .photo-section {
    margin: 3.5rem 0 1rem;
  }

  .photo-event-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
    gap: 1rem;
  }

  .photo-event-card {
    display: block;
    color: inherit;
    text-decoration: none;
    border-bottom: 1px solid var(--photo-line);
    padding-bottom: 1rem;
  }

  .photo-event-card:hover {
    color: inherit;
    text-decoration: none;
  }

  .photo-event-card img {
    width: 100%;
    aspect-ratio: 4 / 5;
    object-fit: cover;
    border-radius: 8px;
    display: block;
    transition:
      transform 180ms ease,
      filter 180ms ease;
  }

  .photo-event-card:hover img {
    transform: translateY(-2px);
    filter: contrast(1.04);
  }

  .photo-event-card h4 {
    margin: 0.85rem 0 0.25rem;
    color: var(--photo-ink);
  }

  .photo-event-card p {
    margin: 0.25rem 0 0;
    color: var(--photo-muted);
  }

  .photo-empty {
    background: var(--photo-warm);
    border: 1px solid var(--photo-line);
    border-radius: 8px;
    padding: clamp(1.25rem, 3vw, 2rem);
    color: var(--photo-muted);
  }

  @media (max-width: 720px) {
    .photo-hero {
      min-height: 440px;
      padding: 2rem 1.25rem;
    }

    .photo-intro {
      grid-template-columns: 1fr;
    }
  }
</style>

<div class="photo-page">
  <section class="photo-hero" aria-label="Photography portfolio header">
    <div>
      <div class="photo-hero__label">event photography</div>
      <h2>Professional gatherings, documented with care.</h2>
      <p>Selected photo galleries from conferences, community events, public programs, and academic gatherings.</p>
    </div>
  </section>

  <section class="photo-intro">
    <div>
      <p class="photo-kicker">approach</p>
      <h3>Visual records for the moments that make an event feel alive.</h3>
      <p>
        This portfolio is a home for event galleries: candid interactions, speakers, details, room atmosphere, and the small in-between moments
        that help people remember what it felt like to be there.
      </p>
    </div>
    <div class="photo-details" aria-label="Photography focus areas">
      <div><strong>Focus</strong><span>events and programs</span></div>
      <div><strong>Style</strong><span>candid, warm, editorial</span></div>
      <div><strong>Use</strong><span>web, press, archives</span></div>
    </div>
  </section>

  <section class="photo-section">
    <p class="photo-kicker">galleries</p>
    <h3>Event Galleries</h3>

    {% assign photo_events = site.data.photo_events | sort: "date" | reverse %}
    {% if photo_events.size > 0 %}
      <div class="photo-event-grid">
        {% for event in photo_events %}
          <a class="photo-event-card" href="{{ event.url | relative_url }}">
            <img src="{{ event.cover | relative_url }}" alt="{{ event.title | escape }} cover photo">
            <p class="photo-event-card__meta">
              {% if event.date_label %}{{ event.date_label }}{% elsif event.date %}{{ event.date | date: "%B %-d, %Y" }}{% endif %}
              {% if event.location %} &middot; {{ event.location }}{% endif %}
            </p>
            <h4>{{ event.title }}</h4>
            <p>{{ event.description }}</p>
          </a>
        {% endfor %}
      </div>
    {% else %}
      <div class="photo-empty">
        Event galleries will appear here once photos are ready to publish.
      </div>
    {% endif %}
  </section>
</div>
