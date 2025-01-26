# Cryptocurrency-Analysis
Cryptocurrency Prices Analysis: Data Preparation, Analysis, and Interactive Visualization Using Python and Tableau

## Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Tools](#tools)
- [Data Preparation](#data-preparation)
- [Data Analysis](#data-analysis)
- [Results and Insights](#results-and-insights)
- [Visualization](#visualization)
  
## Project Overview

This project focuses on analyzing daily price trends of the top 23 cryptocurrencies by market cap. Using Python and Tableau, the goal is to uncover insights about price volatility, trends, and other patterns that can help understand the dynamics of the cryptocurrency market.

## Data Sources

Source: Proprietary dataset consisting of 23 Excel files, one for each cryptocurrency.

Columns:
- Ticker: Cryptocurrency symbol (e.g., BTC, ETH).
- Date: Date of the price entry.
- Open: Opening price on the given day.
- High: Highest price of the day.
- Low: Lowest price of the day.
- Close: Closing price of the day.

## Tools

**Python:** Pandas for data cleaning and manipulation in jupyter notebook, Matplotlib/Seaborn for exploratory data analysis.
**Tableau:** Interactive dashboards and visualizations.

## Data Preparation

- Combined the 23 individual Excel files into a single DataFrame for analysis.
- Managed missing date values by ensuring chronological consistency.
- Standardized formats and ensured data integrity.

## Exploratory Data Analysis

## Data Analysis

Importing necessary libraries

```python
import pandas as pd
```

Reading CSV files for each cryptocurrency into separate dataframes, each file contains historical price data for a specific cryptocurrency

```python
df_aave = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_Aave.csv")
df_bnb = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_BinanceCoin.csv")
df_btc = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_Bitcoin.csv")
df_ada = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_Cardano.csv")
df_link = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_ChainLink.csv")
df_atom = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_Cosmos.csv")
df_cro = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_CryptocomCoin.csv")
df_doge = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_Dogecoin.csv")
df_eos = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_EOS.csv")
df_eth = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_Ethereum.csv")
df_miota = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_Iota.csv")
df_ltc = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_Litecoin.csv")
df_xmr = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_Monero.csv")
df_xem = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_NEM.csv")
df_dot = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_Polkadot.csv")
df_sol = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_Solana.csv")
df_xlm = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_Stellar.csv")
df_usdt = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_Tether.csv")
df_trx = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_Tron.csv")
df_uni = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_Uniswap.csv")
df_usdc = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_USDCoin.csv")
df_wbtc = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_WrappedBitcoin.csv")
df_xrp = pd.read_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\Cryptocurrency Historical Prices\coin_XRP.csv")
```

List of all dataframes

```python
dfs = [df_aave, df_bnb, df_btc, df_ada, df_link, df_atom, df_cro, df_doge, df_eos, df_eth, df_miota, df_ltc, df_xmr, df_xem, df_dot, df_sol, df_xlm, df_usdt, df_trx, df_uni, df_usdc, df_wbtc, df_xrp]
```
Ensure the 'Date' column is in datetime format for all dataframes

```python
for df in dfs:
    df['Date'] = pd.to_datetime(df['Date'], errors='coerce') # Coerce invalid dates to NaT (Not a Time)
```
Iterate through the list of dataframes and display data types for each

```python
for idx, df in enumerate(dfs, 1): # Start enumeration at 1 for easier readability
    print(f"Data types for dataframe {idx}:") 
    print(df.dtypes) # Display the data types of each column in the DataFrame
    print("\n") # Add a blank line for better output formatting
```

Output:

    Data types for dataframe 1:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 2:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 3:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 4:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 5:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 6:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 7:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 8:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 9:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 10:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 11:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 12:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 13:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 14:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 15:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 16:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 17:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 18:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 19:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 20:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 21:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 22:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
    
    Data types for dataframe 23:
    SNo                   int64
    Name                 object
    Symbol               object
    Date         datetime64[ns]
    High                float64
    Low                 float64
    Open                float64
    Close               float64
    Volume              float64
    Marketcap           float64
    dtype: object
    
Combine all 23 dataframes into a single dataframe using pd.concat

```python
dfs = pd.concat([df_aave, df_bnb, df_btc, df_ada, df_link, df_atom, df_cro, df_doge, df_eos, df_eth, df_miota, df_ltc, df_xmr, df_xem, df_dot, df_sol, df_xlm, df_usdt, df_trx, df_uni, df_usdc, df_wbtc, df_xrp]
)
```

Get unique values in the "Symbol" column

```python
dfs['Symbol'].unique()
```

Output:

    array(['AAVE', 'BNB', 'BTC', 'ADA', 'LINK', 'ATOM', 'CRO', 'DOGE', 'EOS',
           'ETH', 'MIOTA', 'LTC', 'XMR', 'XEM', 'DOT', 'SOL', 'XLM', 'USDT',
           'TRX', 'UNI', 'USDC', 'WBTC', 'XRP'], dtype=object)

Display dataframes

```python
dfs
```

Output:
  
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>SNo</th>
      <th>Name</th>
      <th>Symbol</th>
      <th>Date</th>
      <th>High</th>
      <th>Low</th>
      <th>Open</th>
      <th>Close</th>
      <th>Volume</th>
      <th>Marketcap</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Aave</td>
      <td>AAVE</td>
      <td>2020-10-05 23:59:59</td>
      <td>55.112358</td>
      <td>49.787900</td>
      <td>52.675035</td>
      <td>53.219243</td>
      <td>0.000000e+00</td>
      <td>8.912813e+07</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Aave</td>
      <td>AAVE</td>
      <td>2020-10-06 23:59:59</td>
      <td>53.402270</td>
      <td>40.734578</td>
      <td>53.291969</td>
      <td>42.401599</td>
      <td>5.830915e+05</td>
      <td>7.101144e+07</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>Aave</td>
      <td>AAVE</td>
      <td>2020-10-07 23:59:59</td>
      <td>42.408314</td>
      <td>35.970690</td>
      <td>42.399947</td>
      <td>40.083976</td>
      <td>6.828342e+05</td>
      <td>6.713004e+07</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>Aave</td>
      <td>AAVE</td>
      <td>2020-10-08 23:59:59</td>
      <td>44.902511</td>
      <td>36.696057</td>
      <td>39.885262</td>
      <td>43.764463</td>
      <td>1.658817e+06</td>
      <td>2.202651e+08</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5</td>
      <td>Aave</td>
      <td>AAVE</td>
      <td>2020-10-09 23:59:59</td>
      <td>47.569533</td>
      <td>43.291776</td>
      <td>43.764463</td>
      <td>46.817744</td>
      <td>8.155377e+05</td>
      <td>2.356322e+08</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2888</th>
      <td>2889</td>
      <td>XRP</td>
      <td>XRP</td>
      <td>2021-07-02 23:59:59</td>
      <td>0.667287</td>
      <td>0.634726</td>
      <td>0.659890</td>
      <td>0.656763</td>
      <td>2.061607e+09</td>
      <td>3.030759e+10</td>
    </tr>
    <tr>
      <th>2889</th>
      <td>2890</td>
      <td>XRP</td>
      <td>XRP</td>
      <td>2021-07-03 23:59:59</td>
      <td>0.683677</td>
      <td>0.644653</td>
      <td>0.655639</td>
      <td>0.672888</td>
      <td>1.872820e+09</td>
      <td>3.105172e+10</td>
    </tr>
    <tr>
      <th>2890</th>
      <td>2891</td>
      <td>XRP</td>
      <td>XRP</td>
      <td>2021-07-04 23:59:59</td>
      <td>0.707783</td>
      <td>0.665802</td>
      <td>0.673218</td>
      <td>0.694945</td>
      <td>1.885242e+09</td>
      <td>3.206960e+10</td>
    </tr>
    <tr>
      <th>2891</th>
      <td>2892</td>
      <td>XRP</td>
      <td>XRP</td>
      <td>2021-07-05 23:59:59</td>
      <td>0.695653</td>
      <td>0.648492</td>
      <td>0.695653</td>
      <td>0.654300</td>
      <td>2.076373e+09</td>
      <td>3.019395e+10</td>
    </tr>
    <tr>
      <th>2892</th>
      <td>2893</td>
      <td>XRP</td>
      <td>XRP</td>
      <td>2021-07-06 23:59:59</td>
      <td>0.679923</td>
      <td>0.652676</td>
      <td>0.653055</td>
      <td>0.665402</td>
      <td>1.938959e+09</td>
      <td>3.072284e+10</td>
    </tr>
  </tbody>
</table>
<p>37082 rows × 10 columns</p>
</div>
```

Check for missing values in the entire dataframe

```python
missing_values = dfs.isna().sum()

print(missing_values)
```

Output:

    SNo          0
    Name         0
    Symbol       0
    Date         0
    High         0
    Low          0
    Open         0
    Close        0
    Volume       0
    Marketcap    0
    dtype: int64
    
Save data and export into csv file for visualization

```python
dfs.to_csv(r"C:\Users\corvi\OneDrive\Desktop\Data Sets\crypto_daily.csv", index=False)
```

## Results and Insights

- [Bitcoin (BTC)] consistently maintained its dominance with the highest average closing price of [value].
- Stablecoins like [USDT, USDC] showed minimal price variation, reflecting their pegged nature.

## Visualization

Interactive Tableau Dashboard can be found here
