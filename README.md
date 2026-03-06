# Retail Data Pipeline

This project demonstrates a **full ETL pipeline** for Walmart retail sales data. The pipeline extracts data from multiple sources, cleans and transforms it, performs aggregation, and saves the results.

## Project Overview

The pipeline performs the following steps:

1. **Extract**  
   Extract retail sales data from PostgreSQL and complementary data from a Parquet file, then merge the datasets into a single DataFrame.

2. **Transform**  

   * Fill missing numerical values for CPI and Unemployment using forward/backward fill
   * Create a `Month` column from the `Date` column
   * Filter out weekly sales below $10,000

3. **Aggregation**  
   Calculate the **average weekly sales per month**.

4. **Load**  
   Persist the cleaned dataset and aggregated dataset as CSV files.

5. **Validate**  
   Check that the output CSV files were successfully created.

## Project Structure

```
retail-data-pipeline/
│
├── etl_retail_pipeline.ipynb
├── extra_data.parquet
├── clean_data.csv
├── agg_data.csv
├── README.md
```

## How to Run

1. Install required packages:

```bash
pip install pandas pyarrow psycopg2
```

2. Open the notebook:

```
etl_retail_pipeline.ipynb
```

3. Run all cells to execute the pipeline.

4. The pipeline will generate:

* `clean_data.csv`
* `agg_data.csv`

5. The `validation()` function confirms that the files were created.

## Notes

* Missing CPI and Unemployment values are filled using forward/backward fill.
* Weekly sales below $10,000 are removed.
* The original `Date` column is dropped after creating the `Month` column.
* Aggregated results are rounded to two decimals and the column is renamed `Avg_Sales`.

## Author

Sarah Kichou — Data Engineer
