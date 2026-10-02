# Turf Ground Booking System — Requirement Analysis

**Prepared by:** Product Management Intern
**Date:** [insert date]

---

## 1. Problem Understanding

The turf currently manages all bookings manually — through phone calls, Facebook messages, and WhatsApp. This creates a few core problems:

- **Customers** have no single, reliable way to see which slots are actually free. They have to reach out and wait for a reply, which is slow and sometimes leads to them booking elsewhere.
- **Double-bookings** happen because the owner is tracking availability across multiple channels (phone, FB, WhatsApp) with no central source of truth.
- **The turf management team** spends time manually confirming, rejecting, and rescheduling bookings instead of running the business.

The core product idea is a simple web-based booking system where customers can see real-time slot availability and book instantly, while the owner manages availability, pricing, and bookings from one place — removing the need for manual coordination for every booking.

---

## 2. Main Users

**1. Customer**
Wants to quickly check which slots are free on a given date and book one with minimal friction — ideally without creating an account.

**2. Turf Owner / Admin**
Wants a simple way to manage turf availability (including blocking slots for maintenance or private use), see all upcoming bookings in one place, and avoid double-bookings — without needing technical knowledge.

*(Out of scope for v1: multiple turf locations, staff/sub-admin roles — see Assumptions.)*

---

## 3. Information the Customer Needs to Provide

- Full name
- Phone number (primary contact and booking lookup)
- Desired date
- Desired time slot
- Sport/activity (if the turf supports more than one sport)
- Number of players (optional, for the owner's planning)

---

## 4. Information the Turf Owner Needs to Manage

- Turf details: name, location, sports supported
- Slot configuration: operating hours, slot duration (e.g. 1-hour blocks)
- Pricing per slot (if applicable)
- Real-time availability calendar
- List of all bookings (confirmed and cancelled), with customer contact details
- Ability to block dates/slots for maintenance, weather, or private events
- Cancellation records

---

## 5. Questions to Ask Before Development Starts

1. Is this for a single turf, or will the owner eventually want to manage multiple turfs/venues?
2. Will payment be collected online at the time of booking, or on-site (cash/card at the venue)?
3. Do customers need to create an account/log in, or should guest booking (name + phone) be sufficient for v1?
4. What is the cancellation and refund policy, if any payment is involved?
5. How should the owner be notified of new bookings — SMS, email, app notification, or a dashboard they check manually?
6. Are slots a fixed duration (e.g. always 1 hour), or should customers be able to choose custom durations?
7. Is there a need to support recurring/weekly bookings for regular customers (e.g. a weekly 6-team league)?
8. What's the expected scale — roughly how many bookings per day/week should the system be designed to handle?

---

## 6. Assumptions

Since the requirements are informal, the following assumptions are made for scoping v1:

- This is for a **single turf** (not a multi-venue marketplace).
- Slots are **fixed-duration** (e.g. 1-hour blocks) for simplicity.
- **No online payment** in v1 — customers pay at the venue; the system only handles reservation, not transactions.
- **Guest booking** is allowed — customers do not need to create an account, just provide name and phone number.
- The product is a **mobile-responsive web app**, not a native mobile app, for v1.
- The turf owner is the sole admin user for v1 (no multi-staff roles/permissions).
- Booking confirmations are sent via **SMS or email** (exact channel to be confirmed with the owner based on what they already use with customers).
