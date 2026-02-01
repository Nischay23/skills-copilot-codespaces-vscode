# MetaRedefine — Project Overview

## 1) What this website is
MetaRedefine is a **frontend-only gaming showcase / landing experience** built to demonstrate **advanced UI/UX**, **high-motion interactions**, and **scroll-driven storytelling**.

It presents a “metagame” themed brand (Zentry / MetaRedefine) using:
- Cinematic **video-led hero section**
- Scroll-based transitions and pinned sections
- Interactive hover effects (3D tilt/parallax, radial hover glow)
- Strong typography + custom fonts + bold color system

Deployed: http://meta-redefine.vercel.app/

---

## 2) Why I created it (interview-ready narrative)
I built this project primarily as a **portfolio-grade UI/UX + animation showcase**.

Key motivations:
- Prove I can build **high-fidelity, modern landing pages** with smooth motion.
- Practice **GSAP + ScrollTrigger** for production-style animations.
- Design a UI that feels like a **premium game/product reveal**, not a standard website.
- Learn how to structure a React project where each page section is a reusable component.

---

## 3) Use cases
This type of site is useful when you need:
- A **marketing/launch landing page** for a game studio, game product, or community.
- A **showcase page** for games/features (videos, highlights, story sections).
- A **portfolio piece** demonstrating motion design + interaction design.
- A **prototype** to validate UI direction before building a full platform.

---

## 4) What it demonstrates (key features)
### High-impact sections
The single-page layout is composed of multiple hero/section blocks:
- **Navbar**: anchored navigation with smart visibility on scroll.
- **Hero**: full-screen video background with interactive preview + cinematic transitions.
- **About**: pinned scroll section with expanding masked media.
- **Features**: bento-grid layout with interactive tilt cards and autoplay videos.
- **Story**: narrative section with 3D tilt image interaction + stylized masking.
- **Contact**: strong CTA with layered clipped images.
- **Footer**: social links and basic site footer.

### Animation and interaction highlights
- **Scroll-triggered animations** (GSAP ScrollTrigger)
- **Pinned section + mask expansion** (About section)
- **Clip-path morphing** + border-radius transitions (Hero video frame)
- **Video carousel-like transitions** (Hero “next video” reveal)
- **3D hover/parallax preview** (VideoPreview)
- **3D tilt on cards and images** (Features and Story)
- **Audio loop toggle + animated indicator** in the navbar

---

## 5) Tech stack
### Core
- **React (Vite)** for component-based UI
- **Tailwind CSS** for utility-first styling
- **GSAP + @gsap/react** for timeline animation
- **ScrollTrigger** for scroll-driven motion

### Supporting
- **react-icons** for icons
- **react-use** (`useWindowScroll`) for scroll position tracking
- **Vercel** for deployment (plus caching header config for videos)

---

## 6) Architecture (how the app is structured)
### High level
This is a single-page React app. The main component simply composes section components in order.

Entry points:
- `src/main.jsx` mounts the React app.
- `src/App.jsx` lays out the site sections.

### Folder structure (important parts)
- `src/components/`
  - `Navbar.jsx`: navigation + audio toggle + scroll hide/show behavior
  - `Hero.jsx`: video-based hero, loading state, click-to-transition logic
  - `About.jsx`: scroll-pinned mask expansion animation
  - `Features.jsx`: bento grid + interactive tilt cards + hover gradient
  - `Story.jsx`: story section + image tilt interactions
  - `Contact.jsx`: CTA section with clipped images
  - `Footer.jsx`: social links
  - `AnimatedTitle.jsx`: reusable animated headings (scroll-triggered word reveal)
  - `VideoPreview.jsx`: reusable hover-parallax wrapper
  - `Button.jsx`: reusable button styling

- `public/`
  - `videos/` hero + feature videos used as background/ambient media
  - `img/` background and section imagery
  - `audio/loop.mp3` used in the navbar audio toggle
  - `fonts/` custom fonts used throughout the UI

---

## 7) Component-by-component notes (what to say in an interview)
### `App.jsx`
- Composes sections in a clear, maintainable order.
- Keeps the page layout simple and delegates behavior to section components.

### `Navbar.jsx`
- Uses `useWindowScroll()` to detect scroll direction.
- Implements a “floating nav” style and GSAP-driven hide/show:
  - When scrolling down: nav slides up and fades.
  - When scrolling up: nav returns and remains floating.
- Adds a small but memorable touch: **audio loop + animated bars indicator**.

### `Hero.jsx`
- Uses GSAP + ScrollTrigger for the **video-frame clip-path morph** on scroll.
- Implements an interactive “mini preview” that triggers:
  - Scale/visibility changes
  - A smooth transition to the next video
- Includes a loader state; it preloads videos and hides the loader after enough are ready.

### `About.jsx`
- Uses a pinned ScrollTrigger timeline.
- Expands a masked container to full viewport size while scrolling.
- This is a classic “storytelling reveal” pattern used in premium product sites.

### `Features.jsx`
- Bento-grid layout with multiple autoplay video cards.
- `BentoTilt` adds cursor-driven **3D perspective tilt**.
- `BentoCard` adds a “coming soon” chip with a **radial gradient hover spotlight**.

### `Story.jsx`
- Uses GSAP to rotate an image slightly based on cursor position.
- Also uses SVG filters/masks to create a stylized, soft-edged frame effect.

### `AnimatedTitle.jsx`
- Reusable title component.
- Splits text into words and animates each word into place on scroll using ScrollTrigger.
- Uses `dangerouslySetInnerHTML` intentionally to support styled `<b>` characters.

### `VideoPreview.jsx`
- A reusable interaction wrapper that creates:
  - Container movement + 3D rotation
  - Inner content parallax in the opposite direction
- Helps keep `Hero.jsx` cleaner by isolating the interaction pattern.

---

## 8) Styling system
- Tailwind config extends:
  - Custom fonts (`zentry`, `general`, `circular-web`, `robert-*`)
  - Custom color palette (blue/violet/yellow variants)
- `src/index.css` defines project-specific utility classes for:
  - Clip paths (`mask-clip-path`, contact clip shapes, sword clip shape)
  - Typography styles (`special-font`, `hero-heading`, `animated-title`)
  - Reusable layout helpers (`absolute-center`, `flex-center`)

---

## 9) Performance considerations (what I thought about)
- Videos are set to `muted` + `loop` and used as ambient visuals.
- Hero preloads videos and shows a loader until enough media is ready.
- Deployment includes a Vercel header rule for `public/videos/*` to control caching behavior.

---

## 10) How to run locally
From the project root:
- Install: `npm install`
- Dev server: `npm run dev`
- Build: `npm run build`
- Preview build: `npm run preview`

---

## 11) What I would add next (future improvements)
If I had more time, I’d extend it with:
- **Real game data** (JSON/REST) and dynamic “game cards” with filtering.
- **Accessibility improvements**: reduced motion mode, keyboard focus states, ARIA labels.
- **Performance hardening**: `prefers-reduced-motion` handling, video fallback images, lazy-loading below-the-fold media.
- **Better SEO**: update document title/meta tags, add Open Graph tags.
- **Routing** (optional): split sections into routes or keep as a scroll-based one-pager.

---

## 12) 30-second interview pitch
“I built MetaRedefine as a frontend-only gaming showcase to demonstrate advanced UI/UX and animation. It’s a React + Vite + Tailwind project where each page section is a component, and motion is handled with GSAP/ScrollTrigger. The hero uses clip-path scroll effects and a video transition interaction, the About section uses pinned scrolling with a mask expansion, and the Features and Story sections add 3D hover/tilt interactions. The goal was to ship a premium, high-motion experience similar to modern game/product launch sites.”
