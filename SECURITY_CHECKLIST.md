# Alpina Brew — Security & Safe Coding Checklist

**Security Posture:** Production E-Commerce Theme (Shopify Online Store 2.0)  
**Compliance Target:** Shopify App & Theme Security Requirements, OWASP Top 10  

---

## 1. Credential & Secrets Hygiene

- [x] **No Hardcoded API Keys or Secrets**:
  - Zero private access tokens, app secrets, Razorpay secret keys, or webhook signing keys in Liquid, JavaScript, or Git repository.
  - Razorpay merchant credentials managed strictly via Shopify Admin Payment Settings, never in theme settings or theme files.
- [x] **Git Repository Sanity**:
  - `.gitignore` configured to ignore `.env`, build artifacts, credentials, local session logs, and personal keys.
- [x] **Theme Settings Safety**:
  - Settings schemas only allow presentation and configuration data (colors, typography, toggles, text strings). No credentials stored in `settings_data.json`.

---

## 2. Liquid Security & XSS Mitigation

- [x] **Context-Aware Output Escaping**:
  - User-submitted or customer-controlled inputs (search query, customer names, form messages) escaped using `| escape` or `| json`.
  - Unsafe filters like `| json_string` avoided; `| escape_once` used where multiple render passes occur.
  - Safe HTML only rendered for trusted merchant-authored rich text via Shopify rich text fields.
- [x] **Safe DOM Manipulation**:
  - Client-side JavaScript uses `textContent`, `setAttribute`, or sanitized templating rather than unvetted `innerHTML` with raw user input.
- [x] **No `eval()` or Unsafe Dynamic Execution**:
  - Zero dynamic script injections, `eval()`, `new Function()`, or unvetted external CDN script tags.

---

## 3. Customer Data & Privacy (GDPR / Indian DPDP Act)

- [x] **New Customer Accounts Privacy**:
  - Passwordless email OTP handled exclusively within Shopify's secure domain (`shopify.com`).
  - No customer passwords or OTP tokens intercepted or logged in theme frontend code.
- [x] **PII Protection**:
  - No logging of customer email, phone, shipping addresses, or payment details in `console.log()` or third-party client analytics without consent.
- [x] **Shopify Native Forms**:
  - Contact forms and newsletter subscriptions use Shopify's native `{% form 'contact' %}` and `{% form 'customer' %}` tags, leveraging Shopify's native CSRF token injection and honeypot protections.

---

## 4. Payment Integrity (Razorpay / Shopify Checkout)

- [x] **Platform-Owned Checkout**:
  - All financial transactions and order creation occur strictly inside Shopify's PCI-DSS Level 1 compliant checkout.
  - No custom client-side payment verification or simulated orders.
  - Payment statuses (Authorized, Paid, Refunded) synchronized directly between Razorpay and Shopify backend.

---

## 5. Third-Party Dependencies & Subresource Integrity

- [x] **Lightweight Vanilla Core**:
  - Zero bloated libraries (jQuery, lodash, heavy UI frameworks).
  - Modern ES6+ JavaScript modules used natively in supported browsers.
- [x] **Asset Verification**:
  - External fonts loaded through Shopify's native `font_picker` and CDN via `font_face`.
  - All SVG graphics inlined or loaded from Shopify CDN with sanitized markup.
