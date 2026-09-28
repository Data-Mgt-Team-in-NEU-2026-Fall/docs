# EER Diagram Review Suggestions for the Seattle Campus Second-hand Trading Platform

## 1. Issues and Resolution Steps

### P1. A report must target exactly one of: an item or a transaction

The diagram rules require each `REPORT` to target only one second-hand item or one transaction, but the current two independent `REPORTS` relationships cannot express this exclusivity. Additionally, the submitter of a transaction report must be either the buyer or the seller of that transaction.

**Resolution steps:**

1. Treat `REPORT` as a superclass and add two subclasses, `ITEM_REPORT` and `TRANSACTION_REPORT`, marked as a **total and disjoint** specialization: every report must and can only belong to one of these subclasses.
2. Let `ITEM_REPORT` associate with exactly one `SECONDHAND_ITEM`, and `TRANSACTION_REPORT` associate with exactly one `TRANSACTION_ORDER`; remove the original `REPORTS` relationships from the superclass `REPORT` to both objects, so as to avoid duplicate or dual-pointing representations.
3. Keep the `SUBMITS` relationship from the reporter to `REPORT`, and note that the submitter of a `TRANSACTION_REPORT` must be the buyer or seller of the associated order; this cross-relationship constraint cannot be enforced by the subtype itself and still requires validation in subsequent logical design.

### P2. Buyer reviews and seller reviews should be constrained separately

The rules allow at most two reviews per transaction: the buyer reviews the seller once, and the seller reviews the buyer once. Merely annotating the order-to-review relationship as `0..2` cannot prevent the same party from reviewing repeatedly.

**Resolution steps:**

1. Treat `TRANSACTION_REVIEW` as a superclass and add two **total and disjoint** subclasses, `BUYER_REVIEW` (written by the buyer, evaluating the seller) and `SELLER_REVIEW` (written by the seller, evaluating the buyer), sharing attributes such as rating, comment, and date.
2. Each subclass review must belong to exactly one `TRANSACTION_ORDER`; each order may be associated with at most one `BUYER_REVIEW` and one `SELLER_REVIEW`. Annotate the two order-review relationships with `0..1` respectively, and note that each review corresponds to its order with `1..1`. The pre-generalization order-review `HAS` relationship should not be kept in parallel with the subclass relationships.
3. Make the relationship between review author and reviewee explicit in the two subclasses: the author of a buyer review is the order's buyer and the target is the seller, and vice versa for a seller review. Remove or replace the original `WRITES` and `RECEIVES` relationships that could not distinguish these two roles, to avoid modeling the same fact twice; in subsequent logical design, validate that these users match the order participants and that the buyer and seller are not the same user.

### P3. Item categories support multiple hierarchy levels

Currently `ITEM_CATEGORY` does not express hierarchy among categories. When multi-level categorization is needed, use a recursive relationship in which a category participates with itself to represent parent-child categories, rather than creating a subtype for each level.

**Resolution steps:**

1. Add a self-relationship `HAS_SUBCATEGORY` to `ITEM_CATEGORY`, labeling the two ends with the "parent category" and "child category" roles respectively.
2. Each category has `0..1` parent categories (a top-level category has no parent) and may have `0..N` child categories; keep the existing `CLASSIFIES` relationship between items and categories.
3. Prohibit a category from being its own ancestor in the business rules to avoid cycles; if multiple parents are allowed in the future, re-evaluate the cardinality at the parent end.

### P4. Every user must belong to a campus

On-campus shopping requires every `USER` to be associated with exactly one `CAMPUS`. This is **not a one-to-one relationship**: one campus may be associated with multiple users, so `CAMPUS` and `USER` form a one-to-many relationship.

**Resolution steps:**

1. Keep `USER`—`BELONGS_TO`—`CAMPUS`, and make explicit that each user corresponds to `1..1` campus and each campus corresponds to `0..N` users; the user end is mandatory participation.
2. Check and adjust the cardinality labels at both ends of `BELONGS_TO` on the diagram according to the above semantics, so as not to mistakenly write "a user has only one campus" as "a campus has only one user".
3. State this requirement explicitly in the diagram's business rules; the project description includes administrators, and if administrators are also modeled as `USER`, they must likewise be associated with a campus.

### P5. Purchase requests cannot replace two-way communication under an item

`PURCHASE_REQUEST` expresses a buyer's purchase intention, offer, and request status; the existing `message` attribute can only record a single piece of text for that request and cannot represent the back-and-forth messages exchanged between buyer and seller around the same item. Even without submitting a purchase request, a user should still be able to contact the item's publisher.

**Resolution steps:**

1. Keep `PURCHASE_REQUEST` and its existing relationships to express a formal purchase intention; add `CONVERSATION` (a conversation, with `conversation_id` and `created_at`), where each conversation is associated with exactly one `SECONDHAND_ITEM`, one interested `USER`, and that item's publishing `USER`. One item or one user may participate in multiple conversations.
2. Add `MESSAGE` (a message, with `message_id`, `content`, and `sent_at`), where each message belongs to exactly one conversation and is sent by one user in that conversation; a conversation may contain multiple messages and either party may send them. Messages should be ordered by send time and identifier, and the `PURCHASE_REQUEST.message` field should not be used as chat history.
3. Do **not** impose a mandatory relationship between conversations and purchase requests: a user may start a conversation without a request; if tracing which conversation a request originated from is needed later, add an optional conversation association to the request, but do not let message sending depend on request status.
4. State clearly in the business rules that the conversation's publisher must be the associated item's publisher, the two participants cannot be the same, and the message sender must be a participant; to avoid duplicate conversations for the same buyer and item, adopt the convention of at most one conversation per "item + buyer" pair.

### P6. Pickup location belongs in the order, not as a fixed admin-designated pickup point

In real life it is rare for an administrator to designate fixed pickup locations for users, unless that location is an actual warehouse. Therefore, pickup-location-related content is better considered within the user's order, and the original assumption of fixed admin-managed pickup points should be treated as a requirement that needs re-discussion and redesign.

**Resolution steps:**

1. Do not introduce a fixed `PICKUP_POINT` entity managed by an administrator in the current EER; this design does not match common real-world practice and would over-model an unrealistic assumption.
2. If a physical exchange location is needed, model it as an attribute or relationship attached to `TRANSACTION_ORDER` (e.g., a delivery/pickup address or a chosen meeting location), keeping it within the order's scope rather than as a standalone fixed entity.
3. Only treat a pickup location as a first-class entity when it represents an actual warehouse or stock location; in that case, re-discuss the requirement and redesign accordingly instead of reusing the admin-fixed pickup-point concept.
4. Flag this as a requirement that needs re-discussion and redesign before finalizing the EER, since the premise of administrator-fixed pickup points is generally unrealistic and affects how orders and logistics are modeled.