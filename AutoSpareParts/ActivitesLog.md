# Activities Log

All development activities, feature updates, and tasks performed in this repository are logged here.

## [2026-07-26]
- **Task**: Car outline visibility improvement and animation implementation on home page.
- **Details**: 
  - Adjusted stroke styles in `WhyChooseSection.vue` to make the car outline stand out.
  - Implemented CSS keyframe animations for wheel rotation, chassis drive bounce, and road dash-array line sliding movement.
  - Verified visual responsiveness and design quality.
  - Redesigned the car vector profile to look like a realistic sports car with proper wheel arches, windows, headlights, and tail lights.
- **Task**: Scroll-triggered staggered brand logo fade-in on the home page.
  - **Details**:
    - Integrated `IntersectionObserver` in `BrandsSection.vue` to trigger animations only when scrolled into viewport.
    - Utilized dynamic CSS variables (`--delay`) to staggered-fade individual logo cards one-by-one (40ms interval).
    - Preserved zero-delay instant hover transition for responsive interactive feedback.
- **Task**: Corrected brand logo SVG assets on the home page.
  - **Details**:
    - Replaced incorrect mock inline SVGs (for Mercedes, GMC, Chrysler, Jaguar, Isuzu, Land Rover, UD Trucks, Daihatsu, Mopar, Hino) with their corresponding official SVG files located in `/public/images/brands/`.
    - Simplified rendering template in `BrandsSection.vue` to uniformly load SVG assets as images.
- **Task**: Populated empty brand SVG assets.
  - **Details**:
    - Wrote correct valid SVG vector paths and text markup definitions directly into all 10 files (`mercedes.svg`, `gmc.svg`, `chrysler.svg`, `jaguar.svg`, `isuzu.svg`, `landrover.svg`, `udtrucks.svg`, `daihatsu.svg`, `mopar.svg`, `hino.svg`), resolving the broken image links.
- **Task**: Downloaded and applied correct corporate brand SVGs.
  - **Details**:
    - Installed `node-vehicle-logos` package temporarily to extract official, verified car logo SVG files for Chrysler, Isuzu, Jaguar, and Renault.
    - Curated and downloaded the official vector SVGs for Daihatsu, Hino, and Mopar from Wikimedia Commons.
    - Replaced the previous placeholders in `/public/images/brands/` with these correct corporate assets.
    - Cleaned up node_modules by uninstalling `node-vehicle-logos`.
- **Task**: Updated brand logos with official detailed/colored SVGs matching user reference images.
  - **Details**:
    - Downloaded the official detailed SVG for Land Rover (classic green/gold oval), UD Trucks (official oval emblem), GMC (red letters logo), and Volvo (Iron Mark emblem) from Wikimedia Commons.
    - Replaced existing files in `/public/images/brands/` to render these correct official corporate designs.
- **Task**: Fixed text contrast and mobile stacking order on About page.
  - **Details**:
    - Brighter grey (`rgba(255, 255, 255, 0.75)`) text styling added to the "Quality Guaranteed" card in `AboutView.vue` for legibility.
    - Opacity of the "Genuine" stamp SVG details increased so it stands out clearly.
    - Removed `order: -1` from the visual container in the mobile media query, ensuring introduction text renders above the card on smaller viewports.
- **Task**: Prefilled product quotation request form and smoothed modal animations.
  - **Details**:
    - Created a reactive `prefilledText` variable in `useModal.js` composable.
    - Updated `ProductsView.vue` to set `prefilledText.value` with the clicked product's name and code when clicking the "Request Quote" buttons.
    - Watched `isRequestModalOpen` in `RequestModal.vue` to automatically fill the inquiry message textarea with `prefilledText`.
    - Upgraded CSS transitions on `.modal-overlay` and `.modal-content` inside `RequestModal.vue` to use a high-performance, premium cubic-bezier timing curve (`cubic-bezier(0.16, 1, 0.3, 1)`) for ultra-smooth backdrop blur/fade and slide-up entrance animations.
