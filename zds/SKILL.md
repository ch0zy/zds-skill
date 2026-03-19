---
name: zero-design-system
description: >
  Apply the full Zero Design System — covering the Zero Foundation (colour
  tokens, typography, spacing, elevation, border, motion, grid) and the Zero
  Component Library (buttons, forms, navigation, feedback, content, structure)
  — to any React or HTML artifact. Use this skill whenever the user asks to
  build, style, or update a UI using the Zero design system, Zero Component
  Library, Zero Foundation, Zero Pattern Library, or Zero brand. Also trigger
  when the user mentions token names like "gb-teal", asks to match their Figma
  design system, or requests a Zero-branded component, dashboard, form, chat
  UI, navigation, or any other interface. When in doubt, use this skill — it's
  better to apply the correct tokens than to guess at colours and fonts.
---

# Zero Design System

This skill encodes the complete **Zero Design System** — foundation tokens
(colour, typography, spacing, elevation, border radius, motion, grid) and
component conventions from the **Zero Component Library** — so you can produce
pixel-accurate, on-brand artifacts without re-reading the Figma files each time.

The design system has four parts:
1. **Zero Foundation** — design tokens (documented in this file)
2. **Zero Component Library** — 30+ components (documented in this file)
3. **Zero Pattern Library** — page-level patterns (see Figma link)
4. **Zero Icon Library** — `solid/` and `outline/` icon sets (see Figma link)

---

## Quick-start checklist

1. Load **Lexend** from Google Fonts (see Typography section)
2. Paste the **colour token blocks** (`brand`, `grayCool`, `grayNeutral`, `color`)
3. Apply the **type scale** using token objects — never hardcode sizes
4. Use the **spacing scale** for all gaps, padding, and margin
5. Apply **elevation shadows** to surfaces that need depth
6. Follow **component conventions** for interactive states
7. Use `solid/` icon variant by default; `outline/` for secondary/lighter contexts

---

## 1. Brand Colours — Teal (GB) Palette

Token format: `gb-teal-{step}`

| Token       | Hex       | Primary use                                         |
|-------------|-----------|-----------------------------------------------------|
| gb-teal-10  | `#E9F4F5` | Subtle surface, active sidebar bg, hover bg         |
| gb-teal-20  | `#CEE6E8` | Light border, active sidebar border                 |
| gb-teal-30  | `#9FCED3` | Disabled text, light icon                           |
| gb-teal-40  | `#6BB3BA` | Placeholder text, medium border                     |
| gb-teal-50  | `#2D949E` | Helper text, icon default, focus ring colour        |
| gb-teal-60  | `#03727D` | **Primary action** — buttons, links, focus border   |
| gb-teal-70  | `#02545D` | Hover on primary, dark icon                         |
| gb-teal-80  | `#013D43` | Active / pressed on primary                         |
| gb-teal-90  | `#01282C` | Very dark accent                                    |
| gb-teal-100 | `#01181B` | Near-black, deepest shade                           |

### Neutral Gray Palette

| Token            | Hex       |
|------------------|-----------|
| gray-neutral-0   | `#FFFFFF` |
| gray-neutral-10  | `#F3F3F3` |
| gray-neutral-20  | `#E1E1E1` |
| gray-neutral-30  | `#C6C6C6` |
| gray-neutral-40  | `#A8A8A8` |
| gray-neutral-50  | `#878787` |
| gray-neutral-60  | `#676767` |
| gray-neutral-70  | `#4C4C4C` |
| gray-neutral-80  | `#373737` |
| gray-neutral-90  | `#242424` |
| gray-neutral-100 | `#151515` |

### Cool Gray Palette (used for UI chrome, typography)

| Token          | Hex       |
|----------------|-----------|
| gray-cool-0    | `#FFFFFF` |
| gray-cool-10   | `#F2F3F5` |
| gray-cool-20   | `#DEE1E7` |
| gray-cool-30   | `#C1C6D1` |
| gray-cool-40   | `#9FA8B9` |
| gray-cool-50   | `#7C879F` |
| gray-cool-60   | `#5C677E` |
| gray-cool-70   | `#444C5D` |
| gray-cool-80   | `#323743` |
| gray-cool-90   | `#21242C` |
| gray-cool-100  | `#13151A` |

### Full Token Block — paste verbatim into every artifact

```js
// ─── Zero Foundation Design Tokens ───────────────────────────────────────────
const brand = {
  10:"#E9F4F5",20:"#CEE6E8",30:"#9FCED3",40:"#6BB3BA",
  50:"#2D949E",60:"#03727D",70:"#02545D",80:"#013D43",
  90:"#01282C",100:"#01181B",
};
const grayCool = {
  0:"#FFFFFF",10:"#F2F3F5",20:"#DEE1E7",30:"#C1C6D1",40:"#9FA8B9",
  50:"#7C879F",60:"#5C677E",70:"#444C5D",80:"#323743",90:"#21242C",100:"#13151A",
};
const grayNeutral = {
  0:"#FFFFFF",10:"#F3F3F3",20:"#E1E1E1",30:"#C6C6C6",40:"#A8A8A8",
  50:"#878787",60:"#676767",70:"#4C4C4C",80:"#373737",90:"#242424",100:"#151515",
};
const color = {
  // Backgrounds
  bgDefault:           "#FFFFFF",
  bgSubtle:            brand[10],        // hover bg, subtle surface
  bgSurface:           "#FFFFFF",
  bgOverlay:           grayCool[10],     // page bg
  bgAlternate:         grayCool[10],     // table headers, alt rows
  bgDark:              grayCool[90],
  bgDisabled:          "#F0F1F2",
  // Borders
  borderLighter:       grayCool[20],     // default card / table border
  borderLight:         brand[20],
  borderDark:          brand[40],
  borderPrimary:       brand[60],        // focus ring
  borderNegative:      "#CC1616",        // error / destructive
  borderInverse:       "#FFFFFF",
  // Typography
  typeHeaderDark:      grayCool[100],    // #13151A
  typeHeaderLight:     grayCool[90],     // #21242C
  typeLabelDark:       grayCool[80],     // #323743
  typeLabelLight:      grayCool[60],     // #5C677E
  typeBodyDark:        grayCool[80],
  typeBodyLight:       grayCool[70],     // #444C5D
  typePlaceholder:     brand[40],
  typeHelper:          brand[50],
  typeDisabled:        brand[30],
  typeInverse:         "#FFFFFF",
  // Icons
  iconLight:           brand[30],
  iconDefault:         brand[50],
  iconDark:            brand[70],
  // Primary brand
  primary:             brand[60],        // #03727D
  primaryHover:        brand[70],        // #02545D
  primaryActive:       brand[80],        // #013D43
  primarySubtle:       brand[10],
  primarySubtleBorder: brand[20],
  // Semantic states
  negative:            "#CC1616",        // error / destructive
  negativeHover:       "#A81212",
  positive:            "#1E7F34",        // success green
  warning:             "#C45B00",
};
```

---

## 2. Typography — Lexend Type Scale

**Font:** Lexend · always load from Google Fonts:

```html
<link href="https://fonts.googleapis.com/css2?family=Lexend:wght@300;400;600;700&display=swap" rel="stylesheet">
```

```js
const font = "'Lexend', system-ui, sans-serif";

const type = {
  // Display
  displayLg:      { fontSize:48, fontWeight:700, lineHeight:"56px", letterSpacing:"-1px"    },
  displayMd:      { fontSize:40, fontWeight:700, lineHeight:"48px", letterSpacing:"-1px"    },
  displaySmBold:  { fontSize:32, fontWeight:700, lineHeight:"40px", letterSpacing:"-0.4px"  },
  displaySmLight: { fontSize:32, fontWeight:300, lineHeight:"40px", letterSpacing:"-0.4px"  },
  // Headings
  headingXlBold:  { fontSize:32, fontWeight:700, lineHeight:"40px", letterSpacing:"-0.4px"  },
  headingLgBold:  { fontSize:28, fontWeight:700, lineHeight:"36px", letterSpacing:"-0.4px"  },
  headingLgLight: { fontSize:28, fontWeight:300, lineHeight:"36px", letterSpacing:"-0.4px"  },
  headingMdSemi:  { fontSize:24, fontWeight:600, lineHeight:"32px", letterSpacing:"0"       },
  headingMdLight: { fontSize:24, fontWeight:300, lineHeight:"32px", letterSpacing:"0"       },
  headingSmSemi:  { fontSize:20, fontWeight:600, lineHeight:"28px", letterSpacing:"0"       },
  headingSmLight: { fontSize:20, fontWeight:300, lineHeight:"28px", letterSpacing:"0"       },
  // Body
  bodyMdReg:      { fontSize:16, fontWeight:400, lineHeight:"24px", letterSpacing:"0"       },
  // Labels
  labelLgSemi:    { fontSize:16, fontWeight:600, lineHeight:"24px", letterSpacing:"0"       },
  labelLgReg:     { fontSize:16, fontWeight:400, lineHeight:"24px", letterSpacing:"0"       },
  labelMdSemi:    { fontSize:14, fontWeight:600, lineHeight:"20px", letterSpacing:"0"       },
  labelMdReg:     { fontSize:14, fontWeight:400, lineHeight:"20px", letterSpacing:"0"       },
  labelSmSemi:    { fontSize:12, fontWeight:600, lineHeight:"16px", letterSpacing:"0"       },
  labelSmReg:     { fontSize:12, fontWeight:400, lineHeight:"16px", letterSpacing:"0"       },
  // Utility
  caption:        { fontSize:11, fontWeight:500, lineHeight:"16px", letterSpacing:"0.04em"  },
  overline:       { fontSize:12, fontWeight:400, lineHeight:"16px", letterSpacing:"2px"     },
};
```

**Typography principles:**
- **Contrast, skip one** — skip ≥1 size + weight when combining styles to create hierarchy
- **Tracking** — larger/bolder = tighter tracking; smaller/lighter = looser
- **Line length** — body: 40–60 chars; short labels: 20–40 chars
- **Alignment** — left-align by default (F-Pattern)

---

## 3. Spacing Scale

```js
const sp = {
  0:0, 1:2, 2:4, 3:8, 4:12, 5:16, 6:20, 7:24, 8:32, 9:48, 10:64, 11:96, 12:128
};
// Usage: sp[5] → 16   |   `${sp[7]}px` → "24px"
// Token names: spacing-0 through spacing-12
```

---

## 4. Border Radius & Border Width

```js
const radius = {
  none: 0,    // border-radius-none
  sm:   4,    // border-radius-4
  md:   8,    // border-radius-8  ← default for almost all components
  lg:   16,   // border-radius-16
  full: 512,  // border-radius-full — pills, chips, avatars
};

const borderWidth = {
  thin:    1,  // default borders
  thick:   2,  // focus/emphasis
  thicker: 4,  // strong accent
};
```

**Rule:** Zero rounds almost everything. Use `radius.md` (8px) for inputs, buttons, cards, modals. Use `radius.full` for chips, pills, tags.

---

## 5. Elevation (Shadow Scale)

```js
const elevation = {
  1: "0px 0px 2px rgba(19,21,26,0.04), 0px 2px 12px rgba(19,21,26,0.08), 0px 4px 4px -2px rgba(19,21,26,0.08)",
  2: "0px 0px 2px rgba(19,21,26,0.04), 0px 2px 12px rgba(19,21,26,0.08), 0px 16px 16px -8px rgba(19,21,26,0.08)",
  3: "0px 0px 2px rgba(19,21,26,0.04), 0px 2px 12px rgba(19,21,26,0.08), 0px 24px 24px -12px rgba(19,21,26,0.08)",
  raiseTop:    "0px 2px 4px rgba(19,21,26,0.08)",
  raiseBottom: "0px -2px 4px rgba(19,21,26,0.08)",
};
```

| Level         | Components                                      |
|---------------|-------------------------------------------------|
| 0 (flat)      | Page bg, sidebar, non-sticky header             |
| 1             | Cards, form elements, option cards              |
| 2             | Dropdowns, tooltips, mega menu, snackbar, toast |
| 3             | Modal, drawer — full-focus overlays             |
| raiseTop/Bottom | Sticky headers, bottom sheets                 |

---

## 6. Motion / Easing

```js
const transition = {
  entrance: "all 200ms cubic-bezier(0.15, 0.6, 0.6, 1)",  // fade/slide in
  exit:     "all 200ms cubic-bezier(0.1, 0, 0.5, 0)",     // fade/slide out
  standard: "all 350ms cubic-bezier(0.25, 0, 0.25, 1)",   // move place-to-place
  fast:     "all 120ms ease",                              // micro-interactions
};
// Durations: entrance/exit 100–300ms | standard 300–500ms
```

---

## 7. Grid

12-column layout · 1440px max · 132px left/right margins · 48px gutters.
Content zones: 1176px (full), 768px (copy/text), 564px (half-width).

---

## 8. Scrollbar (add to every artifact)

```css
::-webkit-scrollbar       { width: 4px; }
::-webkit-scrollbar-track { background: transparent; }
::-webkit-scrollbar-thumb { background: #CEE6E8; border-radius: 2px; }
```

---

## 9. Component Library

### 9.1 — Action

#### Button

Three **hierarchy tiers** — one primary per screen:

| Tier      | Brand variant                              | Inverse variant                           | Negative variant                          |
|-----------|--------------------------------------------|-------------------------------------------|-------------------------------------------|
| Primary   | `#03727D` bg, white text                   | white bg, `#03727D` text                  | `#CC1616` bg, white text                  |
| Secondary | `#03727D` border, `#03727D` text           | white border, white text                  | `#CC1616` border, `#CC1616` text          |
| Ghost     | no bg, no border, `#03727D` text           | no bg, no border, white text              | no bg, no border, `#CC1616` text          |

Three **sizes:**

| Size   | Padding x | Padding y | Font                     |
|--------|-----------|-----------|--------------------------|
| Small  | 12px      | 8px       | `labelSmSemi` (12/600)   |
| Medium | 20px      | 12px      | `labelMdSemi` (14/600)   |
| Large  | 24px      | 12px      | `labelLgSemi` (16/600)   |

All sizes: `border-radius: radius.md (8px)` · optional 20×20 icon left or right.

```js
// Example primary medium button
const btn = {
  display:"inline-flex", alignItems:"center", justifyContent:"center",
  gap: sp[2],
  padding:`${sp[4]}px ${sp[6]}px`,
  borderRadius: radius.md,
  background: color.primary,
  color: color.typeInverse,
  border: "none",
  fontFamily: font,
  fontSize: 14, fontWeight: 600, lineHeight: "20px",
  cursor: "pointer",
  transition: transition.fast,
};
// Hover: background → color.primaryHover
// Active: background → color.primaryActive
// Disabled: background → color.bgDisabled, color → color.typeDisabled
```

#### Icon Button
- Size: 36px (or 44px touch target)
- Border-radius: `radius.md`
- Icon: 20×20px or 24×24px

#### Chip
- Height: ~32px · border-radius: `radius.full`
- Padding: `8px 12px`
- Variants: filled (brand[10] bg, brand[60] text), outlined, removable (× icon)

#### Link
- Color: `color.primary`, underline on hover
- Inherits surrounding font size

---

### 9.2 — Forms

All form inputs share:
- **Height:** 44px
- **Border-radius:** `radius.md` (8px)
- **Border:** `1px solid ${color.borderLighter}`
- **Focus:** `border-color: ${color.borderPrimary}` + `outline: 3px solid ${brand[50]}33`
- **Error:** border `#CC1616` + error message below in red
- **Transition:** `border-color 120ms ease, outline 120ms ease`

#### Text Field
```js
const inputStyle = {
  height: 44, borderRadius: radius.md,
  paddingLeft: sp[5], paddingRight: sp[3],
  border: `1px solid ${color.borderLighter}`,
  fontFamily: font, fontSize: 14,
  // placeholder weight: 300 (Light) | filled weight: 600 (SemiBold)
};
```
Anatomy: Container · Label (above) · Placeholder · Border · Helper text · Supporting icon (optional)

#### Text Area
Same rules, flexible height (min ~88px), vertical-only resize.

#### Checkbox — 20×20px, 4px radius. Checked = `#03727D` fill + white tick.
#### Radio Button — 20×20px circle. Selected = `#03727D` ring + inner dot.
#### Select / Combobox — 44px height, chevron icon right, elevation[2] dropdown.
#### Search Input — magnifier icon prefix, clear (×) icon suffix when filled.
#### Date Picker — text field trigger + calendar panel (elevation[2]).
#### Combobox — text field + filtered option list (elevation[2]).
#### Rating — star icons (20×20), filled `#03727D`, empty `grayCool[20]`.

---

### 9.3 — Content

#### Card
- White bg · `1px solid ${color.borderLighter}` · `radius.md` · `elevation[1]`
- Internal padding: typically `sp[5]` (16px)

#### Image Card — full-bleed image top + text below, outer `radius.md`.

#### Accordion
- Full-width header + chevron right, collapse with `transition.standard`
- Divider: `1px solid ${color.borderLighter}` between items

#### Tooltip
- Bg: `grayCool[90]` · text: white · `radius.sm` (4px) · `elevation[2]`
- Font: `labelSmReg` · max-width: ~240px

#### Callout Banner
- Left accent border 4px solid (colour = intent: info/success/warning/error)
- Tinted bg (e.g. success = `#EFF8F1`, info = `#E9F4F5`)

#### Table
- Header: `bgAlternate`, `labelLgSemi` · Cell padding: `24px 20px`
- Row divider: `1px solid ${color.borderLighter}`

#### Description List — term: `labelMdSemi`, value: `labelMdReg`.
#### Info Tag / Badge — `radius.full` pill, semantic colour bg + text.
#### Icon List — 20×20 icon left + text, `sp[3]` vertical row padding.
#### Expander — single expandable block, similar to Accordion.
#### Average Rating / Review — star display + numeric score + count.

---

### 9.4 — Feedback

#### Alert Banner — full-width strip, info/success/warning/error variants.
#### Announcement Bar — slim top ribbon, priority colour.
#### Skeleton — shimmer animation `grayCool[10]→grayCool[20]` for loading states.
#### Snackbar / Toast
- Fixed bottom-center · `elevation[2]` · `radius.md` · auto-dismiss 3–5s
- Max-width ~480px desktop

---

### 9.5 — Navigation

#### Breadcrumb — `/` separator, last item not linked, previous items `color.primary`.

#### Header (Main Domain)
- White bg · `elevation.raiseBottom` sticky shadow · height ~92px
- Logo left, nav centre/right, CTA button far right

#### Header (Sub-domain) — ~64px, sub-brand identity.

#### Mega Navmenu — full-width panel, `elevation[2]`, columns of links.

#### Side Navmenu
- Active: `bgSubtle` bg + left border `borderPrimary` + `color.primary` text, weight 600
- Item height: ~48px

#### Simple / In-page Navmenu — horizontal tabs or vertical list, active = teal-10 bg.

#### Pagination — active page: `color.primary` bg, white text, `radius.md`.

#### Footer / Pre-footer — dark bg (`grayCool[90]`/`[100]`), white text, multi-column.

---

### 9.6 — Structure & Sheets

#### Modal — `elevation[3]` · `radius.lg` (16px) · backdrop `rgba(19,21,26,0.8)` · 480–720px wide
#### Drawer — slides from right, `elevation[3]`, `transition.standard`, 320–480px wide
#### Divider — `1px solid ${color.borderLighter}`
#### Scrim — `rgba(19,21,26,0.8)` full-viewport overlay under modals/drawers

---

## 10. Focus Ring (Accessibility)

Apply to ALL interactive elements:

```js
// CSS
// outline: 3px solid rgba(45, 148, 158, 0.2);
// outline-offset: 2px;
const focusRing = `outline: 3px solid ${brand[50]}33; outline-offset: 2px;`;
```

---

## 11. React Artifact Template

```jsx
import { useState } from "react";

const brand={10:"#E9F4F5",20:"#CEE6E8",30:"#9FCED3",40:"#6BB3BA",50:"#2D949E",60:"#03727D",70:"#02545D",80:"#013D43",90:"#01282C",100:"#01181B"};
const grayCool={0:"#FFFFFF",10:"#F2F3F5",20:"#DEE1E7",30:"#C1C6D1",40:"#9FA8B9",50:"#7C879F",60:"#5C677E",70:"#444C5D",80:"#323743",90:"#21242C",100:"#13151A"};
const color={bgDefault:"#FFFFFF",bgSubtle:brand[10],bgOverlay:grayCool[10],bgAlternate:grayCool[10],bgDisabled:"#F0F1F2",borderLighter:grayCool[20],borderPrimary:brand[60],borderNegative:"#CC1616",borderInverse:"#FFFFFF",typeHeaderDark:grayCool[100],typeHeaderLight:grayCool[90],typeLabelDark:grayCool[80],typeLabelLight:grayCool[60],typeBodyLight:grayCool[70],typeHelper:brand[50],typeDisabled:brand[30],typeInverse:"#FFFFFF",iconDefault:brand[50],iconDark:brand[70],primary:brand[60],primaryHover:brand[70],primaryActive:brand[80],primarySubtle:brand[10],negative:"#CC1616",positive:"#1E7F34"};
const sp={0:0,1:2,2:4,3:8,4:12,5:16,6:20,7:24,8:32,9:48,10:64,11:96,12:128};
const radius={sm:4,md:8,lg:16,full:512};
const font="'Lexend',system-ui,sans-serif";
const elevation={1:"0px 0px 2px rgba(19,21,26,0.04),0px 2px 12px rgba(19,21,26,0.08),0px 4px 4px -2px rgba(19,21,26,0.08)",2:"0px 0px 2px rgba(19,21,26,0.04),0px 2px 12px rgba(19,21,26,0.08),0px 16px 16px -8px rgba(19,21,26,0.08)",3:"0px 0px 2px rgba(19,21,26,0.04),0px 2px 12px rgba(19,21,26,0.08),0px 24px 24px -12px rgba(19,21,26,0.08)"};
const transition={entrance:"all 200ms cubic-bezier(0.15,0.6,0.6,1)",exit:"all 200ms cubic-bezier(0.1,0,0.5,0)",standard:"all 350ms cubic-bezier(0.25,0,0.25,1)",fast:"all 120ms ease"};

export default function MyComponent() {
  return (
    <>
      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=Lexend:wght@300;400;600;700&display=swap');
        *{box-sizing:border-box;margin:0;padding:0}
        ::-webkit-scrollbar{width:4px}
        ::-webkit-scrollbar-track{background:transparent}
        ::-webkit-scrollbar-thumb{background:#CEE6E8;border-radius:2px}
      `}</style>
      <div style={{fontFamily:font, background:color.bgOverlay, minHeight:"100vh"}}>
        {/* content here */}
      </div>
    </>
  );
}
```

---

## 12. Pattern Library & Icon Library

Detailed specs for the Pattern Library (layout blocks, panels, templates) and the Icon Library are in separate reference files. Read them when building page-level layouts or when you need icon usage rules.

- `references/pattern-library.md` — Layout Blocks, Content Blocks, Panels, Templates
- `references/icon-library.md` — Icon styles (outline/solid), sizes, naming, common icons, spot illustrations

**When to read `references/pattern-library.md`:**
- User asks for a "listing page", "detail page", "landing page", "hub page", or similar page-level layout
- User asks for an "info card", "result card", "filter column", "hero", or any named pattern
- User asks to build a full page template

**When to read `references/icon-library.md`:**
- User asks which icon style to use (outline vs solid)
- User needs to find an icon by name or purpose
- User asks about icon sizes or how icons are tokenised

---

## 13. Figma Source Files

| File                   | URL + key nodes                                                                          |
|------------------------|------------------------------------------------------------------------------------------|
| **Zero Foundation**    | https://www.figma.com/design/LJlM5kM0AfYE83vPz23CMf/Zero-Foundation                    |
| → Color palette        | node `332-7922` — Neutral gray + Cool gray                                               |
| → Elevation            | node `544-9068` — 3-level shadows + usage map                                            |
| → Grid                 | node `336-9144` — 12-col, 1440px, 132px margins                                          |
| → Border               | node `335-9055` — radius (0/4/8/16/512px) + width (1/2/4px)                              |
| → Spacing              | node `334-8719` — spacing-0 → spacing-12                                                 |
| → Motion               | node `1035-1160` — entrance/exit/standard curves                                         |
| → Typography           | node `318-15768` — Lexend scale + principles                                             |
| **Zero Component Library** | https://www.figma.com/design/48cSN8wRRPb51bvzP6BBBC/Zero-Component-Library          |
| → Button               | node `157-18245` · Chip `13103-14918` · Icon Button `155-13033` · Link `57-3833`        |
| → Accordion `887-22313` · Avg Rating `7950-40583` · Callout `1509-88294` · Card `3270-12355` |
| → Icon List `7850-52693` · Expander `9440-14396` · Desc List `10673-13448` · Image Card `1449-84556` |
| → List `9149-121829` · Review `7879-14036` · Table `12741-21827` · Tooltip `2391-5720` |
| → Checkbox `781-45134` · Combobox `13112-20384` · Date Picker `899-35778` · Radio `6357-32274` |
| → Rating `7362-39190` · Search `908-7894` · Select `878-17283` · Text Area `13233-77507` · Text Field `873-12688` |
| → Alert Banner `12947-17566` · Announcement `2449-8429` · Info Tag `886-20172` · Skeleton `8096-46216` · Snackbar `12980-23945` |
| → Breadcrumb `31-1467` · Footer `381-9935` · Pre-footer `11376-38969` · Header Main `11006-18544` · Header Sub `11365-21023` |
| → In-page Nav `4130-56242` · Mega Nav `11081-16546` · Mobile Nav `11119-31160` · Pagination `908-3728` |
| → Side Nav `411-3691` · Simple Nav `600-41957` · Subdomain Nav `4096-19814` |
| → Modal `13024-10297` · Divider `2407-9742` · Drawer `13030-136996` · Scrim `13031-139704` |
| **Zero Pattern Library** | https://www.figma.com/design/a7hOP4X9XYINnBwzlnWkXW/Zero-Pattern-Library — see `references/pattern-library.md` |
| **Zero Icon Library**  | https://www.figma.com/design/No1ah7cbT62NoMFsXmo1re/Zero-Icon-Library — see `references/icon-library.md`        |

> To refresh any token or component spec, call `Figma:get_design_context` with the
> relevant fileKey + nodeId, then update the relevant section above.
