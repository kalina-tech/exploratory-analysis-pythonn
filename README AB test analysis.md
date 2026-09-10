# A/B Testing & Conversion Analysis

A Python and SQL portfolio project that extracts multi-variant A/B testing data from **Google BigQuery**, performs automated statistical significance testing (Z-test for proportions), and structures performance metrics for a Tableau dashboard[cite: 3].

## Interactive Dashboard

An interactive Tableau Public dashboard has been built to visualize the test variants and conversion metrics:
👉 [View A/B Test Dashboard on Tableau Public](https://public.tableau.com/app/profile/illia.kalinchuk/viz/ABtest_17890290636060/Dashboard1?publish=yes)[cite: 3]

## What it does

The script evaluates multiple concurrent A/B tests by automating key conversion funnel stages (`add_payment_info`, `add_shipping_info`, `begin_checkout`, and `new account`) relative to total session volume[cite: 3]. 

The analytical workflow incorporates:
* **BigQuery Extraction**: Aggregates daily session telemetry, country data, device dimensions, channel splits, test variants (`test`), and test groups (`test_group`) into a unified long-format event dataset[cite: 3].
* **Data Aggregation**: Pulls baseline session metrics, order conversions, account creation events, and granular funnel step counts per variant[cite: 3].
* **Statistical Testing**: Calculates conversion rates for control (Group 1) vs. test (Group 2) variations and executes a two-proportion Z-test (`statsmodels.api.stats.proportions_ztest`) for each metric[cite: 3].
* **Significance Check**: Flags statistically significant outcomes based on an alpha threshold (`p_value < 0.05`) and computes relative percentage metric changes[cite: 3].

The final output is saved locally as `ab_test_results.csv` (semi-colon separated with UTF-8 encoding) ready for direct reporting and dashboard integration[cite: 3].

## Tables used

* `DA.ab_test` — Assignment records mapping sessions to specific tests and test groups[cite: 3].
* `DA.session` — Core session identifiers and timestamps[cite: 3].
* `DA.session_params` — Session-level metadata (country, device type, continent, traffic channel)[cite: 3].
* `DA.order` — Transaction records linking sessions to purchase events[cite: 3].
* `DA.event_params` — Detailed event tracking containing custom funnel actions (`event_name`)[cite: 3].
* `DA.account_session` — User account association table tracking new user registrations[cite: 3].

## Output columns / Metrics (`ab_test_results.csv`)

* `test_number` — Unique identifier for the specific A/B test variant cycle (e.g., Test 1, 2, 3, 4)[cite: 3]
* `metric` — Shorthand label for the funnel conversion step (`add_payment`, `add_shipping`, `begin_checkout`, `new_accounts`)[cite: 3]
* `numerator_event` — Core event name from the tracking logs (`add_payment_info`, `add_shipping_info`, etc.)[cite: 3]
* `denominator_event` — Baseline scaling event (standardized to `session`)[cite: 3]
* `conversion_rate_test` / `conversion_rate_control` — Proportion of successful tracking events per session for Test (Group 2) vs. Control (Group 1)[cite: 3]
* `metric_change` — Relative percentage lift or drop of the test group compared to control (`(Conv_Test - Conv_Control) / Conv_Control * 100`)[cite: 3]
* `z_stat` / `p_value` — Output results from the two-proportion Z-test evaluating statistical deviation[cite: 3]
* `significant` — Boolean flag (`TRUE` / `FALSE`) confirming if the variance passes the significance threshold at alpha = 0.05[cite: 3]

## Notes / assumptions

* Designed to run in **Google Colab** with standard BigQuery client initialization against the `data-analytics-mate.DA` database[cite: 3].
* Processes data dynamically using `UNION ALL` structures to group different types of user behavior into a unified structure (`value` column mapped to specific `event_name` attributes)[cite: 3].
* Statistical evaluation assumes independent random sampling per session identifier across control and variant buckets[cite: 3].

## How to use

Run the blocks sequentially inside the Google Colab notebook (`AB_test_project.ipynb`)[cite: 3]. Ensure your Google Cloud account is authenticated (`google.colab.auth`) and has access to query the project datasets[cite: 3].
