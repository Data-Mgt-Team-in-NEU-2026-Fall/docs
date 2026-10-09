# Campus Secondhand Marketplace EER Diagram: PlantUML Version

This article converts the [original draw.io EER diagram](Seattle%20Campus%20Second%20Hand%20Market%20Place%20-%20EER%202.drawio) into editable PlantUML. It preserves the original entities, attributes, relationship names, cardinalities, and subtype constraints without adding database fields, data types, or foreign keys.

## Conversion Conventions

- Native Chen EER syntax starts with `@startchen`: `entity` renders as an entity rectangle, attributes render as ellipses, and `relationship` explicitly defines a relationship diamond. This is not a relational database schema.
- The connection labels `1`, `(0,1)`, `(0,N)`, and `(1,N)` correspond to the original `1..1`, `0..1`, `0..N`, and `1..N`, respectively, preserving the cardinality labels at each entity end.
- `SAVES` remains a many-to-many relationship between users and items. Its `date_saved` attribute is defined inside `relationship SAVES` and renders as an attribute ellipse connected to the relationship diamond.
- `=>= d` represents total, disjoint specialization, corresponding to the original diagram's `t` and `d`. Subtypes inherit their supertype's attributes; no additional IDs are introduced.
- Relationships with the same display name use distinct aliases. For example, `SUBMITS_REQUEST` and `SUBMITS_REPORT` both display as `SUBMITS` but represent separate relationship diamonds. In the recursive category relationship `CATEGORY_HAS`, the `(0,1)` end represents the parent category and the `(0,N)` end represents child categories.
- In the original file, the `item_id` connection is not bound to the item endpoint, and the order-to-`BUYER REVIEW` connection through `HAS` is not bound to the review endpoint. These connections are restored based on their drawn positions and the design notes. Two standalone cardinality labels at the item end are assigned to `TAGGED_WITH` (`0..N`) and `REQUESTS` (`1..1`). These adjustments restore drawing connections rather than introduce new business rules.

## Complete PlantUML

The following code defines a complete conceptual ER diagram. Render it with a recent PlantUML preview tool that supports Chen EER; a standard Markdown reader may display only the code. The `smetana` layout does not require an external Graphviz installation.

```plantuml
@startchen campus_secondhand_marketplace_eer
!pragma layout smetana
left to right direction
skinparam shadowing false

title Seattle Campus Second Hand Marketplace - EER

entity USER {
  user_id
  first_name
  last_name
  email
  phone
  birth_date
  date_joined
}

entity USER_ROLE {
  role_id
  role_name
}

entity CAMPUS {
  campus_id
  campus_name
  address
  city
  state
  zip_code
  latitude
  longitude
}

entity SECONDHAND_ITEM {
  item_id
  title
  description
  asking_price
  condition
  listing_date
  status
  brand
  model
  year_acquired
  photo_url
}

entity ITEM_CATEGORY {
  category_id
  category_name
  description
  active_status
}

entity ITEM_TAG {
  tag_id
  tag_name
}

entity PURCHASE_REQUEST {
  request_id
  request_date
  offered_price
  message
  status
}

entity TRANSACTION_ORDER {
  transaction_id
  agreed_price
  transaction_date
  pickup_datetime
  status
}

entity PICKUP_POINT {
  pickup_point_id
  pickup_point_name
  address
  latitude
  longitude
  description
  active_status
}

entity CONVERSATION {
  conversation_id
  created_at
}

entity MESSAGE {
  message_id
  content
  sent_at
}

entity TRANSACTION_REVIEW {
  review_id
  rating
  comment
  review_date
  review_status
}

entity "BUYER REVIEW" as BUYER_REVIEW {
}

entity "SELLER REVIEW" as SELLER_REVIEW {
}

entity REPORT {
  report_id
  reason
  description
  report_date
  status
}

entity ITEM_REPORT {
}

entity TRANSACTION_REPORT {
}

relationship HAS_ROLE {
}
relationship BELONGS_TO {
}
relationship LISTS {
}
relationship SAVES {
  date_saved
}
relationship CLASSIFIES {
}
relationship "HAS" as CATEGORY_HAS {
}
relationship TAGGED_WITH {
}
relationship "SUBMITS" as SUBMITS_REQUEST {
}
relationship REQUESTS {
}
relationship RESULTS_IN {
}
relationship BUYS {
}
relationship SELLS {
}
relationship USES {
}
relationship ABOUT {
}
relationship "BY" as CONVERSATION_BY {
}
relationship CONTAINS {
}
relationship "BY" as MESSAGE_BY {
}
relationship WRITES {
}
relationship RECEIVES {
}
relationship "HAS" as HAS_BUYER_REVIEW {
}
relationship "HAS" as HAS_SELLER_REVIEW {
}
relationship "SUBMITS" as SUBMITS_REPORT {
}
relationship "REPORTS" as REPORTS_ITEM {
}
relationship "REPORTS" as REPORTS_TRANSACTION {
}

USER -(0,N)- HAS_ROLE
HAS_ROLE -(1,N)- USER_ROLE
USER -(0,N)- BELONGS_TO
BELONGS_TO -1- CAMPUS
USER -1- LISTS
LISTS -(0,N)- SECONDHAND_ITEM
USER -(0,N)- SAVES
SAVES -(0,N)- SECONDHAND_ITEM

ITEM_CATEGORY -1- CLASSIFIES
CLASSIFIES -(0,N)- SECONDHAND_ITEM
ITEM_CATEGORY -(0,1)- CATEGORY_HAS
CATEGORY_HAS -(0,N)- ITEM_CATEGORY
SECONDHAND_ITEM -(0,N)- TAGGED_WITH
TAGGED_WITH -(0,N)- ITEM_TAG

USER -1- SUBMITS_REQUEST
SUBMITS_REQUEST -(0,N)- PURCHASE_REQUEST
SECONDHAND_ITEM -1- REQUESTS
REQUESTS -(0,N)- PURCHASE_REQUEST
PURCHASE_REQUEST -1- RESULTS_IN
RESULTS_IN -(0,1)- TRANSACTION_ORDER
USER -1- BUYS
BUYS -(0,N)- TRANSACTION_ORDER
USER -1- SELLS
SELLS -(0,N)- TRANSACTION_ORDER
PICKUP_POINT -1- USES
USES -(0,N)- TRANSACTION_ORDER

CONVERSATION -(0,N)- ABOUT
ABOUT -1- SECONDHAND_ITEM
CONVERSATION -(0,N)- CONVERSATION_BY
CONVERSATION_BY -(1,N)- USER
CONVERSATION -1- CONTAINS
CONTAINS -(1,N)- MESSAGE
MESSAGE -(0,N)- MESSAGE_BY
MESSAGE_BY -1- USER

USER -1- WRITES
WRITES -(0,N)- TRANSACTION_REVIEW
USER -1- RECEIVES
RECEIVES -(0,N)- TRANSACTION_REVIEW
TRANSACTION_REVIEW =>= d { BUYER_REVIEW, SELLER_REVIEW }
TRANSACTION_ORDER -1- HAS_BUYER_REVIEW
HAS_BUYER_REVIEW -(0,1)- BUYER_REVIEW
TRANSACTION_ORDER -1- HAS_SELLER_REVIEW
HAS_SELLER_REVIEW -(0,1)- SELLER_REVIEW

USER -1- SUBMITS_REPORT
SUBMITS_REPORT -(0,N)- REPORT
REPORT =>= d { ITEM_REPORT, TRANSACTION_REPORT }
SECONDHAND_ITEM -1- REPORTS_ITEM
REPORTS_ITEM -(0,N)- ITEM_REPORT
TRANSACTION_ORDER -1- REPORTS_TRANSACTION
REPORTS_TRANSACTION -(0,N)- TRANSACTION_REPORT
@endchen
```

## Interpretation and Scope

All users are modeled as `USER`. Buyer and seller are transaction roles expressed through `BUYS` and `SELLS`, not user subtypes. Each order originates from one purchase request and has one buyer, one seller, and one pickup point. A request can produce at most one order. Each order can have at most one review of its buyer and one review of its seller.

`BUYER REVIEW` refers to a review of the buyer, and `SELLER REVIEW` refers to a review of the seller, not the author's role. Each report targets either one item or one transaction, never both. Only the buyer or seller of an order may submit a transaction report about that order.

Conversations concern specific items, with participation and message authorship modeled separately. The original cardinalities require at least one participant and at least one message per conversation. This version neither restricts participation to exactly two users nor permits empty conversations.

The original diagram does not define attribute data types, primary-key markers, or physical foreign keys, so this version does not infer them. Item reservations and cancellations, seller confirmation of completion, ownership of personal pickup locations, messaging permissions, and review eligibility remain implementation constraints. See the [EER design decisions](er-design-decisions.md) for details.