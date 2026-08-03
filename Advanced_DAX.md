# Advanced DAX Documentation

# Executive Financial Analytics Dashboard

## Overview

This document explains the advanced DAX techniques used throughout the Executive Financial Analytics Dashboard.

Rather than only presenting formulas, this guide explains the business purpose behind each calculation and why specific DAX functions were chosen.

---

# 1. DIVIDE()

## Why use DIVIDE instead of "/"

DIVIDE safely performs division while preventing divide-by-zero errors.

### Example

```DAX
Profit Margin % =
DIVIDE(
    [Total Profit],
    [Total Sales],
    0
)
```

### Why?

If Total Sales equals zero, Power BI returns **0** instead of an error.

Used in

- Profit Margin KPI
- Country Profit Margin
- Product Profitability

---

# 2. DISTINCTCOUNT()

## Purpose

Counts unique values.

### Example

```DAX
Total Countries =
DISTINCTCOUNT(FactFinancials[Country])
```

Business Value

Calculates how many countries the company operates in.

Another example

```DAX
Total Products =
DISTINCTCOUNT(FactFinancials[Product])
```

---

# 3. VAR

## Purpose

Stores values temporarily to improve readability and performance.

Example

```DAX
Dashboard Title =
VAR SelectedYear =
IF(
    HASONEVALUE(Date[Year]),
    SELECTEDVALUE(Date[Year]),
    "All Years"
)

RETURN

"Executive Financial Analytics Dashboard | "
&
SelectedYear
```

Why use VAR?

- Cleaner code
- Faster calculations
- Easier debugging

---

# 4. HASONEVALUE()

## Purpose

Checks whether only one value has been selected.

Example

```DAX
HASONEVALUE(Date[Year])
```

Business Value

Allows dashboard titles to change depending on slicer selections.

---

# 5. SELECTEDVALUE()

## Purpose

Returns the selected value from a slicer.

Example

```DAX
SELECTEDVALUE(Date[Year])
```

Business Value

Used in:

- Dynamic Dashboard Titles
- Product Page Titles
- Regional Dashboard Titles

---

# 6. IF()

## Purpose

Returns different results depending on logical conditions.

Example

```DAX
IF(
    HASONEVALUE(Date[Year]),
    SELECTEDVALUE(Date[Year]),
    "All Years"
)
```

Business Value

Improves user experience by making reports dynamic.

---

# 7. TOPN()

## Purpose

Returns the highest-ranking records.

Example

```DAX
Top Product =
MAXX(
    TOPN(
        1,
        VALUES(FactFinancials[Product]),
        [Total Sales]
    ),
    FactFinancials[Product]
)
```

Business Value

Automatically identifies the highest-selling product.

---

# 8. MAXX()

## Purpose

Returns the maximum value after evaluating an expression.

Example

```DAX
Most Profitable Product =
MAXX(
    TOPN(
        1,
        VALUES(FactFinancials[Product]),
        [Total Profit]
    ),
    FactFinancials[Product]
)
```

Business Value

Finds the product generating the greatest profit.

---

# 9. VALUES()

## Purpose

Returns a unique list of values from a column.

Example

```DAX
VALUES(FactFinancials[Product])
```

Business Value

Creates dynamic rankings and product lists.

---

# 10. TOTALYTD()

## Purpose

Calculates Year-To-Date values.

Example

```DAX
YTD Sales =
TOTALYTD(
    [Total Sales],
    'Date'[Date]
)
```

Business Value

Allows executives to monitor cumulative sales throughout the year.

---

# 11. AVERAGEX()

## Purpose

Calculates averages by evaluating expressions over a table.

Example

```DAX
Average Monthly Sales =
AVERAGEX(
    VALUES('Date'[Month Name]),
    [Total Sales]
)
```

Business Value

Shows average monthly business performance.

---

# 12. Dynamic Dashboard Titles

Instead of static page titles, DAX generates titles based on filters.

Example

```DAX
Regional Page Title =
VAR SelectedYear =
IF(
    HASONEVALUE(Date[Year]),
    SELECTEDVALUE(Date[Year]),
    "All Years"
)

RETURN

"🌍 Regional Performance Analytics | "
&
SelectedYear
```

Benefits

- Interactive reporting
- Better user experience
- Executive-ready dashboards

---

# 13. Dynamic Business Insights

Example

```DAX
Product Insight =
"Top Revenue Product: "
&
[Top Product]
&
UNICHAR(10)
&
"Top Profit Product: "
&
[Most Profitable Product]
```

Business Value

Creates automated business commentary without manual updates.

---

# DAX Functions Used

The project demonstrates practical experience with:

- SUM()
- DIVIDE()
- DISTINCTCOUNT()
- IF()
- VAR
- RETURN
- HASONEVALUE()
- SELECTEDVALUE()
- VALUES()
- TOPN()
- MAXX()
- AVERAGEX()
- TOTALYTD()
- UNICHAR()

---

# Business Intelligence Skills Demonstrated

This project demonstrates the ability to:

- Build reusable DAX measures
- Create dynamic dashboards
- Develop executive KPI calculations
- Apply time intelligence
- Design interactive reports
- Generate automated business insights
- Implement financial performance metrics
- Build enterprise-level reporting solutions

---

# Key Takeaways

Through this project, DAX was used not only to calculate metrics but also to improve report interactivity, enhance executive reporting, and support data-driven decision-making.
