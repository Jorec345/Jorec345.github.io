---
layout: post
title: MARTINGALES APPROACH TO OPTIONS PRICING 
categories: [Financial markets, Financial engineering]
tags: [capital markets]
math: true
useMath: true
---
### MARTINGALES APPROACH TO OPTIONS PRICING

Building from the previous blog on options pricing, the most common method of pricing options has been Black-Scholes.

Despite laying a good foundation for pricing options, the Black-scholes model falls short in taking account of capturing market complexities and nuances.

The modern option pricing models and theories have come in to help fill these gaps and have also provided a foundation for understanding, risk management, hedging strategies and investment decisions.

To price options one needs to take account of the different elements that collectively come together to give us the value of the option. One of the key elements is the price of the underlying asset, the strike price (the exercise price), time to maturity, interest rates and dividends.

The price of the underlying asset is key because of the presence of volatility in the price of the underlying asset. The more volatile an asset, the more the opportunity of profit. However, profit and risk are positively correlated.

The strike price and the price of the underlying asset are key because they help in determining the intrinsic value of the option. For example, if the market price (price of the underlying asset) is more favorable then the option has an intrinsic value. 

Options are time dependent financial instrument, that is, their value diminishes as they approach their maturity. This is know as time decay and is more common when an option is out of the money.

- A longer time to maturity has a downside of having a higher premium, however, it also gives the underlying asset an opportunity to move more favorably.

The risk free interest rate are important because they influence the cost of carrying the underlying asset.

An upward increase in the interest rates increases the cost of holding an asset because, higher interest affects the premium paid on the option.

Dividends are a key consideration especially on stock options, because expected dividend payments can have a tremendous impact on the price of the underlying asset since they reduce asset's value.

One of the advanced mathematical that has emerged to offer more precise and adaptable models is the martingales.

##### Martingale
A martingales is a stochastic process where the conditional expectation of the next value is equivalent to the present value given all prior values.

Ordinarily this would be written as:

$$
\mathbb{E}[X_{t+1} \mid \mathcal{I}_t] = X_t
$$


Where:
- \(X_t\) represents the stochastic process at time \(t\).
- \({I}_t\) denotes all available information at a particula time \(t\).

Given a European call option with strike price \(K\), maturing at \(T\):

$$

   [
   C = e^{-rT} \mathbb{E}^{\mathbb{Q}}[(S_T - K)^+]
   ]

$$

   Where:
   - \(r\) is the risk-free interest rate.
   - \(S_T\) price of the asset at maturity.
   - \((S_T - K)^+\) this is the exercise price of the option.
   
$$
   [
   dS_t = rS_t dt + \sigma S_t dW_t^{\mathbb{Q}}
   ]
$$



   Here:
   - sigma is the standard deviation which represents the volatility of the stock.
   - W_t^{Q}} is a Wiener process under the risk-neutral measure.


This property is applicable in options pricing given the property that no arbitrage opportunities should exist for any players.

Martingales approach helps in development of models which incorporate the dynamics of asset prices.

This approach was mostly used for gambling since it helps amplify the chances of recovering from losing streaks.

It is often known as a risk-seeking method of investing with the notion that one cannot loose all the time and hence encourages an investor to increase their allocation of investment

The martingales approach is heavily reliant on the mean reversion theory which postulates that assets will eventually return to their long-term mean or average level.

This strategy is same as what is used in betting. It is often said that when one looses a bet, they often double the size of their next bet with the hope that they will eventually even out with a win. In a martingale system, this is actually true.

This assumes one has enough money to make enough bets until they finally even out, which is not always the case. In the case that one does not have the money, they may end up losing everything.

The Advantages of the martingale approach include:
- The martingales approach emphasizes on the no arbitrage opportunities.
- It gives a clear interpretation of probability by emphasizing on expectations under a transformed probability.


The draw backs of the martingale system when it comes to options trading include:
- The company go out of business before an investor finally evens out a win
- The risks are much higher than the rewards because the system proposes an increase in the investment with each loss
- There is a risk of losing everything with this approach.
- The market eventually revert to their mean, however the timelines are not predictable or defined.


#### Conclusion
The martingales approach provides an 'interesting' way to price options and other derivatives. It emphasizes on an arbitrage free market.  




