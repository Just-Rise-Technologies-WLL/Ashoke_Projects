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


