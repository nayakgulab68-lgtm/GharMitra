# GharMitra — Your Companion, Everywhere

Responsive React + Vite + Tailwind CSS + Framer Motion hackathon prototype, based on Team GharMitra’s 16-slide presentation.

#demo preview
link:-https://gharmitra-companion-lokesh.honeyelf8.chatgpt.site/

## Run in VS Code

Install Node.js 20.19+ or 22.12+. Open this folder in VS Code, then run:

```sh
npm install
npm run dev
```

Open the URL printed by Vite. Build for deployment with `npm run build`; preview with `npm run preview`.

## Full demo walkthrough

1. Choose **Log in → Customer** (Lokesh). Find a companion, inspect matching reasons, and book a future public outing.
2. For a child outing, select the child checkbox or School route. Requests are blocked at **Awaiting guardian**. Switch to Parent / guardian (Priya) and explicitly approve.
3. Switch to the requested companion’s named demo account in Login. Accept the request.
4. Switch to Customer. Simulate UPI using `demo@upi`. No PIN or real money is involved. Inspect or print the receipt.
5. Switch to the companion. Start the outing. Open Trip status to explore animated simulated positions, guardian sharing, and SOS demonstration.
6. Complete the outing from the companion dashboard. Return to customer and submit a review.
7. Open Ask Mitra, try Book a walk, Safety, or Prices. Toggle spoken replies, select Telugu/Hindi/English, or use the microphone if the browser supports it. Rule-based FAQ replies are localized in all three languages; the main interface remains English.
8. Report or block a profile. Switch to Admin to resolve reports and review simulated verification.
9. Use Profile & settings for local preferences, and Privacy to clear all records.

## Architecture

- `src/main.jsx`: routing, role sessions, persisted local demo state, connected booking lifecycle, dashboard and assistant UI.
- `src/pages/Home.jsx`: responsive homepage with a layered, perspective-reactive photo scene, floating cards, gradients, CSS spheres and Framer Motion entrance.
- `src/components/UI.jsx`: shared controls and modal surfaces.
- `src/data.js`: illustrative companions, services, equal-weight explainable matching and initial state.
- `src/styles.css`: Tailwind import, responsive design system, micro-interactions and reduced-motion support.

State uses localStorage (`gharmitra-v1`) in one browser, not a shared backend. Sessions intentionally reset on reload. Switching roles preserves bookings; another tab reload reads the stored records. No paid API keys required. Lifestyle images load from Unsplash; avatar images from Pravatar; Google Fonts is optional with system fallbacks. The core UI and booking logic work if these cosmetic external resources fail.

## Operational boundaries

Working prototype features: forms, filters, matching, favorites, roles, registration, approvals, requests, status transitions, receipts, local reviews/reports, block, settings, assistant rules and browser speech hooks.

**Simulated:** identity verification, background checks, payments, account authorization, map positions, guardian location sharing, SOS, income, reviews of seeded profiles and AI. No real government ID, card data, UPI PIN, GPS or raw verification documents are collected. SOS never contacts any person or agency. Hospital visits mean companionship only. Children's services require explicit guardian approval and public places only.

This is NOT suitable for real-world deployment as a safeguarding service. A production release requires authenticated accounts, server-side role and ownership checks, approved consent/guardian identity workflows, secure storage and retention controls, vetted adult verification, scheduling conflict checks, payment reconciliation/refunds, monitored abuse handling, emergency protocols, and consented real location integrations. Current role selection is intentionally open for judges to explore. Do not enter sensitive personal data.

## Deployment

Vercel: import repository, choose Vite, build `npm run build`, output `dist`.
Netlify: same build/output settings; `netlify.toml` is included. Hash routes work on static hosting without rewrite dependencies.

The home scene uses CSS perspective and lightweight transform animations rather than a WebGL dependency, reducing download and rendering cost on mobile. Reduced-motion settings disable continuous animations.

## Separate login pages

Choose a role from Login to open `#customer-login`, `#companion-login`, `#guardian-login` or `#admin-login`. Customer and guardian pages support local account creation and returning ID login. Companion registration captures a personal profile; returning users enter their saved companion ID. IDs are case-insensitive within a role.

For the walkthrough: customer ID `lokesh`, parent ID `priya`, administrator ID `admin` with displayed demo access code `admin-demo`. Sample companions are available inside the companion login page. All are local prototype simulations, not secure authentication or shared accounts across devices. Administrator signup is intentionally unavailable.
