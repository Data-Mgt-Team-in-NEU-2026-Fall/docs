# Seattle Farmers Market Ordering System

## 1. ER Entity List

| Entity | Description | Example |
| --- | --- | --- |
| User | A local resident or university student consumer. | UW student Lily Zhou or Capitol Hill resident Emma Chen. |
| Farmer | A local farm or market vendor supplying goods. | A Snoqualmie Valley organic farm or Pike Place jam vendor. |
| Product Category | A dictionary for fresh-product classification and search. | Produce, baked goods, jams and honey, dairy. |
| Farm Product | A product listed by a farmer for sale. | Five pounds of Washington organic apples for $12. |
| Market Session | A physical farmers market event linked to farmers and products. | Pike Place Saturday Farmers Market. |
| Order | A customer's product purchase record and status. | Apples and jam for September 27 pickup. |
| Pickup Point | A physical product pickup location for a market session. | Pike Place Market pickup counter 3. |
| Product Review | A rating and review of product taste and quality. | Five stars: “Fresh and crisp.” |
| Saved Product | A product saved for a later repeat purchase. | Emma saves handmade raspberry jam. |
| Delivery Record | A shipping record for farm-provided delivery service. | A UW housing delivery marked delivered. |

## 2. Core Business Scenarios

### Consumers

- Filter products by category and farm and order for a market session.
- Pick up at the market or select home delivery.
- Submit quality reviews and save farms and products.
- View personal orders, favorites, and reviews.

### Farmers and Vendors

- Maintain farm profiles; publish products and set price and inventory.
- Manage market registration, orders, and pickup preparation.
- Review feedback and sales data and update products and inventory.
