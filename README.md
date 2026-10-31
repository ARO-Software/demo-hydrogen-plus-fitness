# Hydrogen+ Fitness & Spa — website (design build)

A one-page website for Hydrogen+ Fitness & Spa, Irbid. It's plain HTML, CSS and JavaScript, with no build step and no libraries.

## Run it

- **Quickest:** open `index.html` in Chrome, Safari or Firefox.
- **Recommended:** serve the folder so the videos stream properly. Run `npx serve .` or `python3 -m http.server`, then open the address it prints.

`hydrogen-website-standalone.html` is the same site in one file, with every photo and video embedded (about 34 MB). It's handy for sharing a preview, but use this folder for development.

## What's inside

```
index.html      markup, styles and logic
assets/         11 looping MP4 videos (H.264, muted) and 21 JPG photos and posters
```

Fonts (Anton, Inter, Cairo) load from Google Fonts, so they need an internet connection.

## How the page works

- The page markup sits inside `<template id="page">`. A small renderer at the bottom of the file fills in `{{values}}`, repeats `<sc-for>` blocks and shows or hides `<sc-if>` blocks.
- The data and behaviour live in `class Component`, in `renderVals()`:
  - coaches and their shifts
  - the weekly class schedule
  - opening hours
  - the six services
- Elements marked `data-region="..."` re-render when a coach or day is tapped, and once a minute for the live status.
- All of this can be moved to React, Vue or Next.js one-to-one: the template already uses components, props and state the same way.

## Features to keep

- **Live status in Asia/Amman time:** the hero "Open now / Closed" pill, the "Open" labels on the hours list, and green dots for coaches on shift. It refreshes every minute.
- **Class schedule:** opens on today's classes, fades finished ones, and marks "Next up" or "On now". On Friday (rest day) it shows Saturday.
- **Services stripe:** a sideways scroll-snap row with arrow buttons. Each card loops its own video.
- **Coach picker:** tap a coach to see their photo, shift bar, achievements, Instagram and a direct message link.
- **Video playback:**
  - Background videos play only while on screen (IntersectionObserver) and pause otherwise.
  - With "reduce motion" switched on, the videos and animations stop.
  - Every loop crossfades its last second into its first, so the restart doesn't show.
- **Phones (860 px wide and under):** a bottom action bar with Call, Classes and Map, and a shorter top menu.

## Before launch (content to confirm with the gym)

- **Videos and photos:** these were taken from the gym's and coaches' public Instagram posts. Get the original files from the gym for full quality, plus the OK from every coach and member who appears.
- **Logo:** the logo is drawn in plain type with a dumbbell icon. Swap in the official vector logo.
- **Prices:** membership prices aren't shown yet ("Ask about memberships & current offers").
- **Seasonal details:** confirm the Friday ladies' pool day and the swim-course dates are still current.
- **Coach contact numbers:** none are published yet. The coach buttons call the gym's front desk or open an Instagram message.
- **Gym phone numbers:** 079 214 1000 and 079 215 1000. Lounge: 079 837 0157.
