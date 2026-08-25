---
layout: page
title: Photography
description: Event photography galleries and visual storytelling.
img: assets/img/photography/header/pic5.jpg
importance: 1
category: creative
permalink: /projects/photography/
images:
  lightbox2: true
hero_images:
  - image: /assets/img/photography/header/pic1.jpg
    alt: Event photography header image 1
  - image: /assets/img/photography/header/pic2.jpg
    alt: Event photography header image 2
  - image: /assets/img/photography/header/pic3.jpg
    alt: Event photography header image 3
  - image: /assets/img/photography/header/pic4.jpg
    alt: Event photography header image 4
  - image: /assets/img/photography/header/pic5.jpg
    alt: Event photography header image 5
  - image: /assets/img/photography/header/dsc06025.jpg
    alt: Event photography header image 6
---

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
    position: relative;
    min-height: clamp(340px, 58vh, 620px);
    display: grid;
    align-items: end;
    padding: clamp(2rem, 5vw, 4.5rem);
    margin: 0 calc(50% - 50vw) 3rem;
    overflow: hidden;
    background: #111111;
    color: #ffffff;
  }

  .photo-hero::after {
    content: "";
    position: absolute;
    inset: 0;
    z-index: 1;
    pointer-events: none;
    background: linear-gradient(180deg, rgba(0, 0, 0, 0.08), rgba(0, 0, 0, 0.6));
  }

  .photo-hero__slides,
  .photo-hero__slide,
  .photo-hero__slide img {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
  }

  .photo-hero__slide {
    opacity: 0;
    transition: opacity 650ms ease;
  }

  .photo-hero__slide.is-active {
    opacity: 1;
  }

  .photo-hero__slide img {
    object-fit: cover;
    display: block;
  }

  .photo-hero__content {
    position: relative;
    z-index: 2;
  }

  .photo-hero__controls {
    position: absolute;
    right: clamp(1.25rem, 5vw, 4.5rem);
    bottom: clamp(1.25rem, 3vw, 2.5rem);
    z-index: 3;
    display: flex;
    gap: 0.65rem;
  }

  .photo-hero__control {
    width: 44px;
    height: 44px;
    display: grid;
    place-items: center;
    border: 1px solid rgba(255, 255, 255, 0.78);
    border-radius: 999px;
    background: rgba(0, 0, 0, 0.22);
    color: #ffffff;
    cursor: pointer;
    font-size: 1.35rem;
    line-height: 1;
    transition:
      background-color 160ms ease,
      transform 160ms ease;
  }

  .photo-hero__control:hover,
  .photo-hero__control:focus-visible {
    background: rgba(255, 255, 255, 0.2);
    transform: translateY(-1px);
    outline: none;
  }

  .photo-hero__label,
  .photo-kicker,
  .photo-event-card__meta {
    text-transform: uppercase;
    font-size: 0.72rem;
    letter-spacing: 0;
    font-weight: 700;
  }

  .photo-hero__label {
    color: #ffffff;
  }

  .photo-kicker--title {
    text-transform: none;
    font-size: 0.86rem;
  }

  .photo-hero h2 {
    max-width: 720px;
    margin: 0.6rem 0 0;
    font-size: clamp(1.65rem, 4.8vw, 3.6rem);
    line-height: 1.04;
    color: #ffffff;
  }

  .photo-hero p {
    max-width: 560px;
    margin: 1rem 0 0;
    color: rgba(255, 255, 255, 0.88);
    font-size: clamp(0.92rem, 1.5vw, 1.05rem);
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

  .photo-contact {
    border-top: 1px solid var(--photo-line);
    border-bottom: 1px solid var(--photo-line);
    display: flex;
    flex-wrap: wrap;
    align-items: center;
    gap: 0.85rem 1rem;
    grid-column: 1 / -1;
    justify-content: center;
    padding: 1rem 0;
  }

  .photo-contact a {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 2.4rem;
    height: 2.4rem;
    border: 1px solid var(--photo-line);
    border-radius: 999px;
    color: var(--photo-ink);
    font-weight: 600;
    line-height: 1.4;
    text-decoration: none;
    transition:
      border-color 160ms ease,
      color 160ms ease,
      transform 160ms ease;
  }

  .photo-contact i {
    color: var(--global-theme-color);
    font-size: 1.05rem;
  }

  .photo-contact .al-email-protect {
    font-size: 0;
  }

  .photo-contact .al-email-protect::before {
    content: "";
    display: block;
    width: 1.12rem;
    height: 1.12rem;
    background-color: var(--global-theme-color);
    mask: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='black' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Crect width='20' height='16' x='2' y='4' rx='2'/%3E%3Cpath d='m22 7-8.97 5.7a2 2 0 0 1-2.06 0L2 7'/%3E%3C/svg%3E") center / contain no-repeat;
    -webkit-mask: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='black' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3E%3Crect width='20' height='16' x='2' y='4' rx='2'/%3E%3Cpath d='m22 7-8.97 5.7a2 2 0 0 1-2.06 0L2 7'/%3E%3C/svg%3E") center / contain no-repeat;
  }

  .photo-contact a:hover {
    border-color: var(--global-theme-color);
    color: var(--global-hover-color);
    transform: translateY(-1px);
  }

  .photo-contact a:hover i,
  .photo-contact .al-email-protect:hover::before {
    color: var(--global-hover-color);
    background-color: var(--global-hover-color);
  }

  .photo-contact__label {
    color: var(--photo-ink);
    font-size: 0.92rem;
    font-weight: 700;
    line-height: 1.4;
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

    .photo-hero__controls {
      right: 1.25rem;
      bottom: 1.25rem;
    }

    .photo-intro {
      grid-template-columns: 1fr;
    }
  }
</style>

<div class="photo-page">
  <section class="photo-hero" aria-label="Photography portfolio header" data-photo-carousel>
    <div class="photo-hero__slides" aria-hidden="true">
      {% for hero_image in page.hero_images %}
        <div class="photo-hero__slide{% if forloop.first %} is-active{% endif %}" data-photo-slide>
          <img
            src="{{ hero_image.image | relative_url }}"
            alt="{{ hero_image.alt | default: 'Event photography image' | escape }}"
            {% if forloop.first %}
              loading="eager"
            {% else %}
              loading="lazy"
            {% endif %}
          >
        </div>
      {% endfor %}
    </div>
    <div class="photo-hero__content">
      <div class="photo-hero__label">photography</div>
      <h2>Capturing all things Skydiving: Events, vibes, and the love of the game!</h2>
    </div>
    {% if page.hero_images.size > 1 %}
      <div class="photo-hero__controls" aria-label="Photography header image controls">
        <button class="photo-hero__control" type="button" aria-label="Previous photo" data-photo-prev>&larr;</button>
        <button class="photo-hero__control" type="button" aria-label="Next photo" data-photo-next>&rarr;</button>
      </div>
    {% endif %}
  </section>

  <section class="photo-intro">
    <div>
      <p class="photo-kicker photo-kicker--title">About Me</p>
      <h3>Flying is one of my favourite things and catching amazing moments in the sky and on the ground to share makes it that much better!</h3>
      <p>
        I've been skydiving since 2021 and have worked as a Packer, Coach, Instructor, Manifester and Tandem Videoflyer. I have ~900 jumps, and I'm
        excited to branch out into event and fun-jumper camera flying to capture the stoke and pure joy that comes from all of our favourite
        moments at the DZ with the ones we love! - Daisy
      </p>
    </div>
    <div class="photo-contact" aria-label="Photography contact links">
      {% al_email_protect_link site.data.socials.email %}
      <a href="https://www.instagram.com/daisy.fisker/" rel="external nofollow noopener" target="_blank" aria-label="Daisy Fisker on Instagram">
        <i class="fa-brands fa-instagram" aria-hidden="true"></i>
      </a>
      <span class="photo-contact__label">get in touch</span>
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

<script>
  (() => {
    document.querySelectorAll("[data-photo-carousel]").forEach((carousel) => {
      const slides = Array.from(carousel.querySelectorAll("[data-photo-slide]"));
      const previous = carousel.querySelector("[data-photo-prev]");
      const next = carousel.querySelector("[data-photo-next]");
      const reduceMotion = window.matchMedia("(prefers-reduced-motion: reduce)").matches;
      let activeIndex = 0;
      let timer;

      if (slides.length < 2 || !previous || !next) return;

      const showSlide = (nextIndex) => {
        slides[activeIndex].classList.remove("is-active");
        activeIndex = (nextIndex + slides.length) % slides.length;
        slides[activeIndex].classList.add("is-active");
      };

      const stopRotation = () => {
        if (timer) window.clearInterval(timer);
      };

      const startRotation = () => {
        if (reduceMotion) return;
        stopRotation();
        timer = window.setInterval(() => showSlide(activeIndex + 1), 6500);
      };

      previous.addEventListener("click", () => {
        showSlide(activeIndex - 1);
        startRotation();
      });

      next.addEventListener("click", () => {
        showSlide(activeIndex + 1);
        startRotation();
      });

      carousel.addEventListener("mouseenter", stopRotation);
      carousel.addEventListener("mouseleave", startRotation);
      carousel.addEventListener("focusin", stopRotation);
      carousel.addEventListener("focusout", startRotation);

      startRotation();
    });
  })();
</script>
