# 🛒 Ecommerce Performance & Retention Analysis

## 🧭 Executive Summary 
<p>
This analysis examines Olist's (Brazilian e-commerce marketplace) data from 2016–2018, focusing on GMV, order volume, cancellations, and repeat buyers to understand core marketplace performance and customer behavior patterns.

Pre-2019 data was selected to establish a clean baseline, free from pandemic-era distortions that emerged after 2020.

</p>

---

### 💼 Business Problem
<p>
Olist marketplace wanted to understand trends in order volumes, cancellations, and repeat buyers over time, as these metrics affect revenue and customer retention. Without this insight, management cannot identify growth opportunities or operational challenges.
  
Key Questions:
<ul>
  <li> Which sellers and product categories drive the most GMV and revenue?</li>
  
  <li> How order volumes and cancellations are trending month-to-month?</li>
  
  <li> How repeat customers behave and which segments are most valuable?</li>
</ul

Answering these questions helps the business identify growth opportunities, reduce operational issues (like cancellations), and improve customer retention.

<b>Core Challenge</b>: How can the marketplace increase revenue, reduce cancellations, and retain more customers?
</p>

---
## ❓ Analysis Questions 
<p>
  
#### GMV:
Which sellers contribute the most to GMV?

Which product categories drive the highest GMV?

How does GMV trend over months? Are there seasonal spikes?

#### Order Volume & Growth

How many orders are placed per month?

How many new vs returning customers are placing orders?

#### Customer Behavior

What is the repeat buyer rate per month?

Which cities or regions have the highest number of active buyers?

Do certain product categories have higher repeat purchases?

#### Operational / Cancellation Metrics

What is the order cancellation rate over time?

Are cancellations clustered by seller? Which seller regions are slower to ship?

Which product categories have the most canceled orders?

#### Delivery / Logistics

What is the average delivery time?

Are certain sellers or cities experiencing delays?


#### Customer Segmentation / Clustering

Can we segment buyers into high-value / mid-value / low-value groups using RFM (Recency, Frequency, Monetary)?

Which segments contribute most to GMV?


</p>

---

## 💻 Git File Structure Explained:

<strong>analysis_notebooks/olist_analysis_with_eda.ipynb</strong> : This code does EDA, generates answers for each analysis question and can also be used to validate the final bi analysis results.

<strong>analysis_notebooks/olist_analysis_for_bi.ipynb</strong> : This code generates combined tables to answer multiple business questions for use in a BI tool.

<strong>final_demo/Olist-Ecommerce-Analysis</strong> : Final demo/business insights showcase made by storing data in Google BigQuery and using Looker to visualize.

<strong>config</strong> : All paths

<strong>data</strong> : Raw and processed data

<strong>etl</strong> : All ETL steps split into clear stages for ease of testing, replacing

<strong>utils</strong> : Common reusable functions

<strong>pipelines</strong> : A central place to define what runs, in which order, and how. They orchestrate the different ETL steps (extract, transform, load) and ensure everything runs smoothly.

---

## 🧠 Skills & Tech Stack

| Layer | Tool | Detail |
|-------|------|--------|
| Dataset | Olist (Kaggle) | 94,383 customers · 3,095 sellers · 71 categories · 2016–2018 |
| Data Store | PostgreSQL | Raw ingestion with FK constraints across 8 relational tables |
| Warehouse | Google BigQuery | Cloud-scale analytical queries |
| Visualization | Looker | 4-tab executive dashboard: GMV · Order Volume · Cancellations · RFM |
| Analysis | Python + SQL | CTEs, window functions, RFM scoring, customer segmentation |

---

## ⚙️ Methodology 

Designed a multi-table analytical model using SQL (joins, CTEs, window functions) and Python to derive core e-commerce metrics. Conducted category, regional, and customer segmentation analysis to identify GTM opportunities and growth signals, and communicated insights via Looker dashboards.

<h3>1. Dataset Used:</h3> 
Olist Dataset - https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce/

<h3>2. Architecture Diagram:</h3>
<img width="863" height="747" alt="Screenshot 2026-01-27 at 12 15 14 PM" src="https://github.com/user-attachments/assets/4f361c8a-4a83-4d78-a5b6-8a27fed42b3a" />

<h3>3. Database (Postgres) showing cardinality relationship</h3>
<img width="1461" height="814" alt="Screenshot 2026-01-29 at 5 14 20 PM" src="https://github.com/user-attachments/assets/65e1e763-07a8-4db0-90fb-7d74d2534433" />

---

## 📈 Results

Looker Report Snapshot:

<img width="1461" height="814" alt="ss" src="https://github.com/devsarahgeo/Ecommerce-Performance-and-Retention-Analysis/blob/main/looker%20results/Screenshot%202026-03-14%20at%204.56.14%E2%80%AFPM.png" />

<img width="1461" height="814" alt="ss" src="https://github.com/devsarahgeo/Ecommerce-Performance-and-Retention-Analysis/blob/main/looker%20results/Screenshot%202026-03-14%20at%204.56.26%E2%80%AFPM.png" />

<img width="1461" height="814" alt="ss" src="https://github.com/devsarahgeo/Ecommerce-Performance-and-Retention-Analysis/blob/main/looker%20results/Screenshot%202026-03-14%20at%204.56.33%E2%80%AFPM.png" />

<img width="1461" height="814" alt="ss" src="https://github.com/devsarahgeo/Ecommerce-Performance-and-Retention-Analysis/blob/main/looker%20results/Screenshot%202026-03-14%20at%204.57.00%E2%80%AFPM.png" />

---

## 📊 Business Insights & Recommendations


<u>**Key Metrics / Highlights**</u>:

| **Metric**                   | **Highlight**                           |
| ---------------------------- | --------------------------------------- |
| **Top Seller GMV**           | 227k                                    |
| **Top Product Category**     | Health & Beauty                         |
| **Highest Repeat Purchases** | Arts & Craftsmanship                    |
| **Peak Sales Months**        | May & August                            |
| **Highest Cancellations**    | Sports Leisure product category         |
| **Top Cities**               | Sao Paulo & Rio de Janeiro              |


**Business Insights, Impact & Recommendations**:

> Analyzed 94,383 customers across 3,095 sellers and 71 product 
> categories (2016–2018).
> <br>
> Core finding: with only a 6.7% repeat rate, 
> acquisition drives growth but retention is the untapped lever. The 
> At Risk segment alone holds 20% of customers and significant GMV recovery 
> potential.

| # | Finding | Business Impact | Recommendation |
|---|---------|----------------|----------------|
| 1 | New customers drive 30.84% of GMV; repeat rate is only 6.7% (6,342 of 94,383 customers) | Acquisition is the #1 growth lever today, but low retention signals long-term revenue risk | Invest in paid acquisition while building post-purchase loyalty flows to improve repeat rate |
| 2 | Repeat activity peaks sharply in October then collapses with near-zero repeat rate from Jan–Jul | Retention window is narrow; missing October = missing the only natural re-engagement moment | 93% of customers never return after their first purchase. With repeat activity naturally spiking in October, launch re-engagement campaigns targeting one-time buyers in September. Converting even a fraction into repeat buyers during this window would meaningfully improve the 6.7% repeat rate. |
| 3 | São Paulo (15.5K) and Rio (6.9K) dominate; other cities drop to 2.8K (Belo Horizonte) | Geographic concentration = high-value but high-risk dependency | Deepen seller density and logistics SLAs in top cities; run targeted acquisition in Belo Horizonte, Brasília, Curitiba |
| 4 | At Risk segment = 20.21% of customers but only 8.03% of GMV; Champions = 3.53% of customers, 2.89% GMV | At Risk customers are churning before reaching full value - early intervention is high ROI | Urgent re-engagement campaigns for At Risk; loyalty rewards for Champions; personalized cross-sell for Potential Loyalists |
| 5 | GMV peaks at $1.5M in May and orders peak at 12.3K in August; September drops to $607.5K | 2.5x swing between peak and trough - predictable pattern enables proactive planning |Front-load marketing ahead of peak months(May and August). Tailoring strategy - 1) in GMV-driven peaks (May) - maximize AOV by promoting premium/high-priced products or offering bundles ("Buy 2, save more") 2) in order-driven peaks (August): Run Discount / flash sales campaigns, limited-time offers / deals campaigns, also ensure inventory + volume readiness |
| 6 | Cancellation rate improved from 7.9% (2016) -> 0.62% (2018); Sports Leisure has highest cancelled orders (47) | Strong operational improvement over time; Sports Leisure remains an outlier dragging satisfaction | Audit Sports Leisure sellers by ship time; enforce SLA thresholds; avg delivery of 12.47 days needs category-level benchmarking |

---

## ⚡ Future Scope - Scalable Implementation 
*(If the project needs to handle additional data or extended time periods in the future)*

<ul>
<li> <b>Data Validation</b>: Implement CI/CD pipelines to automatically check schema consistency, null values, and aggregation sanity.</li>

<li> <b>Cloud Data Warehouse</b>: Store both raw and BI-ready tables directly in BigQuery or Snowflake, bypassing local Postgres to ensure scalability and performance.</li>

</ul>




