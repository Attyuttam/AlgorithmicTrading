# AlgorithmicTrading
This repository contains 3 projects: 
1. Equal-Weight S&P Index Fund:
   - This is a pretty simple project where the input is a simple list of details about various stocks(taken from the excel sheet provided in this          folder itself) and the total amount that the user wants to invest and the output is the amount of shares that the user should buy for each stock. As you might have seen in the name that the name of the project is Equal-Weight S&P Index fund, so we assume that all the stocks have equal weight. So, these are the high level steps done in this project: 
     - Read the csv file sp_500_stocks.csv which has the list of all the tickers(short abbreviation of stock names, like Apple stock is                      AAPL)
     - Create a datframe which contains of the following fields: 'Ticker','Stock Price', 'Market Capitalization','Number of Shares to                       Buy'. These will be the row headers of our resultant excel file.
     - Initialize the IEX_CLOUD_API token, we will be using the APIs exposed by IEX_CLOUD_API(the free one which gives random values for                     details of a stock, the real one is paid).
     - Parse the csv file mentioned in step 1 and parse the stock tickers, then make a call to the IEX_CLOUD_API with a chunk of the                       tickers to get the details of the corresponding stock
     - Parse the output from the API and fill in the dataframe with the values 'Ticker', 'Share Price' and 'Market Capitalization'. For                     the field 'Number of Shares to Buy' we set all the cells of this column to 'N/A' as the values of this column is based upon the                       user input
     - We take as input the total amount the user wants to invest
     - As all the stocks have equal weight, hence the amount to be invested in each stock(position size) is equal to the total amount the                   user wants to invest divided by the total number of shares available(which is 505)
     - Now in step 7 we have calculated the total amount to be invested in each stock, thus, we divide the amount to be invested in                       each stock by the share value of that stock to get the number of shares to buy for each stock.
     - We then populate the dataframe with the number of shares to buy for each stock
     - We finally convert this dataframe to an excel file('Recommended Trades') which is ready for download
                
2. Quantitative Momentum Investing Strategy
   - In this project, we are not just dividing the portfolio size by the price of each share to get the number of stocks to buy but here, we find out the 50 most valuable stocks to buy on the basis of their collective performance in one year, six month, three month and one month. So the steps we follow to achieve this is as (NOTE: I am skipping the part where we attach IEX_CLOUD_TOKEN etc as we have already discussed that in the first project):
      - Import the necessary libraries
      - Get all the stock tickers from the excel that we have. 
      - We create a data frame with the columns:  
         - 'Ticker',
         - 'Price',
         - 'Number of shares to buy',
         - 'One-year price return',
         - 'One-year return percentile',
         - 'Six-month price return',
         - 'Six-month return percentile',
         - 'Three-month price return',
         - 'Three-month return percentile',
         - 'One-month price return',
         - 'One-month return percentile',
         - 'HQM score'
      - The values for the one-year percent return and all the monthly percent returns are obtained from the stats API which I have mentioned in the notebook
      - We then fill up all the values that we have received from the API and leave all the rest as N/A
      - We then calculate the percentile for each time period(one year, six month, three month, one month) by using the stats method from scipy library
      - Then we calculate the HQM score or High Quality Momentum score which is essentially the mean of percentiles of all the available time periods, higher the HQM score, better performing is the stock
      - So, we then sort the dataframe on the basis of the HQM score to extract the 50 best performing stocks(Stocks with the highest HQM score).
      - We then put our resultant dataframe in an excel.
4. Quantitative Value Investing Strategy
   - In this project, we are using another technique to sort out the best 50 stocks (the weight of each and every stock is same as discussed previously). This technique is called the Value investing strategy, in this strategy, we pick out the stocks on the basis of their value which is dettermined by several paramters but the one used in this project are: 'Price-to-earnings ratio','Price-to-book ratio','Price-to-sales ratio','Enterprise value','Gross Profit' and 'EBITDA' which stands for Earnings Before Interest, Taxes, Depreciation, and Amortization and is a metric used to evaluate a company's operating performance. The steps are exactly similar to what we had done in the 2nd project, only the API used is different and in this project as there were lots of cells with 'None' value we did a basic data cleaning process.

These codes are done as part of the tutorial provided by free code camp on algorithmic trading.
Youtube link: https://youtu.be/xfzGZB4HhEE

