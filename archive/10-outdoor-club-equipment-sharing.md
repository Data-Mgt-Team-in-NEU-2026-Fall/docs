# Seattle Campus Outdoor Club Activity and Equipment-Sharing System

## 1. ER Entity List

| Entity | Description | Example |
| --- | --- | --- |
| User | A student, club administrator, or activity leader. | UW student Leo Wang, SU club president Emma Chen, or WFA-certified Alex Zhang. |
| Outdoor Club | A university outdoor organization responsible for activities and equipment. | UW Hiking Club, SU Ski & Snowboard Club, UW Kayak Club. |
| Activity Type | A dictionary for classifying and filtering outdoor activities. | Hiking, alpine skiing, flatwater kayaking, camping, mountain biking. |
| Outdoor Activity | A club-published activity connecting routes, leaders, and registrations. | A Paradise Trail day hike limited to 25 people. |
| Outdoor Route | A reusable Seattle-area outdoor location or route. | Skyline Trail, Bainbridge Island kayak route, Snoqualmie Valley camping route. |
| Activity Leader | A qualified trip leader associated with a user and club. | Alex has led 42 trips and holds WFA certification. |
| Equipment Category | A dictionary for managing and finding outdoor equipment. | Camping, hiking, water-sports, and protective gear. |
| Outdoor Equipment | Club-owned equipment available for shared rental. | A UW Hiking Club two-person tent, eight in stock, $12 daily. |
| Activity Registration | A user's activity registration record and participation status. | Leo registers for a Mount Rainier hike. |
| Equipment Rental Order | A rental record covering order placement through return. | Leo rents a tent from October 4 through October 6. |
| Activity Review | Participant feedback that records activity quality. | Five stars: “Excellent scenery and professional guidance.” |

## 2. Core Business Scenarios

### Students

- Browse and filter club activities by type, time, and difficulty; register or cancel online.
- View routes around Mount Rainier, Puget Sound, and the Cascades and save favorites.
- Reserve shared equipment, select pickup and return times, and review rental costs and status.
- Submit optional anonymous ratings and reviews after activities and view personal history.

### Club Administrators

- Maintain club information, leader permissions, and member rosters.
- Publish, edit, or cancel activities; link routes and leaders; set capacity and fees.
- Manage equipment inventory, condition, and daily rental price.
- Review rental requests, record check-out and returns, and update order status.
- View registrations, equipment utilization, and aggregated reviews.

### Activity Leaders

- View participant lists and contact information.
- Check in participants and update activity progress on site.
- Review feedback to improve future trips.
