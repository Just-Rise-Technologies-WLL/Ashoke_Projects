# Activities Log

This file tracks user requests and activities performed in the workspace.

## [2026-07-23]
- **Activity:** Checked and fixed the blank image issue in the Hero slider.
- **Details:** Identified that the first image was returning 404. Downloaded all slider images locally to `/public/images/` and updated `HeroSection.vue` to reference them locally.
- **Activity:** Implemented dynamic text slider in Hero section and auto-scroll client marquee.
- **Details:** 
  - Updated `HeroSection.vue` to bind custom subtitles, titles, and descriptions dynamically for each background image slide. Included a CSS transition wrapper (`text-slide`) for a smooth fade & translate effect when the text changes.
  - Redesigned `ClientsSection.vue` to display clients in a continuous, infinite marquee slider that auto-scrolls horizontally, has smooth fade gradients at the edges, and pauses on hover.
- **Activity:** Fixed Vercel deployment EBADPLATFORM error.
- **Details:** Removed the Windows-specific `@rolldown/binding-win32-x64-msvc` from the `package.json` file.
- **Activity:** Optimised layout dimensions, local images migration, and loading preloader implementation.
- **Details:** 
  - Reverted typewriter animation in `HeroSection.vue` back to the smooth fade-in/slide-up transition based on user feedback.
  - Adjusted `.hero-section` viewport settings (`min-height: 540px` and desktop media query height calculation `calc(100vh - 252px)`) to perfectly fit the Hero & green stats bar on laptop viewports on load.
  - Fixed deep selector issue for dynamic highlight text styling by adding `:deep(.highlight)`.
  - Migrated broken Unsplash URLs inside `AboutSection.vue`, `AboutView.vue` and `IndustriesView.vue` to local downloaded assets under `/public/images/`.
  - Added a premium, brand-matching preloader screen overlay inside `App.vue` with a pulsing company logo and linear progress loader.
  - Added an SEO-friendly `developed by Just Rise Technologies` backlink to `justrise.bh` in the footer copyright area of `Footer.vue`.
  - Cleared developer "Simulated backend" notifications from form success popups in `RequestModal.vue` and `ContactView.vue` with professional success feedback.
  - Implemented automatic scroll-to-top behavior inside Vue Router (`router/index.js`) on every page navigation.
  - Redesigned the responsive layout of `StatsSection.vue` to use CSS Grid on tablets (centering the 5th item) and 1 vertical column on mobile screens to prevent cramped text.
  - Created and registered new page views for `PrivacyPolicyView.vue` and `TermsConditionsView.vue` to resolve the non-functional bottom footer links.
  - Copied `contact.php` to the `/public` directory and updated the frontend submit calls to use relative API endpoints (`/contact.php`) for seamless hosting.
