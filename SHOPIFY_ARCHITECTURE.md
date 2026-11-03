# Alpina Brew — Shopify Architecture

**Platform:** Shopify Online Store 2.0  
**Store Plan:** Shopify Basic (India)  
**Currency:** INR (`₹`)  
**Payment Gateway:** Official Razorpay Shopify Integration  

---

## 1. Directory Structure

```
E:\tea-store\
├── assets/
│   ├── critical.css                # Base critical styles, resets, typography variables
│   ├── theme.css                   # Global component and utility classes
│   ├── theme.js                    # Mobile drawer, cart drawer, variant selector, micro-interactions
│   ├── wavy-background.svg         # Organic topographic tea background pattern
│   ├── icon-account.svg            # Account SVG icon
│   ├── icon-cart.svg               # Cart bag SVG icon
│   ├── icon-search.svg             # Search glass SVG icon
│   ├── icon-close.svg              # Close / dismiss SVG icon
│   ├── icon-leaf.svg               # Botanical leaf accent
│   ├── icon-whatsapp.svg           # WhatsApp social icon
│   ├── icon-facebook.svg           # Facebook social icon
│   └── icon-instagram.svg          # Instagram social icon
├── blocks/
│   ├── text.liquid                 # Text block with rich typography controls
│   ├── button.liquid               # Customizable CTA button
│   ├── group.liquid                # Layout container block
│   ├── accordion-item.liquid       # FAQ accordion item
│   └── tea-feature-item.liquid     # Icon + headline + description tea benefit block
├── config/
│   ├── settings_schema.json        # Global color schemes, typography, layout, radii, social links
│   └── settings_data.json          # Default values for Alpina Brew aesthetic
├── layout/
│   ├── theme.liquid                # Global layout with header-group, content_for_layout, footer-group
│   └── password.liquid             # Password page layout
├── locales/
│   ├── en.default.json             # Core English translations
│   └── en.default.schema.json      # Theme editor translations schema
├── sections/
│   ├── header-group.json           # Header section group (Announcement bar + Header)
│   ├── announcement-bar.liquid     # Shipping notice, discount banner, multi-message ticker
│   ├── header.liquid               # Sticky/transparent header with logo badge, navigation, cart count
│   ├── hero-alpina.liquid          # Custom hero matching inspiration image (Tea visual + Form CTA)
│   ├── featured-collection.liquid  # Product grid with quick add, variant badges, rating
│   ├── tea-benefits.liquid         # 3/4 column botanical benefits (100% Organic, Himalayan Origin, etc.)
│   ├── why-choose-us.liquid        # Storytelling section with image and key value propositions
│   ├── brewing-guide.liquid        # Visual steeping guide (water temp, time, leaf grams)
│   ├── tea-menu-highlights.liquid  # Curated menu list with flavor profiles and notes
│   ├── lifestyle-gallery.liquid    # Visual tea lifestyle photo grid / mosaic
│   ├── testimonials.liquid         # Verified tea connoisseur reviews slider/grid
│   ├── newsletter.liquid           # Email subscription with botanical styling
│   ├── footer-group.json           # Footer section group
│   ├── footer.liquid               # Multi-column footer with social icons, policies, newsletter
│   ├── main-product.liquid         # Rich product page (gallery, variants, pack size, brewing specs, accordion)
│   ├── main-collection.liquid      # Filterable, sortable collection grid with pagination
│   ├── main-cart.liquid            # Full cart page with line items, note, subtotal, checkout button
│   ├── cart-drawer.liquid          # Slide-out AJAX cart drawer
│   ├── main-page.liquid            # Standard rich text page layout
│   ├── main-about.liquid           # About Us brand story & estate heritage
│   ├── main-contact.liquid         # Contact form with phone, email, map, address
│   ├── main-faq.liquid             # Interactive accordion FAQ section
│   ├── main-search.liquid          # Predictive search results grid
│   └── main-404.liquid             # Elegant 404 page with return to shop button
├── snippets/
│   ├── css-variables.liquid        # Theme editor CSS custom property injection
│   ├── meta-tags.liquid            # SEO, OpenGraph, Twitter card tags
│   ├── image.liquid                # Responsive image helper with srcset and sizes
│   ├── product-card.liquid         # Modular tea product card (image, title, price, variants, add to cart)
│   ├── price.liquid                # Formatted price snippet (regular, sale, unit price)
│   ├── icon.liquid                 # SVG icon renderer helper
│   ├── social-icons.liquid         # WhatsApp, Facebook, Instagram circular link group
│   └── structured-data.liquid      # Schema.org JSON-LD for Products, Organization, BreadcrumbList
└── templates/
    ├── index.json                  # Homepage section layout & order
    ├── product.json                # PDP section layout (main-product, brewing guide, recommendations)
    ├── collection.json             # Collection page section layout
    ├── cart.json                   # Cart page layout
    ├── page.json                   # Standard static page layout
    ├── page.about.json             # About page template
    ├── page.contact.json           # Contact page template
    ├── page.faq.json               # FAQ page template
    ├── search.json                 # Search page template
    ├── 404.json                    # 404 template
    └── password.json               # Storefront password template
```

---

## 2. Global Design System & Section Color Control

### Settings Schema (`config/settings_schema.json`)
1. **Color System**:
   - `color_background`: Default page background (`#D4F1E0` / mint mist).
   - `color_text`: Primary body text (`#0C4A34` / deep forest).
   - `color_headings`: Heading text (`#0C4A34`).
   - `color_accent`: Vibrant accent (`#059669`).
   - `color_cta`: Primary button background (`#00BFA5`).
   - `color_cta_text`: Primary button text (`#0C3827` or `#FFFFFF`).
   - `color_card_bg`: Surface card background (`#FFFFFF`).
   - `color_terracotta`: Secondary accent / terracotta (`#D97736`).
   - `color_border`: Subtle borders (`rgba(12, 74, 52, 0.12)`).
2. **Typography**:
   - `type_header_font`: Shopify font picker for headings.
   - `type_body_font`: Shopify font picker for body.
   - Base font sizes, line heights, letter spacing.
3. **Layout & Radii**:
   - `max_page_width`: 1200px / 1400px.
   - `button_border_radius`: 9999px (pill).
   - `input_border_radius`: 9999px (pill) / 24px.
   - `card_border_radius`: 16px / 20px.

### Per-Section Color Control Architecture
Every major section includes a schema settings block for color autonomy:
- `use_custom_colors`: Boolean toggle (`false` uses global theme colors, `true` overrides).
- `custom_bg_color`: Custom background color.
- `custom_text_color`: Custom body text color.
- `custom_heading_color`: Custom heading color.
- `custom_button_bg`: Custom button background.
- `custom_button_text`: Custom button label color.
- `custom_border_color`: Custom border color.

This enables merchants to configure dark emerald sections, warm terracotta feature banners, or clean cream cards without touching CSS.

---

## 3. Product Metafields & Structured Data Schema

For Alpina Brew's premium teas, the following product metafields are integrated into `main-product.liquid`:

| Metafield Namespace.Key | Type | Label | Example Value |
| :--- | :--- | :--- | :--- |
| `custom.tea_origin` | `single_line_text_field` | Estate / Region | "Darjeeling, 6,200ft Altitude" |
| `custom.flavour_notes` | `list.single_line_text_field` | Flavor Notes | ["Muscatel", "Wild Orchid", "Honeyed Pine"] |
| `custom.caffeine_level` | `single_line_text_field` | Caffeine Level | "Low", "Medium", "High" |
| `custom.brewing_temp` | `single_line_text_field` | Ideal Water Temp | "85°C / 185°F" |
| `custom.brewing_time` | `single_line_text_field` | Steeping Time | "3 - 4 mins" |
| `custom.leaf_measurement` | `single_line_text_field` | Leaf Quantity | "2.5g per 200ml" |
| `custom.tea_ingredients` | `multi_line_text_field` | Ingredients | "100% Organic Himalayan Green Tea, Jasmine Blossoms" |
| `custom.storage_advice` | `single_line_text_field` | Storage Advice | "Store in an airtight caddy away from direct sunlight" |

---

## 4. Native Customer Accounts (Shopify New Customer Accounts)

- **Authentication Flow**: Native passwordless email OTP handled directly by Shopify.
- **Storefront Entry Points**:
  - Direct account navigation via `routes.account_url` and `routes.account_login_url`.
  - Sign-in badge in header matching inspiration image ("SIGN IN" pill button).
  - Profile completion prompt: Soft, non-blocking reminder banner informing the customer they can add their phone number and shipping preferences for express checkout.
  - Full account extension target `customer-account.profile.block.render` documented for Phase 6.

---

## 5. Razorpay Payment Gateway Integration

- **Shopify Basic Architecture**:
  - Razorpay integrated via the official Shopify Payment Gateway app in India.
  - Supported methods: UPI (Google Pay, PhonePe, Paytm, BHIM), Credit/Debit Cards (Visa, Mastercard, RuPay, Amex), Net Banking, and Wallets.
  - Theme code strictly delegates all payment handling to Shopify's native `/checkout` pipeline.
  - Zero custom payment endpoints or fake webhook handlers in Liquid.
