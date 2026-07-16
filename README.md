# Sales Data Analysis

An end-to-end exploratory data analysis of a retail sales dataset — uncovering trends in
**when**, **where**, and **what** customers buy, and which products are most often
purchased together.

## Objectives

- Identify the best-performing months, days, and hours for sales
- Find which city generates the most orders
- Determine the best-selling and highest-revenue products
- Discover which products are frequently bought together (market basket analysis)
- Segment products by revenue contribution using ABC / Pareto analysis

## Dataset

The dataset (`data/sales_data.ftr`) contains individual order line items, with the
following fields:

| Column             | Description                              |
|---------------------|-------------------------------------------|
| Order ID            | Unique identifier for the order           |
| Product             | Product name                              |
| Quantity Ordered    | Units of the product purchased            |
| Price Each          | Unit price at time of purchase            |
| Order Date          | Date and time the order was placed        |
| Purchase Address     | Delivery address (used to derive city)    |

> Add a note here on where the dataset came from (e.g. Kaggle link) and its license.

## Technologies Used

- Python 3.13
- pandas — data cleaning and aggregation
- matplotlib — visualizations
- networkx — product co-purchase network graph
- mlxtend — association rule mining (Apriori algorithm)
- pyarrow — reading the `.ftr` (Feather) data file

## Project Structure

```
retail-sales-market-basket-analysis/
├── data/
│   └── sales_data.ftr        # raw dataset
├── Sales_Analysis.ipynb  # main analysis notebook
│   
├── README.md
├── requirements.txt
└── .gitignore
```

## Installation

```bash
git clone https://github.com/<your-username>/sales-data-analysis.git
cd sales-data-analysis
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate
pip install -r requirements.txt
```

## Requirements

See [`requirements.txt`](requirements.txt) for the full list of dependencies.

## How to Run

```bash
jupyter notebook notebook/Sales_Analysis.ipynb
```
Run all cells from top to bottom.

## Analysis Workflow

1. **Data Loading & Inspection** — load the raw Feather file, check for missing values
2. **Data Cleaning** — drop empty/duplicate rows and stray header rows
3. **Feature Engineering** — derive `Month`, `City`, `Sales`, `Hour`, and `Day` columns
4. **Exploratory Data Analysis** — sales by month, city, product, and time of day
5. **Market Basket Analysis** — products frequently bought together, using co-purchase
   networks and association rule mining (Apriori)
6. **Revenue Analysis (ABC / Pareto)** — classify products into revenue tiers

## Key Findings

- Sales show clear seasonality, peaking in specific months
- A small number of cities account for a disproportionate share of orders
- Lower-priced products sell in much higher volumes than premium products
- Orders cluster around specific hours of the day
- Phones are frequently purchased together with their matching charging cable — a clear
  cross-sell opportunity (Lift ≈ 2.1–2.2)
- A small set of "A" tier products drives the majority of total revenue


## Future Improvements

- Add year-over-year comparison once multiple years of data are available
- Build a sales forecasting model (e.g. Prophet or ARIMA) on the monthly trend
- Turn the ABC/Pareto and market-basket outputs into an interactive dashboard
- Add automated data-quality checks (e.g. with `pandera`)
- Parameterize the notebook (e.g. with `papermill`) to re-run it on new data drops

