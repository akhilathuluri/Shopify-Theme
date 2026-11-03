# Alpina Brew — Deployment & Preview Guide

**Branch:** `master`  
**Shopify CLI Target:** Online Store 2.0 Development Theme / Unpublished Theme  

---

## 1. Prerequisites

1. **Shopify CLI**: Ensure Shopify CLI v5.0+ is installed (`shopify version`).
2. **Store Authentication**:
   ```bash
   shopify theme dev --store <your-store>.myshopify.com
   ```
   *Note: Official OAuth login prompt will open in the browser.*
3. **Theme Check**:
   ```bash
   shopify theme check
   ```
   *Must pass with 0 errors and 0 warnings before pushing or packaging.*

---

## 2. Local Previewing Workflow

To preview theme changes live with real store data in development mode without impacting visitors:

```bash
# Start local theme development server
shopify theme dev --store alpina-brew.myshopify.com
```

- Shopify CLI will output:
  - **Local Development URL**: e.g., `http://127.0.0.1:9292` (hot-reloading preview)
  - **Theme Editor URL**: e.g., `https://admin.shopify.com/store/alpina-brew/themes/<id>/editor` (test customize settings live)
  - **Shareable Preview URL**: Share with team / stakeholders to review on actual mobile devices.

---

## 3. Pushing to Unpublished Theme

Never push directly to the live theme. Always push to a separate unpublished development theme for user review:

```bash
# Push current repository as an unpublished theme
shopify theme push --unpublished --theme "Alpina Brew - Staging Preview"
```

---

## 4. Pre-Publish Verification Checklist

Before publishing "Alpina Brew" as the live theme:

- [ ] `shopify theme check` passes with 0 offenses.
- [ ] Responsive inspection completed on Mobile (375px/390px/430px), Tablet (768px), and Laptop (1440px).
- [ ] Product variants (Pack sizes: 100g, 250g, 500g) switch cleanly and update prices accurately.
- [ ] Add-to-cart, cart drawer, and checkout button reach Shopify Checkout without errors.
- [ ] Razorpay payment gateway enabled and tested in Test Mode in Shopify Admin.
- [ ] Customer account login flow verified using Shopify New Customer Accounts.
- [ ] All Theme Editor settings (Global colors, Per-section colors, Typography, Banners) tested in Theme Customizer.
- [ ] Client / Store Owner explicit written approval received.

---

## 5. Live Theme Publishing

Only when client gives explicit instruction:

```bash
# Publish unpublished theme to live storefront
shopify theme publish --theme <theme-id>
```
