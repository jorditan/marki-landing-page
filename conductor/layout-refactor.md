# Layout Refactor for Full-Width Sections

## Problem
Currently, `index.astro` wraps all content in a `<main>` tag that has `max-w-[1600px]` and horizontal padding (`px-8`, etc.). This forces all child `<section>` elements to sit inside this padded box. If a section gets a background color, it looks like a floating block instead of an edge-to-edge band.

## Solution Strategy
The industry standard approach is the **"Full-Width Wrapper, Constrained Content"** pattern.
1. Make `<main>` and `<section>` elements `w-full` (100% viewport width) with no padding.
2. Put the background color on the `<section>`.
3. Wrap the content *inside* the `<section>` in a constrained container (`max-w-[1600px] mx-auto px-4 ...`).

## Execution Plan
1. **Create `Container.astro`:** A shared component in `src/components/shared/` containing the exact `px` and `max-w` logic.
2. **Update `index.astro`:** Remove padding, gap, and max-width from `<main>`.
3. **Update Views (`Hero.astro`, `Benefit.astro`, `StepsView.astro`, `AllYouNeedView.astro`, `TablePlans.astro`, `FaqsView.astro`):**
   - Import `Container.astro`.
   - Wrap the existing content of the `<section>` in `<Container>`.
   - Add vertical padding (`py-16` or similar) directly to the `<section>`.
   - Apply distinct background colors to alternating sections to demonstrate the edge-to-edge color capability (e.g., `bg-surface-primary-subtle` or `bg-surface-muted`).