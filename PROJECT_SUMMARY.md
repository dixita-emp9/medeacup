# MediaCap Web Application Summary

## Project Overview
MediaCap is a highly interactive, premium web application built using **Astro**. The core design philosophy revolves around a native **macOS desktop experience**, utilizing a bottom dock, draggable-style windows, and sleek animations rather than a traditional scrolling webpage. 

## Technology Stack
- **Framework**: Astro (Static Site Generation / SSR)
- **Styling**: Pure Vanilla CSS. Focuses on glassmorphism, blur effects, drop shadows, and absolute positioning to emulate a desktop environment. No heavy CSS frameworks (like Tailwind) are used to ensure maximum bespoke design control.
- **Interactivity**: Vanilla JavaScript (ES6+). State management (z-index tracking, modal visibility, event delegation) is handled locally within the single page architecture.

## Core UI/UX Features
- **macOS Bottom Dock**: A central navigation hub at the bottom of the screen featuring glassmorphism styling.
- **Dock Stack Animation**: Hovering over the "Cases & Projects" folder icon triggers a macOS-style fan animation where 6 core document/folder icons elegantly fan outwards and upwards in a Bezier curve.
- **Genie Effect**: Opening and closing windows utilizes a custom CSS transform animation (the "Genie Effect"), scaling and translating windows back down into the dock.
- **Traffic Light Controls**: Each full-screen window features the iconic Red/Yellow/Green macOS window controls. The red dot closes the active modal.
- **Z-Index Management**: Clicking different windows automatically calculates and bumps the active `z-index` so the most recently interacted window always comes to the front.

## Core Application Modules
All interactive "pages" are built as overlaid full-screen modals inside `src/components/IndividualPageModals.astro`.

1. **The 1% Principle**: A core philosophy document view.
2. **Cup Cases (Case Studies)**:
   - A dual-pane layout. The left side is a grid of case studies. 
   - Clicking a case study triggers a right-side slide-in containing the full-width case study details (e.g., FabIndia).
   - Features a seamless "Back" button to return to the grid view.
3. **Cup Framework**:
   - A stylized interactive layout featuring a watermark background.
   - Contains a left sidebar navigation for the C-U-P methodology (Clarity, Uncaptured, Power).
   - Clicking sidebar items triggers floating speech-bubble style pop-over cards.
4. **Core Capabilities / About Us / Where We Work**: Additional informational full-screen windows built into the modal registry.

## File Structure & Architecture
- **`src/pages/index.astro`**: The main application shell. It imports all UI components, renders the background, and houses the Vanilla JS engine that wires up all click events, dock interactions, and modal animations.
- **`src/components/BottomDock.astro`**: Contains the HTML and CSS for the macOS bottom navigation bar and the complex curved Stack Fan animation.
- **`src/components/IndividualPageModals.astro`**: A central registry file that contains the HTML and CSS structure for all the individual full-screen windows (Cases, Framework, Mission, etc.).
- **`src/components/FullScreenTabWindow.astro`**: Reusable component layouts for standard full-screen window structures.

## Development & Build
The project is run locally via the Astro CLI.
- **Start Dev Server**: `ASTRO_TELEMETRY_DISABLED=1 npx astro dev --background`
- **Build for Production**: `ASTRO_TELEMETRY_DISABLED=1 npx astro build`
*(Note: Telemetry is explicitly disabled locally to prevent EPERM file locking issues).*
