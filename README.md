# Hydrogen+ Fitness & Spa — website (design build)

A one-page website for Hydrogen+ Fitness & Spa, Irbid. It's plain HTML, CSS and JavaScript, with no build step and no libraries.

**Live demo:** https://aro-software.github.io/demo-hydrogen-plus-fitness/

## Run it

- **Quickest:** open `index.html` in Chrome, Safari or Firefox.
- **Recommended:** serve the folder so the videos stream properly. Run `npx serve .` or `python3 -m http.server`, then open the address it prints.

## What's inside

```
index.html      markup, styles and logic
assets/         11 looping MP4 videos (H.264, muted), 21 JPG photos and posters,
                favicon.svg, apple-touch-icon.png and og.jpg (link-preview image)
```

## Motion layer

The last `<script>` in `index.html` and the "Final-touch layer" block at the end of the `<style>` add the animation. All of it switches off when the visitor has "reduce motion" turned on.

- **Intro (once per browser session):** the heartbeat line draws, the logo pulses twice, then the screen lifts away in the same three columns as the hero. Any click, scroll or key skips it. It's also skipped when the page opens on a `#section` link.
- **Headlines:** words rise out of a mask as each heading scrolls into view (`class="split"`).
- **Reveals:** `data-reveal` (one block), `data-stagger` (children one after another), `data-curtain` (photos and videos uncovered by a lifting panel).
- **Stats** count up the first time they're seen (`data-count`).
- **Marquee tapes:** two crossed bands that drift, speed up with scroll and reverse when you scroll up.
- **Header:** a red reading-progress line, a deeper background after scrolling, and an underline that follows the section on screen.
- **Coaches and class days:** tapping a coach or a day animates the new card in. The once-a-minute live refresh doesn't replay it.
- **Services stripe:** drag with the mouse on desktop; a line underneath shows where you are.
- **Phones:** a menu button opens a full-screen red menu. "Join now" moves out of the header under 480 px, since the bottom bar already has Call.
- **Footer:** the HYDROGEN+ wordmark is sized to the full width at any screen size.

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
