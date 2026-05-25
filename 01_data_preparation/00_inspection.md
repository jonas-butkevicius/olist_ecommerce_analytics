# Data Inspection

Initial inspection was performed to check data quality before cleaning.

---

## Customers

- Rows: **99,441**
- Missing values: **none**
- Uniqueness:
  - `customer_id` unique
  - `customer_unique_id` shows some customers placed multiple orders (**3,345**)
- Status: **clean**

---

## Sellers

- Rows: **3,095**
- Duplicates: **none**
- Missing values: **none**
- Status: **clean**

---

## Orders

- Rows: **99,441**
- Missing delivery dates: **4,908** (kept blank)
- Notes: missing dates mostly correspond to non-delivered order statuses
- Status: **acceptable**

---

## Order Payments

- Rows: **103,886**
- Missing values: **none**
- Checks performed: payment type distribution checked
- Issues: **9** rows where `payment_value ≤ 0` detected
- Status: **requires cleaning**

---

## Order Items

- Rows: **112,650**
- Missing values: **none**
- Notes: price and freight values valid
- Status: **clean**

---

## Order Products

- Rows: **32,951**
- Missing category-related metadata: **610** products
- Issues: **4** invalid weight values detected
- Status: **requires cleaning**

---

## Order Reviews
- Rows: 99,224 
- Notes: 
   Many blank comment fields (optional). 
 - Review dates are valid. 
 - Critical Issue: **551 duplicate order_id entries identified**, causing many-to-many relationship conflicts in the data model.

- Status: Needs Cleaning (Requires aggregation to ensure unique order_id per review).
---

## Category translation

- Rows: **71**
- Missing values: **none**
- Duplicates: **none**
- Status: **clean**

## Geolocation

- Issues: **full-row duplicates found**
- Status: **requires cleaning**
