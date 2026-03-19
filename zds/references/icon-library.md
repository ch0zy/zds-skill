# Zero Icon Library

Figma file: https://www.figma.com/design/No1ah7cbT62NoMFsXmo1re/Zero-Icon-Library

---

## Overview

Zero icons are **flat, single-colour** vector icons. They are distinct from spot illustrations (which use 3+ colours).

Two pages in the icon library:
1. **Iconography / Guidelines** (node `530-10028`) — design rules, sizes, naming
2. **Spot Illustration Library** (node `530-10289`) — multi-colour marketing illustrations

---

## Icon Styles

Two style variants for every icon:

| Style | Usage |
|-------|-------|
| `outline/` | **Default** — most UI contexts, form elements, navigation, labels |
| `solid/` | Feedback states (success, error), icons against dark/coloured bg (e.g. footer), active/selected states |

**Example names:** `outline/check-circle`, `solid/check-circle`, `outline/archive-box`, `outline/clock`, `solid/clock`

---

## Icon Sizes

Six sizes available (`xs` → `2xl`). Only sizes up to `md` (24px) are currently used in production components.

| Token | Size (px) | Typical use |
|-------|-----------|-------------|
| icon-size-xs | 16px | Compact UI, captions |
| icon-size-sm | 20px | **Most common** — inputs, labels, inline |
| icon-size-md | 24px | Navigation, standalone icons |
| icon-size-lg | 32px | Feature icons, larger UI |
| icon-size-xl | 40px | Section icons |
| icon-size-2xl | 48px | Hero / marketing icons |

**Default in components:** 20×20px (`icon-size-sm`)

---

## Icon Tokens (3 semantic tokens per icon)

```js
const iconTokens = {
  // Size — always use even pixel values (16, 20, 24, 32, 40, 48)
  size: {
    xs: 16, sm: 20, md: 24, lg: 32, xl: 40, "2xl": 48,
  },

  // Stroke — rounded end caps, corresponds to size token
  // e.g. icon-stroke-sm goes with icon-size-sm
  stroke: {
    xs: 1,    // 16px icon
    sm: 1.5,  // 20px icon (most common)
    md: 1.5,  // 24px icon
    lg: 2,    // 32px icon
    xl: 2,    // 40px icon
    "2xl": 2, // 48px icon
  },

  // Color — single colour only (icons never use more than 1 colour)
  color: {
    light:   brand[30],   // #9FCED3 — disabled, decorative
    default: brand[50],   // #2D949E — default icon colour
    dark:    brand[70],   // #02545D — high-emphasis icons
    inverse: "#FFFFFF",   // on dark backgrounds
    negative: "#CC1616",  // error icons (solid/ style)
    positive: "#1E7F34",  // success icons (solid/ style)
  },
};
```

---

## Design Principles

**Rounded design** — No sharp corners. Icons use rounded strokes (rounded end caps) and/or rounded corners. Consistent with Zero's overall `border-radius-md` (8px) design language.

**Flat & single colour** — Always one `icon-color` token at a time. Never gradients, never multiple colours.

**Outline vs Solid usage:**
- `outline/` — Default for most UI (inputs, nav items, labels, buttons, tooltips)
- `solid/` — Use only for:
  - Feedback notifications (success ✓, error ✗, warning !)
  - Icons against dark backgrounds (footer, dark panels)
  - Active/selected states where visual weight is needed

**Avoid type in icons** — Icons should be language-independent. If currency symbols are needed, draw them as vectors, not typefaces.

**Pixel grid alignment** — All icon paths must snap to the pixel grid for crisp rendering at all sizes.

---

## Naming Convention

Format: `[style]/[icon-name]` or `[style]/[icon-name]-[variant]`

- **Style:** `outline` or `solid`
- **Icon name:** Based on what the icon *shows*, not what it *means conceptually*
  - ✅ `stopwatch` (not `speed`)
  - ✅ `lightbulb` (not `idea`)
  - ✅ `cloud-arrow-down` (not `download`)
- **Variants:** Use dash separator for multi-word and variant names
  - `banknotes-dollar`, `banknotes-euro`

---

## Common Icons Used in Components

| Icon name | Where used |
|-----------|-----------|
| `outline/check-circle` | Success states, status tables (Ready) |
| `solid/check-circle` | Success feedback, notifications |
| `outline/information-circle` | Tooltip trigger, info labels |
| `outline/chevron-right` | Breadcrumb separator, accordion toggle |
| `outline/chevron-down` | Select/combobox, accordion |
| `outline/magnifying-glass` | Search input prefix |
| `outline/x-circle` | Search input clear, error |
| `outline/x-mark` | Close button (modal, drawer, snackbar) |
| `outline/calendar` | Date picker trigger |
| `outline/star` | Rating (empty) |
| `solid/star` | Rating (filled) |
| `outline/exclamation-circle` | Warning, error field indicator |
| `solid/exclamation-circle` | Error feedback notification |
| `outline/bars-3` | Mobile hamburger menu |
| `outline/arrow-left` | Back navigation, pagination prev |
| `outline/arrow-right` | Next, navigation forward, pagination next |
| `outline/ellipsis-horizontal` | More options (kebab menu) |

---

## Spot Illustration Library (node `530-10289`)

Spot illustrations are distinct from icons:
- Use **3 or more colours**
- Used in **marketing, empty states, onboarding, error pages**
- Larger sizes (typically 96px+)
- Not suitable for UI chrome (use `outline/` icons instead)

For marketing "icons" or decorative imagery, always check the spot illustration library first before creating custom graphics.
