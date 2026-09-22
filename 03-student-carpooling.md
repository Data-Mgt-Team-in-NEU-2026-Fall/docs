# Seattle Student Carpooling System

## 1. ER Entity List

| Entity | Description | Example |
| --- | --- | --- |
| User | A student driver or passenger. | UW graduate student driver Leo Wang and SU passenger Lily Zhou. |
| Driver Profile | Verified supplemental information for a driver account. | Leo has five years of accident-free driving experience. |
| Vehicle | A registered vehicle used for eligibility verification. | A 2020 Toyota Corolla licensed in Washington, seating four. |
| Carpool Route | A reusable template for a regular commute route. | UW main campus to Seattle-Tacoma International Airport. |
| Carpool Trip | A single bookable ride published by a driver. | A September 30 airport trip with three open seats at $15 each. |
| Ride Registration | A passenger's booking record and status. | Lily books the airport trip; status confirmed. |
| Saved Location | A frequently used pickup or drop-off location. | UW North Campus housing or the airport arrivals level. |
| Trip Review | A post-trip rating between driver and passenger. | “Punctual, clean car, and smooth driving.” |
| Complaint | A report concerning a trip or user behavior. | A late cancellation complaint, marked resolved. |
| Notification | A message about trip changes or booking confirmations. | “The driver confirmed your booking.” |

## 2. Core Business Scenarios

### Drivers

- Verify driver and vehicle information; publish trips with time, route, and fare.
- Review, confirm, or cancel passenger registrations.
- Manage trip history, feedback, and notifications.

### Passengers

- Filter trips by route and time and submit registrations.
- Save frequent locations and review registration status.
- Submit reviews or report inappropriate trips or drivers.
