# Photography Galleries

The public photography hub lives at `/projects/photography/` and is powered by:

- `_projects/photography.md` for the main portfolio page.
- `_data/photo_events.yml` for the event cards shown on that page.
- `_pages/photography/event-template.md` as a hidden page to duplicate for each event.
- `assets/img/photography/events/<event-slug>/` for the event photos.

## Publish a New Event

1. Make a folder for the event photos:

   ```txt
   assets/img/photography/events/my-event/
   ```

2. Add the photos to that folder. Use web-friendly filenames, such as:

   ```txt
   cover.jpg
   photo-01.jpg
   photo-02.jpg
   photo-03.jpg
   ```

3. Copy `_pages/photography/event-template.md` to a new file, such as:

   ```txt
   _pages/photography/my-event.md
   ```

4. In the new page, remove `published: false`, update the title, date, location, description, `permalink`, `event_slug`, `event_cover`, and `gallery_dir`.

5. Add a matching entry to `_data/photo_events.yml` so the event appears on the photography hub:

   ```yaml
   - title: "My Event"
     date: 2026-04-18
     location: "New York, NY"
     description: "A brief one-sentence description of the event."
     cover: /assets/img/photography/events/my-event/cover.jpg
     url: /projects/photography/my-event/
   ```

6. Preview locally, then commit and push.

The event page automatically lists `.jpg` files in `gallery_dir`. It skips `cover.jpg`, so use that filename for the header/card image.
