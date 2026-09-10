# Exploratory Data Analysis (EDA) for Online Store

This project focuses on performing an Exploratory Data Analysis (EDA) for an online store using Python and Jupyter Notebook in Google Colab. The goal of the analysis is to clean the dataset, uncover hidden patterns, analyze sales performance across products and regions, and extract valuable business insights.

---

## Dataset Structure

The project utilizes three primary datasets:
1. **`products.csv`** — Information about products (assortment, item types, etc.).
2. **`events.csv`** — Order logs (order and ship dates, priorities, sales channels, units sold, unit prices, and unit costs).
3. **`countries.csv`** — Country reference table (regions, sub-regions, and country codes).

---

## Key Steps & Analysis Workflow

1. **Environment Setup & Data Loading:**
   * Mounting Google Drive to load datasets directly within Google Colab.
   * Importing essential Data Science libraries (`Pandas`, `NumPy`, `Matplotlib`, `Seaborn`, `Plotly`).

2. **Data Cleaning & Preprocessing:**
   * Handling specific country code adjustments (e.g., Namibia and Antarctica formatting).
   * Identifying and dropping missing values and duplicate rows.
   * Converting order and shipping date strings into proper `datetime` objects.
   * Standardizing text data (string stripping and upper casing).
   * Validating logical constraints (e.g., ensuring `Unit Price` is never lower than `Unit Cost`).

3. **Data Merging & Feature Engineering:**
   * Merging datasets using `Product ID` and `Country Code`.
   * Calculating core business metrics: unit profit (`Profit`), total order profit (`Profit From Order`), total income, and total costs.

4. **Exploratory Data Analysis (EDA) & Visualization:**
   * **General Metrics:** Computing total orders, total profit, unique countries count, and the ratio between online and offline sales channels.
   * **Product Performance:** Generating multi-panel subplots analyzing income, cost, profit, and popularity by product type.
   * **Logistics & Delivery Analysis:** Analyzing average delivery times (`Delivery Days`) grouped by product type, country, and region.
   * **Interactive Choropleth Maps:** Building global geographic visualizations using `Plotly` to display price, cost, profit, and popularity distribution across countries.

---

## Technologies & Libraries

* **Python**
* **Google Colab / Jupyter Notebook**
* **Pandas & NumPy** — Data manipulation and analysis.
* **Matplotlib & Seaborn** — Static data visualization.
* **Plotly** — Interactive mapping and plotting.

---

## How to Run the Project

1. Open or download the Jupyter Notebook file `Exploratory_data_analysis_for_online_store.ipynb`.
2. Upload `products.csv`, `events.csv`, and `countries.csv` to your Google Drive directory (by default, the notebook looks in `/content/drive/MyDrive/mate`).
3. Open the notebook in Google Colab and run all cells sequentially.

---

##  Author
* **kalina-tech** — [GitHub Profile](https://github.com/kalina-tech)
