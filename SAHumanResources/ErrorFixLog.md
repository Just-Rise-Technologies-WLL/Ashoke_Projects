# Error Fix Log

This file tracks errors, issues identified, and the fixes applied to the project.

## [2026-07-23] Header First Slider Image Blank
- **Issue:** The first slider image in the header was blank.
- **Root Cause:** The Unsplash image URL (`https://images.unsplash.com/photo-1541888086425-d81bb19240f5?ixlib=rb-4.0.3&auto=format&fit=crop&w=2000&q=80`) returned a **404 Not Found** status from Unsplash.
- **Fix:** Downloaded the images locally to `/public/images/` and updated [HeroSection.vue](file:///Volumes/Files/AppDev/justrise_bahrain/Ashoke_Project_Management_and_HRM_Dubai/SAHumanResources/frontend/src/components/sections/HeroSection.vue) to reference them locally as `/images/hero1.jpg`, `/images/hero2.jpg`, and `/images/hero3.jpg`.
- **Status:** Resolved.

## [2026-07-23] Vercel Deploy EBADPLATFORM Error
- **Issue:** Vercel deployment failed during `npm install` step.
- **Root Cause:** A platform-specific Windows dependency (`@rolldown/binding-win32-x64-msvc`) was explicitly declared in `devDependencies` in `package.json`.
- **Fix:** Removed `"@rolldown/binding-win32-x64-msvc"` from [package.json](file:///Volumes/Files/AppDev/justrise_bahrain/Ashoke_Project_Management_and_HRM_Dubai/SAHumanResources/frontend/package.json). Vite/Rolldown will resolve/install the correct platform binary automatically at runtime.
- **Status:** Resolved.

