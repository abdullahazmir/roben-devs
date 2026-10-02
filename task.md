# 🏟️ Turf Ground Booking System — PM Internship Assignment

Role: Product Management Intern
Goal: Show problem understanding, logical thinking, requirement breakdown, attention to detail, and clear communication — **not** to build the product.

---

## 0. Setup

- [ ] Create a dedicated Google Drive folder: `Turf Booking System - PM Assignment`
- [ ] Inside it, create:
  - [ ] Google Doc: `Turf Booking - Requirement Analysis & User Flow`
  - [ ] Google Sheet: `Turf Booking - Jira Tickets & QA Test Cases`
  - [ ] Figma/FigJam/Slides file for the user flow diagram
- [ ] Set sharing on all files to "Anyone with the link can view" before submitting

---

## 1. Requirement Analysis (Google Doc)

Keep it short — bullet points over paragraphs.

- [ ] **Problem understanding** — 3-4 sentences: turf owner relies on manual channels (phone/FB/WhatsApp) → double-bookings, no visibility into availability, manual overhead for owner.
- [ ] **Main users** — define 2 personas:
  - [ ] Customer (wants to quickly check availability and book a slot)
  - [ ] Turf Owner/Admin (wants to manage slots, pricing, bookings, block maintenance time)
- [ ] **Information customer provides**: name, phone number, date, time slot, sport/duration, number of players (optional), payment/advance (if applicable)
- [ ] **Information turf owner manages**: turf details (name, location, sports supported), slot availability/calendar, pricing per slot, booking list, cancellations, blackout/maintenance dates
- [ ] **Questions to ask before development starts** (aim for 5-8), e.g.:
  - [ ] Is this for a single turf or multiple turfs/venues?
  - [ ] Is payment collected online or on-site?
  - [ ] Do we need login/signup, or is guest booking okay?
  - [ ] What's the cancellation/refund policy?
  - [ ] Should the owner get notified instantly (SMS/email/push)?
  - [ ] Are slots fixed-duration (e.g. 1hr) or flexible?
  - [ ] Is there a need for recurring/weekly bookings?
- [ ] **Assumptions** (document anything you guessed since requirements are informal), e.g.:
  - [ ] Single turf, single sport type for v1
  - [ ] Fixed 1-hour slots
  - [ ] No online payment in v1 (pay at venue)
  - [ ] Web app, mobile-responsive (no native app)

---

## 2. User Flow (Figma / FigJam / Slides)

- [ ] Draw the primary happy path:
  `View Turf → Select Date → View Available Slots → Select Slot → Enter Details → Confirm Booking → Booking Confirmed`
- [ ] Add branch: **slot already booked** → show error/alternative slots → back to slot selection
- [ ] Add branch: **customer cancels** → confirm cancellation → slot released back to availability
- [ ] Add branch: **something goes wrong** (payment fails / network error / server error) → show error message → retry or exit gracefully
- [ ] Label each step clearly; use simple boxes/arrows — no need for high-fidelity UI mockups
- [ ] Export or share link; paste the link into the Google Doc too

---

## 3. Jira Tickets (Google Sheet — Tab 1: "Tickets")

Columns: `Type | Title | Description | Acceptance Criteria | Priority`

Target 4-8 tickets. Suggested set:

- [ ] **Story** — View Available Turf Slots (High)
- [ ] **Story** — Book a Turf Slot (High)
- [ ] **Story** — Cancel a Booking (Medium)
- [ ] **Task** — Booking Confirmation (Email/SMS) (Medium)
- [ ] **Story** — Prevent Double-Booking of Same Slot (High)
- [ ] **Task** — Admin: Manage Slot Availability / Block Dates (Medium)
- [ ] **Task** — Admin: View All Bookings (Medium)
- [ ] **Story** — Handle Booking Errors Gracefully (Low/Medium)

For each: write 1-2 line description + 2-4 bullet acceptance criteria (Given/When/Then style is fine but plain bullets are okay too).

---

## 4. QA / UAT Test Cases (Same Google Sheet — Tab 2: "Test Cases")

Columns: `Test Case | Steps (optional) | Expected Result`

Cover at least these scenarios:

- [ ] Book an available slot → Booking is confirmed
- [ ] Book an already-booked slot → System blocks it / shows "slot unavailable"
- [ ] Leave required field empty (e.g. phone number) → Form shows validation error, booking not submitted
- [ ] Cancel an existing booking → Booking removed, slot becomes available again
- [ ] Two customers try to book the same slot simultaneously → Only one succeeds, other sees unavailable
- [ ] Turf marked unavailable due to maintenance → Slot not shown / not selectable
- [ ] Complete booking end-to-end → Confirmation shown + confirmation message sent
- [ ] (Optional) Invalid phone number format entered → Validation error shown

---

## 5. Loom / Video Walkthrough (≤ 6 minutes)

Script outline:

- [ ] **0:00–1:00** — Problem understanding, target users, core product idea (in your own words)
- [ ] **1:00–3:00** — Product approach: requirements, user flow, prioritization logic, one key decision + trade-off, how you'd collaborate with design/engineering (show the Doc/flow on screen)
- [ ] **3:00–6:00** — Walkthrough: key user journeys, main features, one important edge case, expected outcome
- [ ] Record via Loom/YouTube/Drive, set to "Anyone with link can view"
- [ ] Do a timed dry run once before recording final take

---

## 6. Final Submission Checklist

- [ ] Google Doc link works in incognito (view access confirmed)
- [ ] Google Sheet link works in incognito (view access confirmed)
- [ ] Video link works in incognito (view access confirmed)
- [ ] Doc is concise, well-formatted (headers, bullets — no walls of text)
- [ ] 4-8 tickets present, each with all 5 columns filled
- [ ] At least 6-8 QA test cases covering happy path + edge cases
- [ ] Video is under 6 minutes
- [ ] Submit all 3 links together via the provided submission form
