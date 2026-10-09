# Seattle Pet Boarding Mutual-Aid Platform

## 1. ER Entity List

| Entity | Description | Example |
| --- | --- | --- |
| User | A pet owner or a host household among local residents and students. | UW student Leo Wang or Ballard resident Lisa Park. |
| Pet | Registered pet details and the core boarding object. | Doudou, a vaccinated and gentle two-year-old Golden Retriever. |
| Pet Breed | A classification dictionary for pet breeds. | Golden Retriever, Ragdoll, Corgi, British Shorthair. |
| Host Household | A verified household offering boarding services. | Lisa's house has a yard and accepts medium-sized dogs. |
| Boarding Request | An owner's requested boarding dates, pet, and requirements. | Seven-day Golden Retriever care with two walks daily. |
| Boarding Order | A confirmed service order and its lifecycle status. | An October 1-7 order costing $350. |
| Vaccination Record | A pet immunization record for eligibility review. | Doudou's rabies and combination vaccines are valid. |
| Boarding Review | A post-service rating between the owner and household. | “Thoughtful care and daily videos.” |
| Favorite | A saved host household or pet. | A saved highly rated Ballard host household. |
| Complaint | A boarding-dispute report used for mediation. | A missed-walk complaint marked under mediation. |

## 2. Core Business Scenarios

### Pet Owners

- Register pets and vaccinations and publish boarding requests.
- Filter households by area, price, and rating and submit requests.
- Receive daily updates, then review or report disputes.

### Host Households

- Verify qualifications and set accepted pets, prices, and services.
- Review requests, confirm orders, and update daily pet status.
- Manage reviews, orders, and service information.
