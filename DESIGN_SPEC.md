# Alpina Brew — Visual Design Specification

**Reference Image Source:** User-provided inspiration graphic (`media_1793700794612_0cb8ae87.jpg`)  
**Design Mood:** Whimsical artisan meets premium botanical tea atelier  
**Brand Identity:** Alpina Brew — Single-origin Himalayan teas, ceremonial matcha, and botanical infusions  

---

## 1. Visual Language & Atmosphere Analysis

The reference image captures a distinctive aesthetic balancing **fresh Japanese tea garden tranquility** with **warm artisan craftsmanship**:

1. **Background Atmosphere**:
   - Primary surface: Refreshing pale matcha/mint mist.
   - Texture: Flowing, organic contour lines (similar to tea leaf veins or topographic garden curves) drawn in delicate semi-transparent sage strokes across the viewport.
   - Feeling: Calm, breathable, natural, high-end yet warm and approachable.

2. **Contrast & Color Harmonization**:
   - The cool, serene matcha/mint base is grounded by a warm **terracotta / cedar wood medallion** behind the main tea vessel.
   - This prevents the design from feeling cold or clinical; the warm terracotta invites tactile comfort and evokes earthenware teaware and wood-fired tea roasting.

3. **Illustration & Visual Centerpiece**:
   - Handcrafted tea kettle tilted at an inviting pour angle into a ceramic cup.
   - Steaming droplets of vibrant jade/matcha tea with playful glossy highlights.
   - Teacup detailed with speckled clay dots, striped artisan handle, and tea bag hanging tag.
   - Radiating botanical accents / accent sparkles celebrating the vitality of fresh tea.

4. **Typography & Layout Architecture**:
   - Logo Lockup: Distinctive framed badge (e.g., stacked "ALPINA" / "BREW" inside a rounded badge frame with dark pine green accent).
   - Navigation: Clean, letter-spaced uppercase links (`HOME`, `ABOUT US`, `RECIPES`, `CONTACT`) with active indicator underline and a pill CTA button (`SIGN IN`).
   - Content Hierarchy:
     - Prominent headline: "Matcha Tea" / "Alpina Reserve" in rich organic bold letterforms.
     - Welcoming subheading: "Subscribe and taste the new flavor first!".
     - Refined, easy-to-read descriptive paragraph.
     - Inline subscription / tasting sample form with pill input fields and a pill "CONFIRM" CTA button.
   - Social Floating Anchors: Discrete circular badges (WhatsApp, Facebook, Instagram) in dark forest green.

---

## 2. Color Palette Specification

| Token Name | Hex Code | Role & Usage | Fallback / Contrast Notes |
| :--- | :--- | :--- | :--- |
| `--color-alpina-mint` | `#CCEBD7` / `#D4F1E0` | Primary page background | Meets contrast with deep green text |
| `--color-alpina-deep-forest` | `#0C4A34` | Primary brand text, headings, logo badge, icon frames | AAA contrast against mint backgrounds |
| `--color-alpina-emerald` | `#059669` | Active state underlines, accents, tags | Interactive highlights |
| `--color-alpina-teal-cta` | `#00BFA5` / `#14B8A6` | Primary CTA pill buttons, active sign-in button | Crisp, energetic conversion button |
| `--color-alpina-terracotta` | `#D97736` / `#C86432` | Warm terracotta medallion, artisan badges, sale tags | Warm complement to green base |
| `--color-alpina-sand-cream` | `#FBFDF9` | Input field background, card surfaces, modal sheets | Clean white-tinted cream |
| `--color-alpina-charcoal-muted`| `#3D5A4C` | Secondary body text, captions, brewing notes | AA accessible contrast |
| `--color-alpina-border` | `rgba(12, 74, 52, 0.12)` | Subtle card borders, input borders, dividers | Refined delicate structure |

---

## 3. Typography Hierarchy

- **Primary Headings (H1, H2, H3)**:
  - Font Family: High-elegance modern serif or humanist grotesque (configurable in Theme Editor, defaulting to `Playfair Display`, `Cormorant Garamond`, or refined modern serif).
  - Letter Spacing: `-0.02em` on large titles, `0.05em` on uppercase badges.
  - Weight: SemiBold (600) / Bold (700).
- **Body & Product Meta**:
  - Font Family: Clean, readable sans-serif (e.g., `Work Sans`, `Plus Jakarta Sans`, `Inter`).
  - Line Height: `1.6` for optimal readability across device sizes.
  - Weights: Regular (400) for prose, Medium (500) for labels, SemiBold (600) for prices and variant chips.
- **Micro-Copy & Badges**:
  - Uppercase `0.08em` tracking, 11px-13px font size.

---

## 4. Spacing, Geometry & Component Design

- **Corner Radii**:
  - Buttons: Full pill radius (`9999px`) matching the inspiration image.
  - Form Inputs: Pill or smooth rounded (`24px` to `9999px`).
  - Cards & Containers: `16px` to `24px` soft rounded edges.
  - Medallions: Perfect circle (`50%`).
- **Wavy Line Backgrounds**:
  - Modular SVG background pattern with organic curved lines injected via CSS or configurable section setting.
- **Shadows**:
  - Subtle diffuse ambient shadows: `box-shadow: 0 10px 25px -5px rgba(12, 74, 52, 0.08), 0 8px 10px -6px rgba(12, 74, 52, 0.04)`.
  - Button elevation on hover: `transform: translateY(-2px); box-shadow: 0 12px 20px -4px rgba(0, 191, 165, 0.3)`.

---

## 5. Responsive Adaptation Rules

### Desktop (≥ 1024px)
- Split hero: Hero visual on the left (50%), copy + subscription/CTA on the right (50%).
- Full horizontal navigation with logo badge, centered menu links, and right utility cluster.
- Generous container margins (max width `1280px` to `1440px`).

### Tablet (768px – 1023px)
- Hero scales gracefully; tea medallion scales to `380px` diameter.
- 2-column product grids and 2-column feature blocks.
- Collapsible navigation or drawer menu when viewport constraints require.

### Mobile (≤ 767px) — Priority
- Single column stacked layout:
  1. Header with brand badge, search trigger, account icon, and cart badge.
  2. Hero headline and hook presented first with high contrast for immediate context.
  3. Centered, beautifully scaled tea kettle & cup illustration / photo with responsive terracotta medallion (scaled to 260px-300px width).
  4. Lead paragraph + mobile-optimized touch-friendly input fields (48px tap targets) + full-width CTA button.
  5. Floating or dock social bar.
- Product cards: Crisp 2-column grid or fluid 1-column cards with swipeable image galleries.
- Sticky bottom Add-to-Cart bar on product pages on mobile devices.
