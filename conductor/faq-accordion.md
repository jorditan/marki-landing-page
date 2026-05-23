# FaqAccordion Styling Plan

## Objective
Update the `FaqAccordion.astro` component to closely match the provided Figma design using native HTML `<details>` and `<summary>` elements. The component should handle open/close states elegantly without requiring client-side JavaScript libraries like React.

## Scope & Impact
- **File to modify:** `src/components/views/Faqs/FaqAccordion.astro`
- **Impact:** The FAQ section will have a professional, polished look consistent with the rest of the landing page, featuring a rounded border, correct typography, and a rotating plus/cross icon on toggle.

## Proposed Solution

1.  **HTML Structure:**
    -   Maintain the `<details>` wrapper.
    -   Use `<summary>` for the clickable header. Inside, place an `h3` for the title and the `<Plus />` icon from Lucide.
    -   Wrap the description (`<p>`) in a `<div>` inside `<details>` to control padding independently from the summary.

2.  **Tailwind Styling & States:**
    -   **Base (`details`):** `group w-full bg-surface-background border border-border-default rounded-[32px] overflow-hidden transition-all duration-300`
    -   **Open State (`details[open]`):** Use Tailwind's `open:` modifier to change the background to `bg-surface-primary-subtle` and border to `border-border-primary` when expanded.
    -   **Summary (`summary`):** `flex justify-between items-center px-6 py-4 lg:px-8 lg:py-5 cursor-pointer list-none [&::-webkit-details-marker]:hidden`
    -   **Icon Animation:** Add `transition-transform duration-300 group-open:rotate-45` to the icon container so the Plus turns into an 'X' when opened.

3.  **CSS Fallbacks:**
    -   Add a `<style>` block to ensure `list-style: none` and `::-webkit-details-marker { display: none; }` are strictly applied to the `summary` element, ensuring cross-browser removal of the default black triangle.

## Verification
-   Render the component and verify the default browser marker is hidden.
-   Click the accordion to verify the Plus icon rotates 45 degrees.
-   Verify the background and border colors change on open.
-   Check padding and typography against Figma specs.