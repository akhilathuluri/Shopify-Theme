# Changelog — Alpina Brew Theme Development

All notable changes to the Alpina Brew Shopify Online Store 2.0 theme are documented in this file.

---

## [1.0.0] - Complete Storefront Implementation

### Added
- **Design System & Visual Identity**:
  - Palette inspired directly by reference: Pale Matcha Mist (`#D4F1E0`), Deep Forest (`#0C4A34`), Vibrant Teal CTA (`#00BFA5`), Terracotta Clay (`#D97736`), Soft Alternate Green (`#EBF7EE`), Card White (`#FFFFFF`).
  - `assets/tea-illustration.svg`: High-resolution vector reproduction of the inspiration reference's artisan wood-slat medallion, tilted teapot, steaming jade tea splashes, and speckled ceramic teacup with tea tag.
  - `assets/wavy-background.svg`: Organic topography / botanical wave curves.
  - Complete SVG icon suite: `icon-search.svg`, `icon-cart.svg`, `icon-close.svg`, `icon-whatsapp.svg`, `icon-facebook.svg`, `icon-instagram.svg`, `icon-leaf.svg`, `icon-check.svg`.
  - Global theme settings schema (`config/settings_schema.json` & `config/settings_data.json`) with autonomous per-section color controls, typography scale, pill button radii, and social links.
  - `snippets/css-variables.liquid`: Dynamic CSS custom property generation from merchant settings.
  - `assets/critical.css`: Lightweight, mobile-first CSS architecture with grid containers, typography, pill buttons, input pills, and WCAG focus states.

- **Header, Navigation & Alpina Hero Section**:
  - `sections/announcement-bar.liquid`: Announcement ticker with free shipping threshold notices and customizable colors.
  - `sections/header.liquid`:
    - Distinctive Alpina Brew framed badge logo ("ALPINA / BREW").
    - Clean uppercase navigation links with active indicator underline.
    - "SIGN IN" pill CTA button in vibrant teal (`#00BFA5`).
    - Predictive search trigger, cart bag icon with reactive item count badge.
    - Touch-optimized slide-out mobile drawer menu with search bar and social links.
  - `sections/hero-alpina.liquid`:
    - Faithful reproduction of inspiration image with split desktop layout and responsive mobile stack.
    - Artisan teapot and cup illustration with fallback/toggle for custom photography.
    - Headline, hook, paragraph, inline customer newsletter/sample form ("Name", "Email", "CONFIRM" CTA pill).
    - Bottom-left docked circular social icons (WhatsApp, Facebook, Instagram).

- **Homepage Conversion Sections**:
  - `sections/tea-benefits.liquid`: 4-column value proposition blocks (Single Estate, High Altitude 6,200ft, Whole Leaf, Direct Fair Trade).
  - `sections/featured-collection.liquid`: Bestselling teas grid with interactive product cards (`snippets/product-card.liquid`), price snippet (`snippets/price.liquid`), stock badges, and view all button.
  - `sections/brewing-guide.liquid`: Master steeping parameters (water temperature, steep time, leaf ratio, tasting notes).
  - `sections/why-choose-us.liquid`: Terroir storytelling section with floating altitude badge ("6,200 Feet Altitude").
  - `sections/testimonials.liquid`: Verified customer & sommelier reviews with 5-star ratings.
  - `sections/newsletter.liquid`: Alpina Tea Society subscription card with 15% discount hook.
  - `sections/footer.liquid`: Muted forest green footer with brand ethos, quick links, policies, customer concierge, and Indian payment methods.
  - `templates/index.json`: Full homepage ordering configured.

- **Product Detail Page (PDP) & Catalog**:
  - `sections/product.liquid` & `templates/product.json`: Full PDP with image gallery & interactive thumbnails, dynamic price in INR (`₹`), interactive pack size variant selection (`100g`, `250g`, `500g`), quantity stepper, stock status, Add to Cart, Buy Now (`payment_button`), trust badges, and accordion tabs for tasting notes, brewing guide, and ingredients.
  - `sections/collection.liquid` & `templates/collection.json`: Collection catalog with sorting, product count, responsive grid, and pagination.

- **Shopping Journey & Storefront Supporting Pages**:
  - `sections/cart.liquid` & `templates/cart.json`: Full cart page with free shipping progress bar, line items, quantity controls, order notes, order summary, and checkout button.
  - `sections/search.liquid` & `templates/search.json`: Predictive search results with popular tea keyword chips.
  - `sections/404.liquid` & `templates/404.json`: Branded 404 page.
  - `sections/contact-form.liquid` & `templates/page.contact.json`: Full contact page with native Shopify form and atelier details.
  - `sections/faq-accordion.liquid` & `templates/page.faq.json`: Interactive accordion FAQ page.
  - `sections/main-about.liquid` & `templates/page.about.json`: About Us estate story.
  - `snippets/profile-completion-banner.liquid`: Non-blocking profile completion banner for New Customer Accounts.

### Verified
- Ran `shopify theme check`: **58 files inspected with 0 offenses found (0 errors, 0 warnings)**.

### Fixed
- Unnested `{% stylesheet %}` and `{% javascript %}` tags from `{% if customer %}` in [`snippets/profile-completion-banner.liquid`](file:///e:/tea-store/snippets/profile-completion-banner.liquid) to comply with Liquid top-level tag syntax requirements.

### Enhanced
- **Hero Alpina Carousel**:
  - Transformed [`sections/hero-alpina.liquid`](file:///e:/tea-store/sections/hero-alpina.liquid) into a modular, multi-slide hero carousel with repeatable `slide` blocks.
  - Enabled custom background image upload per slide with an adjustable overlay slider to ensure text readability.
  - Added support for both lead-capture newsletter forms and direct product action buttons per slide.
  - Included smooth desktop navigation arrows, interactive pagination dots, touch/swipe gesture recognition on mobile, and autoplay interval controls.
  - Reordered slides and replaced the lead capture form with a dedicated product showcase:
    - **Slide 1**: Himalayan First Flush (Single Estate 6,200ft, tasting notes, price badge, and "EXPLORE FIRST FLUSH" CTA).
    - **Slide 2**: Ceremonial Matcha Tea (Shade-grown spring tencha, umami froth notes, price badge, and "SHOP CEREMONIAL MATCHA" CTA).
