# Seattle Independent Coffee Shop Check-in and Review System

## 1. ER Entity List

| Entity | Description | Example |
| --- | --- | --- |
| User | A coffee enthusiast, primarily a Seattle student or local professional. | UW student Emma Chen and Capitol Hill professional Alex Park. |
| Coffee Shop | A local independent coffee shop and the system's core resource. | Stumptown Coffee Roasters Capitol Hill or La Marzocco Cafe. |
| Coffee Category | A dictionary for categorizing menu drinks. | Espresso, pour-over, cold brew, oat latte. |
| Shop Tag | A shop attribute used for filtering and recommendations. | Good for studying, outdoor seating, pet friendly, Wi-Fi. |
| Check-in | A record of a user's visit, time, and purchase. | Emma checks in at Stumptown after ordering a Geisha pour-over. |
| Drink Review | A rating and written review for an individual drink. | An oat latte rated 4.5: “Smooth foam.” |
| Shop Note | A long-form visit report posted by a user. | “A Guide to Five Hidden Coffee Shops in Ballard.” |
| Saved Shop | A shop saved by a user for a future visit. | Emma saves coffee shops in Ballard. |
| Coffee Event | An offline event published by a shop. | A fall pour-over cupping, limited to 15 people. |
| Comment Reply | A response to a shop note or review. | “I have been there; it is busy on weekends.” |

## 2. Core Business Scenarios

### General Users

- Filter local coffee shops by neighborhood, tags, and rating.
- Check in after a visit and review individual drinks.
- Publish shop notes, reply to others, and save shops.
- Register for cupping sessions and roasting workshops.

### Shop Administrators

- Maintain shop details, menus, and tags.
- Publish events and review check-in and feedback data.
- Respond to reviews to improve service and drink quality.
