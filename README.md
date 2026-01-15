# Nykaa-Powerbi-sales-performance-analysis

this project analyzes nykaa’s sales, marketing, logistics, and customer behavior
using power bi, with a focus on understanding what drives revenue and where
operational friction impacts performance.

the analysis covers two major product categories — makeup and skincare —
and evaluates how campaigns, delivery performance, customer behavior,
and refunds influence overall business outcomes.

---

## project objectives
- identify the top-performing product category
- evaluate whether logistics impact revenue and repeat purchases
- measure campaign roi and conversion performance
- analyze refund and return patterns across campaigns
- understand customer behavior trends and retention signals
- forecast future sales, orders, and refund amounts

---

## data overview
- total rows: ~7,000–8,000
- total tables: 8
- data sources:
  - csv files
  - sql server
- a small calculated table was created for mapping urls and brand images
  to improve report visuals

---

## data cleaning & preprocessing (power query)

### orders table
- handled rating outliers (negative values and values >5) by replacing them with median values
- filled missing delivery and shipping dates based on observed patterns
- rounded delivery partner ratings to two decimals for consistency

### products table
- trimmed text fields
- corrected inconsistent brand names (e.g., k-beauty → kay beauty)
- cleaned malformed strings like “82e (brand)”

### customers table
- standardized data types and text formatting
- extracted month fields where required
- created age bands using conditional logic (16–20, 21–30, etc.)

### campaigns table
- retained null campaign records since they naturally lack start dates, end dates, or budgets

### returns table
- cleaned rating fields
- created brand rating bands such as low performer, average performer, and excellent

### date table
- built a dedicated date dimension for time intelligence calculations

---

## data modeling
- orders table acts as the central fact table
- all other tables function as dimension tables
- resolved relationship ambiguity between customers and products
  by making one relationship inactive
- used `userelationship()` in dax when required for specific calculations

---

## report structure

### home page
- navigation hub for seamless report movement

### main dashboard
- key kpis and performance visuals
- tooltip-enabled visuals for quick metric insights
- drill-through support for deeper customer and sales analysis

### comparison page
- category-level comparison (makeup vs skincare)
- brand-wise performance analysis
- makeup consistently outperforms skincare

### forecasting page
- 6–8 month forecasts for:
  - sales
  - order volume
  - refund amounts
- includes 85% confidence intervals to represent realistic future ranges

---

## key business insights
- revenue drops correlate strongly with late deliveries
- product ratings remain high, indicating demand is not the issue
- late deliveries increase refund probability and reduce repeat purchases
- logistics performance directly impacts revenue stability
- forecast shows revenue growth potential if delivery performance improves

---

## business takeaway
the product is not the problem.
delivery performance is.

improving logistics offers the fastest and most reliable return on investment.

---

## tools used
- power bi
- power query
- dax
- sql server
