# Trace Spaces — Business Rules

## Purpose

Trace Spaces manages bookings for TRACE Sri Lanka spaces. These rules protect availability, prevent conflicts, and ensure that bookings meet venue and payment requirements.

## Scope

The current system manages the Atlas Training Room, Orion Meeting Room, Nova Auditorium, and four Focus Desks. Staff create bookings after selecting a specific space.

## Booking status

- **Active** bookings occupy a space.
- **Cancelled** bookings do not occupy a space. The system should retain them in history, along with any cancellation penalty.
- A booking may record its advance-payment amount. Payment does not override availability or policy checks.

## Rules

### BR-01: A space cannot be double-booked

An active booking must not overlap another active booking for the same named space. Different spaces may be booked during the same period.

For time-based bookings, an overlap occurs when one booking starts before the other ends and ends after the other starts.

### BR-02: Cleaning buffers block the next booking

The system reserves cleaning time after every active booking. A following booking for the same space must begin only after this buffer ends.

| Space type | Cleaning buffer |
| --- | --- |
| Auditorium | 2 hours |
| Training room | 1 hour |
| Meeting room | 30 minutes |
| Focus desk | 15 minutes |

### BR-03: Room and auditorium dates

- Training rooms and meeting rooms use a start and end date.
- If a training-room or meeting-room booking starts and ends on the same date, the client must also provide a start time and end time.
- For a multi-day booking, the space remains unavailable for the selected booking period and its following cleaning buffer.
- The end time must be later than the start time.

### BR-04: Focus desks use timed bookings

- The system has four named Focus Desks.
- Each Focus Desk accommodates up to **2 people**.
- A Focus Desk booking requires a booking date, start time, and end time.
- Focus Desk clashes and cleaning buffers are evaluated per named desk, not against all desks together.

### BR-05: Capacity and amenities

The published capacity, amenities, and rate of the selected space must be visible before booking. The requested number of people must not exceed the capacity of that space.

### BR-06: Alcohol policy

- The client may state whether alcohol will be used during the booking.
- If alcohol will be used, the client must accept the venue alcohol agreement before the booking is saved.
- The agreement confirms that **selling alcohol on the premises is prohibited**.
- Staff may reject or cancel a booking that violates the agreement or venue policy.

### BR-07: Extra services

Clients may request optional services such as a projector, sound system, or decoration. A service request does not guarantee availability; staff confirm it separately.

### BR-08: Advance payment

- The Atlas Training Room and Nova Auditorium require an advance payment when booked.
- The minimum advance is **50% of the calculated booking total**.
- The system must reject an affected booking when the entered advance is below the required amount.
- The Orion Meeting Room and Focus Desks do not require an advance under the current rules.

### BR-09: Cancellation penalties

Cancellation penalties apply only to the Training Room and Auditorium.

| Time before booking start | Penalty |
| --- | --- |
| More than 24 hours | 0% |
| 12–24 hours | 25% |
| 6–12 hours | 40% |
| Less than 6 hours | 50% |

The system calculates the penalty from the applicable booking total before the cancellation is confirmed.

### BR-10: Pricing

Each space has a published daily rate. The system calculates the booking total from the selected space and duration. The current application uses LKR rates from the space catalogue.

## Validation outcome

Before saving an active booking, the system must check the selected space, dates or time slot, capacity, cleaning buffer, overlap, alcohol agreement when required, and minimum advance payment when applicable. If validation fails, the user must see a clear reason.

## Examples

- A Training Room booking from 09:00–10:00 blocks a following booking until 11:00 because of its one-hour cleaning buffer.
- A Focus Desk booking from 09:00–10:00 blocks another booking for that same desk until 10:15.
- A client who chooses alcohol use but does not accept the agreement cannot save the booking.
- Cancelling an Auditorium booking five hours before it starts results in a 50% penalty.
- A Training Room booking with a total of LKR 24,000 requires an advance of at least LKR 12,000.

## Implementation note

The application should implement these rules on the server, not only in the browser, so they cannot be bypassed.
