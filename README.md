# Challenge-7
The Directory for this respoitory is:
[Summary](https://github.com/mimisull/Challenge-7/blob/main/README.md)
[Code](https://github.com/mimisull/Challenge-7/blob/main/etf_analyzer.ipynb)
[Database](https://github.com/mimisull/Challenge-7/blob/main/etf.db)

**Proptech Consulting for SF realestate**

Specifically, I am building a tool to interact with a SQL database that can analyze different stocks in an ETF. This tool sorts, analyzes, and diagrams historical performance.

I accomplish this using data visualization skills, including aggregation, interactive visualizations, and the use of SQLAlchemy, to find trends in 4 stocks:['GDOT', 'GS', 'PYPL', 'SQ'].

*User Story*:
As a user, I need to determine what are good investment opportunities.

As a user, I need to be able to visualize trends in the ETF.

As a user, I need to have be able to store and sort through data in a database.

*Acceptance Criteria*:
Given that I’m unable to store data in excel files and go through them, I need to use this tool along with a SQL database.


## Usage
The project works by retrieving accurate data using open, high, low, close, volume, and daily_returns stats for each stock.

Imported the necessary tools with this code:

'''import numpy as np
import pandas as pd
import hvplot.pandas
import sqlalchemy
database_connection_string = 'sqlite:///etf.db'
engine = sqlalchemy.create_engine(database_connection_string)
engine.table_names()'''

Selected info with this:

'''query = """
SELECT * FROM PYPL;
"""
results = engine.execute(query)
pypl_dataframe = pd.read_sql_query(query, con=engine, index_col='time')
pypl_dataframe'''

'''query = """
SELECT time, close 
FROM PYPL
WHERE close > 200;
"""'''

'''query = """
SELECT time, daily_returns
FROM PYPL
ORDER BY daily_returns DESC
LIMIT 10;
"""'''

visualized with this:

'''pypl_dataframe.hvplot(y= 'daily_returns', x='time', figsize=(20,30), title='PYPL')'''
'''pypl_cumulative = (1 + pypl_dataframe['daily_returns']).cumprod()
pypl_cumulative.hvplot(ylabel= "return", x='time', figsize=(20,30), title='PYPL')'''

## Contributors
Michael Sullivan

Cal Berkeley Fintech 

Kevin Lee
