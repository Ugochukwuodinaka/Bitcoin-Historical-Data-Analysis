# Bitcoin-Historical-Data (Jan, 2012 - March, 2021)

## Project Overview
Cryptocurrency is a type of digital or virtual currency that uses cryptography for security and operates on a decentralized network of computers. Unlike traditional currencies issued by governments , cryptocurrencies operate on a technology called blockchain. Blockchain is a distributed ledger that records all transactions across a network of computers.
Bitcoin is the first and most well-known cryptocurrency, created in 2009 by an unknown person or group using the pseudonym Satoshi Nakamoto. Bitcoin is often referred to as digital gold and is designed to be a decentralized and censorship-resistant form of currency. Here are some key features of Bitcoin and cryptocurrencies in general:
Decentralization: Cryptocurrencies operate on a decentralized network of computers, which means no single entity, such as a government or financial institution, has control over the entire network. 
Blockchain Technology: The blockchain is a distributed ledger that records all transactions in a secure and transparent manner. 
Cryptography: Cryptocurrencies use cryptographic techniques to secure transactions and control the creation of new units. 
Limited Supply: Many cryptocurrencies, including Bitcoin, have a limited supply. For example, the total supply of Bitcoin is capped at 21 million coins, making it a deflationary asset. 
Mining: Some cryptocurrencies, including Bitcoin, use a process called mining to validate transactions and secure the network. 
Volatility: Cryptocurrency prices can be highly volatile, with values subject to rapid and unpredictable changes. 
Use Cases: Cryptocurrencies can be used for various purposes, including online transactions, remittances, and as a store of value. 

Let's move forward to the analysis of the Bitcoin Historical Data (Jan, 2012 - March, 2021)

## Dataset Overview
The primary dataset used in this the "bitstampUSD_1-min_data 2012-01-01_to_2021-03-31_new.csv" file. This dataset was released by [Quantum Analytics](https://www.quantumanalyticsco.org/). It is made up of CSV files for select bitcoin exchanges for the time period of Jan 2012 to December March 2021, with a minute to minute updates of OHLC (Open, High, Low, Close), Volume in BTC and indicated currency, and weighted bitcoin price. Timestamps are in Unix time. Timestamps without any trades or activity have their data fields filled with NaNs. If a timestamp is missing, or if there are jumps, this may be because the exchange (or its API) was down, the exchange (or its API) did not exist, or some other unforeseen technical error in data reporting or gathering. All effort has been made to deduplicate entries and verify the contents are correct and complete to the best of my ability, but obviously trust at your own risk.

## Metadata
The dataset contains 8 columns and they include:

- Timestamp: This column represents the timestamp or time at which the data point was recorded. It is a reference to a specific moment in time, often in Unix timestamp format (measured in seconds since January 1, 1970).

- Open: The opening price of the financial instrument (e.g., a cryptocurrency) during the specified time period. It is the price at which the first trade occurred.

- High: The highest price reached during the specified time period.

- Low: The lowest price reached during the specified time period.

- Close: The closing price of the financial instrument at the end of the specified time period. It is the price at which the last trade occurred.

- Volume_(BTC): The total trading volume of the financial instrument in terms of the base currency (e.g., Bitcoin) during the specified time period. It represents the total quantity of the financial instrument traded.

- Volume_(Currency): The total trading volume of the financial instrument in terms of the quote currency (e.g., US dollars) during the specified time period. It represents the total value of the trades.

- Weighted_Price: The volume-weighted average price (VWAP) or the average price of the financial instrument during the specified time period, considering the trading volume. It provides a more comprehensive view of the average transaction price.

## Tools
- Python (Was used for Data Cleaning and Exploratory Data Analysis)
  
- Power BI (Was used to create reports and dashboard for this analysis)

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

## Key Performance Indicators (KPIs)

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

## Visualization and observations

### Univariate Analysis

Descriptive Statistics Observation
```
df_new.describe().astype(int)
```
![image](https://github.com/Ugochukwuodinaka/Bitcoin-Historical-Data/assets/157266999/a2b65da6-7087-488c-b04c-5c626f8506b9)

#### Observation

The dataset provides a comprehensive overview of cryptocurrency market trends, specifically focused on Bitcoin, with descriptive statistics revealing key insights.
The mean values for Open, High, Low, and Close suggest a relatively stable market, hovering around $6000. However, the substantial standard deviations (std) indicate considerable volatility. The range from the minimum to maximum values showcases the cryptocurrency's evolution since 2011, with a notable surge in 2017, as indicated by the median values. The Volume statistics underline the varying degrees of market participation, with a median Volume_(BTC) of 1 but a maximum of 5853, highlighting instances of heightened trading activity. The Weighted_Price, representing the average price weighted by volume, aligns closely with the mean values for Open, High, Low, and Close. The temporal distribution of the data, illustrated by the Year statistics, spans from 2011 to 2021, capturing the cryptocurrency's journey over the past decade. These statistics collectively portrays a picture of Bitcoin's market dynamics, reflecting both stability and volatility within the observed period.

