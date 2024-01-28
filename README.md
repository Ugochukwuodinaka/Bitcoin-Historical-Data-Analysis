# Bitcoin-Historical-Data (Jan, 2012 - March, 2021)
![](bitcoin1.jpg)

## Table of Contents
- [Project Overview](#project-overview)
- [EDA With Python](#data-cleaning-and-exploratory-data-analysis-using-python)
- [KPIs](#key-performance-indicators)
- [Univariate Analysis](#univariate-analysis)
- [Bivariate Amalysis](#bivariate-analysis)
- [Multivariate Analysis](#multivariate-analysis)
- [Observation and Summary](#observation-and-summary)
- [View Dashboard Report](#view-power-bi-dashboard-report)

## Project Overview
### Introduction:

Bitcoin, the pioneering cryptocurrency, has garnered significant attention and investment over the past decade. Understanding its historical price movements and trading volumes is crucial for investors, traders, and researchers alike. This data analysis project aims to explore Bitcoin's historical data spanning from 2012 to 2021, uncovering trends, patterns, and insights that can inform investment decisions and provide valuable market insights.
  
### Problem Statement
- What was the trading volume of Bitcoin between 2012 - 2021?
- What was the transaction value within this period?
- Whay was the average transaction value within this period?
- What was the total weighted price of Bitcoin within this period?
- What was the minimum open price and maximum close price within this period?
- Explain all these with charts showing their trends over the years.
- Any other relevant data driven insights from the analysis

### Objectives:

- Analyze Bitcoin Trading Volume: Investigate the trading volume of Bitcoin from 2012 to 2021 to understand the level of market activity and liquidity over time.

- Evaluate Transaction Value: Determine the total transaction value of Bitcoin within the specified period to assess the monetary value of transactions conducted on the Bitcoin network.

- Calculate Average Transaction Value: Calculate the average transaction value of Bitcoin transactions over the period under consideration, providing insights into the typical size of transactions.

- Assess Total Weighted Price: Determine the total weighted price of Bitcoin within the period to understand the overall price trend and market valuation of Bitcoin.

- Identify Price Extremes: Identify the minimum open price and maximum close price of Bitcoin within the period to highlight the range of price fluctuations and extremes observed in the market.

- Visualize Trends with Charts: Present trends and patterns in Bitcoin trading volume, transaction value, average transaction value, weighted price, minimum open price, and maximum close price, open, low, high and close price over the years, using visualizations such as line charts.

- Provide Data-Driven Insights: Extract additional insights from the analysis beyond the specified questions, uncovering any notable trends, anomalies, or correlations observed in the data that may inform decision-making or provide deeper understanding of Bitcoin market dynamics.

### Tools Used
- Python (Was used for Data Cleaning, profilling and Exploratory Data Analysis)
  
- Power BI (Was used to create reports and dashboard for this analysis)

### Methodology (Python):

- Data Collection: Gather Bitcoin historical data covering the period from 2012 to 2021, ensuring data integrity and accuracy.
  
- Data Preprocessing:
    1. Remove data rows with null values or has "NaN" because we have 1243608 rows of data with only Timestamp column data and without the rest of the column data.
    2. Create a datetime column from the Timestamp column and name it "Date"
    3. Create a "Year" column from the "Date" column
    4. Remove the "Timestamp" column
    5. Re-arrange the columns     

- Exploratory Data Analysis (EDA): Conduct EDA to gain insights into Bitcoin price dynamics, trading volume patterns, and overall market behavior. Visualize trends using line charts, and other charts.
  
### Statistical Analysis:

- Calculate descriptive statistics, including mean, median, standard deviation, and correlation coefficients, to quantify Bitcoin's price movements and trading activity.

### Volatility Analysis:

- Measure Bitcoin's volatility using standard deviation, historical volatility, or other volatility metrics. Explore the implications of volatility on risk management and investment strategies.

### Conclusion:

The data analysis project provides valuable insights into Bitcoin's historical performance and market dynamics between 2012 and 2021. By understanding past trends and patterns, investors and stakeholders can make informed decisions, manage risks effectively, and capitalize on opportunities in the ever-evolving cryptocurrency market. Further research and analysis may be warranted to explore emerging trends and developments in the cryptocurrency ecosystem.

## Dataset Overview
The primary dataset used in this analysis was released by [Quantum Analytics](https://www.quantumanalyticsco.org/). Ii could not upload it to github because of the size. It has 4857377 rows of data and has a size of almost 300 megabyte. You can also download this dataset [here](https://www.kaggle.com/datasets/mczielinski/bitcoin-historical-data). It is made up of CSV files for select bitcoin exchanges for the time period of Jan 2012 to December March 2021, with a minute to minute updates of OHLC (Open, High, Low, Close), Volume in BTC and indicated currency, and weighted bitcoin price. Timestamps are in Unix time. Timestamps without any trades or activity have their data fields filled with NaNs. If a timestamp is missing, or if there are jumps, this may be because the exchange (or its API) was down, the exchange (or its API) did not exist, or some other unforeseen technical error in data reporting or gathering. All effort has been made to deduplicate entries and verify the contents are correct and complete to the best of my ability, but obviously trust at your own risk. It is worth noting that there are 4857377 rows and 8 columns present in the Bitcoin Historical data.

The dataset contains 1 sheet/table and the columns includes:

- **Timestamp:** This column represents the timestamp or time at which the data point was recorded. It is a reference to a specific moment in time, often in Unix timestamp format (measured in seconds since January 1, 1970).

- **Open:** The opening price of the financial instrument (e.g., a cryptocurrency) during the specified time period. It is the price at which the first trade occurred.

- **High:** The highest price reached during the specified time period.

- **Low:** The lowest price reached during the specified time period.

- **Close:** The closing price of the financial instrument at the end of the specified time period. It is the price at which the last trade occurred.

- **Volume_(BTC):** The total trading volume of the financial instrument in terms of the base currency (e.g., Bitcoin) during the specified time period. It represents the total quantity of the financial instrument traded.

- **Volume_(Currency):** The total trading volume of the financial instrument in terms of the quote currency (e.g., US dollars) during the specified time period. It represents the total value of the trades.

- **Weighted_Price:** The volume-weighted average price (VWAP) or the average price of the financial instrument during the specified time period, considering the trading volume. It provides a more comprehensive view of the average transaction price.

## Data Analysis and Visuals in Python:

## Data Cleaning and Exploratory Data Analysis using Python
### Import all the necessary libraries
```
import pandas as pd
import os
import numpy as np
import plotly.express as px
```
For visual
```
import matplotlib.pyplot as plt
import seaborn as sns
```
Assign df as pandas DataFrame
```
df = pd.DataFrame()
```
Import and read file
```
df = pd.read_csv(r"bitstampUSD_1-min_data 2012-01-01_to_2021-03-31.csv")
df
```
![image](https://github.com/Ugochukwuodinaka/Bitcoin-Historical-Data/assets/157266999/f595b469-e467-431c-94cd-c4a24a8284e6)

The 10 rows at the top of the data
```
df.head(10)
```
![image](https://github.com/Ugochukwuodinaka/Bitcoin-Historical-Data/assets/157266999/d497c89f-f38b-4870-b614-c5cd72ac15a9)

### DATA PROFILING STEPS
Data profiling utilizes methods of descriptive statistics such as:

1. Data type
2. Quantile statistics (central tendecies)
3. Length (length and shape of the dataset)
4. Discrete values
5. Uniqueness (unique values)
6. Occurence of null values and etc.

Shape of the data
```
df.shape
```
Size of the data
```
df.size
```
Check the data types
```
df.dtypes
```
Check for missing values

The below doesn't give me explicit details of the null values
```
df.isnull()
```
The below works better and is explicit
```
df.isnull().sum()
```
### Data Profiling

Check the descriptive statistics
```
df.describe()
```
Make the descriptive statistic clearer by removing the zeros
```
df.describe().astype(int)
```
Check for numerical columns
```
categorical_cols = df.select_dtypes(include = [int, float]).columns.tolist()
categorical_cols
```
Check for categorical columns
```
numerical_cols = df.select_dtypes(include = ['category', 'object']).columns
numerical_cols
```

### Data Cleaning Processes
1. Remove data rows with null values or has "NaN" because we have 1243608 rows of data with only Timestamp colu,mn data and without the rest of the column data.
2. Create a datetime column from the Timestamp column and name it "Date"
3. Create a "Year" column from the "Date" column
4. Remove the "Timestamp" column

Remove data rows with null values or has "NaN" because we have 1243608 rows of data with only Timestamp column data.
```
df = df.dropna()
df
```
Check if there are still data rows with null values
```
df.isnull().sum()
```
Create a copy of the DatFrame

Create a datetime column from the Timestamp column and name it "Date"
```
df_new = df.copy()
df_new['Date'] = pd.to_datetime(df_new['Timestamp'], unit='s')
df_new
```

Create a "Year" column from the "Date" column
```
df_new['Year'] = df_new['Date'].dt.year
df_new
```
Remove the "Timestamp" column
```
df_new = df_new.drop('Timestamp', axis=1)
```

### Further Exploratory Data Analysis after Data Cleaning

Get the first 10 rows of data
```
df_new.head(10)
```
![image](https://github.com/Ugochukwuodinaka/Bitcoin-Historical-Data/assets/157266999/9887400f-1818-471e-b9d2-ef7e63c1c07c)

Re-check the shape of the data
```
df_new.shape
```
Re-check the size of the data
```
df_new.size
```
Get the full info of the columns once again
```
df_new.info()
```
Get the descriptive statistics
```
df_new.describe().astype(int)
```
Check once again for interger and float columns
```
df_new.select_dtypes(include=[int, float]).columns
```
Check for object or categorical columns
```
df_new.select_dtypes(include=['object', 'category']).columns
```
Check for unique dates
```
df_new.Date.nunique()
```

## Key Performance Indicators

### Total Trading Volume

```
TradingVolume_sum = df_new['Volume_(BTC)'].sum()
```
round to one decimal place and display in millions
```
rounded_TradingVolume = round(TradingVolume_sum, 1) 
Trading_Volume = (f"{rounded_TradingVolume/1e6:.0f}m")
Trading_Volume
```

### Transaction Value
```
TransactionValue_sum = df_new['Volume_(Currency)'].sum()
```

round to one decimal place and display in billions
```
rounded_TransactionValue = round(TransactionValue_sum, 1) 
Transaction_Value = (f"{rounded_TransactionValue/1e9:.0f}bn")
Transaction_Value
```
### Total Weighted Price
```
WeightedPrice_sum = df_new['Weighted_Price'].sum()
```
round to one decimal place and display in 
```
rounded_WeightedPrice_sum = round(WeightedPrice_sum, 1) 
Total_Weighted_Price = (f"{rounded_WeightedPrice_sum/1e9:.0f}bn")
Total_Weighted_Price
```
### Minimum Open Price
```
Minimum_Open_Price = df_new['Open'].min()
Minimum_Open_Price
```
### Maximum Close Price
```
MaximumClosePrice = df_new['Close'].max()
round to one decimal place and display in thousands
rounded_MaximumClosePrice = round(MaximumClosePrice, 1) 
Maximum_Close_Price = (f"{rounded_MaximumClosePrice/1000:.1f}k")
Maximum_Close_Price
```
![KPIs](https://github.com/Ugochukwuodinaka/Bitcoin-Historical-Data/assets/157266999/d4857699-ed8e-4335-9823-2f59d0a53103)

## Visualization and observations

### Univariate Analysis

Descriptive Statistics and Observation
```
df_new.describe().astype(int)
```
![image](https://github.com/Ugochukwuodinaka/Bitcoin-Historical-Data/assets/157266999/a2b65da6-7087-488c-b04c-5c626f8506b9)

#### Observation and Summary:

The dataset provides a comprehensive overview of cryptocurrency market trends, specifically focused on Bitcoin, with descriptive statistics revealing key insights.
The mean values for Open, High, Low, and Close suggest a relatively stable market, hovering around $6000. However, the substantial standard deviations (std) indicate considerable volatility. The range from the minimum to maximum values showcases the cryptocurrency's evolution since 2011, with a notable surge in 2017, as indicated by the median values. The Volume statistics underline the varying degrees of market participation, with a median Volume_(BTC) of 1 but a maximum of 5853, highlighting instances of heightened trading activity. The Weighted_Price, representing the average price weighted by volume, aligns closely with the mean values for Open, High, Low, and Close. The temporal distribution of the data, illustrated by the Year statistics, spans from 2011 to 2021, capturing the cryptocurrency's journey over the past decade. These statistics collectively portrays a picture of Bitcoin's market dynamics, reflecting both stability and volatility within the observed period.

### Bivariate Analysis

#### Trading Volume Over the Years
```
Trading_Volume_By_Year = df_new.groupby('Year')['Volume_(BTC)'].sum().reset_index(name= 'Trading Volume By Year')
Trading_Volume_By_Year
```
#### Plotting a Line Chart

Trading_Volume_By_Year as DataFrame

```
plt.figure(figsize=(10, 6))
```
round the values
```
rounded_values = Trading_Volume_By_Year['Trading Volume By Year']
labels = []

for value in rounded_values:
    if value >= 1e6:
        labels.append(f'{value / 1e6:.2f}M')
    elif value >= 1e3:
        labels.append(f'{value / 1e3:.2f}K')
    else:
        labels.append(f'{value:.2f}')

plt.plot(Trading_Volume_By_Year['Year'], rounded_values, marker='o', linestyle='-', color='b')
plt.title('Trading Volume Over the Years')
plt.xlabel('Year')
plt.ylabel('Trading Volume')
plt.xticks(Trading_Volume_By_Year['Year'])
```
Adding rounded labels to data points
```
for i, txt in enumerate(labels):
    plt.annotate(txt, (Trading_Volume_By_Year['Year'][i], rounded_values[i]), textcoords="offset points", xytext=(0, 5), ha='center')
plt.show()
```
![image](https://github.com/Ugochukwuodinaka/Bitcoin-Historical-Data/assets/157266999/cc8e039a-8282-4dde-a3fe-8f84fcebfba2)

#### Observation and Summary:

The provided data represents the annual trading volume in Bitcoin (BTC) over the years, spanning from 2011 to 2021. Below is a summary of the trading volumes for each year:

- 2011: The trading volume in 2011 was approximately 95.32 BTC.

- 2012: The trading volume saw a significant increase in 2012, reaching around 567,948 BTC.

- 2013: The trend of increased trading volume continued in 2013, with the volume surging to approximately 5.03 million BTC.

- 2014: The trading volume in 2014 remained consistent with the previous year, hovering around 5.02 million BTC.

- 2015: The year 2015 witnessed a slight increase in trading volume, reaching approximately 5.53 million BTC.

- 2016: There was a notable decline in trading volume in 2016, with the volume dropping to around 1.99 million BTC.

- 2017: The trading volume rebounded in 2017, reaching approximately 4.70 million BTC.

- 2018: The trading volume decreased in 2018, amounting to about 3.93 million BTC.

- 2019: Further decline was observed in 2019, with the trading volume dropping to around 2.99 million BTC.

- 2020: The year 2020 saw a slight increase in trading volume, reaching approximately 3.07 million BTC.

- 2021: The trading volume experienced a notable decrease in 2021, amounting to around 851,118 BTC.

In summary, the Bitcoin trading volume exhibited fluctuations over the years, influenced by market dynamics, technological developments, and global events. The years 2012 and 2013 stand out with substantial increases in trading activity, while subsequent years showed varying degrees of volatility and stabilization. The data provides insights into the evolving dynamics of the cryptocurrency market during this period.

#### Transaction Value Over Tthe Years
```
Transaction_Value_By_Year = df_new.groupby('Year')['Volume_(Currency)'].sum().reset_index(name= 'Transaction Value By Year')
Transaction_Value_By_Year
```
#### Plotting a Line Chart

Transaction_Value_By_Year as DataFrame
```
plt.figure(figsize=(10, 6))
```
Convert the transaction values to billions for better readability and plot the chart
```
Transaction_Value_By_Year['Transaction Value By Year (Billion)'] = Transaction_Value_By_Year['Transaction Value By Year'] / 1e9

plt.plot(Transaction_Value_By_Year['Year'], Transaction_Value_By_Year['Transaction Value By Year (Billion)'], marker='o', linestyle='-', color='b')
plt.title('Transaction Value Over the Years')
plt.xlabel('Year')
plt.ylabel('Transaction Value (Billion USD)')
plt.xticks(Transaction_Value_By_Year['Year'])  # Set x-axis ticks to match the years
```
Adding labels to data points with exact values in billions
```
for i, txt in enumerate(Transaction_Value_By_Year['Transaction Value By Year (Billion)']):
    plt.annotate(f'{txt:.2f}B', (Transaction_Value_By_Year['Year'][i], txt), textcoords="offset points", xytext=(0,5), ha='center')

plt.show()
```
![image](https://github.com/Ugochukwuodinaka/Bitcoin-Historical-Data/assets/157266999/8fd92e7d-e5ca-4ca6-b766-897d97de0117)

#### Observation and Summary:

The data on transaction value by year provides valuable insights into the evolution of Bitcoin's financial activity over the past decade. Here are key observations:

- Early Years (2011-2015): The transaction values in the early years, particularly in 2011, 2012, and 2015, were relatively modest, ranging from hundreds of millions to a few billion USD. This suggests a developing and nascent stage for Bitcoin as a financial asset during this period.

- Significant Increase in 2013-2014: The year 2013 witnessed a notable uptick in transaction value, reaching 1.55 billion USD, and this trend continued in 2014, reaching 2.62 billion USD. This surge aligns with increased adoption and recognition of Bitcoin within the financial landscape.

- Stability and Fluctuations (2015-2019): From 2015 to 2019, transaction values fluctuated but remained within the range of approximately 1 billion to 3 billion USD. This period reflects a level of stability in Bitcoin transactions, with variations possibly influenced by market sentiment, regulatory developments, and technological advancements.

- Peak in 2017: The year 2017 marked a significant turning point, with a remarkable surge in transaction value to 21.78 billion USD. This substantial increase aligns with the broader cryptocurrency boom during that period, characterized by heightened market interest, increased institutional participation, and skyrocketing Bitcoin prices.

- Sustained High Transaction Values (2018-2021): Despite fluctuations, the years 2018, 2019, 2020, and 2021 maintained high transaction values, ranging from 23.16 billion to 35.12 billion USD. This suggests a sustained and growing interest in Bitcoin, with increased financial activity in the cryptocurrency market.

- Year 2021: The data for 2021 indicates a transaction value of 35.12 billion USD, reinforcing the ongoing prominence of Bitcoin in the financial landscape. The sustained high transaction values in recent years highlight Bitcoin's role as a significant asset class and a store of value.

In summary, the observed transaction values depict the dynamic nature of Bitcoin's financial activity, with notable spikes in 2013, 2017, and sustained high values in subsequent years. These trends may be indicative of evolving market dynamics, increased adoption, and the growing integration of Bitcoin into the broader financial ecosystem.

### Weighted Price Value Over The Years
```
Weighted_Price_By_Year = df_new.groupby('Year')['Weighted_Price'].sum().reset_index(name= 'Weighted Price By Year')
Weighted_Price_By_Year
```
### Plotting a Line Chart

Convert the weighted prices to billions for better readability and plot the chart
```
Weighted_Price_By_Year['Weighted Price By Year (Billion)'] = Weighted_Price_By_Year['Weighted Price By Year'] / 1e9

plt.figure(figsize=(10, 6))
plt.plot(Weighted_Price_By_Year['Year'], Weighted_Price_By_Year['Weighted Price By Year (Billion)'], marker='o', linestyle='-', color='b')
plt.title('Weighted Price Over the Years')
plt.xlabel('Year')
plt.ylabel('Weighted Price (Billion USD)')
plt.xticks(Weighted_Price_By_Year['Year'])  # Set x-axis ticks to match the years
```
Adding labels to data points with rounded values in billions
```
for i, txt in enumerate(Weighted_Price_By_Year['Weighted Price By Year (Billion)']):
    rounded_value = round(txt, 2)  # Round to two decimal places
    plt.annotate(f'{rounded_value}B', (Weighted_Price_By_Year['Year'][i], txt), textcoords="offset points", xytext=(0,5), ha='center')

plt.show()
```

![image](https://github.com/Ugochukwuodinaka/Bitcoin-Historical-Data/assets/157266999/77b13eba-5ea9-49bc-bcd7-b9864a6b064a)

#### Observation and Summary:

The data on weighted prices by year provides insights into the valuation dynamics of Bitcoin over the past decade. Here are key observations:

- Early Years (2011-2015): In the early years, from 2011 to 2015, the weighted prices were relatively modest, ranging from approximately 18 USD in 2011 to around 102 million USD in 2015. This period suggests a gradual establishment of Bitcoin's valuation with a significant increase in 2013, reflecting growing market recognition.

- Notable Increase in 2013-2016: A significant increase in weighted prices is observed from 2013 to 2016, reaching a peak of approximately 1.97 billion USD in 2016. This period likely reflects a combination of factors, including increased adoption, heightened market interest, and the maturation of Bitcoin as a financial asset.

- Peak in 2017: The year 2017 stands out with a substantial peak in weighted prices, reaching 2.01 billion USD. This aligns with the broader cryptocurrency boom during that period, characterized by heightened market speculation and increased institutional interest.

- Sustained High Valuations (2018-2021): From 2018 to 2021, weighted prices remained consistently high, ranging from 3.77 billion to 5.76 billion USD. This sustained high valuation suggests that Bitcoin has maintained its status as a significant and valuable asset, attracting continued investor interest.

- Year 2020-2021: The data for 2020 and 2021 indicates relatively stable weighted prices, with both years hovering around the 5.76 billion USD mark. This suggests that Bitcoin's valuation has reached a level of stability after the peak observed in 2017.

In summary, the observed trends in weighted prices reflect the evolving perception and valuation of Bitcoin in the financial markets. The peak in 2017 marked a period of exceptional valuation, while the subsequent years indicate sustained high levels, showcasing Bitcoin's resilience and recognition as a valuable asset class. The relatively stable valuations in recent years may suggest a maturation of the cryptocurrency market.

### Multivariate Analysis
### Total of Open, Low, High, and Close Price Over the Years

Group by 'Year' and calculate the sum for each column
```
sum_by_year = df_new.groupby('Year').agg({
    'Open': 'sum',
    'Low': 'sum',
    'High': 'sum',
    'Close': 'sum'
}).reset_index()
```
Convert sums to billions for better readability
```
sum_by_year['Sum_Open (Billion)'] = round(sum_by_year['Open'] / 1e9, 2)
sum_by_year['Sum_Low (Billion)'] = round(sum_by_year['Low'] / 1e9, 2)
sum_by_year['Sum_High (Billion)'] = round(sum_by_year['High'] / 1e9, 2)
sum_by_year['Sum_Close (Billion)'] = round(sum_by_year['Close'] / 1e9, 2)

print(sum_by_year)
```
### Plotting a Multi-Line Chart

Plotting the multi-spaced line chart with no grids
```
plt.figure(figsize=(12, 8))
```
Adding some vertical spacing between the lines
```
spacing = 0.5
```
Iterate through columns and plot each line separately
```
for column in ['Open', 'Low', 'High', 'Close']:
    plt.plot(sum_by_year['Year'], sum_by_year[column] / 1e9 + spacing * sum_by_year.columns.get_loc(column), marker='o', linestyle='-', label=column)
```
Adding labels to data points with exact values in billions
```
    for i, year in enumerate(sum_by_year['Year']):
        plt.annotate(f'{sum_by_year[column][i] / 1e9:.2f}B', (year, (sum_by_year[column][i] / 1e9) + spacing * sum_by_year.columns.get_loc(column)), textcoords="offset points", xytext=(0, 5), ha='center')

plt.title('Total of Open, Low, High, and Close Prices Over the Years')
plt.xlabel('Year')
plt.ylabel('Sum (Billion USD)')
plt.xticks(sum_by_year['Year'])  # Set x-axis ticks to match the years
plt.legend()
```
![image](https://github.com/Ugochukwuodinaka/Bitcoin-Historical-Data/assets/157266999/ae3717de-0837-46d8-b5f2-5ace93223d0a)

### Observation and Summary:

The provided data represents the summary statistics for Bitcoin price levels (Open, Low, High, and Close) for each year from 2011 to 2021. Here are key observations:

- Open Price: The Open price shows a significant increase over the years, starting from approximately  18𝑖𝑛2011𝑎𝑛𝑑𝑟𝑒𝑎𝑐ℎ𝑖𝑛𝑔𝑜𝑣𝑒𝑟
 5.7 billion in 2021. There is a consistent upward trend, reflecting the overall growth and interest in Bitcoin during this period.

- Low Price: The Low price exhibits a similar trend to the Open price, indicating that even the lowest daily prices have increased substantially. The Low price in 2011 was around  17.86,𝑤ℎ𝑖𝑙𝑒𝑖𝑛2021,𝑖𝑡𝑟𝑒𝑎𝑐ℎ𝑒𝑑𝑎𝑝𝑝𝑟𝑜𝑥𝑖𝑚𝑎𝑡𝑒𝑙𝑦
 5.74 billion.

- High Price: The High price reflects the highest daily trading price of Bitcoin, and it follows a consistent upward trajectory. From around  17.93𝑖𝑛2011,𝑡ℎ𝑒𝐻𝑖𝑔ℎ𝑝𝑟𝑖𝑐𝑒𝑠𝑢𝑟𝑔𝑒𝑑𝑡𝑜𝑎𝑏𝑜𝑢𝑡
 5.75 billion in 2021.

- Close Price: The Close price, representing the final trading price of the day, also shows a notable increase over the years. Starting from  17.93𝑖𝑛2011,𝑡ℎ𝑒𝐶𝑙𝑜𝑠𝑒𝑝𝑟𝑖𝑐𝑒𝑟𝑒𝑎𝑐ℎ𝑒𝑑𝑎𝑝𝑝𝑟𝑜𝑥𝑖𝑚𝑎𝑡𝑒𝑙𝑦
 5.75 billion in 2021.

-Overall Trend: The data suggests a remarkable long-term bullish trend in Bitcoin prices, with each year's metrics significantly surpassing the previous year. The cryptocurrency market, as reflected in Bitcoin prices, has experienced substantial growth and attention over the analyzed period.

It's important to note that these figures represent the aggregated summary for each year and provide an overview of the broader trend in Bitcoin prices. Individual factors, market events, and external influences can contribute to fluctuations within each year. The data underscores the dynamic and evolving nature of the cryptocurrency market during the specified timeframe.


Save the updated DataFrame to CSV without the python generated index column
```
df_new.to_csv('historical_bitcoin_data.csv', index=False)
```
## View Power BI Dashboard Report
Here’s a link to a [Dashboard Report](https://app.powerbi.com/view?r=eyJrIjoiYTczNTZlNzgtYzJiYS00OWZlLThiNTEtNTMxMzk2ZGM5ZjNkIiwidCI6IjdlYzI5NjU5LTNjZjItNGYzZi1hYmIzLWE3MjJlZGY3ZmYyZCJ9)
 I created in the second phase of this project . This dashboard report displays a vivid visual of this analysis on Historical Bitcoin trading trend between 2012 - 2021.
