# Global UI/UX Audit and Refinement Plan

## Objective
Refine the entire landing page to achieve high-fidelity visual parity with the Figma design, ensuring consistency in typography, backgrounds, and adding global dynamicity through scroll-based animations. Address accessibility by removing forced uppercase styling where appropriate, while respecting specific exceptions.

## Scope & Impact
- **Affected Files:**
  - `src/components/views/Plans/TablePlans.astro`
  - `src/components/views/HeroView/Hero.astro`
  - `src/components/views/BenefitsView/Benefit.astro`
  - `src/components/views/Steps/StepsView.astro`
  - `src/components/views/AllYouNeed/AllYouNeedView.astro`
  - `src/layouts/Layout.astro`
  - `src/styles/global.css`
- **Impact:** The entire landing page will feel much more polished, cohesive, and dynamic. The user experience will be enhanced by subtle animations, and the visual hierarchy will closely match the design system.

## Proposed Solution & Implementation Steps

### Phase 1: Typography and Styling Cleanup
1.  **Remove Uppercase (Selective):**
    -   Update `TablePlans.astro` to remove `uppercase` classes from the 'Recomendado' badge text and the currency labels (`ARS`), utilizing standard capitalization for better readability.
    -   *Constraint:* Ensure `uppercase` is **kept** in `Subheading.astro` and `IntegrationsCard.astro` as explicitly requested.
2.  **Typography Verification:** Ensure all main headings and body text across views respect the letter-spacing (`tracking`) and font weights defined in `global.css`.

### Phase 2: Global Backgrounds and 
s
1.  **Background Application:**
    -   Review the Figma design to identify where the subtle gradient background should be applied.
    -   Update `Layout.astro` or individual view components (`Hero`, etc.) to use the `bg-hero-gradient` utility class to create the soft, modern look requested.

### Phase 3: Global Dynamism & Animations
1.  **Scroll Reveal Logic:**
    -   Add a lightweight vanilla JavaScript Intersection Observer to `Layout.astro` (or a dedicated script file) that detects when elements with a specific class (e.g., `scroll-animate`) enter the viewport.
    -   When in view, the script will add an active class (e.g., `in-view`) that triggers CSS transitions.
2.  **CSS Animation Definitions:**
    -   Expand `global.css` to include reusable animation classes for scroll reveals (e.g., fade-in, slide-up with subtle delays).
3.  **Apply Animations to Sections:**
    -   Apply the `scroll-animate` base classes to key elements (headers, cards, feature lists) across `HeroView`, `BenefitsView`, `StepsView`, `AllYouNeedView`, and `TablePlans`.
    -   Use animation delays to create pleasing staggered entry effects within sections.

## Verification
-   Visually inspect the landing page on desktop and mobile viewports.
-   Confirm that scrolling down the page triggers smooth, sequential animations.
-   Verify that the background gradient is present and consistent.
-   Confirm that `Subheading` and `IntegrationsCard` still have uppercase text, while the pricing table labels do not.

## Rollback Plan
-   Since these are mostly styling and class additions, reverting involves discarding the CSS/Astro file changes using `git checkout`.
