# PLP Data Analytics Assignment 3: Duka Sales and Agent Cleanup

## Engagements
1. **Duka Electronics:** explores 1,000 orders from January–June 2026, derives revenue/time/price-band fields, compares branches/products/weekend performance/months, and filters Premium online orders in Nairobi and Mombasa.
2. **Mobile-money agent network:** audits and cleans a 600-transaction extract, removes duplicate transaction IDs, standardises transaction types and dates, imputes missing amounts, flags outliers, preserves unknown-agent transactions through a left join, and produces county/weekly summaries.

## Regenerate the data
From the repository root, run:
```bash
python generate_data.py
```
This creates `duka_sales.csv`, `agents.csv`, and `agent_transactions.csv` in the repository root. These are generated inputs and should not be committed.

## Run the notebooks
Install dependencies:
```bash
pip install -r requirements.txt
```
Then open Jupyter and run `duka_sales_exploration.ipynb` and `agent_cleanup.ipynb` from top to bottom. The notebooks read the generated CSV files from the repository root. The cleaning notebook imports `clean_agent_data` from `cleaning_pipeline.py`.

## Duka Executive Summary
Duka Electronics recorded **1,000 orders** and generated **KES 71,792,500.00** in revenue during the six-month review period.
**Nairobi** led the five branches with **KES 26,106,100.00**, while **Eldoret** recorded the lowest branch revenue.
**Laptop** was the top product by revenue at **KES 41,535,000.00**, whereas **Tablet** led unit sales with **691 units**.
The best month was **2026-04** at **KES 13,518,300.00**, compared with **2026-06** at **KES 10,903,400.00**.
There were **83 Premium online orders** from Nairobi and Mombasa, contributing **KES 10,218,000.00**.

## Agent row counts
- Generated transaction extract: **612 rows** (600 original records plus 12 appended duplicate records).
- After duplicate removal and cleaning: **600 rows**.
- Duplicate transaction records removed: **12**.
- Unknown-agent transactions retained after the left merge: **7**.

## Repository contents
- `generate_data.py` – both original deterministic data generators.
- `duka_sales_exploration.ipynb` – sales exploration and business interpretation.
- `excel/duka_branch_summary.xlsx` – SUMIFS/XLOOKUP worksheet and branch/channel revenue summary.
- `outputs/premium_online_coast_capital.csv` – filtered Premium online orders.
- `cleaning_pipeline.py` – reusable cleaning function and log.
- `agent_cleanup.ipynb` – data-quality audit, cleaning validation, summaries and report.
- `outputs/agent_transactions_clean.csv` – cleaned transaction data.

## Privacy and governance
If customer phone numbers were added to the extract, they would be personal data under the Kenya Data Protection Act, 2019 because they can identify or make a customer identifiable. The provider should document a lawful basis and specified purpose, collect only necessary fields, restrict access by role, encrypt data in transit and at rest, mask or tokenize phone numbers in analytical outputs, set retention limits, maintain access logs, and follow applicable data-subject rights and breach-notification obligations. Raw identifiers should not be included in public repositories or shared notebooks.
