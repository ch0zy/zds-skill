---
name: zero-design-system
description: >
  Apply the Zero Foundation design system — Teal (GB) brand colour tokens and
  Lexend type scale — to any React or HTML artifact. Use this skill whenever
  the user asks to build, style, or update a UI using the Zero design system,
  Zero Component Library, Zero Foundation, or Zero brand. Also trigger when
  the user mentions token names like "gb-teal", asks to match their Figma
  design system, or requests a Zero-branded component, dashboard, form, chat
  UI, or any other interface. When in doubt, use this skill — it's better to
  apply the correct tokens than to guess at colours and fonts.
---

# Zero Design System

This skill encodes the **Zero Foundation** design tokens — brand colours, type
scale, spacing, and component conventions — so you can produce pixel-accurate,
on-brand artifacts without re-reading the Figma files each time.

## Quick-start checklist

1. Load the **Lexend** font from Google Fonts (see Typography section)
2. Import the **colour tokens** from the Brand Colours section
3. Apply the **type scale** using the token objects (never hardcode sizes)
4. Use the **spacing scale** for all gaps, padding, and margin
5. Follow the **component conventions** for interactive states

---

## Brand Colours — Teal (GB) Palette

Token name format: `gb-teal-{step}`

| Token         | Hex       | Primary use                                   |
|---------------|-----------|-----------------------------------------------|
| gb-teal-10    | `#E9F4F5` | Subtle surface, active sidebar bg, hover bg   |
| gb-teal-20    | `#CEE6E8` | Light border, active sidebar border           |
| gb-teal-30    | `#9FCED3` | Disabled text, light icon                     |
| gb-teal-40    | `#6BB3BA` | Placeholder text, medium border               |
| gb-teal-50    | `#2D949E` | Helper text, icon default, focus ring colour  |
| gb-teal-60    | `#03727D` | **Primary action** — buttons, links, focus border, user bubbles, avatars |
| gb-teal-70    | `#02545D` | Hover on primary, dark icon                   |
| gb-teal-80    | `#013D43` | Active / pressed on primary                   |
| gb-teal-90    | `#01282C` | Very dark accent                              |
| gb-teal-100   | `#01181B` | Near-black, deepest shade                     |

### Semantic colour map

Copy this constant block verbatim into every artifact:

```js
// ─── Zero Foundation — Brand Colour Tokens ────────────────────────────────────
const brand = {
  10: "#E9F4F5", 20: "#CEE6E8", 30: "#9FCED3", 40: "#6BB3BA",
  50: "#2D949E", 60: "#03727D", 70: "#02545D", 80: "#013D43",
  90: "#01282C", 100: "#01181B",
};

const color = {
  // Backgrounds
  bgDefault:           "#FFFFFF",
  bgSubtle:            brand[10],   // teal-10 — subtle surfaces, hover
  bgSurface:           "#FFFFFF",
  bgOverlay:           "#F2F5F5",
  bgDisabled:          "#F0F1F2",

  // Borders
  borderLighter:       "#DEE1E7",
  borderLight:         brand[20],   // teal-20
  borderDark:          brand[40],   // teal-40
  borderPrimary:       brand[60],   // teal-60 — focus ring

  // Typography
  typeHeaderDark:      "#13151A",
  typeLabelDark:       "#323743",
  typeBodyLight:       "#444C5D",
  typePlaceholder:     brand[40],   // teal-40
  typeHelper:          brand[50],   // teal-50
  typeDisabled:        brand[30],   // teal-30
  typeInverse:         "#FFFFFF",

  // Icons
  iconLight:           brand[30],   // teal-30
  iconDefault:         brand[50],   // teal-50
  iconDark:            brand[70],   // teal-70

  // Primary brand
  primary:             brand[60],   // #03727D — main CTA colour
  primaryHover:        brand[70],   // #02545D
  primaryActive:       brand[80],   // #013D43
  primarySubtle:       brand[10],   // #E9F4F5
  primarySubtleBorder: brand[20],   // #CEE6E8
};
```

---

## Typography — Lexend Type Scale

**Font family:** Lexend (all weights)
**Load via Google Fonts** — include this import in every artifact:

```html
<!-- HTML -->
<link href="https://fonts.googleapis.com/css2?family=Lexend:wght@300;400;600;700&display=swap" rel="stylesheet">
```

```js
// React / CSS-in-JS
@import url('https://fonts.googleapis.com/css2?family=Lexend:wght@300;400;600;700&display=swap');
```

**Font variable:**
```js
const font = "'Lexend', system-ui, sans-serif";
```

### Type scale token objects

```js
const type = {
  // Display — large editorial text
  displayLg:     { fontSize: 48, fontWeight: 700, lineHeight: "56px", letterSpacing: "-1px"   },
  displayMd:     { fontSize: 40, fontWeight: 700, lineHeight: "48px", letterSpacing: "-1px"   },
  displaySmBold: { fontSize: 32, fontWeight: 700, lineHeight: "40px", letterSpacing: "-0.4px" },
  displaySmLight:{ fontSize: 32, fontWeight: 300, lineHeight: "40px", letterSpacing: "-0.4px" },

  // Headings — section and component headers
  headingXlBold: { fontSize: 32, fontWeight: 700, lineHeight: "40px", letterSpacing: "-0.4px" },
  headingLgBold: { fontSize: 28, fontWeight: 700, lineHeight: "36px", letterSpacing: "-0.4px" },
  headingMdSemi: { fontSize: 24, fontWeight: 600, lineHeight: "32px", letterSpacing: "0"      },
  headingMdLight:{ fontSize: 24, fontWeight: 300, lineHeight: "32px", letterSpacing: "0"      },
  headingSmSemi: { fontSize: 20, fontWeight: 600, lineHeight: "28px", letterSpacing: "0"      },
  headingSmLight:{ fontSize: 20, fontWeight: 300, lineHeight: "28px", letterSpacing: "0"      },

  // Labels — UI chrome, buttons, inputs
  labelLgSemi:   { fontSize: 16, fontWeight: 600, lineHeight: "24px", letterSpacing: "0" },
  labelLgReg:    { fontSize: 16, fontWeight: 400, lineHeight: "24px", letterSpacing: "0" },
  labelMdReg:    { fontSize: 14, fontWeight: 400, lineHeight: "20px", letterSpacing: "0" },
  labelSmReg:    { fontSize: 12, fontWeight: 400, lineHeight: "16px", letterSpacing: "0" },

  // Utility
  caption:       { fontSize: 11, fontWeight: 500, lineHeight: "16px", letterSpacing: "0.04em" },
};
```

**Usage rule:** always spread a type token onto your style object:
```js
<p style={{ ...type.labelLgSemi, fontFamily: font, color: color.typeLabelDark }}>
  Label text
</p>
```

---

## Spacing Scale

```js
const sp = { xs: 4, sm: 8, md: 12, lg: 16, xl: 24 };
// Usage: sp.lg → 16  (in px, pass as a number to inline styles)
```

---

## Component Conventions

### Input / Text field
- Height: **44px**
- Border-radius: **8px**
- Padding-left: `sp.lg` (16px), padding-right: `sp.sm` (8px)
- Border default: `1px solid color.borderDark`
- Border focus: `1px solid color.borderPrimary` + `outline: 3px solid ${brand[50]}33`
- Placeholder font-weight: **300** (Lexend Light), filled font-weight: **600**
- Transition: `border-color 0.12s ease, outline 0.12s ease`

### Buttons (primary)
- Height: **44px**, border-radius: **8px**
- Background: `color.primary` (#03727D)
- Hover: `color.primaryHover` (#02545D)
- Active: `color.primaryActive` (#013D43)
- Disabled background: `color.bgDisabled`, disabled text: `color.typeDisabled`

### Buttons (secondary / ghost)
- Border: `1px solid color.borderLighter`
- Background: `color.bgDefault`
- Text: `color.typeLabelDark`

### Cards / surface containers
- Background: `color.bgSurface` (#FFFFFF)
- Border: `1px solid color.borderLighter` (#DEE1E7)
- Border-radius: **8px**

### Active / selected states (sidebar items, tabs)
- Background: `color.primarySubtle` (gb-teal-10)
- Border: `1px solid color.primarySubtleBorder` (gb-teal-20)
- Text: `color.primary` (gb-teal-60), font-weight: **600**

### Focus ring (accessibility)
- `outline: 3px solid ${brand[50]}33` (teal-50 at ~20% opacity)
- Always paired with `border-color: color.borderPrimary`

---

## Scrollbar styling

Add to every artifact's `<style>` block:

```css
::-webkit-scrollbar       { width: 4px; }
::-webkit-scrollbar-track { background: transparent; }
::-webkit-scrollbar-thumb { background: #CEE6E8; border-radius: 2px; } /* gb-teal-20 */
```

---

## React artifact template

Use this skeleton for any new React artifact:

```jsx
import { useState } from "react";

// paste brand, color, type, font, sp constants here (see sections above)

export default function MyComponent() {
  return (
    <>
      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=Lexend:wght@300;400;600;700&display=swap');
        * { box-sizing: border-box; margin: 0; padding: 0; }
        ::-webkit-scrollbar       { width: 4px; }
        ::-webkit-scrollbar-track { background: transparent; }
        ::-webkit-scrollbar-thumb { background: #CEE6E8; border-radius: 2px; }
      `}</style>
      <div style={{ fontFamily: font, background: color.bgOverlay }}>
        {/* component content */}
      </div>
    </>
  );
}
```

---

## Figma source files (for reference)

| File                     | URL                                                                                   |
|--------------------------|---------------------------------------------------------------------------------------|
| Zero Foundation          | https://www.figma.com/design/LJlM5kM0AfYE83vPz23CMf/Zero-Foundation                 |
| → Brand colour tokens    | node-id `351-9996` — Teal (GB) palette with all hex values                           |
| → Text styles            | node-id `437-24105` — Full Lexend type scale (Display → Caption)                     |
| Zero Component Library   | https://www.figma.com/design/48cSN8wRRPb51bvzP6BBBC/Zero-Component-Library           |
| → Text field spec        | node-id `157-18201` — Input anatomy, states, measurements                            |

> If the Figma files are updated, re-read the relevant node with `Figma:get_design_context`
> and update the token values in this skill accordingly.
