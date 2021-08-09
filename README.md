# Challenge-Assignment-7
Build a financial database and web application by using SQL, Python, and the Voilà library to analyze the performance of a hypothetical fintech ETF.
Executive Summary:
The return on an ETF portfolio consisting of four ETF Stocks ['GDOT', 'GS', 'PYPL', 'SQ'] were analyzed for their performance. Based on the analysis of the cumulative returns the best performing stock are ranked as follows based on their average returns:
ETF Stock         Mean Return
"SQ_RETURNS"      0.003300
"PYPL_RETURNS"    0.001957
"GDOT_RETURNS"    0.001504
"GS_RETURNS"      0.000196

Analytical Tools used: The prinmary downloads for performing thos analysis was use of Conda version 3.8, Pandas, Pathlib, SQLAlchemy(n open-source SQL library for Python. It’s designed to ease the communication between Python-based programs and databases) & Voilà to build a web application as per the Userstories requirements.

The required libraries and dependencies are required to run this file and are to be imported as follows:
import numpy as np
import pandas as pd
import hvplot.pandas
import sqlalchemy as sql

Procedure: Once the inital libraries and tools were imported, the next step was to reate a temporary SQLite database and populate the database with content from the etf.db seed file followed by creating an engine to interact with the SQLite database. The engine was used to confirm that the table names were being read correctly with the following output: ['GDOT', 'GS', 'PYPL', 'SQ'].
The first step in the analytical process was to analyze a single stock PYPL. The extraction of this stock data was accomplished using a SQL query (using an f-string) to SELECT all of the data from the PYPL table and then Use the query to read the PYPL data into a Pandas DataFrame. The dataframe outputs were confirmed using the Head & Tail commands. As an additonal step the mean returns for PYPL was confirmed to be [0.00195722193656932]. Next a interactive visualization with hvplot to plot the daily returns for PYPL was completed as shown below:
![image](https://user-images.githubusercontent.com/85462153/128660738-8fa73f18-fda9-4aca-9a55-b33d18a91909.png)

Next the cumulative returns for PYPL was generated using the cumprod fuunction & plotted using the hvplot command. The PYPL cumulative plot showed a constant growth rate across 800 days followed by a brief slump (days 800 - 830) and then more than doubled its growth rate over the last 90 days.  A SQL SELECT statement was used to select the dates where the PYPL closing price was higher than 200.0.There were 10 days in total where the PYPL stock was greater than 200.  The top 10 daily returns for PYPL were then generated (using a SQL statement SELECT + ORDER + LIMIT) & shown below in descending order:
time	daily_returns
0	2020-03-24 00:00:00.000000	0.140981
1	2020-05-07 00:00:00.000000	0.140318
2	2020-03-13 00:00:00.000000	0.138700
3	2020-04-06 00:00:00.000000	0.100877
4	2018-10-19 00:00:00.000000	0.093371
5	2019-10-24 00:00:00.000000	0.085912
6	2020-11-04 00:00:00.000000	0.080986
7	2020-03-10 00:00:00.000000	0.080863
8	2020-04-22 00:00:00.000000	0.075321
9	2018-12-26 00:00:00.000000	0.074656

Next the performance of the combined asset was to be determined to obtain  the average returns of the portfolio to calculate the annualized returns and the cumulative returns. A SQL query to join each table in the portfolio into a single DataFrame was then written to performa inner join as per instructions.
index   time	"GDOT_RETURNS"	"PYPL_RETURNS"	"GS_RETURNS"	"SQ_RETURNS"
0	2016-12-16 00:00:00.000000	-0.023218	-0.005564	-0.016708	0.017339
1	2016-12-19 00:00:00.000000	-0.007923	0.003306	0.000795	-0.001043
2	2016-12-20 00:00:00.000000	0.001261	0.007351	0.016602	0.009053
3	2016-12-21 00:00:00.000000	0.001679	0.008807	-0.006911	-0.007591
4	2016-12-22 00:00:00.000000	0.006077	-0.010227	-0.005178	-0.023644
![image](https://user-images.githubusercontent.com/85462153/128660798-ef740709-7da5-400d-93e0-10838a4ab61b.png)

The mean returns for each stock was then computed [using the .mean() function]:
GDOT_RETURNS"    0.001504
"PYPL_RETURNS"    0.001957
"GS_RETURNS"      0.000196
"SQ_RETURNS"      0.003300

Next the average daily returns provided by the etf_portfolio_returns DataFrame to calculate the annualized return for the portfolio. 
With trading_days = 252; annualized_etf_portfolio_returns = etf_portfolio_returns * trading_days
The cumulative returns for the portfolio was calculated using the cumprod function & then plotted using the hvplot fucntionality in  Jupyter Notebook

"GDOT_RETURNS"    1.001504
"PYPL_RETURNS"    1.003464
"GS_RETURNS"      1.003660
"SQ_RETURNS"      1.006972
![image](https://user-images.githubusercontent.com/85462153/128660784-ee03a296-efa0-441f-89e8-303ef6099327.png)

Finally the Viola library to deploy notebook as a web application. The output was copied into a word file & is part of the final uploads to Github 
