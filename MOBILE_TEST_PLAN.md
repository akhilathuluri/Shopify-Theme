# Alpina Brew — Mobile-First Test Plan

**Standard:** Responsive, Touch-Optimized, Accessible, Zero Layout Shifts  
**Target Viewports:** 320px, 360px, 375px, 390px, 414px, 430px, 768px, 1024px, 1440px  

---

## 1. Viewport & Breakpoint Testing Matrix

| Breakpoint / Device | Width | Expected Layout Behavior | Pass/Fail Criteria |
| :--- | :--- | :--- | :--- |
| **Small Phone (iPhone SE)** | 320px – 375px | Single column hero, logo badge scales to 36px, search/cart icons intact, zero overflow. | No horizontal scroll (`document.documentElement.scrollWidth <= window.innerWidth`). |
| **Standard Phone (iPhone 14/15)**| 390px – 430px | Split elements stack gracefully; tea kettle illustration scales without clipping; CTA button full width. | All text readable (≥ 15px body); touch targets ≥ 48px × 48px. |
| **Phablet / Large Phone** | 414px – 480px | 2-column compact product grid or 1-column featured cards with horizontal scroll chips. | Image aspect ratio 1:1 or 4:5 preserved without distortion. |
| **Tablet Portrait (iPad Mini/Air)**| 768px – 834px | 2-column or 3-column product grid; drawer navigation or condensed horizontal menu. | Smooth drawer open/close; sticky cart accessible. |
| **Tablet Landscape / Small Laptop**| 1024px – 1280px | Split hero (tea medallion left, copy right); full horizontal nav; 4-column product grid. | Ample padding (≥ 32px margins); no cramped elements. |
| **Desktop / Widescreen** | 1440px – 1920px | Contained max-width (1280px or 1400px); centered layout with rich botanical margins. | Crisp SVG rendering; no blurry assets. |

---

## 2. Touch & Interaction Testing Checklist

- [ ] **Mobile Navigation Drawer**:
  - [ ] Hamburger button opens drawer smoothly without lag.
  - [ ] Close button ('X') and backdrop overlay tap close drawer reliably.
  - [ ] Focus trapped inside drawer when open; `aria-expanded` and `aria-hidden` update correctly.
  - [ ] Page scroll is locked behind open drawer.
- [ ] **Mobile Hero Section**:
  - [ ] "Subscribe and taste the new flavor first!" input fields easy to tap with native virtual keyboard.
  - [ ] Form submission doesn't zoom in iOS Safari (font-size ≥ 16px on inputs).
  - [ ] Terracotta medallion and teapot visual centered above or below text block without vertical overcrowding.
- [ ] **Product Variant & Pack Size Selection**:
  - [ ] Weight chips (`100g`, `250g`, `500g`) tap easily with instant visual state feedback (active border/background).
  - [ ] Price updates immediately when switching variant.
  - [ ] Sold-out variants clearly visually disabled with strikethrough and non-clickable state.
- [ ] **Cart Drawer / AJAX Add-to-Cart**:
  - [ ] Tapping "Add to Cart" provides immediate feedback (spinner or success checkmark).
  - [ ] Cart drawer slides in from the right smoothly without page reload.
  - [ ] Quantity increment (`+`) and decrement (`-`) buttons respond cleanly with debounce.
  - [ ] Removing line item animates smoothly and updates subtotal and header cart count.
- [ ] **Accordions & Disclosures (Brewing Guide & FAQs)**:
  - [ ] Smooth expand/collapse animation without layout jitter.
  - [ ] Keyboard accessible (Enter and Space toggle accordion).
- [ ] **Checkout Transition**:
  - [ ] Checkout button navigates smoothly to Shopify's secure `/checkout`.
  - [ ] Zero blocking scripts or third-party interference on mobile redirect.

---

## 3. Performance & Core Web Vitals (Mobile)

- **LCP (Largest Contentful Paint)**: Main hero image preloaded with `fetchpriority="high"` and proper `sizes` attribute. Target: < 2.5s on 4G.
- **CLS (Cumulative Layout Shift)**: Explicit `width` and `height` attributes on all images and SVGs. Target: < 0.1.
- **FID / INP (Interaction to Next Paint)**: Zero heavy JavaScript bundles; pure vanilla JS for drawers and selectors. Target: < 100ms.
- **Theme Check Compliance**: 0 errors, 0 warnings on mobile markup rules.
