# Risks, Limitations and Next Steps – Trace Spaces

Owner: G.L.D.A. De Silva

## Project risks
| Risk | Impact | Mitigation |
|---|---|---|
| Run out of time | High | Must stories first, clash logic before UI polish |
| Merge conflicts | Medium | One owner per file, pull before push, small commits |
| Scope creep (payments, logins) | Medium | Marked Won't for today in the backlog |
| Real email needs a server | Low | Inquiry inbox in the app for now |

## Current limitations (prototype)
- Data is stored in each browser (localStorage), so staff do not share data yet.
- The request form does not send a real email; requests appear in the Inquiries tab.
- Spaces, seats and rates come from TRACE's Spaces listing. Hot desk pools and rates are sample values. Several listings show 150 seats and identical facilities, to be confirmed with TRACE.

## Next steps
1. Confirm seat counts, desk pricing and "On demand" rates with TRACE, and link the EventHub Spaces page to this booking engine.
2. Shared database and staff login so all staff see the same bookings.
3. Email notifications to admins and confirmations to customers.
4. Online payment, invoices, monthly occupancy and revenue reports.
5. The multi-location model already works, so the product can be sold to BMICH, wedding halls and theatres.
