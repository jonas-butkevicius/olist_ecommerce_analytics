# Data Cleaning Report

### Order_Payments
- **Issue:** 9 rows where payment_value ≤ 0 detected.
- **Action:** Deleted invalid rows.
- **Method:**
    - Created a helper boolean column (is_valid) to flag invalid rows.
    - Filtered and removed flagged rows.

---

### Order_Products
- **Issue:** 4 invalid product_weight_g values (≤ 0).
- **Action:** Values set to blank.
- **Method:**
    - Used a helper boolean column to identify invalid weights.
    - Filtered rows and replaced values with null (blank).

---

### Order_Reviews
- **Issue:** 551 duplicate order_id entries detected, causing Many-to-Many relationship conflicts.
- **Action:** Consolidated to unique rows while preserving metadata and averaging scores.
- **Method:**
    - **Power Query Group By (Advanced):** Grouped by order_id.
    - **Aggregation 1:** Calculated Average of review_score.
    - **Aggregation 2:** Used All Rows to capture entire records in a table column.
    - **Transformation:** Applied `Table.FirstN` function to the grouped tables to retain original metadata (review_id, comments) from the first occurrence.
- **Result:** Established a 1-to-1 relationship with the orders table, resolving data model filtering issues.

---

### Geolocation
- **Issue:** Full row duplicates detected.
- **Action:** Removed duplicates.
- **Method:**
    - Used Excel "Remove Duplicates" tool selecting all columns.
- **Result:** 261,831 duplicate rows removed.

---

### Summary
All other tables passed validation checks and require no additional cleaning. The data model is now optimized for One-to-Many or One-to-One relationships across all key ID fields.