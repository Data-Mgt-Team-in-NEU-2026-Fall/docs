# Seattle Campus Event Ticketing and Check-in System

## 1. ER Entity List

| Entity | Description | Example |
| --- | --- | --- |
| User | A participant, organizer, or venue administrator. | UW student Leo Wang or a UW Tech Club organizer. |
| Organizer | A campus organization that publishes events. | UW Computer Science, UW Entrepreneurship Association. |
| Event Type | A dictionary for categorizing campus events. | Tech talk, academic forum, startup session, performance. |
| Campus Event | A published event open for registration. | An AWS AI technology talk limited to 200 people. |
| Event Venue | A reservable campus venue linked to an event. | UW Kane Hall 225. |
| Guest Speaker | Event speaker or invited guest details. | Alex Zhang presents production LLM engineering. |
| E-ticket | A registration-generated ticket used for entry. | Ticket ACT20260925001. |
| Check-in Record | A record of a participant's arrival time. | Leo checks in at 18:55 on September 25. |
| Event Review | A participant's rating and feedback. | Five stars: “Practical and insightful.” |
| Registration Record | An event registration record and its status. | Lily registers for a startup session. |

## 2. Core Business Scenarios

### Student Participants

- Filter events by type, organizer, and time; register for e-tickets.
- Check in with e-tickets and submit feedback afterward.
- View personal registrations, check-ins, and reviews.

### Organizers

- Publish events, link venues and speakers, and set capacity limits.
- Review registrations, export check-in data, and collect feedback.
- Manage event status and publish cancellation or rescheduling notices.
