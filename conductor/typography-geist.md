# Typography Update: Switch to Geist

## Problem
The application is currently using the `Inter` font because the original Figma design specified it in its CSS tokens (e.g., `font-['Inter:Bold',sans-serif]`). The user wants to use the `Geist` font instead, but it is not being applied because `global.css` explicitly imports and sets `Inter` as the default sans-serif font.

## Solution Strategy
1.  **Update Font Import:** Replace the Google Fonts `@import` URL in `src/styles/global.css` to fetch `Geist` instead of `Inter`.
2.  **Update CSS Variables:** Modify the `--font-sans` and `--font-base` CSS variables in the `@theme` block of `src/styles/global.css` to use `"Geist", sans-serif`.

## Execution Plan
1.  Open `src/styles/global.css`.
2.  Replace `@import url("https://fonts.googleapis.com/css2?family=Inter...");` with `@import url("https://fonts.googleapis.com/css2?family=Geist:wght@100..900&display=swap");`.
3.  Replace `--font-sans: "Inter", sans-serif;` with `--font-sans: "Geist", sans-serif;`.
4.  Replace `--font-base: "Inter", sans-serif;` with `--font-base: "Geist", sans-serif;`.

## Rollback Plan
Revert changes using `git checkout src/styles/global.css` to restore the `Inter` font.