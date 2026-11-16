# Olist E-commerce Sales Intelligence

**Module 1 project:** Python foundations, Pandas, NumPy, data cleaning, feature creation, EDA, and visualization.

## 1. Folder structure

```text
Olist_Ecommerce_Sales_Intelligence/
├── data/
│   ├── raw/                  # Original Kaggle CSVs; do not edit these files
│   └── processed/            # Save cleaned/derived datasets here
├── notebooks/
│   └── 01_project_workbook.ipynb
├── reports/
│   ├── figures/              # Save exported charts here
│   └── findings.md           # Record findings supported by your analysis
├── src/                      # Optional reusable Python functions later
├── requirements.txt
├── .gitignore
└── README.md
```

## 2. Put the folder in your Windows user directory

1. Extract `Olist_Ecommerce_Sales_Intelligence.zip`.
2. Move the extracted folder to:
   `C:\Users\User\Olist_Ecommerce_Sales_Intelligence`
3. Open Anaconda Prompt or terminal and run:

```powershell
cd C:\Users\User\Olist_Ecommerce_Sales_Intelligence
python -m pip install -r requirements.txt
jupyter lab
```

4. In JupyterLab, open `notebooks/01_project_workbook.ipynb`.

If JupyterLab is already installed in your Anaconda environment, you can skip installing it separately. If the `jupyter lab` command is not recognized, activate the environment where JupyterLab is installed or run `python -m jupyter lab`.

## 3. Project goal

Investigate Olist's Brazilian e-commerce data by:
- auditing each table's shape, columns, data types, missing values, and duplicates;
- checking key columns and table grain before joining tables;
- cleaning and transforming data with Pandas;
- creating features such as purchase month, delivery duration, delivery delay, and item-plus-freight value;
- answering business questions with grouped summaries and clear visualizations;
- writing evidence-based findings and recommendations.

## 4. Recommended order

**Do not start by joining every CSV.** First inspect each table independently.

1. Load and inspect `orders`, `order_items`, `products`, and `customers`.
2. Record data-quality issues before changing anything.
3. Parse date columns and handle missing values based on what they mean.
4. Create features and validate their values.
5. Join only the tables needed for a specific question; check row counts and totals before/after every merge.
6. Build visualizations and write findings only after verifying the calculations.
7. Save cleaned data to `data/processed/` and charts to `reports/figures/`.

The geolocation file is comparatively large. Leave it for later unless a location-based question requires it.

## 5. Important data-grain warning

An order can contain multiple item rows and multiple payment rows. Joining these tables directly can multiply rows and inflate revenue/payment totals. Before each merge, write down what one row represents in each table, check key uniqueness, and validate row counts and totals after the merge.

For `item_revenue`, start with `price` at the **order-item row level**. `price + freight_value` is item price plus allocated freight, not necessarily the same as a payment total. State the metric definition in your notebook.

## 6. GitHub and data handling

- Keep the original CSV files unchanged.
- Do not commit large raw datasets to GitHub. The `.gitignore` excludes `data/raw/` and `data/processed/`; if you want to publish your notebook, ensure it can be reproduced using the public Kaggle dataset.
- Never invent findings. Write only results your code actually calculates.
- Add your own observations to `reports/findings.md`.

Dataset source: https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce
