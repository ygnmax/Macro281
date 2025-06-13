## Idea 1: The Spatial Asset Pricing
The paper [Monetary Policy, Redistribution,
and Risk Premia](https://onlinelibrary.wiley.com/doi/full/10.3982/ECTA18014) and [Financial Heterogeneity and the Investment Channel of Monetary Policy](https://onlinelibrary.wiley.com/doi/full/10.3982/ECTA15949) emphasize the impact of the monetary policy shock on household investment or firm investment through the heterogeneous agent scope. This research pattern (an aggregated shock with heterogeneuous response) leads me to think of the spatial heterogeneities: different places respond to the aggregated risk differently. Locations could affect firm risk through (i) production cost (local factor prices) and (ii) cash flow (local consumption and services).

 Some intuitions are following: On the one hand, the firms located in the place with higher exposure to the aggregate shock will face more procyclical production factor price (such as office/plants rent and local wage). On the other hand, the households living in the place with higher exposure to the aggregate shock will have more counter-cyclical consumption (because this aggregate shock could turn to the income shock and households want to smooth the consumption over them), and in the end, they will become cash flow shocks for firms. How the trade-off between these two forces affect the asset price is unclear to me. 

For the exploration purpose, it would be interesting to check whether the location pattern mentioned above exists. First, I need to construct the local risk measure. By following the literature ([Local Risk, Local Factors, and Asset Prices](https://onlinelibrary.wiley.com/doi/full/10.1111/jofi.12465)), it could be *the average of the GDP betas of the industries operating in that area, weighted by the employment share of the industries.* Then this local risk measure is the RHS variable, and the LHS variable could be the local wages from Census Data, local consumption from the SafeGraph Spend Dataset, local Housing Price/Office Rent from the Compstak Data. If the sign of consumption does differ from that of the wages and office rent, then it is worthwhile to enter the firm level  analysis. The next step could be exploring whether firms' beta and firms' equity return (LHS variables) is explained by these local risks.

## Juan's thoughts.

I tried to follow this idea but I struggled to see specifically what you are proposing to do.


## Idea 2: The real effect of financial market on firm investment
According to the paper [Financial Heterogeneity and the Investment Channel of Monetary Policy](https://onlinelibrary.wiley.com/doi/full/10.3982/ECTA15949), the aggregate shock, such as monetary policy shock, influences firm investment decision through the default risk. More generally speaking, these financial frictions, such as default and limit of financing, are directly related to the stock prices. Although many activities in the financial sector occurs in secondary financial markets, where securities are traded among investors without capital flowing to firms, the financial market could have a real effect due to the transmission of information in the price.

It would be interesting for me to (i) measure the financial shock to individual firms through the stock returns and corporate bond returns and (ii) investigate how the firm investments differently respond to the stock returns and corporate bond returns and (iii) how these different responses aggregate to the macro level investment responses to shock to the firm asset prices.




For (i), the stock price data could be from CRSP and the corporate bond price data could be from TRACE, then the financial shock can be the average of these two returns weighted by the market value of the outstanding equity and debt. Τhis is a firm-time panel dataset. For (ii), the firm-level investment can be from the Compustats from quarterly report and this is also a firm-time panel dataset. The LHS variable is the investment, the RHS variable is the financial shock. If the reponse coefficients are significant and heterogenuous (in terms of the industries, banking relationship, or other dimensions), then it is interesting to investigate which channel matters for this real effect: Are firm managers learning from the market price to adapt their investment decisions? To what extent that the secondary market prices influence the primary market conditions and the capital flow to firm?
For (iii), it is interesting to set up a model with good market and financial market with the feed back mechanism as suggested in [The Real Effects of Financial Markets](https://academic.oup.com/rof/article-abstract/27/1/1/6659542?redirectedFrom=fulltext).

## Juan's thoughts.

I'm concerned that changes in stock returns are going to reflect reverse causality: changes in the expectations of market participants about the investment opportunities of the firm.
