# South End Mother’s Day RSVP Landing Page — Cursor Build Brief

## Goal

Build a dynamic Mother’s Day RSVP landing page as a **standalone site** (not a route on the main South End website). Deploy it with **Firebase Hosting** so it lives at its **own URL** (Firebase default domain and/or a custom domain), separate from southendclub.com’s primary hosting.

The page should promote the event, explain the menu and policies, and embed a Tally RSVP/payment form that dynamically prices reservations based on:

- Adult count
- Kids ages 2–12 count
- Bottomless mimosa add-on count
- Optional reservation details and seating preferences

The website should act as the polished public-facing landing page. Tally should handle form logic, calculations, RSVP collection, Stripe payment, and confirmation.

### Hosting note (this project)

- **Delivery:** static page(s) in a small dedicated folder/repo (e.g. `index.html` at the root).
- **Deploy:** Firebase Hosting (`firebase.json`, `.firebaserc`, `firebase deploy`).
- **URL:** use the Firebase project’s Hosting URL for canonical, Open Graph, and `twitter:url` meta tags (update when the project id or custom domain is final).
- **Linking:** the main South End site (or email/social) should point visitors to this Firebase URL; no need for `/mothers-day` on the main site.

---

## Event Context

### Event

**Mother’s Day at South End**

### Timing

- **11:00 AM – 3:00 PM**
- One slot only

### Guest Policy

- Members may bring nonmembers

### Pricing

- **Adults:** $105 per person
- **Kids ages 2–12:** $40 per child
- **Kids under 2:** optional/free if included
- **Bottomless mimosas:** +$25 per person
- **House margaritas:** $10, available at event
- **Mother’s Day cocktails:** TBD / available at event
- **All RSVPs are non-refundable**

### Reservation Rules

- Table reservations are based on speed of reservation
- Patio reservations require **8+ guests**
- Patio seating is not guaranteed unless confirmed by South End

### Decor / Setup

- Flower decorations
- Bouquets for tableware
- Setup required

---

## Menu

### Entrees

- Oven Roast Rib Eye with carving person
- Grilled Salmon
- Pork BBQ Ribs
- Grilled Chicken Breast
- Scampi Shrimp

### Kids Entrees

- Chicken Tenders
- Pizza
  - Cheese
  - Pepperoni

### Sides

- Mashed Potatoes
- French Fries
- Dinner Rolls
- Roasted Corn
- Oven Roasted Vegetables
- Salad Station

### Dessert

- Cheesecake Bites
- Brownie Bites
- Cookies
- Fruit Platter

### Drinks

Included:

- Fresh Squeezed OJ
- Soda
- Lemonade
- 1 comped house wine, Angeline Cab or Angeline Chardonnay
- OR 1 bottled beer

Add-ons / available at event:

- Bottomless mimosas: +$25
- House margaritas: $10
- Two Mother’s Day cocktails, TBD

---

## Recommended Stack

### Website

Standalone **static HTML** (or the smallest setup you need) in **its own** directory/repo, deployed only to **Firebase Hosting**.

- **Entry:** typically a single `index.html` served at `/` on the Firebase Hosting URL.
- **Design:** follow the **Visual Direction** section below so the page still feels on-brand for South End, even without shared WordPress/theme components.

### Form + Payment

Use:

```txt
Tally + Stripe
```

Tally should handle:

- Guest details
- RSVP quantities
- Dynamic price calculation
- Required policy acknowledgments
- Stripe payment
- Submission storage
- Email notifications
- Optional Google Sheets export

The website should not process payments directly. It should embed the Tally form.

---

## Page Requirements

### Page Purpose

The page should:

1. Sell the event visually.
2. Explain what is included.
3. Make pricing clear.
4. Explain reservation rules.
5. Embed the RSVP form.
6. Reduce support questions.

### Required Sections

1. Hero
2. Event details
3. Pricing cards
4. Menu
5. Drink details
6. Reservation notes
7. RSVP form embed
8. Footer / contact note

---

## Page Copy

### Hero Section

Headline:

```txt
Mother’s Day at South End
```

Subheadline:

```txt
Celebrate Mother’s Day with a special buffet-style dining experience featuring carved rib eye, grilled salmon, BBQ ribs, fresh sides, desserts, cocktails, and more.
```

Details line:

```txt
Sunday, Mother’s Day • 11 AM–3 PM • One seating only
```

CTA button:

```txt
Reserve Your Table
```

CTA behavior:

- Scroll to RSVP form section

---

## Pricing Section

Suggested heading:

```txt
Pricing
```

Suggested cards:

### Adults

```txt
$105 per adult
Includes Mother’s Day dining experience, soda, lemonade, fresh squeezed OJ, and one comped house wine or bottled beer.
```

### Kids Ages 2–12

```txt
$40 per child
Includes kids entree options, sides, desserts, and included non-alcoholic beverages.
```

### Bottomless Mimosas

```txt
+$25 per person
Optional add-on available during RSVP.
```

Policy note:

```txt
All RSVPs are non-refundable.
```

---

## Menu Section Copy

### Suggested Intro

```txt
Enjoy a full Mother’s Day spread with premium entrees, kid-friendly options, classic sides, desserts, and included beverages.
```

### Entrees

- Oven Roast Rib Eye with carving person
- Grilled Salmon
- Pork BBQ Ribs
- Grilled Chicken Breast
- Scampi Shrimp

### Kids Entrees

- Chicken Tenders
- Cheese Pizza
- Pepperoni Pizza

### Sides

- Mashed Potatoes
- French Fries
- Dinner Rolls
- Roasted Corn
- Oven Roasted Vegetables
- Salad Station

### Dessert

- Cheesecake Bites
- Brownie Bites
- Cookies
- Fruit Platter

### Drinks

Included:

- Fresh Squeezed OJ
- Soda
- Lemonade
- 1 comped house wine, Angeline Cabernet or Angeline Chardonnay
- OR 1 bottled beer

Available / add-ons:

- Bottomless mimosas: +$25
- House margaritas: $10
- Two Mother’s Day cocktails: TBD

---

## Reservation Notes Section

Suggested heading:

```txt
Reservation Details
```

Suggested copy:

```txt
Members may bring nonmembers. Table reservations are based on speed of reservation. Patio reservations require 8+ guests and are not guaranteed unless confirmed by South End.
```

Required policy box:

```txt
All RSVPs are non-refundable. Please confirm your party size and add-ons before submitting payment.
```

---

## RSVP Form Strategy

### Form Platform

Use Tally.

### Payment Processor

Use Stripe connected through Tally.

### Website Integration

Embed the Tally form in the RSVP section using Tally’s official embed code.

The landing page should not calculate payment itself unless you want a preview calculator. The authoritative total should be calculated inside Tally.

---

## Tally Form Fields

### Section 1 — Contact Information

Required fields:

- Full Name
- Email
- Phone Number
- Member Name, if different
- Member Number, optional

Optional field:

- Are you bringing nonmembers?
  - Yes
  - No

### Section 2 — Party Size

Fields:

- Number of Adults
  - Required
  - Minimum: 1
  - Price: $105 each

- Number of Kids Ages 2–12
  - Required or default 0
  - Minimum: 0
  - Price: $40 each

- Number of Kids Under 2
  - Optional or default 0
  - Minimum: 0
  - Price: $0

### Section 3 — Seating Preference

Field:

- Preferred Seating
  - Indoor
  - Patio
  - No preference

Conditional message if Patio is selected:

```txt
Patio reservations require 8+ guests and are based on reservation timing. Patio seating is not guaranteed unless confirmed by South End.
```

Optional field:

- Notes / Seating Requests

### Section 4 — Add-ons

Field:

- Number of Bottomless Mimosa Add-ons
  - Minimum: 0
  - Price: $25 each

Display-only note:

```txt
House margaritas will be available at the event for $10. Two Mother’s Day cocktails will also be available.
```

### Section 5 — Dynamic Total

Create a calculated field in Tally.

Formula:

```txt
(adults * 105) + (kids_2_12 * 40) + (mimosas * 25)
```

Use whatever exact internal field references Tally assigns.

Example:

```txt
Number of Adults × 105
+
Number of Kids Ages 2–12 × 40
+
Number of Bottomless Mimosa Add-ons × 25
```

### Section 6 — Required Acknowledgments

Required checkbox:

```txt
I understand that all Mother’s Day RSVPs are non-refundable.
```

Required checkbox:

```txt
I understand that patio reservations require 8+ guests and are based on reservation timing. Patio seating is not guaranteed unless confirmed by South End.
```

Required checkbox:

```txt
I confirm that my party size and add-ons are accurate before submitting payment.
```

### Section 7 — Stripe Payment

Payment amount:

```txt
Calculated Total
```

Payment button:

```txt
Submit RSVP & Pay
```

---

## Confirmation Message

Use this Tally confirmation message after payment:

```txt
Thank you for your Mother’s Day RSVP. Your reservation request has been received.

Reminder: all RSVPs are non-refundable. Patio reservations require 8+ guests and are based on reservation timing. Patio seating is not guaranteed unless confirmed by South End.
```

---

## Internal Notification Email

Send a notification email for every RSVP.

Suggested subject:

```txt
New Mother’s Day RSVP - South End
```

Include:

- Full name
- Email
- Phone
- Adult count
- Kids 2–12 count
- Kids under 2 count
- Bottomless mimosa count
- Total paid
- Seating preference
- Bringing nonmembers: yes/no
- Notes
- Stripe payment status

---

## Landing Page Technical Implementation

This implementation is **intentionally separate** from the main South End website codebase.

Before coding:

1. Confirm the folder is a **Firebase Hosting** root (`firebase.json` `public` points at `.` or `dist`, with `index.html` as the main document).
2. Use **static HTML** for the landing unless you have a strong reason to add a framework.
3. Recreate **layout and polish** using the **Visual Direction** section (colors, typography, spacing)—not by importing the main site’s templates.
4. Optional: add `README.md` with `npm run deploy` / Firebase login steps for anyone deploying later.

Payments stay in **Tally + Stripe**; this page only embeds the form.

---

## Visual Direction

Use the existing South End website style.

Preferred design characteristics:

- Clean, modern, premium club feel
- Dark teal / deep blue accents where appropriate
- Cream or warm neutral backgrounds
- High contrast CTA buttons
- Clear section spacing
- Mobile-first layout
- Easy-to-scan pricing and policy cards

If you have a logo asset, you may place it in the hero or header; there is no shared header from the main website in this Firebase setup.

---

## Suggested Component / Page Structure

If this is a React or Next.js repo, build something like:

```txt
MothersDayPage
  HeroSection
  EventDetailsSection
  PricingSection
  MenuSection
  DrinksSection
  ReservationPolicySection
  RsvpEmbedSection
```

If this is static HTML, build equivalent sections in one page.

---

## Tally Embed Placeholder

Add this placeholder until the actual Tally form URL is created:

```html
<div class="rsvp-embed-placeholder">
  <p>RSVP form coming soon.</p>
</div>
```

Once Tally is ready, replace with Tally embed code:

```html
<iframe
  data-tally-src="https://tally.so/embed/YOUR_FORM_ID?alignLeft=1&hideTitle=1&transparentBackground=1&dynamicHeight=1"
  loading="lazy"
  width="100%"
  height="700"
  frameborder="0"
  marginheight="0"
  marginwidth="0"
  title="Mother’s Day RSVP Form">
</iframe>
<script>
  var d = document;
  var w = "https://tally.so/widgets/embed.js";
  var v = function () {
    if (typeof Tally !== "undefined") {
      Tally.loadEmbeds();
    } else {
      d.querySelectorAll("iframe[data-tally-src]:not([src])").forEach(function (e) {
        e.src = e.dataset.tallySrc;
      });
    }
  };
  if (typeof Tally !== "undefined") {
    v();
  } else if (d.querySelector('script[src="' + w + '"]') == null) {
    var s = d.createElement("script");
    s.src = w;
    s.onload = v;
    s.onerror = v;
    d.body.appendChild(s);
  }
</script>
```

Replace:

```txt
YOUR_FORM_ID
```

with the live Tally form ID.

---

## Optional Front-End Pricing Preview

This is optional. Tally should remain the source of truth for final payment.

If you want a front-end preview on the website before the form, use this formula:

```js
const adultPrice = 105;
const kidPrice = 40;
const mimosaPrice = 25;

const total = adults * adultPrice + kids * kidPrice + mimosas * mimosaPrice;
```

Recommended default:

Do not build a custom calculator unless needed. Keep pricing logic in Tally to avoid mismatch.

---

## Step-by-Step Cursor Plan

### Step 1 — Inspect Standalone Firebase Repo

Ask Cursor to identify:

- `firebase.json` / `.firebaserc` (Hosting root and project id)
- Main HTML entry (`index.html` or equivalent)
- How deploy is run (`package.json` scripts if any)

Prompt:

```txt
Inspect this repo. Confirm it targets Firebase Hosting, where the public `index.html` lives, and how to deploy. Do not modify files yet.
```

---

### Step 2 — Create the Landing Page

Prompt:

```txt
Build or refresh the Mother’s Day landing as the main `index.html` for this Firebase site. Use the event details from this brief. Include sections for hero, pricing, menu, drinks, reservation notes, and RSVP embed placeholder. Do not add payment logic to the website — only embed Tally later. Match the Visual Direction in the brief (premium club feel, teal/blue accents, warm background).
```

---

### Step 3 — Polish Styling

Prompt:

```txt
Refine the Mother’s Day `index.html` styles so the page feels cohesive and on-brand per the brief: clear typography, spacing, cards, and CTAs. Keep everything in this single page (or minimal assets) suitable for Firebase Hosting.
```

---

### Step 4 — Add RSVP Form Anchor

Prompt:

```txt
Make the hero CTA button scroll smoothly to the RSVP form section. Add an anchor id of rsvp to the form section.
```

---

### Step 5 — Add Tally Placeholder

Prompt:

```txt
Add a clean RSVP form placeholder section that says "RSVP form coming soon." Leave a clear comment showing where the Tally iframe embed code should go.
```

---

### Step 6 — Build Tally Form

Do this outside Cursor in Tally.

Create form fields:

1. Full Name
2. Email
3. Phone
4. Member Number, optional
5. Bringing nonmembers? yes/no
6. Number of Adults
7. Number of Kids Ages 2–12
8. Number of Kids Under 2
9. Preferred Seating
10. Notes / Seating Requests
11. Number of Bottomless Mimosa Add-ons
12. Calculated Total
13. Required non-refundable acknowledgment
14. Required patio policy acknowledgment
15. Required payment confirmation
16. Stripe payment block

Pricing formula:

```txt
(adults * 105) + (kids_2_12 * 40) + (mimosas * 25)
```

---

### Step 7 — Connect Stripe in Tally

In Tally:

1. Add payment block.
2. Connect Stripe.
3. Set payment amount to calculated total.
4. Test with Stripe test mode if available.
5. Confirm confirmation message.
6. Confirm notification email.
7. Submit test RSVP.

---

### Step 8 — Replace Placeholder with Tally Embed

Prompt:

```txt
Replace the RSVP placeholder with this Tally embed code. Preserve the page styling and make sure the iframe is responsive on mobile.
```

Then paste the Tally embed code.

---

### Step 9 — Mobile QA

Prompt:

```txt
Review the Mother’s Day landing page (`index.html`) for mobile layout issues. Check hero spacing, pricing cards, menu sections, policy cards, and the embedded RSVP form. Fix any responsive issues without changing the overall design.
```

---

### Step 10 — SEO + Social Metadata

Prompt:

```txt
Add appropriate SEO title, meta description, and social sharing metadata on `index.html` for the Mother’s Day event. Use the final Firebase Hosting URL (or custom domain) in canonical, og:url, and twitter:url once it is decided.
```

Suggested title:

```txt
Mother’s Day at South End | RSVP
```

Suggested description:

```txt
Reserve your table for Mother’s Day at South End. Enjoy premium entrees, kids options, sides, desserts, included drinks, and optional bottomless mimosas.
```

---

### Step 11 — Final QA Checklist

Confirm:

- Page loads at the Firebase Hosting site root (`/` on the deployed URL)
- Local layout reads clearly as a complete landing (no dependency on main site header/footer)
- CTA scrolls to RSVP form
- Pricing is clear
- All menu items are accurate
- Non-refundable policy is visible
- Patio policy is visible
- Tally iframe loads
- Tally total calculates correctly
- Stripe payment works
- Confirmation message works
- Internal notification email works
- Mobile layout works
- No console errors
- Page is ready to publish

---

## Test Cases for Dynamic Pricing

Use these test cases in Tally.

### Test 1

Adults: 2  
Kids 2–12: 0  
Mimosas: 0  

Expected total:

```txt
$210
```

### Test 2

Adults: 2  
Kids 2–12: 2  
Mimosas: 0  

Expected total:

```txt
$290
```

### Test 3

Adults: 4  
Kids 2–12: 2  
Mimosas: 2  

Expected total:

```txt
$550
```

### Test 4

Adults: 8  
Kids 2–12: 0  
Mimosas: 4  

Expected total:

```txt
$940
```

### Test 5

Adults: 1  
Kids 2–12: 1  
Mimosas: 1  

Expected total:

```txt
$170
```

---

## Important Implementation Notes

- Do not hardcode the final Tally form ID until the form exists.
- Do not collect credit card data directly on this landing page.
- Do not create custom Stripe checkout unless the project specifically needs full custom payment control.
- Keep Tally as the payment source of truth.
- Avoid duplicating pricing logic on the front end unless it is clearly labeled as a preview.
- Make all policy language visible before the RSVP form.
- Make mobile layout a priority.

---

## Future Enhancements

Possible later upgrades:

- Google Sheets RSVP tracking
- Automatic confirmation email with reservation details
- Admin-only RSVP dashboard
- Capacity limit
- Patio request waitlist
- Sold-out state
- Private event reuse template
- Similar pages for Easter, brunches, wine dinners, and holiday events
