# DAX Measures Documentation

## Overview
This document contains the DAX measures developed for the Brazilian E-Commerce Business Intelligence project using Power BI.

All measures are organized in a dedicated `_Measures` table to maintain a clean and structured data model.

## 1. Total Revenue

```dax
Total Revenue =
SUM(Order_Items[price])
```

**Purpose:** Calculates total product sales value, excluding freight charges.

## 2. Total Orders

```dax
Total Orders =
DISTINCTCOUNT(Orders[order_id])
```

**Purpose:** Calculates the number of unique orders.

## 3. Total Customers

```dax
Total Customers =
DISTINCTCOUNT(Customers[customer_unique_id])
```

**Purpose:** Calculates the number of unique customers.

## 4. Average Order Value

```dax
Average Order Value =
DIVIDE(
    [Total Revenue],
    [Total Orders],
    0
)
```

**Purpose:** Calculates average product sales value per order.

## 5. Delivered Orders

```dax
Delivered Orders =
CALCULATE(
    [Total Orders],
    Orders[order_status] = "delivered"
)
```

**Purpose:** Counts orders with delivered status.

## 6. Average Review Score

```dax
Average Review Score =
AVERAGE(Reviews[review_score])
```

**Purpose:** Calculates the average customer review score.

## 7. Total Freight

```dax
Total Freight =
SUM(Order_Items[freight_value])
```

**Purpose:** Calculates total freight charges associated with order items.

## 8. Total Payment Value

```dax
Total Payment Value =
SUM(Payments[payment_value])
```

**Purpose:** Calculates the total recorded payment transaction value.

## 9. Expected Order Charges

```dax
Expected Order Charges =
[Total Revenue] + [Total Freight]
```

**Purpose:** Calculates expected product and freight charges.

## 10. Payment Difference

```dax
Payment Difference =
[Total Payment Value] - [Expected Order Charges]
```

**Purpose:** Identifies the difference between recorded payments and expected product-plus-freight charges.

## Financial Reconciliation Note

Payment differences represent discrepancies between recorded payment values and expected product-plus-freight charges.

These differences should not automatically be interpreted as missing funds, retained payments, or unprocessed refunds. Further investigation using refund and transaction records would be necessary.

## Technical Skills Demonstrated
- DAX measure development
- Aggregation functions
- CALCULATE and filter context
- DIVIDE and error handling
- SUMX and iterator functions
- DISTINCTCOUNT
- Financial reconciliation
- Business KPI development
