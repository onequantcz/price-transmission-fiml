# Agricultural Price Transmission Analysis
Investigating shock propagation across the Czech flour supply chain using ECM and simultaneous equation models

## Motivation
Price changes in agricultural markets rarely affect all participants equally. A shock originating at the farm level may be amplified, delayed or partially absorbed before reaching processors and final consumers. 
Traditional approaches often model price transmission as a one-directional process: producer -> processor -> customer. However, real markets are characterized by a lot of factors, not always observable, and prices may be determined simultaneously rather than sequentially. 

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

## ECM results
The ECM analysis revealed statistically significant short-run and long-run relationships across all levels of the pricing chain. Table with ECM model estimated parameters below

<img width="1126" height="327" alt="image" src="https://github.com/user-attachments/assets/bbae7002-b7a2-48e0-afc7-1cd97f80d039" />

Based on those models was built a prediction interval for short period of time for significance level of 5%

<img width="333" height="298" alt="image" src="https://github.com/user-attachments/assets/316d91c9-98f6-456f-9b1f-0eb06b8221b2" /><img width="334" height="301" alt="image" src="https://github.com/user-attachments/assets/a347c8a6-d30c-4017-991b-44bd0de35185" /><img width="329" height="297" alt="image" src="https://github.com/user-attachments/assets/52d9cf08-5d00-4186-943a-5abbdcaa761f" />



### Short-Run Dynamics
Consumer prices (SC) respond strongly to changes in agricultural producer prices (CZV), with an estimated elasticity of 0.85. This indicates that agricultural price shocks are transmitted rapidly to final consumers, although the coefficient below one suggests partial shock absorption within the processing sector. Price shock absorbtion effect is clearly visible with normalized price data, below

<img width="483" height="453" alt="image" src="https://github.com/user-attachments/assets/22085a84-c3f3-4005-9539-4e73fc306e36" />


The processing sector (CPV) acts as a transmission hub. Changes in agricultural prices significantly affect processor prices (0.17), while energy prices also play an important role in explaining short-run fluctuations.
Agricultural producer prices exhibit strong feedback effects from downstream markets. The elasticity of agricultural prices with respect to consumer prices reaches 0.85, suggesting that demand-side signals are transmitted back to primary producers.

Across all equations, lagged variables and error-correction mechanisms indicate the presence of dynamic adjustment processes and short-run price corrections.

### Long-Run Dynamics
Long-run elasticities were derived from the ECM specification and represent equilibrium relationships between the different levels of the pricing chain, table below

<img width="1024" height="320" alt="image" src="https://github.com/user-attachments/assets/bbb9c955-b218-4b95-94e2-5b5eebf29de9" />

Consumer prices remain strongly linked to agricultural producer prices, with an estimated long-run elasticity of 1.04. This suggests that agricultural price changes are transmitted almost proportionally to the retail market in equilibrium.

The strongest relationships, however, appear in the reverse direction. Agricultural producer prices exhibit substantial long-run responses to both consumer prices (1.14) and industrial producer prices (1.38). These results indicate that price signals originating in downstream markets are eventually transmitted back to primary producers.

Industrial producer prices occupy an intermediate position within the system. While their dependence on agricultural prices is relatively modest (0.12), they remain connected to both upstream and downstream markets and therefore act as a transmission channel between production and final consumption.

To quantify the speed of adjustment, shock persistence was evaluated using the half-life measure. Consumer prices and agricultural producer prices exhibit very rapid adjustment dynamics, with estimated half-lives of approximately 0.42 and 0.51 periods, respectively. In practical terms, roughly half of a price shock is absorbed within less than one observation period.

Taken together, the estimated elasticities do not support the interpretation of the supply chain as a simple one-directional pricing mechanism. Instead, the results suggest a system of simultaneous price determination characterized by feedback effects and mutual dependence between all market levels.


## FIML Estimation
The ECM analysis suggested the presence of endogenous feedback relationships between agricultural producer prices, industrial producer prices and consumer prices. To account for these interactions, the pricing system was reformulated as a structural system of simultaneous equations and estimated using Full Information Maximum Likelihood (FIML).

The structural specification was not chosen arbitrarily. Restrictions imposed on the system were derived from the economic hypotheses developed and tested in the previous ECM analysis. The resulting system therefore combines both statistical evidence and economic theory regarding the structure of price transmission within the supply chain.

Under multivariate normality, FIML provides consistent and asymptotically efficient parameter estimates while accounting for the entire covariance structure of the system. Unlike equation-by-equation estimation, all parameters are estimated jointly, allowing endogenous relationships to be identified within a unified framework.

Because the likelihood function has no closed-form analytical solution, parameter estimation was performed using MLE-based gradient decent, accelerated by a Nesterov momentum. The optimization procedure exhibited stable convergence for both unrestricted and restricted model specifications, see below

<img width="499" height="255" alt="image" src="https://github.com/user-attachments/assets/30dd8c0d-e88d-4d46-b5b7-7c2b85cb0ed3" /><img width="469" height="261" alt="image" src="https://github.com/user-attachments/assets/5e229335-16b1-4817-82de-b9b67ac31ab3" />

Several economically consistent specifications were evaluated and compared using likelihood-based criteria.The unrestricted model was first estimated using all relationships suggested by the structural system. Alternative specifications were then constructed by retaining only statistically significant transmission channels identified during the previous ECM analysis. Model comparison was performed using the Likelihood Ratio (LR) test. The LR test rejected the null hypothesis that the additional restrictions were valid (p = 0.015), indicating that the restricted specification provides a statistically different representation of the pricing system.

Structural form of estimated parameters:

<img width="295" height="146" alt="image" src="https://github.com/user-attachments/assets/d264d972-67be-48ed-a556-c2ec76445fc0" />
<img width="1089" height="228" alt="image" src="https://github.com/user-attachments/assets/7dcb04c7-2549-4525-8bc2-5292a08d0bf3" />

Reduced form:

<img width="1092" height="255" alt="image" src="https://github.com/user-attachments/assets/03f6d80a-ee01-45d9-bee6-c289844ebf38" />

The strongest structural relationships are observed between agricultural and consumer prices, providing evidence that price transmission is not purely one-directional. Instead, downstream market conditions affect upstream producers, while producer prices simultaneously influence final consumer prices.

Energy prices emerge as the dominant cost-side driver within the system, exerting strong positive effects on both industrial and consumer prices. In contrast, expansion of crop areas reduces agricultural prices, reflecting the expected supply-side mechanism.

## Shock Propagation Analysis
To investigate how shocks propagate throughout the system, the Leontief inverse matrix was derived:

<img width="514" height="190" alt="image" src="https://github.com/user-attachments/assets/82ae9e1f-226f-4842-b6aa-5c79c60e4ca3" />

The results indicate that the processing sector (CPV) acts as the primary transmission hub of the entire pricing system. It exhibits the largest column sum within the Leontief matrix, implying that shocks originating in the processing sector generate the strongest system-wide responses.

Agricultural producer prices (CZV) display the largest row sum, indicating that they are the most responsive component of the system and absorb a substantial share of shocks generated elsewhere in the supply chain.

Consumer prices (SC) exhibit a stabilizing role. While they respond to shocks originating in other sectors, they also contribute to the correction of system-wide disequilibria through the error-correction mechanism.

Overall, the evidence suggests that the Czech flour market is best characterized as an industry-driven pricing system in which the processing sector acts as the central transmission node, agricultural prices absorb a large proportion of system shocks, and consumer prices contribute to long-run stabilization.


















