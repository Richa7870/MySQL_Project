# # E-commerce Revenue & Retention Deep Dive

## Overview

A comprehensive analysis of an e-commerce transaction dataset to identify key customer segments, analyze purchasing cohorts, and understand retention patterns. The primary goal is to provide actionable, data-driven recommendations to increase customer lifetime value (LTV) and drive sustainable revenue growth.

## Business Questions

1.  **Customer Value:** Who are our most valuable customers and how much do they contribute to the bottom line?
2.  **Cohort Performance:** How does revenue generation differ based on when a customer first joined?
3.  **Customer Churn:** What are our retention and churn rates, and at what point are we losing customers?


## Data Preparation

**Query:** `0_data_foundation_view.sql`

* Created a consolidated SQL view (`sales_customer_view`) to streamline analysis.
* This view joins transaction and customer tables, calculates key metrics like LTV, and identifies the first purchase date for each customer to establish acquisition cohorts.

---

## Analysis

### 1. Customer Segmentation by Lifetime Value (LTV)

 **Query:** `1_customer_segmentation.sql`

* Categorized all customers into 'High', 'Mid', and 'Low' value tiers based on their total lifetime spending.
* Analyzed the revenue contribution and customer count for each segment.

 **Visualization:**


 **Key Findings:**

* **High-Value (Top 25%):** This elite group of 12,372 customers is the company's engine, driving **66% of all revenue ($135.4M)**.
* **Mid-Value (Middle 50%):** This segment represents the core customer base, generating **32% of revenue ($66.6M)**.
* **Low-Value (Bottom 25%):** This group accounts for only **2% of total revenue ($4.3M)**.

 **Business Insights:**

* **High-Value (66% Revenue):** Implement a 'VIP' loyalty program (e.g., free shipping, early access) to nurture these 12.4k customers. Their high value means churn from this group is extremely costly.
* **Mid-Value (32% Revenue):** Develop targeted 'upsell' campaigns (e.g., 'spend X, get Y') to migrate this group to the high-value tier. This represents a potential **+$68M opportunity**.
* **Low-Value (2% Revenue):** Deploy automated, low-cost re-engagement emails (e.g., price-sensitive offers, 'we miss you' discounts) to increase their purchase frequency.

### 2. Cohort Revenue Analysis

 **Query:** `2_cohort_analysis.sql`

* Grouped customers into annual cohorts based on their first purchase year.
* Tracked the average revenue per customer for each cohort, adjusted for time in the market.
* Analyzed the 3-month rolling average for total revenue and new customers to identify trends.

**Visualization:**



 **Key Findings:**

* **Declining LTV:** Newer cohorts are spending less. Customers from 2016-2018 spent over $2,800 on average, while the 2024 cohort has spent only $1,970 in a comparable timeframe.
* **Recent Downturn:** Both revenue and new customer acquisition peaked in 2022-2023 and are on a significant downward trend in 2024.
* **Market Volatility:** The business is highly volatile, with major revenue drops in 2020 and 2024, indicating poor customer retention during market shifts.

 **Business Insights:**

* **Tackle Recent Churn:** Prioritize the 2022-2024 cohorts for re-engagement, as they are the largest and most at-risk groups.
* **Create Stability:** Introduce subscription-based services or 'subscribe and save' options to build a predictable, recurring revenue stream and smooth out volatility.
* **Learn from Success:** Investigate the marketing and product strategies from 2016-2018 to understand what created such high-value cohorts, and re-apply those lessons.

### 3. Retention & Churn Analysis

 **Query:** `3_retention_analysis.sql`

* Calculated the monthly retention rate for each cohort, showing the percentage of customers who made a repeat purchase in a given month.
* Identified at-risk customers by analyzing their last purchase date.

 **Visualization:**


 **Key Findings:**

* **Systemic Churn:** Retention is consistently low (8-10%) across *all* cohorts, proving this is a long-term, structural business issue, not a recent one.
* **The 2-Year 'Cliff':** Churn accelerates rapidly. The business loses the vast majority of its customers within the first 2-3 years, after which retention stabilizes at a low 10%.
* **No Improvement:** Newer cohorts (2022-2023) are following the *exact same* churn curve as older ones, showing that recent business changes have not improved customer loyalty.

 **Business Insights:**

* **Focus on 'The First Year':** The first 12-24 months are critical. Implement a robust onboarding email series and a 'Year 1' loyalty reward to combat the steep initial drop-off.
* **Win Back High-Value Churn:** Use the list of *churned* customers from the 'High-Value' segment (from Analysis #1) for a targeted, high-effort 'win-back' campaign.
* **Build a Proactive Alert System:** Develop a 'churn risk' flag (e.g., no purchase in 90 days) to trigger automated, proactive retention offers *before* the customer is lost.

---

## Strategic Recommendations

This analysis reveals a classic "leaky bucket" problem: the company is good at acquiring customers, but poor at keeping them. Revenue is declining because new, lower-value customers are not replacing the high-value customers who are churning.

The strategic focus must shift from *acquisition* to *retention*.

1.  **Customer Value Optimization:**
    * **Launch a VIP Loyalty Program** for the top 12.4k customers (66% of revenue) to protect this core income stream.
    * **Create Personalized Upgrade Paths** for the mid-value segment to convert the $66M+ revenue opportunity.
    * **Automate Re-engagement** for the low-value segment with price-sensitive offers.

2.  **Cohort Performance Strategy:**
    * **Implement Recurring Revenue** via subscription models to stabilize volatile revenue.
    * **Re-activate Recent Cohorts (2022-2024)** with targeted offers, as they are the largest at-risk group.
    * **Apply Lessons** from the successful 2016-2018 cohorts to newer customers.

3.  **Retention & Churn Prevention:**
    * **Strengthen Early Engagement** with a robust onboarding program for the critical first 1-2 years.
    * **Focus Win-Back Campaigns** on *high-value* churned customers for the highest ROI.
    * **Implement a Proactive Churn-Risk System** to send intervention offers to at-risk users automatically.

## Technical Details

* **Database:** PostgreSQL
* **Analysis Tools:** SQL (Advanced CTEs, Window Functions), pgAdmin, DBeaver
* **Visualization:** Power BI
