# ACC102_Data_Analysis
Project Title: Financial-Data-Analysis product

Problem and Users: When querying the financial information of listed companies, many people have to go through a large number of financial reports, which is extremely inconvenient and time-consuming. This product extracts standardized financial data from the Compustat database of WRDS by stock ticker and year range, and calculates key financial ratios with one click for users (only applicable to North American listed companies). Its main user groups include students and researchers majoring in finance at universities, financial industry analysts, and corporate strategic analysts.

Dataset: https://wrds-www.wharton.upenn.edu/ (Accessed at: 2026.4.18)

WRDS is a world-leading and authoritative integrated data analysis platform for business, finance, and economics, launched in 1993 by the Wharton School of the University of Pennsylvania.

Methods (main Python steps):

1. Import the packages we will use in Jupyter Notebook. Import the official WRDS Python package, import the Pandas library, and import the NumPy library.
2. Create the WRDS Connection.
3. Define the parameters we want to change easily later. Simply modify the target_companies list to add or replace the target stock tickers. Adjust start_year and end_year to cover the desired time range.
4. Extract data from WRDS Compustat by using SQL query. Extract financial indicators for specified companies and years from comp.funda (Compustat Annual Financial Database) on WRDS. Rename fields using the AS keyword to improve readability. f-string (f""" """): A Python string formatting syntax used for dynamically concatenating SQL statements. db.raw_sql(query) is the core method of the WRDS connection package, used to execute SQL queries and return a structured DataFrame.
5. Calculate the financial ratios. df['Column Name'] = df['Column A'] / df['Column B']: Uses Pandas vectorized operations to calculate financial ratios in batches. df.dropna(subset=[List of Column Names]): Drops rows containing missing values in the specified columns to ensure the integrity of financial ratio calculation results. display(result_df): A built-in function of Jupyter Notebook that displays the DataFrame contents in a tabular format.
6. Save as Excel. df.to_excel(file_name, index=False): An export method in Pandas that saves a DataFrame as an Excel file. index=False means not saving the row index. db.close(): Closes the WRDS database connection and releases resources.

Key Findings: This product uses three U.S. semiconductor companies as examples. NVIDIA achieved explosive growth driven by its AI chip business. Its net profit margin rose from 25.98% in 2020 to 55.85% in 2024, ROE reached 91.87%, and EBITDA surged by more than 13 times. AMD’s profitability fluctuated with industry cycles: its net profit margin was only 3.77% in 2023 and rebounded slightly in 2024. Micron, with a strong focus on memory chips, suffered a loss with a net profit margin of 37.53% in 2023 but returned to profitability in 2024. The AI chip sector (NVIDIA) outperformed the semiconductor cycle, while the memory chip sector (AMD / Micron) was significantly affected by economic cycles, resulting in much higher earnings volatility.

How to Run: After running the code, enter your WRDS username and password, then type "y" in the next field. The result chart will be generated subsequently.

Limitations and Next Steps: First, the data dimension is limited: only annual financial data are covered, while cash flow, R&D investment, and other indicators are excluded, resulting in insufficient analytical depth. Second, the sample size is small: three companies cannot represent the entire semiconductor industry, leading to weak universality of the conclusions. Third, the scope of application is narrow: only North American listed companies are included.

To address these issues, the product can be improved by:

•	Expanding data dimensions, supplementing data on cash flow, stock prices, industry indices, and adding DuPont analysis to decompose profit drivers;

•	Extending the sample scope from North America to global listed companies;

•	Enhancing data visualization by plotting indicator trend charts to improve the readability of results.

Looking forward to your usage!
