# AlgorithmicTrading
This repository contains 3 projects: 
1. Equal-Weight S&P Index Fund:
   - This is a pretty simple project where the input is a simple list of details about various stocks(taken from the excel sheet provided in this          folder itself) and the total amount that the user wants to invest and the output is the amount of shares that the user should buy for each stock. As you might have seen in the name that the name of the project is Equal-Weight S&P Index fund, so we assume that all the stocks have equal weight. So, these are the high level steps done in this project: 
     - Read the csv file sp_500_stocks.csv which has the list of all the tickers(short abbreviation of stock names, like Apple stock is                      AAPL)
     - Create a datframe which contains of the following fields: 'Ticker','Stock Price', 'Market Capitalization','Number of Shares to                       Buy'. These will be the row headers of our resultant excel file.
     - Initialize the IEX_CLOUD_API token, we will be using the APIs exposed by IEX_CLOUD_API(the free one which gives random values for                     details of a stock, the real one is paid).
     - Parse the csv file mentioned in step 'a' and parse the stock tickers, then make a call to the IEX_CLOUD_API with a chunk of the                       tickers to get the details of the corresponding stock
     - Parse the output from the API and fill in the dataframe with the values 'Ticker', 'Share Price' and 'Market Capitalization'. For                     the field 'Number of Shares to Buy' we set all the cells of this column to 'N/A' as the values of this column is based upon the                       user input
     - We take as input the total amount the user wants to invest
     - As all the stocks have equal weight, hence the amount to be invested in each stock(position size) is equal to the total amount the                   user wants to invest divided by the total number of shares available(which is 505)
     - Now in step 'g' we have calculated the total amount to be invested in each stock, thus, we divide the amount to be invested in                       each stock by the share value of that stock to get the number of shares to buy for each stock.
     - We then populate the dataframe with the number of shares to buy for each stock
     - We finally convert this dataframe to an excel file('Recommended Trades') which is ready for download
                
3. Quantitative Momentum Investing Strategy
4. Quantitative Value Investing Strategy

These codes are done as part of the tutorial provided by free code camp on algorithmic trading.
Youtube link: https://youtu.be/xfzGZB4HhEE

