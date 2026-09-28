# Seattle Student Discount Food Discovery System

## 1. ER Entity List

| Entity | Description | Example |
| --- | --- | --- |
| User | A student with a valid student ID at a Seattle university. | UW student Leo Wang or Seattle University student Lily Zhou. |
| Restaurant | A local restaurant offering student discounts. | Dong Ting Chun in Chinatown or Thai Tom in the U District. |
| Food Category | A dictionary for restaurant and dish categories. | Chinese, Thai, American fast food, desserts, Japanese and Korean. |
| Student Discount | A restaurant's exclusive discount policy for students. | 10% off at Dong Ting Chun with a student ID. |
| Food Check-in | A dining check-in that verifies discount use. | Leo spends $28 using a 10% student discount. |
| Dish Review | A rating and written review for a dish. | Spicy boiled fish rated 4.5: “Generous portion.” |
| Food Tag | A restaurant or dish attribute for filtering. | Good value, group dining, open late. |
| Saved Restaurant | A restaurant saved by a user. | Lily saves a high-value U District restaurant. |
| Food Ranking | A popularity and rating-based restaurant leaderboard. | Top 10 student-discount Chinese restaurants near UW. |
| Report | A report of a false discount or inaccurate review. | A discount mismatch report marked verified. |

## 2. Core Business Scenarios

### Student Users

- Filter restaurants by location, category, and discount level.
- Check in, review dishes and service, and save restaurants.
- Browse rankings and report false discounts or inappropriate reviews.
- View personal check-ins, favorites, and reviews.

### Restaurant Administrators

- Maintain restaurant details, menus, and student-discount rules.
- Review check-in data and feedback and reply to reviews.
- Update dishes and promotional offers.
