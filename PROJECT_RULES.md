# Alpina Brew — Project Rules & Guidelines

**Brand:** Alpina Brew  
**Platform:** Shopify Online Store 2.0 (Shopify Basic, India)  
**Development Standard:** Shopify Official Theme Architecture, Shopify AI Toolkit, Theme Check  

---

## 1. Core Operating Principles

1. **Shopify Native Architecture First**
   - Use native Shopify functionality for all e-commerce flows: Products, Variants, Inventory, Cart, Checkout, Discounts, Customers, and Orders.
   - Never build a custom headless backend, external database, or third-party checkout pipeline.
   - Use Shopify Liquid, JSON templates, reusable sections, theme blocks, snippets, modular CSS, and performant vanilla JavaScript.

2. **Mobile-First Without Exception**
   - Mobile is the primary viewport (>70% traffic expected).
   - Design and test at `320px`, `360px`, `375px`, `390px`, `414px`, `430px`, `768px`, `1024px`, `1280px`, `1440px`, and `1920px`.
   - Zero horizontal scroll, zero clipped touch targets, zero layout shifts on load.

3. **Complete Shopify Theme Editor Control**
   - Merchants must be able to control colors, typography, layout widths, spacing, paddings, headings, copy, media, and block visibility without modifying code.
   - Global color schemes defined in `settings_schema.json`.
   - Every individual section must support selecting the global color scheme OR setting custom background, heading, body, border, and button colors.

4. **Strict Liquid & Theme Standards**
   - Valid JSON schemas for every section (`{% schema %}`) and block.
   - Reusable snippets with LiquidDoc headers (`{% doc %}...{% enddoc %}`).
   - Static theme blocks rendered via `{% content_for 'block', ... %}` require LiquidDoc.
   - Use `{{ block.shopify_attributes }}` on all block containers for Theme Editor live drag-and-drop.
   - CSS via `{% stylesheet %}` and scoped component selectors; JS via `{% javascript %}` or modular deferred scripts.

5. **Indian Market & Payment Standards**
   - Store currency: INR (`₹`).
   - Official Razorpay Shopify gateway integration for checkout (UPI, Cards, Netbanking).
   - Never fabricate client-side payment success or write custom payment gateways.

6. **Customer Accounts**
   - Shopify New Customer Accounts (passwordless OTP via email).
   - Profile completion extension planned separately as supported Customer Account extension.

7. **Verification & Tooling**
   - Run `shopify theme check` to maintain 0 offenses.
   - Use Shopify AI Toolkit (`search_docs.mjs`, `validate.mjs`) to validate Liquid syntax and API references.
   - Maintain Git version control on branch `master` or feature branches; never overwrite or delete live theme without explicit confirmation.
