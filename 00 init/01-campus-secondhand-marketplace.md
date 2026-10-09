# Seattle Campus Secondhand Marketplace

## 1. ER Entity List

| Entity | Description | Example |
| --- | --- | --- |
| User | A student buyer, seller, or platform administrator at a Seattle university. | UW computer science student Leo Wang sells a used monitor. |
| Item Category | A classification dictionary for listing and filtering goods. | Electronics, textbooks, home goods, outdoor gear, accessories. |
| Secondhand Item | A user-posted item available for sale. | A like-new Dell 27-inch monitor for $80. |
| Transaction Order | A record of a completed buyer-seller agreement and its status. | Leo sells a monitor to Lily; pickup is pending. |
| Purchase Request | A buyer's request for a specific item. | A UW CSE sophomore seeks textbooks under $200. |
| Pickup Point | A pickup location negotiated and agreed upon by the buyer and seller (typically a campus spot). | UW Red Square or the SU Student Center, as mutually arranged. |
| Item Tag | An item attribute used for search and recommendations. | Like new, negotiable, UW pickup, accessories included. |
| Transaction Review | A post-transaction rating between buyer and seller. | A five-star review: “Condition matched the description.” |
| Favorite | A record of an item saved by a user. | Lily saves a used mechanical keyboard. |
| Report | A report of an inappropriate item or transaction. | A counterfeit-brand report marked received. |

## 2. Core Business Scenarios

### Student Buyers and Sellers

- Post item details, photos, prices, and exchange methods.
- Filter listings by category, price, and campus, or publish purchase requests.
- Complete exchanges at a mutually agreed pickup point, submit reviews, and save items.
- View personal listings, orders, favorites, and reviews.

### Platform Administrators

- Review prohibited listings, process reports, and suspend violating accounts.
- Maintain category and tag dictionaries.
- View transaction, listing-volume, and user-activity data.