# Mother’s Day RSVP — Tally build guide

This file is the **full blueprint** for the form. The actual form must be created in [Tally](https://tally.so) under your account (we cannot log in or publish for you).

**Official Tally docs (keep open while building):**

- [Calculated fields](https://tally.so/help/form-calculator) — dynamic total
- [Payment forms + Stripe](https://tally.so/help/payment-forms)
- [Checkout / dynamic price](https://tally.so/help/how-to-create-a-checkout-form)
- [Embed on your site](https://tally.so/help/embed-your-form)

**Speed tip:** Start from Tally’s [Advanced checkout flow](https://tally.so/templates/advanced-checkout-flow/ew5BNn) or [Booking + checkout](https://tally.so/templates/booking-form/wbeYg3) template, then replace questions and prices. That gives you working **calculated field → payment** wiring you can adapt.

---

## 1. Form title (suggested)

`South End — Mother’s Day Brunch RSVP`

---

## 2. Fields by section (build in this order)

Use clear **question titles** so submission emails and Stripe metadata stay readable.

### Page A — Contact

| Block type | Label | Required | Notes |
|------------|--------|----------|-------|
| Short text | Full name | Yes | |
| Email | Email | Yes | |
| Phone | Phone number | Yes | |
| Short text | Member name (if different from name above) | No | Brief listed this; keep optional so same person isn’t forced to duplicate |
| Short text | Member number | No | |
| Multiple choice (single) | Are you bringing nonmembers? | No | Options: `Yes`, `No` |

### Page B — Party size

| Block type | Label | Required | Validation |
|------------|--------|----------|------------|
| Number | Number of adults | Yes | Min **1** — `$105` each (for your reference / help text) |
| Number | Number of kids ages 2–12 | Yes | Min **0**, default **0** — `$40` each |
| Number | Number of kids under 2 | No | Min **0**, default **0** — `$0` |

Help text (optional, under adults/kids):

`Pricing: adults $105, kids 2–12 $40, under 2 free.`

### Page C — Seating

| Block type | Label | Required | Options |
|------------|--------|----------|---------|
| Multiple choice (single) | Preferred seating | Yes | `Indoor`, `Patio`, `No preference` |
| Long text | Notes / seating requests | No | |

**Conditional content when “Patio” is selected** (use Tally show/hide or insert a **text** block):

`Patio reservations require 8+ guests and are based on reservation timing. Patio seating is not guaranteed unless confirmed by South End.`

### Page D — Add-ons

| Block type | Label | Required | Validation |
|------------|--------|----------|------------|
| Number | Number of bottomless mimosa add-ons | Yes | Min **0**, default **0** — `$25` each |

**Display note** (paragraph block):

`House margaritas will be available at the event for $10. Two Mother’s Day cocktails will also be available.`

---

## 3. Calculated total (critical)

**Target formula (same as project brief):**

```txt
(adults × 105) + (kids_2_12 × 40) + (mimosas × 25)
```

**In Tally:**

1. Add a **Calculated field** (type **Number**), name it e.g. `RSVP total`.
2. Initial value: `0`.
3. Use **conditional logic** with action **Calculate a value** on that field so the running total matches the formula above when respondents change the three number fields.

Tally’s UI evolves; you may need to:

- Use **Calculate** actions that **add** line amounts derived from each quantity field (if the builder lets you multiply an answer by a constant), **or**
- Use **intermediate** calculated fields (e.g. one for adults line, one for kids line, one for mimosas) and a final field that **sums** them — see the multi-variable patterns in Tally’s calculator docs and checkout template.

**After the total works**, add a **paragraph** so guests see the amount (optional but reduces support):

- Example: `Your total: $` then `@RSVP total` (use `@` to insert the calculated field per Tally).

**Sanity checks** (from project brief):

| Adults | Kids 2–12 | Mimosas | Total |
|--------|-----------|---------|-------|
| 2 | 2 | 0 | **$290** |
| 4 | 2 | 2 | **$550** |
| 8 | 0 | 4 | **$940** |
| 1 | 1 | 1 | **$170** |

---

## 4. Required acknowledgments (checkboxes)

All **required**:

1. `I understand that all Mother’s Day RSVPs are non-refundable.`
2. `I understand that patio reservations require 8+ guests and are based on reservation timing. Patio seating is not guaranteed unless confirmed by South End.`
3. `I confirm that my party size and add-ons are accurate before submitting payment.`

---

## 5. Stripe payment block

1. Insert **Payment** (`/payment`).
2. Connect **Stripe** (Tally Connect / Stripe dashboard as prompted).
3. **Price:** choose your calculated field **`RSVP total`** from the dropdown (dynamic amount).
4. Button / label: **`Submit RSVP & Pay`**
5. Currency: **USD**.

Use Stripe **test mode** until amounts and emails are verified.

---

## 6. After submit — confirmation message

```txt
Thank you for your Mother’s Day RSVP. Your reservation request has been received.

Reminder: all RSVPs are non-refundable. Patio reservations require 8+ guests and are based on reservation timing. Patio seating is not guaranteed unless confirmed by South End.
```

---

## 7. Internal notification email (to staff)

**Subject:**

```txt
New Mother’s Day RSVP - South End
```

**Body:** include every answer you collect, especially:

- Full name, email, phone  
- Member name (if provided), member number (if provided)  
- Adults, kids 2–12, kids under 2  
- Bottomless mimosa count  
- **Total paid** (calculated field / payment amount)  
- Seating preference, notes  
- Bringing nonmembers  
- **Stripe payment status** (if available in Tally’s email fields)

---

## 8. Publish and embed on `index.html`

1. In Tally: **Share** → publish → copy **embed** snippet (iframe + script if provided).
2. In this repo, replace the placeholder inside `#rsvp` as described in the HTML comment above `.md-rsvp-placeholder`.
3. Redeploy Firebase Hosting.

Do **not** put Stripe secret keys in `index.html` — only Tally handles cards.

---

## 9. Pre-launch checklist

- [ ] All required fields and mins match the brief  
- [ ] Patio warning shows when Patio is selected  
- [ ] Calculated total matches all four test cases  
- [ ] Payment block uses calculated total, not a fixed price  
- [ ] Test charge in Stripe test mode succeeds  
- [ ] Staff notification email has complete answers + payment status  
- [ ] Guest sees confirmation message after payment  
- [ ] Form embedded on live site and mobile-tested  

---

## Reference

Full product spec: `south_end_mothers_day_rsvp_cursor_brief.md`
