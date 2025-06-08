# 📈 Airflow Stock Data ETL Pipeline

This project demonstrates an end-to-end ETL pipeline using **Apache Airflow** to automate the extraction of daily stock prices from the [Alpha Vantage API](https://www.alphavantage.co/), transform the data, and load it into **Snowflake** for further analysis or warehousing.

---

## 🧰 Technologies Used

- Apache Airflow (ETL orchestration)
- Snowflake (Cloud Data Warehouse)
- Python
- Alpha Vantage API
- SQL Transactions

---

## 🚀 Project Architecture

       +---------------------------+
       |   Airflow DAG Scheduler   |
       +-------------+-------------+
                     |
    +----------------v------------------+
    |  Extract Daily Stock Prices (API) |
    +----------------+------------------+
                     |
     +---------------v------------------+
     |     Transform JSON to Table      |
     +---------------+------------------+
                     |
     +---------------v------------------+
     |   Load Data to Snowflake Table   |
     +----------------------------------+

---

## ⚙️ Setup Instructions

### Prerequisites

- Python 3.x
- Apache Airflow installed and configured
- Snowflake account
- Alpha Vantage API Key

---

### Installation

Clone the repository and install dependencies:

```bash
git clone https://github.com/Nak1106/airflow-stock-etl-pipeline.git
cd airflow-stock-etl-pipeline
pip install -r requirements.txt
Airflow Configuration
Set the following Airflow Variables using the UI or CLI:

alpha_vantage_api_key — Your API key from Alpha Vantage

snowflake_userid — Your Snowflake username

snowflake_password — Your Snowflake password

snowflake_account — Your Snowflake account identifier

Create an Airflow Connection named snowflake_conn using the Snowflake connection type.

How It Works
The DAG stock_data_pipeline performs the following steps daily at 2 AM:

Extract
Fetches stock data for symbol IBM using the Alpha Vantage API.

Transform
Parses and cleans the JSON API response into a list of structured records.

Load
Loads the records into the dev.raw.stock_price table in Snowflake, replacing existing data each run.

