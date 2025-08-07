# Acquiring-and-Processing-Information-on-the-World-s-Largest-Banks

This project implements a simple yet robust **ETL (Extract, Transform, Load)** pipeline using **Python**, **Pandas**, **SQLite**, and **Web Scraping** to process real-time financial data on the world’s largest banks.

## 📌 Project Overview

The goal of this project is to:
- Extract the latest list of the world’s largest banks by market capitalization from a live Wikipedia page.
- Transform the data into a clean, structured format and convert the market cap into various currencies (USD, GBP, EUR, INR).
- Load the cleaned data into both a `.csv` file and a SQLite database for further analysis or reporting.

## 🛠️ Technologies Used

- **Python**
- **Pandas** – for data manipulation and transformation
- **Requests** – for HTTP requests
- **BeautifulSoup** – for web scraping
- **SQLite + SQLAlchemy** – for database storage
- **Logging** – for progress tracking
- **Currency Exchange CSV files** – for conversion rates

## 📈 ETL Pipeline Breakdown

### ✅ 1. Extract
- Scrapes the table of largest banks by market cap from this [Wikipedia page](https://en.wikipedia.org/wiki/List_of_largest_banks).
- Parses the HTML and converts it into a Pandas DataFrame.

### 🧹 2. Transform
- Cleans the table by:
  - Removing unnecessary columns and footnotes.
  - Converting market capitalization to numerical format.
- Reads exchange rates from local CSV files for USD, GBP, EUR, and INR.
- Applies currency conversion using `market_cap_usd * exchange_rate`.

### 💾 3. Load
- Saves the final transformed DataFrame into:
  - A `banks_data.csv` file.
  - A normalized **SQLite** database (`banks.db`) using SQLAlchemy.

## 🧪 Sample Output

| Bank Name          | Country    | Market Cap (USD) | Market Cap (EUR) | Market Cap (INR) |
|--------------------|------------|------------------|------------------|------------------|
| JPMorgan Chase     | USA        | 390.3B           | 358.2B           | 32.5T            |
| ICBC               | China      | 312.0B           | 286.2B           | 26.0T            |
| HDFC Bank          | India      | 150.6B           | 138.0B           | 12.5T            |

---

## 📂 File Structure
-project/
-│
-├── etl_pipeline.py # Main script to run the ETL process
-├── exchange_rates/
-│ ├── usd.csv # USD exchange rates
-│ ├── eur.csv # EUR exchange rates
-│ └── inr.csv # INR exchange rates
-├── banks_data.csv # Output CSV
-├── banks.db # Output SQLite DB
-├── requirements.txt # Python dependencies
-└── README.md # Project documentation

