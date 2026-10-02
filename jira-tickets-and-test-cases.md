# Jira Tickets & QA/UAT Test Cases — Turf Ground Booking System

Copy each table into a tab of the Google Sheet (Tab 1: "Tickets", Tab 2: "Test Cases").

---

## Tab 1: Jira Tickets

### 1. Story — View Available Turf Slots
**Description:** As a customer, I want to select a date and see which time slots are available for the turf, so that I can choose a convenient time to play without calling or messaging the owner.

**Acceptance Criteria:**
- Customer can select a date from a calendar/date picker
- System displays all time slots for that date, clearly marked as "Available" or "Booked"
- Booked/unavailable slots are visually distinct and not selectable
- If no slots are available for the selected date, a clear message is shown (e.g. "No slots available on this date")
- Slot list loads within 2 seconds under normal conditions

**Priority:** High

---

### 2. Story — Book a Turf Slot
**Description:** As a customer, I want to select an available slot and submit my details to reserve it, so that the slot is held for me without risk of someone else taking it.

**Acceptance Criteria:**
- Customer can select exactly one available slot at a time
- Customer must enter required details (name, phone number) before confirming
- Booking cannot be submitted if required fields are empty or invalid
- On submission, the slot is immediately marked as "Booked" and removed from the available list for other users
- Customer sees a success confirmation screen with booking details (date, time, turf name)

**Priority:** High

---

### 3. Story — Prevent Double-Booking of the Same Slot
**Description:** As a turf owner, I want the system to prevent two customers from booking the same slot, so that I never have conflicting bookings for the same time.

**Acceptance Criteria:**
- If two customers attempt to book the same slot at nearly the same time, only the first confirmed request succeeds
- The second customer receives a clear "slot no longer available" message and is prompted to pick another slot
- The slot's availability status updates in real time (or on next refresh) for all users once booked
- No booking record is created for the rejected attempt

**Priority:** High

---

### 4. Story — Cancel a Booking
**Description:** As a customer, I want to cancel a booking I made, so that I'm not charged/held responsible for a slot I can no longer use, and the slot becomes available to others.

**Acceptance Criteria:**
- Customer can access their existing booking (via confirmation link, phone number lookup, or account)
- Customer can trigger a cancellation with a confirmation step ("Are you sure you want to cancel?")
- Once cancelled, the slot status reverts to "Available" immediately
- Customer receives a cancellation confirmation (on-screen and/or via message)
- Cancelled bookings are retained in records for the owner (not hard-deleted) for reference

**Priority:** Medium

---

### 5. Task — Booking Confirmation (Email/SMS)
**Description:** As a customer, I want to receive a confirmation message after booking, so that I have proof of my reservation and the details handy.

**Acceptance Criteria:**
- Confirmation is sent automatically within 1 minute of successful booking
- Message includes: turf name, date, time slot, customer name, and a reference/booking ID
- Delivered via SMS or email based on the contact info provided (configurable)
- If delivery fails, the booking itself is still saved (confirmation failure does not roll back the booking)

**Priority:** Medium

---

### 6. Task — Admin: Manage Slot Availability / Block Dates
**Description:** As a turf owner, I want to block out dates or specific slots (e.g. for maintenance or private events), so that customers cannot book turf time that isn't actually available.

**Acceptance Criteria:**
- Owner can mark a specific date as fully unavailable
- Owner can mark individual slots within a date as unavailable
- Blocked slots/dates are immediately hidden or disabled from the customer-facing booking view
- Owner can unblock a previously blocked date/slot
- Existing confirmed bookings are not silently overwritten by a block (system warns the owner if a conflict exists)

**Priority:** Medium

---

### 7. Task — Admin: View All Bookings
**Description:** As a turf owner, I want to view a list of all upcoming and past bookings, so that I can manage my schedule and avoid relying on memory or separate notebooks.

**Acceptance Criteria:**
- Owner can see a list/table of bookings with date, time, customer name, phone number, and status (confirmed/cancelled)
- List can be filtered or sorted by date
- Owner can view booking details for a given slot
- Cancelled bookings are shown with a "Cancelled" status rather than removed from the list

**Priority:** Medium

---

### 8. Story — Handle Booking Errors Gracefully
**Description:** As a customer, I want to see a clear message if something goes wrong during booking (e.g. network issue, server error), so that I know whether my booking went through and what to do next.

**Acceptance Criteria:**
- If a booking submission fails due to a technical error, customer sees a clear error message (not a blank screen or silent failure)
- Customer is informed whether the slot was reserved or not (no ambiguous state)
- Customer can retry the booking without losing the details they already entered
- Failed attempts do not create a "ghost" booking that blocks the slot for others

**Priority:** Low/Medium

---

## Tab 2: QA / UAT Test Cases

| # | Test Case | Steps | Expected Result |
|---|-----------|-------|------------------|
| 1 | Book an available slot | Select date → select an available slot → enter valid details → confirm | Booking is confirmed; slot now shows as "Booked"; confirmation message received |
| 2 | Book an already-booked slot | Select date → attempt to select a slot marked "Booked" | Slot is not selectable / system shows "Slot unavailable" message; booking is not created |
| 3 | Leave required information empty | Select an available slot → leave name or phone number blank → try to confirm | System shows validation error; booking is not submitted |
| 4 | Enter invalid phone number format | Select an available slot → enter an invalid phone number (e.g. letters or too few digits) → try to confirm | System shows validation error; booking is not submitted until corrected |
| 5 | Cancel a booking | Open an existing confirmed booking → select cancel → confirm cancellation | Booking status changes to "Cancelled"; slot becomes available again for other customers |
| 6 | Two customers book the same slot simultaneously | Two users select the same available slot at nearly the same time and both submit | Only one booking succeeds; the other user sees "slot no longer available" and no duplicate booking is created |
| 7 | Turf unavailable due to maintenance | Owner blocks a date for maintenance → customer views that date | Blocked date/slots are not shown as available / are disabled for booking |
| 8 | Complete booking end-to-end | View turf → select date → select slot → enter details → confirm booking | Booking is confirmed, confirmation screen is shown, and confirmation message (SMS/email) is received within 1 minute |
| 9 | Network/server error during booking | Simulate network failure while submitting a booking | Clear error message is shown; slot is not falsely marked as booked; customer can retry |
| 10 | Owner views booking list | Owner opens bookings dashboard | All bookings (confirmed and cancelled) are listed with correct date, time, customer, and status |
