# Zero Pattern Library

Patterns are pre-composed assemblies of Foundation tokens + Component Library pieces that solve recurring page-level design problems. They have **defined positions within templates**.

Figma file: https://www.figma.com/design/a7hOP4X9XYINnBwzlnWkXW/Zero-Pattern-Library

---

## 01 Layout Blocks

Layout blocks are reusable structural sections placed at fixed positions within a page template.

### Basic Page Detail (node `7539-31274`)
The standard opening block for any content/detail page.

**Anatomy** (desktop, max-width 744px content column):
- **A. Breadcrumb** — 4-tier max, links in `color.primary (#03727D)`, current page in `typeLabelDark`, `labelMdReg` (14px), chevron separator icon (20px)
- **B. Page Title** — `displayMd` (40px/700/–1px tracking), `typeHeaderDark (#13151A)`
- **C. Page Description** — `bodyLg` (20px/400), `typeBodyLight (#444C5D)`, max ~100 chars
- **D. Image** (optional) — 320px height, `radius.md` (8px), full-width of content column

**Layout:** All elements stacked vertically, `gap: sp[8]` (32px) between sections. Description immediately below title, image below description.

---

### Info Card (node `9508-26101`)
A compact data-display card — used in dashboards, course directories, summary panels.

**Dimensions:** Width 320px, white bg, `elevation[3]` shadow, `radius.md` (8px)

**Anatomy:**
- **A. Tooltip** (optional) — `outline/information-circle` icon (20px) beside label
- **B. Label** — `labelMdReg` (14px), `typeLabelLight (#5C677E)`
- **C. Data (primary)** — `headingMdSemi` (24px/600), `typeHeaderDark (#13151A)`
- **D. Prefix** (optional) — small text before data value, `labelSmSemi` (12px)
- **E. Supporting data** (optional) — secondary label+value row below primary data
- **F. Footnote** (optional) — `captionReg` (12px), `typeLabelLight`, max 100 chars
- **G. Divider** — `1px solid borderLighter` separating primary from secondary content
- **H. Sub header** (optional) — `labelLgSemi` (16px/600), max 80 chars
- **I. Description** (optional) — `labelMdReg` (14px), `typeBodyLight`, max 150 chars
- **J. List – icons** (optional) — `IconListGroup` component (vertical, gap 8px), icon 20px + `labelMdReg` text
- **K. Action button** (optional) — full-width Primary button in card footer
- **L. Shadow / elevation** — `elevation[3]`

**Internal spacing:** Padding `sp[7]` (24px) on all sides, `sp[6]` (20px) gap between data groups.

---

### Filter Column (node `7925-18750`)
Left-side filter panel used on listing/search pages. Contains filter groups (checkboxes, toggles, chips) stacked vertically.

---

### Listing Page Detail (node `9216-66919`)
Combined layout: filter column (left) + result cards grid (right), used for search/browse pages.

---

### Result Card (node `7969-20071`)
Card used within listing pages to represent a single search result. Typically: title, metadata tags, description snippet, CTA link.

---

### Reviews (node `8353-19266`)
A reviews/ratings section block: average star rating + individual review cards in a list.

---

### Floating Actions (node `10039-55017`)
Sticky floating action button (FAB) or action bar — anchored to the bottom-right or bottom of the viewport. Used for primary or contextual actions that persist while scrolling.

---

## 02 Content Blocks

Reusable copy-and-media content sections placed within the page body.

### Text (node `7616-42415`)
Pure text content block — heading, body copy, optional link. No media. Max content width 744px.

### Single (node `4168-16787`)
One content item with image + text side by side (or stacked on mobile).

### Group (node `4141-68833`)
Multiple content items in a grid (typically 2–3 columns). Each item: icon or image + heading + body text.

### Custom (node `4274-38535`)
Flexible content block for non-standard compositions.

---

## 03 Panels

Full-width (1440px desktop) sections used to create visual rhythm and hierarchy on a page. Each panel has desktop and mobile variants.

### Hero Panel (node `8855-11578`)
The primary above-the-fold section — split layout: text left, image right.

**Anatomy (desktop, 1440×448px):**
- **Container** — horizontal flex, `bg-gradient-to-b from-white to #E9F4F5` (brand[10])
- **A. Text wrap** (left half, ~720px): flex-col, right-padded `sp[8]` (32px), vertically centred
  - **B. Header** — `displayLg` (48px/700/–1px tracking), `color.primary (#03727D)`, max 60 chars
  - **C. Description** (optional) — `headingSmLight` (20px/300), `typeHeaderLight (#21242C)`, max 100 chars
  - **D. Action button** (optional) — Primary Large button (`px: sp[7]`, `py: sp[4]`, 16px semibold)
- **E. Image wrap** (right half) — full bleed, `object-cover`

**Mobile (375px wide):** Stacks vertically — text block top, image block below (288px height). Header shrinks to `displaySmBold` (32px/700/–0.4px tracking).

**Key tokens used:**
```js
// Hero gradient
background: `linear-gradient(to bottom, #FFFFFF, ${brand[10]})` // #E9F4F5

// Desktop header
{ fontSize: 48, fontWeight: 700, lineHeight: "56px", letterSpacing: "-1px", color: brand[60] }

// Mobile header  
{ fontSize: 32, fontWeight: 700, lineHeight: "40px", letterSpacing: "-0.4px", color: brand[60] }
```

---

### Hero Panel (GB Subdomain Restricted) (node `12776-46029`)
Variant of the Hero Panel for GovTech subdomain — uses restricted branding.

### Text Panel (node `7504-10594`)
Full-width panel with centred text content only. Used for editorial sections, callouts, or between content zones.

### Full Image Panel (node `7504-1318`)
Full-width image with overlaid text. Image stretches to panel edges.

### Half Image Panel (node `7504-4484`)
50/50 split — image on one side, text on the other. Can be image-left or image-right.

### Blockquote (node `7503-54467`)
Pull-quote/blockquote panel — large quotation text centred or left-aligned, with optional attribution.

### Carousel Panel (node `10036-36460`)
Full-width panel with horizontally scrollable cards. Includes prev/next navigation controls.

### Topic Panel (node `12346-10739`)
Grid of topic/category cards — icon + label, used for navigation or category browsing.

### Quicklinks Panel (node `12353-23024`)
A row or grid of short link items — icon + label, for fast navigation to key pages.

---

## 04 Templates

Full-page layout templates composed of Layout Blocks, Content Blocks, and Panels.

### Landing (node `4366-16306`)
Marketing/entry page — typically: Hero Panel → Content Blocks (Group) → CTA Panel → Footer.

### Hub (node `4623-29048`)
Category landing page — Hero Panel → Topic Panel → Listing grid → Footer.

### Info Page (node `4141-67955`)
Long-form informational content — Basic Page Detail header → Text/Single content blocks → Footer.

### User Guide (node `4274-15042`)
Step-by-step instructional page — numbered sections, Text blocks, optional images.

### Search Results (node `9464-20188`)
Search experience — Search input top → Filter Column left + Result Cards grid right → Pagination → Footer.

### Error Page (node `6153-16475`)
404 / 500 error — centered illustration + heading + description + primary CTA button.

---

## Figma Node Reference

| Pattern | Node ID |
|---------|---------|
| Filter Column | `7925-18750` |
| Basic Page Detail | `7539-31274` |
| Info Card | `9508-26101` |
| Listing Page Detail | `9216-66919` |
| Result Card | `7969-20071` |
| Reviews | `8353-19266` |
| Floating Actions | `10039-55017` |
| Text (content block) | `7616-42415` |
| Single (content block) | `4168-16787` |
| Group (content block) | `4141-68833` |
| Custom (content block) | `4274-38535` |
| Blockquote panel | `7503-54467` |
| Carousel panel | `10036-36460` |
| Full Image panel | `7504-1318` |
| Half Image panel | `7504-4484` |
| Hero Panel (GB subdomain) | `12776-46029` |
| Hero Panel | `8855-11578` |
| Text panel | `7504-10594` |
| Topic panel | `12346-10739` |
| Quicklinks panel | `12353-23024` |
| Error page template | `6153-16475` |
| Landing template | `4366-16306` |
| Hub template | `4623-29048` |
| Info page template | `4141-67955` |
| Search results template | `9464-20188` |
| User guide template | `4274-15042` |
