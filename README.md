# Blue Ridge Air Co. — award-style Astro homepage

A cinematic homepage for a fictional HVAC company. **The concept: the scroll is the thermostat** — the page cools from 96.2° to 72.0° as you move through it.

## Run it

```bash
npm install
npm run dev      # http://localhost:4321
```

## Tech

- **Astro 5** — each section is a component, composed in `src/pages/index.astro`
- **Three.js** — hero "air field": 7,000 GPU shader particles flowing across the screen, cooling from ember to glacier as they travel
- **GSAP + ScrollTrigger** — preloader, headline reveals, the pinned cooling narrative, count-up stats, magnetic buttons, cursor-following service previews
- **Lenis** — smooth scrolling, synced to GSAP's ticker

## Section map

| Component | What it does |
|---|---|
| `Preloader.astro` | Temperature counter warms to 72.0°, curtain lifts |
| `Hero.astro` | Three.js particle airflow + split-line headline + magnetic CTAs |
| `Marquee.astro` | Credentials ticker |
| `ThermoScroll.astro` | **Signature** — pinned section, readout scrubs 96.2° → 72.0°, ambient glow cools |
| `Services.astro` | Editorial rows with cursor-following image previews |
| `Process.astro` | 4-step service-call sequence, temperature-coded ticks |
| `Stats.astro` | Count-up numbers on scroll |
| `Testimonials.astro` | Reviews with thermostat status lines |
| `CTABanner.astro` | Giant staggered type + magnetic phone button |
| `Footer.astro` | Sitemap + the gradient line, closed out |

## Quality floor

- `prefers-reduced-motion` disables Lenis, the preloader, all GSAP motion, and freezes the particle field to a single rendered frame
- The hero canvas pauses its render loop when scrolled out of view (IntersectionObserver)
- Cursor effects only attach on `pointer: fine` devices
- No-WebGL fallback: the hero gradient scrim carries the design alone

## Production notes

- Images are hotlinked from Unsplash for the demo — download into `public/` for production
- Phone number: search for `8285550172` and replace
- All copy lives in frontmatter arrays at the top of each component
