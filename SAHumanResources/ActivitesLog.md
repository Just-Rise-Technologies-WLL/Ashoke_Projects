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

## [2026-07-24]
- **Activity:** Created sitemap.xml and robots.txt for all three websites.
- **Details:** 
  - Added `sitemap.xml` and `robots.txt` in `/public` directory for AutoSpareParts (`https://mtnautospareparts.com`).
  - Added `sitemap.xml` and `robots.txt` in `/public` directory for FreshMeet (`https://freshcutsmeat.ae`).
  - Added `sitemap.xml` and `robots.txt` in `/frontend/public` directory for SAHumanResources (`https://shahjadhrconsultancy.com`).

## [2026-07-25]
- **Activity:** Restyled manpower category cards in SAHumanResources.
- **Details:** 
  - Removed the dark shade overlay gradient and standard overlay from `ManpowerCategoriesSection.vue`.
  - Reformatted titles into pill-shaped badges in the top-right corner of each card.
  - Added smooth background image scaling (1.08x) and pill translation on hover.
  - Restyled the `IndustriesView.vue` page cards similarly: removed the bottom green banner overlay, converted labels into top-right pill badges, and added identical hover zoom and badge animations.
  - Replaced duplicate/mismatched assets for `furniture_carpenter.jpg`, `pipe_fitter.jpg`, and `duct_man.jpg` with newly generated, high-quality professional images matching their respective designations.
  - Replaced the structural frame/building image for `welder.jpg` with a professional welder working on steel beams with flying sparks.





