# Agricultural Price Transmission Analysis
Investigating shock propagation across the Czech flour supply chain using ECM and simultaneous equation models

## Motivation
Price changes in agricultural markets rarely affect all participants equally. A shock originating at the farm level may be amplified, delayed or partially absorbed before reaching processors and final consumers. Traditional approaches often model price transmission as a one-directional process: producer -> processor -> customer. However, real markets are characterized by a lot of factors, not always observable, and prices may be determined simultaneously rather than sequentially. 
This project investigates the transmission of flour prices across the Czech agricultural supply chain, focusing on relationships between:
- Agricultural Producer Prices (CZV)
- Industrial Producer Prices (CPV)
- Consumer Prices (SC)

## Problem
Preliminary analysis based on cointegration and Error Correction Models (ECM) revealed significant relationships between all three market levels. However, these models do not fully address the possibility of endogenous feedback effects.
As a result, the pricing system cannot be viewed solely as a sequence of independent relationships. Instead, it must be treated as an interconnected structure in which shocks may propagate through multiple channels and affect all participants of the market.

## Methodology
The analysis was conducted in several stages. The objective was to move from simple statistical relationships toward a structural representation of the pricing system and its shock transmission mechanisms.

Raw Price Series -> Error Correction Models (ECM) -> Structural System Specification -> FIML Estimation -> Model Restrictions -> Likelihood Ratio Testing -> Shock Transmission Analysis

The ECM results were then used as a foundation for constructing a structural system of simultaneous equations. Following identification testing, the system was estimated using a custom Full Information Maximum Likelihood (FIML) estimator. Finally, restricted and unrestricted specifications were compared using likelihood ratio tests to evaluate the significance of individual transmission channels. 
