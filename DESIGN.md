# Design notes

The page takes cues from independent technical journals and small architecture practices: a quiet paper ground, a narrow editorial label column, generous spacing and fine rules. Newsreader gives headings a bookish voice; Source Sans 3 keeps longer copy direct and readable. A monochrome noise layer sits behind the content and repeats on a 160 × 160px tile. The filter can produce its own alpha, while `--grain-opacity` (0.022) controls the overall opacity of the fixed pseudo-element layer. No additional opacity is applied inside the SVG.

The accent is reserved for section numbering and interactive hover/focus states. Sections stay unboxed and the content remains in a single readable flow from capabilities to experience, biography and contact. On smaller screens, the labels move above their content and navigation remains in view without a menu or client-side code.

## Modular scales

Typography uses `--type-base: 1.0625rem` and `--type-ratio: 1.25`. Step 0 uses the base; each positive step multiplies the preceding step by the ratio, and each negative step divides by it. Changing either variable updates the full type scale. Role mapping: labels use step −2; small text uses −1; body uses 0; lead text uses 1; entry headings use 2; contact text uses 3. The hero interpolates from step 4 to step 6 with viewport width, reaching step 5 partway through the desktop range. On narrow screens its width constraint allows natural wrapping while its size stays at or above step 4.

Spacing uses `--space-base: 0.375rem` and `--space-ratio: 1.5`. Step 0 uses the base, and each later step multiplies the preceding step by the ratio. Changing either variable updates the full spacing scale. Layout gaps, margins and padding refer to these tokens; fluid `clamp()` values interpolate between scale steps where the layout needs to grow with the viewport. Page gutters use smaller steps on narrow screens, while section columns stack below 700px. Borders, content widths, letter spacing and line heights remain independent because they serve different layout and reading roles.
