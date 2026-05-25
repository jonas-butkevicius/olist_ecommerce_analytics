# 📌 Integrity Checks (Referential Integrity)

**Goal:** Verify that foreign keys reference existing primary keys.

**Validation Logic Examples:**

Customer Check:

=XLOOKUP([@customer_id]; tbl_customers[customer_id]; "Match"; "Missing Customer")

Product Translation Check:

=XLOOKUP([@product_category_name]; tbl_category_translation[product_category_name]; "Translated"; "Missing Translation")
---

## Relationships Checked

- Orders → Customers (tbl_customers)
- Order Payments → Orders (tbl_orders)
- Order Items → Orders (tbl_orders)
- Order Items → Products (tbl_products)
- Order Items → Sellers (tbl_sellers)
- Order Reviews → Orders (tbl_orders)
- Products → Category Translation (tbl_category_translation)