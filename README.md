# Trace Spaces

A booking system for TRACE Sri Lanka's hubs (from BAY 07 at TRACE Expert City, Colombo 10 to Jaffna, Kandy, Makandura and Uva Wellassa) that replaces the Excel sheets. Built by Squad 04 for the T2T Space Rental Hackathon.

**The one job:** stop double booking and show what is free.

## Team: Squad 04

| Member | Role | Owns in the repo |
|---|---|---|
| Shaffron Wazny | Project lead / Scrum master | `index.html`, `logo.png`, `README.md` |
| R. Anuja Geesara Karunarathana | Business analyst | `docs/BACKLOG.md` |
| Ranithu Kavithmal Dimunga | Developer (clash logic) | `docs/BUSINESS-RULES.md` |
| Thahirah Razmi | Developer (availability) | `docs/DEMO-SCRIPT.md` |
| G.L.D.A. De Silva | Developer / QA | `docs/RISKS-AND-NEXT-STEPS.md` |

## Run it

No install. Open `index.html` in any browser. Data is saved in the browser (localStorage) and comes pre-filled with sample bookings for the demo.

## Features

| Story | Feature | Priority |
|---|---|---|
| US1 | See all spaces with capacity, amenities and rate | Must |
| US2 | Day timeline showing free and booked slots per space | Must |
| US3 | Create a booking (customer, space, date, time) | Must |
| US4 | Clash blocking, with who holds the slot and free alternatives | Must |
| US5 | Booking list with edit, cancel and restore | Must |
| US6 | Desk booking per day, week or month, capped at 20 desks | Should |
| US7 | Total price per booking, paid/unpaid status | Should |
| US8 | Public page with availability and request-to-book form | Should |
| US9 | Search and filters on bookings | Could |
| US10 | Find a free space for a time and group size | Could |
| US12 | Switch between all TRACE locations; each has its own rooms and desks | Could |

## Business rules

1. A room or the auditorium cannot have two active bookings that overlap on the same date.
2. Desks can be booked until every desk at that location is taken on any day of the period (20 at Colombo 10).
3. Desk plans: day = 1 day, week = 7 days, month = 30 days.
4. Opening hours 08:00–20:00; end must be after start.
5. People cannot exceed capacity.
6. BAY 07 is hired per day (Rs. 200,000); other spaces per hour; "On demand" spaces are priced by staff.
7. Cancelled bookings keep their record and free the slot.
8. Clash checks and suggested alternatives stay within the same location.

The clash check lives in `validate()`, `roomClashes()` and `deskUsed()` inside `index.html`.

## Data

Spaces, seats, rates and contacts come from TRACE's own Spaces listing (TRACE EventHub & Spaces Tracker). That site lists spaces but has no live availability or booking, which is the gap this app fills. Hot desk pools and their day/week/month rates are sample values, since TRACE lists no per-desk pricing. Several listings show 150 seats and identical facilities; TRACE should confirm these.

## Demo script

1. Availability: Creator Space is booked 09:00–17:00 today.
2. Click Creator Space at 14:00 → clash shown, Save disabled, free rooms suggested.
3. Switch to a suggested room → green check and price → Save.
4. Book 6 desks for today → refused, not enough desks.
5. Public page → send a request → Inquiries → Create booking.
6. Bookings → filter Unpaid → Mark paid; cancel one and show the slot is free.
7. Switch location to Jaffna → same system, same rules.

## Next steps

Full-stack version (Next.js + PostgreSQL, in progress): shared database and staff login, real email notifications, online payment, reports, real TRACE rates and rooms, selling the multi-location model to other venues (BMICH, wedding halls, theatres).
