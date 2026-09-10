# E-Commerce Sales & User Behavior Analysis

A Python-based portfolio project that connects to Google BigQuery, extracts comprehensive e-commerce telemetry, and performs **exploratory data analysis (EDA)** on global sales, product performance, traffic sources, and user account behavior[cite: 2].

---

## Interactive Dashboard

An interactive Tableau Public dashboard has been built to visualize the key geographic and sales insights:
👉 **[View E-Commerce Sales & Geography Overview Dashboard](https://public.tableau.com/app/profile/illia.kalinchuk/viz/E-CommerceAnalysis_17890397605820/Salesandgeographyoverview?publish=yes)**[cite: 2]

---

## What it does

The notebook answers: *"Which global markets and traffic channels drive the highest revenue, what are our top-selling product categories, and how do subscription and email verification statuses impact user engagement and sales?"*[cite: 2]

It's structured across several key analytical steps[cite: 2]:

| Step | Purpose |
|---|---|
| *BigQuery Extraction* | Authenticates and executes a multi-table SQL query joining session logs, account records, and order/product details from the `DA` dataset[cite: 2]. |
| *Data Export* | Automatically saves and exports the retrieved dataset locally and to Google Drive as `session_product_dataset.csv`[cite: 2]. |
| *Data Health & EDA* | Inspects missing values, checks data types, identifies time periods, and calculates top-performing continents and countries by revenue and session volume[cite: 2]. |
| *Behavioral & Traffic Analysis* | Evaluates email confirmation rates, unsubscription metrics, spending patterns of subscribed vs. unsubscribed users, and revenue shares across traffic sources[cite: 2]. |

The notebook outputs clean structural diagnostics alongside clear visual charts (bar plots, pie charts, and trend lines) detailing the store's performance[cite: 2].

---

## Tables used

* `DA.session` — Core session records including dates and unique session IDs[cite: 2]
* `DA.session_params` — Session-level dimensions including continent, country, device, browser, traffic source, and medium[cite: 2]
* `DA.account` — User account details including verification and unsubscription flags[cite: 2]
* `DA.account_session` — Bridge table mapping accounts to user sessions[cite: 2]
* `DA.order` — Transaction orders linking sessions to specific items purchased[cite: 2]
* `DA.product` — Product catalog data including categories, item names, and pricing[cite: 2]

---

## Output metrics & dimensions

| Dimension / Metric | Description |
|---|---|
| *`continent` & `country`* | Geographic breakdowns identifying top-performing regional markets by sales and session volume[cite: 2] |
| *`product_category`* | Inventory categories (e.g., Sofas & armchairs, Chairs, Beds) ranked by total sales revenue[cite: 2] |
| *`device` & `device_model`* | Technical breakdown analyzing revenue distribution across desktop, mobile, and tablet platforms[cite: 2] |
| *`traffic_source`* | Attribution metrics evaluating organic, direct, and referral traffic performance[cite: 2] |
| *`is_email_confirmed`* | User account metric showing that ~71.7% of registered users successfully verify their email[cite: 2] |
| *`is_unsubscribed`* | Subscription metric tracking that ~16.9% of registered users opt out of marketing emails[cite: 2] |

---

## Notes / assumptions

* Designed for **Google Colab** and requires Google Cloud authentication (`google.colab.auth`) to access BigQuery project `my-portfolio-project-507918`[cite: 2].
* The dataset captures a specific time window from **November 1, 2020, to January 31, 2021** (totaling over 349,000 unique sessions)[cite: 2].
* Handles unauthenticated guest sessions (where account and product details evaluate to null due to left joins) by isolating registered user subsets for account-level behavioral analysis[cite: 2].

---

## How to use

Run the cells sequentially in Google Colab (`E_Commerce_Analysis (1).ipynb`)[cite: 2]. Ensure your GCP credentials have permissions to query the `data-analytics-mate.DA` schema[cite: 2].
