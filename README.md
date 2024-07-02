# Bitcoin Historical Data (Jan, 2012 - March, 2021) Analysis
![](images/bitcoin1.jpg)
<br />

## Table of Contents
- [Project Overview](#project-overview)
- [Tools Used](#tools-used)
- [Dataset Overview](#dataset-overview)
- [Bitcoin Historical Data EDA In Python](#bitcoin-historical-data-eda-in-python)
- [View Power BI Dashboard Report](#view-power-bi-dashboard-report)
<br />

## Project Overview
### Introduction:

Bitcoin, the pioneering cryptocurrency, has garnered significant attention and investment over the past decade. Understanding its historical price movements and trading volumes is crucial for investors, traders, and researchers alike. This data analysis project aims to explore Bitcoin's historical data spanning from 2012 to 2021, uncovering trends, patterns, and insights that can inform investment decisions and provide valuable market insights.
  
### Problem Statement
- What was the trading volume of Bitcoin between 2012 - 2021?
- What was the transaction value within this period?
- What was the average transaction value within this period?
- What was the total weighted price of Bitcoin within this period?
- What was the minimum open price and maximum close price within this period?
- Explain all these with charts showing their trends over the years.
- Any other relevant data driven insights from the analysis

### Objectives:

- __Analyze Bitcoin Trading Volume:__ Investigate the trading volume of Bitcoin from 2012 to 2021 to understand the level of market activity and liquidity over time.

- __Evaluate Transaction Value:__ Determine the total transaction value of Bitcoin within the specified period to assess the monetary value of transactions conducted on the Bitcoin network.

- __Calculate Average Transaction Value:__ Calculate the average transaction value of Bitcoin transactions over the period under consideration, providing insights into the typical size of transactions.

- __Assess Total Weighted Price:__ Determine the total weighted price of Bitcoin within the period to understand the overall price trend and market valuation of Bitcoin.

- __Identify Price Extremes:__ Identify the minimum open price and maximum close price of Bitcoin within the period to highlight the range of price fluctuations and extremes observed in the market.

- __Visualize Trends with Charts:__ Present trends and patterns in Bitcoin trading volume, transaction value, average transaction value, weighted price, minimum open price, and maximum close price, open, low, high and close price over the years, using visualizations such as line charts.

- __Provide Data-Driven Insights:__ Extract additional insights from the analysis beyond the specified questions, uncovering any notable trends, anomalies, or correlations observed in the data that may inform decision-making or provide deeper understanding of Bitcoin market dynamics.
<br />
<br />

### Skills Utilized
1. Data Cleaning
2. Data Visualiziation
3. Descriptive Analytics
4. Critical Thinking and Problem Solving
5. Communication and Reporting
<br />

### Tools Used
1. Python (Was used for Data Cleaning, profilling and Exploratory Data Analysis)
   - The following Python Features were incorporated:
      1. Jupiter Notebook
      2. Numpy
      3. pandas
      4. Visualization
          - Matplotlib
          - Seaborn
          - Plotly
      5. Integration With Other tools
  
3. Power BI (Was used to create reports and dashboard for this analysis)
   - The following Power BI Features were incorporated:
      1. Bookmarking
      2. DAX
      3. Quick Measures
      4. Modelling
      5. Filters
      6. Tooltips
<br />
<br />

### Methodology (Python):

- __Data Collection:__ Gather Bitcoin historical data covering the period from 2012 to 2021, ensuring data integrity and accuracy.
  
- __Data Preprocessing:__
    1. Remove data rows with null values or has "NaN" because we have 1243608 rows of data with only Timestamp column data and without the rest of the column data.
    2. Create a datetime column from the Timestamp column and name it "Date"
    3. Create a "Year" column from the "Date" column
    4. Remove the "Timestamp" column
    5. Re-arrange the columns     

- __Exploratory Data Analysis (EDA):__ Conduct EDA to gain insights into Bitcoin price dynamics, trading volume patterns, and overall market behavior. Visualize trends using line charts, and other charts.
<br />

### Statistical Analysis:

- Calculate descriptive statistics, including mean, median, standard deviation, and correlation coefficients, to quantify Bitcoin's price movements and trading activity.
<br />

### Volatility Analysis:

- Measure Bitcoin's volatility using standard deviation, historical volatility, or other volatility metrics. Explore the implications of volatility on risk management and investment strategies.
<br />
<br />

### Dataset Overview
The primary dataset used in this analysis was provided by [Quantum Analytics](https://www.quantumanalyticsco.org/). Ii could not upload it to github because of the size. It has 4857377 rows of data and has a size of almost 300 megabyte. You can also download this dataset [here](https://www.kaggle.com/datasets/mczielinski/bitcoin-historical-data). It is made up of CSV files for select bitcoin exchanges for the time period of Jan 2012 to December March 2021, with a minute to minute updates of OHLC (Open, High, Low, Close), Volume in BTC and indicated currency, and weighted bitcoin price. Timestamps are in Unix time. Timestamps without any trades or activity have their data fields filled with NaNs. If a timestamp is missing, or if there are jumps, this may be because the exchange (or its API) was down, the exchange (or its API) did not exist, or some other unforeseen technical error in data reporting or gathering. All effort has been made to deduplicate entries and verify the contents are correct and complete to the best of my ability, but obviously trust at your own risk. It is worth noting that there are 4857377 rows and 8 columns present in the Bitcoin Historical data.

The dataset contains 1 sheet/table and the columns includes:

- __Timestamp:__ This column represents the timestamp or time at which the data point was recorded. It is a reference to a specific moment in time, often in Unix timestamp format (measured in seconds since January 1, 1970).

- __Open:__ The opening price of the financial instrument (e.g., a cryptocurrency) during the specified time period. It is the price at which the first trade occurred.

- __High:__ The highest price reached during the specified time period.

- __Low:__ The lowest price reached during the specified time period.

- __Close:__ The closing price of the financial instrument at the end of the specified time period. It is the price at which the last trade occurred.

- __Volume (BTC):__ The total trading volume of the financial instrument in terms of the base currency (e.g., Bitcoin) during the specified time period. It represents the total quantity of the financial instrument traded.

- __Volume (Currency):__ The total trading volume of the financial instrument in terms of the quote currency (e.g., US dollars) during the specified time period. It represents the total value of the trades.

- __Weighted Price:__ The volume-weighted average price (VWAP) or the average price of the financial instrument during the specified time period, considering the trading volume. It provides a more comprehensive view of the average transaction price.
<br />

## Bitcoin Historical Data EDA In Python:

__Trading Volume By Year__                | __Transactrion Value By Year__        
:----------------------------------------:|:--------------------------------:|
 ![](images/Trading_Volume_By_Year.png)   |![](images/Transaction_Value_By_Year.png)


 __Weighted Price By Year__                           |__Total Open, Low, High, Close Price By Year__ 
:----------------------------------------------------:|:----------------------------------------:|
![](images/Weighted_Price_Value_By_Year.png)          |![](images/Open_Low_High_Close_Prices_By_Year.png)  

 To view the complete Exploratory Data Analysis (EDA) of this project in python Jupiter Notebook, please click [here](BITCOIN_HISTORICAL_DATA.ipynb)
<br />
<br />
 
## Data Analysis and Visuals in Power BI:
![](images/Bitcoin_Historical_Dashboard.png)

1. From the dashboard, it was observed that the total Trading Volume between 2012 and 2021 is __34M BTC__.
2. The Total Transaction Value within this period is 151bn, the Average Transaction Value is __644.5__.
3. Total Weighted Price within this period is 22bn, the Minimum Open Price is 3.80, while the maximum is __61.78k__.
4. The Trading Volume by Year experienced its peak period in 2015 capping at 5.53M BTC, while the year with the least volume traded was __567,948 BTC__.
5. 2012 was the year with the least transaction value with a value of __5.8M__ suggesting the nascent stage for Bitcoin as a financial asset whi it peaked in 2021 at __35.12bn__ reinforcing the ongoing prominence of Bitcoin in the financial market.
6. The year __2011__ was not fully included in this analysis because the traded period was just for __3__ months and wasn't well structured at that time.
7. A complete document in pdf containing the observations and summary from this analysis can be viewed [here](A_Complete_Observation_and_Summary_Analysis_of_Bitcoin_Historical_Data.pdf)
<br />
<br />

## View Power BI Dashboard Report
Here’s a link to a [Dashboard Report](https://app.powerbi.com/view?r=eyJrIjoiYTczNTZlNzgtYzJiYS00OWZlLThiNTEtNTMxMzk2ZGM5ZjNkIiwidCI6IjdlYzI5NjU5LTNjZjItNGYzZi1hYmIzLWE3MjJlZGY3ZmYyZCJ9)
 I created in the second phase of this project . This dashboard report displays a vivid visual of this analysis on Historical Bitcoin trading trend between Jan, 2012 - Mmarch, 2021.
<br />
<br />

## Thank You For Following Through!
