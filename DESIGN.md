# Design notes

The page takes cues from independent technical journals and small architecture practices: a quiet paper ground, full-width sections, generous spacing and fine rules. Newsreader gives headings and the hero introduction a bookish voice; Source Sans 3 keeps longer copy direct and readable. A monochrome noise layer sits behind the content and repeats on a 160 × 160px tile. The filter can produce its own alpha, while `--grain-opacity` (0.022) controls the overall opacity of the fixed pseudo-element layer. No additional opacity is applied inside the SVG.

The accent is reserved for section numbering and interactive hover/focus states. Sections stay unboxed and use full-width layouts, with each numbered label above its content. Capabilities use four columns on wide screens, two on tablets and one on mobile. Experience entries stack the organisation heading above its description. Navigation remains in view without a menu or client-side code.

Dark mode follows the operating system through `prefers-color-scheme`. It overrides the paper, ink, muted, rule and accent tokens, and sets the matching `color-scheme`; the dark grain opacity is reduced to keep the texture subtle. Selection and browser theme colour follow the active palette. No theme script or manual toggle is used.

## Modular scales

Typography uses `--type-base: 1.0625rem` and `--type-ratio: 1.25`. Step 0 uses the base; each positive step multiplies the preceding step by the ratio, and each negative step divides it by the ratio. Changing either variable updates the full type scale. Role mapping: section labels use step −1; small text uses −1; body uses 0; lead text uses 1; entry headings use 2. The hero interpolates from step 4 to step 6 with viewport width, reaching step 5 partway through the desktop range. Its 24ch measure aims for two balanced lines on desktop and allows natural wrapping on mobile.

Spacing uses `--space-base: 0.375rem` and `--space-ratio: 1.5`. Step 0 uses the base, and each later step multiplies the preceding step by the ratio. Changing either variable updates the full spacing scale. Layout gaps, margins and padding refer to these tokens; fluid `clamp()` values interpolate between scale steps where the layout needs to grow with the viewport. The header uses step 4 for vertical padding. Page gutters use smaller steps on narrow screens. Borders, content widths, letter spacing and line heights remain independent because they serve different layout and reading roles.
