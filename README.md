# Business Analytics Toolbox Project: Technical Stock Analysis of FAANG Companies

Tableau Dashboard Link: https://public.tableau.com/views/BA775DashboardA10_17022275738370/FAANGPortfolioAnalysis?:language=en-US&:display_count=n&:origin=viz_share_link

## 1. Introduction & Motivation
### 1.1 Executive Report Summary
This portfolio analysis notebook offers a comprehensive evaluation of the performance and trends observed in the FAANG stocks—Apple, Facebook, Amazon, Netflix, and Google (Alphabet)—over the period spanning from 2008 to 2023. The analysis encompasses key financial metrics, technical indicators [1], and portfolio value trends, providing insights into market behavior and potential investment opportunities. Towards the end of the project, we delved into a few key findings using complex SQL queries and presented interesting visualization. Based on these findings, it was determined that all the stocks reached peak prices within the specified time frame, stabilizing towards the end. Notably, NFLX and META exhibited high volatility from 2011 to 2016, which relatively decreased during the COVID period. Additionally, there was a remarkable 300% growth in the average value of the FAANG portfolio data.

The comprehensive portfolio analysis dashboard evaluates the dynamics of FAANG stocks (Apple, Facebook, Amazon, Netflix, and Google/Alphabet) through a dual-layered approach. The first dashboard provides an overarching view of daily market movers, liquidity patterns, and long-term portfolio trends, offering investors strategic insights for navigating the ever-evolving tech landscape. Meanwhile, the second dashboard delves into the intricacies of technical analysis, employing indicators like OBV, MACD, AD, and RSI to uncover nuanced details on momentum, volatility, and trends. Through visualizations such as candle charts, MACD overlays, and volume indicators, investors can decipher market signals, empowering them to make informed decisions. The combined information from both dashboards equips users with a holistic understanding of FAANG stocks, enabling strategic investment decisions in an ever-changing financial landscape.

[1] Note:
The calculation queries of technical indicators, Relative Strength Index and Accumulation/Distribution, of other companies except Apple are added in the appendix (Section 8), as they are similar queries.

### 1.2 Problem Definition
We propose a dynamic dashboard for traders and asset managers, focused on FAANG stocks (Meta, Apple, Amazon, Netflix, Google) over the past decade. This interactive tool integrates stock prices and technical indicators, aiding in trend identification. Developed in the 1950s, these indicators offer valuable signals based on historical trading data. Our goal is to enable traders to visualize these patterns and identify trading opportunities.

The dynamic dashboard goes beyond just visualizations; it actively enables traders to identify market trends and potential entry/exit points by providing real-time insights. By using historical data and known technical indicators our dashboard can act as a comprehensive and sophisticated tool that is basically a decision support system to enhance trading strategies for traders.

Initially, we'll use 15 years of FAANG stock data as an MVP, with the potential to expand to other stocks based on client requirements. Our goal is to enable traders to visualize these patterns and identify trading opportunities for FAANG companies, with the potential to expand to other stocks based on client requirements.

In essence, our dynamic dashboard is designed keeping in mind the complexities of the stock market, making it an important asset for strategic decision making for traders.

### 1.3 Background & Motivation
We were motivated to build a comprehensive dashboard that showcases stock performances as a user-friendly tool for traders and asset managers. We feel this is important because traders often face the challenge of dealing with vast amounts of financial data from multiple sources, but the dynamic dashboard would streamline this process by consolidating the relevant stocks and reducing information overload. We want traders and asset managers to be able to conduct comprehensive analysis by integrating sotck prices and technical indicators, enable them to identify historical trends, and allow the dashboard to be used as a decision support tool for traders to validate their trading strategies, identify risks, and make more informed decisions. We are also motivated by this project as it will enhance our data extraction skills and help us to construct a financial tool. Those who are interested in trading by passion or profession would benefit greatly from reading our analysis as it dives into a myriad of questions that puzzle traders and our dashboard as well as our analysis provides deep insight into answering those questions.

### 1.4 Data + Data Source
The data source for this data set is [IEX Cloud Data](https://iexcloud.io/docs/core). We used the historical equity prices of the FAANG companies for the past decade, and merged them into one table. Each row represents a specific stock’s performance on a specific day. We also merged the historical technical indicators of FAANG companies into one table, with the intention of using JOINS later on.

As new stock data is available daily, we chose, as a convention, to conclude our analysis on November 11th, 2023.

(FYI, in case you need a token to access the dataset, pk_0dac8c928cb54cae8c9a6e3ac1932e5b can be used.)

The merged table of the historical equity prices of the FAANG companies consists of 16,221 rows and 21 columns. Each row in the table describes the stock prices of a particular company for each date for the past 15 years.
The merged table of the technical indicators consists of 16,112 rows and 33 columns. Each row in the table indicates the technical indicators value for a particular company for each date in the time period.

Data Dictionary:

close: Adjusted data for historical dates. Split adjusted only.

fclose: Fully adjusted for historical dates. Close price.

fhigh: Fully adjusted for historical dates. Highest price point in the day.

flow: Fully adjusted for historical dates. Lowest price point in the day.

fopen: Fully adjusted for historical dates. Open price.

fvolume: Fully adjusted for historical dates. Daily trading volume.

high: Adjusted data for historical dates. Split adjusted only.

low: Adjusted data for historical dates. Split adjusted only.

open: Adjusted data for historical dates. Split adjusted only.

priceDate: Associated symbol or ticker.

symbol: Unadjusted data for historical dates.

uclose: Unadjusted data for historical dates.

uhigh: Unadjusted data for historical dates.

ulow: Unadjusted data for historical dates.

uopen: Unadjusted data for historical dates.

uvolume: Unadjusted data for historical dates.

volume: Adjusted data for historical dates. Split adjusted only.

aroon_osc: Aroon Oscillator measures how recently a high or low has occurred; when >0, it indicates a recent high happened more recently than a recent low, suggesting an expected upward price trend.

macd_line: Moving Average Convergence Divergence (MACD) line represents the difference between short-term and long-term Exponential Moving Averages (EMAs), revealing potential trend reversals and indicating momentum strength in asset prices.

Signal_Line: Moving Average Convergence Divergence Signal line is a 9-day exponential moving average of the MACD indicator, employed in technical analysis to generate trading signals in financial markets.

MACD_Histogram: MACD Histogram visually depicts the difference between the MACD line and the signal line, serving as an indicator of momentum and potential trend reversals in financial markets.

Stochastic__K: Stochastic %K is a momentum indicator gauging the relative position of a closing price within a specified range over a defined period, offering insights into potential overbought or oversold market conditions.

Stochastic__D: Stochastic %D is a momentum indicator representing the three-day simple moving average of the Stochastic Oscillator, providing insight into the current closing price relative to the recent price range.

rsi: Relative Strength Index

thirty_day_rolling_avg: Thirty Days Rolling Average

ad: Accumulation/Distribution value

obv: On-Balance Volume
