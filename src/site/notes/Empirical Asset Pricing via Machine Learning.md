---
{"dg-publish":true,"permalink":"/Empirical Asset Pricing via Machine Learning/","dgPassFrontmatter":true,"created":"2025-06-08T21:50:57.513+08:00"}
---



[Skip to Main Content](https://academic.oup.com/rfs/article/33/5/2223/#skipNav)

Journal Article

## Abstract

We perform a comparative analysis of machine learning methods for the canonical problem of empirical asset pricing: measuring asset risk premiums. We demonstrate large economic gains to investors using machine learning forecasts, in some cases doubling the performance of leading regression-based strategies from the literature. We identify the best-performing methods (trees and neural networks) and trace their predictive gains to allowing nonlinear predictor interactions missed by other methods. All methods agree on the same set of dominant predictive signals, a set that includes variations on momentum, liquidity, and volatility.

Authors have furnished an Internet Appendix, which is available on the Oxford University Press Web site next to the link to the final published paper online.

In this article, we conduct a comparative analysis of machine learning methods for finance. We do so in the context of perhaps the most widely studied problem in finance, that of measuring equity risk premiums.

Our primary contributions are twofold. First, we provide a new set of benchmarks for the predictive accuracy of machine learning methods in measuring risk premiums of the aggregate market and individual stocks. This accuracy is summarized two ways. The first is a high out-of-sample predictive $R2$ relative to preceding literature that is robust across a variety of machine learning specifications. Second, and more importantly, we demonstrate large economic gains to investors using machine learning forecasts. A portfolio strategy that times the S&P 500 with neural network forecasts enjoys an annualized out-of-sample Sharpe ratio of 0.77 versus the 0.51 Sharpe ratio of a buy-and-hold investor. And a value-weighted long-short decile spread strategy that takes positions based on stock-level neural network forecasts earns an annualized out-of-sample Sharpe ratio of 1.35, more than doubling the performance of a leading regression-based strategy from the literature.

Return prediction is economically meaningful. The fundamental goal of asset pricing is to understand the behavior of risk premiums.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">1</a></sup> If expected returns were perfectly observed, we would still need theories to explain their behavior and empirical analysis to test those theories. But risk premiums are notoriously difficult to measure: market efficiency *forces* return variation to be dominated by unforecastable news that obscures risk premiums. Our research highlights gains that can be achieved in prediction and identifies the most informative predictor variables. This helps resolve the problem of risk premium measurement, which then facilitates more reliable investigation into economic mechanisms of asset pricing.

Second, we synthesize the empirical asset pricing literature with the field of machine learning. Relative to traditional empirical methods in asset pricing, machine learning accommodates a far more expansive list of potential predictor variables and richer specifications of functional form. It is this flexibility that allows us to push the frontier of risk premium measurement. Interest in machine learning methods for finance has grown tremendously in both academia and industry. This article provides a comparative overview of machine learning methods applied to the two canonical problems of empirical asset pricing: predicting returns in the cross-section and time series. Our view is that the best way for researchers to understand the usefulness of machine learning in the field of asset pricing is to apply and compare the performance of each of its methods in familiar empirical problems.

The definition of “machine learning” is inchoate and is often context specific. We use the term to describe (a) a diverse collection of high-dimensional models for statistical prediction, combined with (b) so-called “regularization” methods for model selection and mitigation of overfit, and (c) efficient algorithms for searching among a vast number of potential model specifications.

The high-dimensional nature of machine learning methods (element (a) of this definition) enhances their flexibility relative to more traditional econometric prediction techniques. This flexibility brings hope of better approximating the unknown and likely complex data generating process underlying equity risk premiums. With enhanced flexibility, however, comes a higher propensity of overfitting the data. Element (b) of our machine learning definition describes refinements in implementation that emphasize stable out-of-sample performance to explicitly guard against overfit. Finally, with many predictors it becomes infeasible to exhaustively traverse and compare all model permutations. Element (c) describes clever machine learning tools designed to approximate an optimal specification with manageable computational cost.

A number of aspects of empirical asset pricing make it a particularly attractive field for analysis with machine learning methods.

First, two main research agendas have monopolized modern empirical asset pricing research. The first seeks to describe and understand differences in expected returns across assets. The second focuses on dynamics of the aggregate market equity risk premium. Measurement of an asset’s risk premium is fundamentally a problem of prediction—the risk premium is the conditional expectation of a future realized excess return. Machine learning, whose methods are largely specialized for prediction tasks, is thus ideally suited to the problem of risk premium measurement.

Second, the collection of candidate conditioning variables for the risk premium is large. The profession has accumulated a staggering list of predictors that various researchers have argued possess forecasting power for returns. The number of stock-level predictive characteristics reported in the literature numbers in the hundreds and macroeconomic predictors of the aggregate market number in the dozens.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">2</a></sup> Additionally, predictors are often close cousins and highly correlated. Traditional prediction methods break down when the predictor count approaches the observation count or predictors are highly correlated. With an emphasis on variable selection and dimension reduction techniques, machine learning is well suited for such challenging prediction problems by reducing degrees of freedom and condensing redundant variation among predictors.

Third, further complicating the problem is ambiguity about the functional forms through which the high-dimensional predictor sets enter into risk premiums. Should they enter linearly? If nonlinearities are needed, which form should they take? Must we consider interactions among predictors? Such questions rapidly proliferate the set of potential model specifications. The theoretical literature offers little guidance for winnowing the list of conditioning variables and functional forms. Three aspects of machine learning make it well suited for problems of ambiguous functional form. The first is its diversity. As a suite of dissimilar methods, it casts a wide net in its specification search. Second, with methods ranging from generalized linear models to regression trees and neural networks, machine learning is explicitly designed to approximate complex nonlinear associations. Third, parameter penalization and conservative model selection criteria complement the breadth of functional forms spanned by these methods in order to avoid overfit biases and false discovery.

We study a set of candidate models that are potentially well suited to address the three empirical challenges outlined above. They constitute the canon of methods one would encounter in a graduate level machine learning textbook.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">3</a></sup> This includes linear regression, generalized linear models with penalization, dimension reduction via principal components regression (PCR) and partial least squares (PLS), regression trees (including boosted trees and random forests), and neural networks. This is not an exhaustive analysis of all methods. For example, we exclude support vector machines as these share an equivalence with other methods that we study <sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">4</a></sup> and are primarily used for classification problems. Nonetheless, our list is designed to be representative of predictive analytics tools from various branches of the machine learning tool kit.

We conduct a large-scale empirical analysis, investigating nearly 30,000 individual stocks over 60 years from 1957 to 2016. Our predictor set includes 94 characteristics for each stock, interactions of each characteristic with eight aggregate time-series variables, and 74 industry sector dummy variables, totaling more than 900 baseline signals. Some of our methods expand this predictor set much further by including nonlinear transformations and interactions of the baseline signals. We establish the following empirical facts about machine learning for return prediction.

At the broadest level, our main empirical finding is that machine learning as a whole has the potential to improve our empirical understanding of asset returns. It digests our predictor data set, which is massive from the perspective of the existing literature, into a return forecasting model that dominates traditional approaches. The immediate implication is that machine learning aids in solving practical investments problems, such as market timing, portfolio choice, and risk management, justifying its role in the business architecture of the fintech industry.

Consider as a benchmark a panel regression of individual stock returns onto three lagged stock-level characteristics: size, book-to-market, and momentum. This benchmark has a number of attractive features. It is parsimonious and simple, and comparing against this benchmark is conservative because it is highly selected (the characteristics it includes are routinely demonstrated to be among the most robust return predictors). [Lewellen (2015)](https://academic.oup.com/rfs/article/33/5/2223/) demonstrates that this model performs about as well as larger and more complex stock prediction models studied in the literature.

In our sample, which is longer and wider (more observations in terms of both dates and stocks) than that studied in [Lewellen (2015)](https://academic.oup.com/rfs/article/33/5/2223/), the out-of-sample $R2$ from the benchmark model is 0.16% per month for the panel of individual stock returns. When we expand the ordinary least squares (OLS) panel model to include our set of 900+ predictors, predictability vanishes immediately, as evidenced by the $R2$ dropping deeply into negative territory. This is not surprising. With so many parameters to estimate, efficiency of OLS regression deteriorates precipitously and therefore produces forecasts that are highly unstable out of sample. This failure of OLS leads us to our next empirical fact.

Vast predictor sets are viable for linear prediction when either penalization or dimension reduction is used. Our first evidence that the machine learning tool kit aids in return prediction emerges from the fact that the “elastic net,” which uses parameter shrinkage and variable selection to limit the regression’s degrees of freedom, solves the OLS inefficiency problem. In the 900+ predictor regression, elastic net pulls the out-of-sample $R2$ into positive territory at 0.11% per month. Principal components regression (PCR) and partial least squares (PLS), which reduce the dimension of the predictor set to a few linear combinations of predictors, further raise the out-of-sample $R2$ to 0.26% and 0.27%, respectively. This is in spite of the presence of many likely “fluke” predictors that contribute pure noise to the large model. In other words, the high-dimensional predictor set in a simple linear specification is at least competitive with the status quo low-dimensional model, as long as overparameterization can be controlled.

Next, we expand the model to accommodate nonlinear predictive relationships via generalized linear models, regression trees, and neural networks. Allowing for nonlinearities substantially improves predictions. We find that trees and neural networks unambiguously improve return prediction with monthly stock-level $R2$ ’s between 0.33% and 0.40%. But the generalized linear model, which introduces nonlinearity via spline functions of each individual baseline predictor (but with no predictor interactions), fails to robustly outperform the linear specification. This suggests that allowing for (potentially complex) interactions among the baseline predictors is a crucial aspect of nonlinearities in the expected return function. As part of our analysis, we discuss why generalized linear models are comparatively poorly suited for capturing predictor interactions.

Shallow learning outperforms deeper learning. When we consider a range of neural networks from very shallow (a single hidden layer) to deeper networks (up to five hidden layers), we find that neural network performance peaks at three hidden layers then declines as more layers are added. Likewise, the boosted tree and random forest algorithms tend to select trees with few “leaves” (on average less than six leaves) in our analysis. This is likely an artifact of the relatively small amount of data and tiny signal-to-noise ratio for our return prediction problem, in comparison to the kinds of nonfinancial settings in which deep learning thrives thanks to astronomical data sets and strong signals (such as computer vision).

The distance between nonlinear methods and the benchmark widens when predicting portfolio returns. We build bottom-up portfolio-level return forecasts from the stock-level forecasts produced by our models. Consider, for example, bottom-up forecasts of the S&P 500 portfolio return. By aggregating stock-level forecasts from the benchmark three-characteristic OLS model, we find a monthly S&P 500 predictive $R2$ of $−0.22%$ ⁠. The bottom-up S&P 500 forecast from the generalized linear model, in contrast, delivers an $R2$ of $0.71%$ ⁠. Trees and neural networks improve upon this further, generating monthly out-of-sample $R2$ ’s between 1.08% to 1.80% per month. The same pattern emerges for forecasting a variety of characteristic factor portfolios, such as those formed on the basis of size, value, investment, profitability, and momentum. In particular, a neural network with three layers produces a positive out-of-sample predictive $R2$ for *every* factor portfolio we consider.

More pronounced predictive power at the portfolio level versus the stock level is driven by the fact that individual stock returns behave erratically for some of the smallest and least liquid stocks in our sample. Aggregating into portfolios averages out much of the unpredictable stock-level noise and boosts the signal strength, which helps in detecting the predictive gains from machine learning.

The economic gains from machine learning forecasts are large. Our tests show clear *statistical* rejections of the OLS benchmark and other linear models in favor of nonlinear machine learning tools. The evidence for *economic* gains from machine learning forecasts—in the form of portfolio Sharpe ratios—are likewise impressive. For example, an investor who times the S&P 500 based on bottom-up neural network forecasts enjoys a 26-percentage-point increase in annualized out-of-sample Sharpe ratio, to 0.77, relative to the 0.51 Sharpe ratio of a buy-and-hold investor. And when we form a long-short decile spread directly sorted on stock return predictions from a neural network, the strategy earns an annualized out-of-sample Sharpe ratio of 1.35 (value-weighted) and 2.45 (equal-weighted). In contrast, an analogous long-short strategy using forecasts from the benchmark OLS model delivers Sharpe ratios of 0.61 and 0.83, respectively.

The most successful predictors are price trends, liquidity, and volatility. All of the methods we study produce a very similar ranking of the most informative stock-level predictors, which fall into three main categories. First, and most informative of all, are price trend variables including stock momentum, industry momentum, and short-term reversal. Next are liquidity variables including market value, dollar volume, and bid-ask spread. Finally, return volatility, idiosyncratic volatility, market beta, and beta squared are also among the leading predictors in all models we consider.

Simulation offers a better understanding of our machine learning findings. In [Internet Appendix A](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA), we perform Monte Carlo simulations that support the above interpretations of our analysis. We apply machine learning to simulated data from two different data generating processes. Both produce data from a high dimensional predictor set. But in one, individual predictors enter only linearly and additively, while in the other predictors can enter through nonlinear transformations and via pairwise interactions. When we apply our machine learning repertoire to the simulated data sets, we find that linear and generalized linear methods dominate in the linear and uninteracted setting, yet tree-based methods and neural networks significantly outperform in the nonlinear and interactive setting.

Machine learning has great potential for improving risk premium *measurement*, which is fundamentally a problem of prediction. It amounts to best approximating the conditional expectation $E(ri,t+1|Ft)$ ⁠, where $ri,t+1$ is an asset’s return in excess of the risk-free rate, and $Ft$ is the true and unobservable information set of market participants. This is a domain in which machine learning algorithms excel.

But these improved predictions are *only* measurements. The measurements do not tell us about economic *mechanisms* or *equilibria*. Machine learning methods on their own do not identify deep fundamental associations among asset prices and conditioning variables. When the objective is to understand economic mechanisms, machine learning still may be useful. It requires the economist to add structure—to build a hypothesized mechanism into the estimation problem—and decide how to introduce a machine learning algorithm subject to this structure. A nascent literature is marrying machine learning to equilibrium asset pricing (e.g., [Kelly, Pruitt, and Su 2019](https://academic.oup.com/rfs/article/33/5/2223/); [Gu, Kelly, and Xiu 2019](https://academic.oup.com/rfs/article/33/5/2223/); [Feng, Giglio, and Xiu forthcoming](https://academic.oup.com/rfs/article/33/5/2223/)), and this remains an exciting direction for future research.

Our work extends the empirical literature on stock return prediction, which comes in two basic strands. The first strand models differences in expected returns across stocks as a function of stock-level characteristics, and is exemplified by [Fama and French (2008)](https://academic.oup.com/rfs/article/33/5/2223/) and [Lewellen (2015)](https://academic.oup.com/rfs/article/33/5/2223/). The typical approach in this literature runs cross-sectional regressions <sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">5</a></sup> of future stock returns on a few lagged stock characteristics. The second strand forecasts the time series of returns and is surveyed by [Welch and Goyal (2008)](https://academic.oup.com/rfs/article/33/5/2223/), [Koijen and Nieuwerburgh (2011)](https://academic.oup.com/rfs/article/33/5/2223/), and [Rapach and Zhou (2013)](https://academic.oup.com/rfs/article/33/5/2223/). This literature typically conducts time-series regressions of broad aggregate portfolio returns on a small number of macroeconomic predictor variables.

These traditional methods have potentially severe limitations that more advanced statistical tools in machine learning can help overcome. Most important is that regressions and portfolio sorts are ill-suited to handle the large numbers of predictor variables that the literature has accumulated over five decades. The challenge is how to assess the incremental predictive content of a newly proposed predictor while jointly controlling for the gamut of extant signals (or, relatedly, handling the multiple comparisons and false discovery problem). Our primary contribution is to demonstrate potent return predictability that is harnessable from the large collection of existing variables when machine learning methods are used.

Machine learning methods have sporadically appeared in the asset pricing literature. [Rapach, Strauss, and Zhou (2013)](https://academic.oup.com/rfs/article/33/5/2223/) apply lasso to predict global equity market returns using lagged returns of all countries. Several papers apply neural networks to forecast derivatives prices ([Hutchinson, Lo, and Poggio 1994](https://academic.oup.com/rfs/article/33/5/2223/); [Yao, Li, and Tan 2000](https://academic.oup.com/rfs/article/33/5/2223/), among others). [Khandani, Kim, and Lo (2010)](https://academic.oup.com/rfs/article/33/5/2223/) and [Butaru et al. (2016)](https://academic.oup.com/rfs/article/33/5/2223/) use regression trees to predict consumer credit card delinquencies and defaults. [Sirignano, Sadhwani, and Giesecke (2016)](https://academic.oup.com/rfs/article/33/5/2223/) estimate a deep neural network for mortgage prepayment, delinquency, and foreclosure. [Heaton, Polson, and Witte (2016)](https://academic.oup.com/rfs/article/33/5/2223/) develop a neural network for portfolio selection.

Recently, variations of machine learning methods have been used to study the cross-section of stock returns. [Harvey and Liu (2016)](https://academic.oup.com/rfs/article/33/5/2223/) study the multiple comparisons problem using a bootstrap procedure. [Giglio and Xiu (2016)](https://academic.oup.com/rfs/article/33/5/2223/) and [Kelly, Pruitt, and Su (2019)](https://academic.oup.com/rfs/article/33/5/2223/) use dimension reduction methods to estimate and test factor pricing models. [Moritz and Zimmermann (2016)](https://academic.oup.com/rfs/article/33/5/2223/) apply tree-based models to portfolio sorting. [Kozak, Nagel, and Santosh (2020)](https://academic.oup.com/rfs/article/33/5/2223/) and [Freyberger, Neuhierl, and Weber (2020)](https://academic.oup.com/rfs/article/33/5/2223/) use shrinkage and selection methods to, respectively, approximate a stochastic discount factor and a nonlinear function for expected returns. The focus of our paper is to simultaneously explore a wide range of machine learning methods to study the behavior of expected stock returns, with a particular emphasis on comparative analysis among methods.

## 1\. Methodology

This section describes the collection of machine learning methods that we use in our analysis. In each subsection we introduce a new method and describe it in terms of its three fundamental elements. First is the statistical model describing a method’s general functional form for risk premium predictions. The second is an objective function for estimating model parameters. All of our estimates share the basic objective of minimizing mean squared predictions error (MSE). Regularization is introduced through variations on the MSE objective, such as adding parameterization penalties and robustification against outliers. These modifications are designed to avoid problems with overfit and improve models’ out-of-sample predictive performance. Finally, even with a small number of predictors, the set of model permutations expands rapidly when one considers nonlinear predictor transformations. This proliferation is compounded in our already high dimension predictor set. The third element in each subsection describes computational algorithms for efficiently identifying the optimal specification among the permutations encompassed by a given method.

As we present each method, we aim to provide a sufficiently in-depth description of the *statistical model* so that a reader having no machine learning background can understand the basic model structure without needing to consult outside sources. At the same time, when discussing the *computational methods* for estimating each model, we are deliberately terse. There are many variants of each algorithm, and each has its own subtle technical nuances. To avoid bogging down the reader with programming details, we describe our specific implementation choices in [Internet Appendix B](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) and refer readers to original sources for further background. [Internet Appendix C](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) summarizes the literature on statistical properties of each estimator.

In its most general form, we describe an asset’s excess return as an additive prediction error model:

(1)

where

(2)

Stocks are indexed as $i=1,...,Nt$ and months by $t=1,...,T$ ⁠. For ease of presentation, we assume a balanced panel of stocks, and defer the discussion on missing data to Section . Our objective is to isolate a representation of $Et(ri,t+1)$ as a function of predictor variables that maximizes the out-of-sample explanatory power for realized $ri,t+1$ ⁠. We denote those predictors as the $P$ -dimensional vector $zi,t$ ⁠, and assume the conditional expected return $g⋆(⋅)$ is a flexible function of these predictors.

Despite its flexibility, this framework imposes some important restrictions. The $g⋆(⋅)$ function depends neither on $i$ nor $t$ ⁠. By maintaining the same form over time and across different stocks, the model leverages information from the entire panel and lends stability to estimates of risk premiums for any individual asset. This contrasts with standard asset pricing approaches that reestimate a cross-sectional model each time period, or that independently estimate time-series models for each stock. Also, $g⋆(⋅)$ depends on $z$ only through $zi,t$ ⁠. This means our prediction does not use information from the history prior to $t$ ⁠, or from individual stocks other than the $i$ th.

### 1.1 Sample splitting and tuning via validation

Important preliminary steps (prior to discussing specific models and regularization approaches) are to understand how we design disjoint subsamples for estimation and testing and to introduce the notion of “hyperparameter tuning.”

The regularization procedures discussed below, which are machine learning’s primary defense against overfitting, rely on a choice of hyperparameters (or, synonymously, “tuning parameters”). These are critical to the performance of machine learning methods as they control model complexity. Hyperparameters include, for example, the penalization parameters in lasso and elastic net, the number of iterated trees in boosting, the number of random trees in a forest, and the depth of the trees. In most cases, there is little theoretical guidance for how to “tune” hyperparameters for optimized out-of-sample performance.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">6</a></sup>

We follow the most common approach in the literature and select tuning parameters adaptively from the data in a validation sample. In particular, we divide our sample into three disjoint time periods that maintain the temporal ordering of the data. The first, or “training,” subsample is used to estimate the model subject to a specific set of tuning parameter values.

The second, or “validation,” sample is used for tuning the hyperparameters. We construct forecasts for data points in the validation sample based on the estimated model from the training sample. Next, we calculate the objective function based on forecast errors from the validation sample, and iteratively search for hyperparameters that optimize the validation objective (at each step reestimating the model from the training data subject to the prevailing hyperparameter values).

Tuning parameters are chosen from the validation sample taking into account estimated parameters, but the parameters are estimated from the training data alone. The idea of validation is to simulate an out-of-sample test of the model. Hyperparameter tuning amounts to searching for a degree of model complexity that tends to produce reliable out-of-sample performance. The validation sample fits are of course not truly out of sample, because they are used for tuning, which is in turn an input to the estimation. Thus, the third, or “testing,” subsample, which is used for neither estimation nor tuning, is truly out of sample and thus is used to evaluate a method’s predictive performance. [Internet Appendix D](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) provides further details for our sample splitting scheme, and [Internet Appendix E](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) summarizes the hyperparameter tuning schemes for each model.

### 1.2 Simple linear

We begin our model description with the least complex method in our analysis, the simple linear predictive regression model estimated via ordinary least squares (OLS). Although we expect this to perform poorly in our high dimension problem, we use it as a reference point for emphasizing the distinctive features of more sophisticated methods.

The simple linear model imposes that conditional expectations $g⋆(⋅)$ can be approximated by a linear function of the raw predictor variables and the parameter vector, $θ$ ⁠,

(3)

This model imposes a simple regression specification and does not allow for nonlinear effects or interactions between predictors.

Our baseline estimation of the simple linear model uses a standard least squares, or “ $l2$ ⁠,” objective function:

(4)

Minimizing $L(θ)$ yields the pooled OLS estimator. The convenience of the baseline $l2$ objective function is that it offers analytical estimates and thus avoids sophisticated optimization and computation.

#### 1.2.1 Extension: Robust objective functions

In some cases, replacing Equation () with a weighted least squares objective, such as

(5)

can possibly improve the predictive performance. This weighted least squares objective allows the econometrician to tilt estimates toward observations that are more statistically or economically informative. For example, one variation that we consider sets $wi,t$ inversely proportional to the number of stocks at time $t$ ⁠. This imposes that every month has the same contribution to the model regardless of how many stocks are available that month. This also amounts to equally weighting the squared loss of all stocks available at time $t$ ⁠. Another variation that we consider sets $wi,t$ proportional to the equity market value of stock $i$ at time $t$ ⁠. This value weighted loss function underweights small stocks in favor of large stocks, and is motivated by the economic rational that small stocks represent a large fraction of the traded universe by count while constituting a tiny fraction of aggregate market capitalization.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">7</a></sup>

Heavy tails are a well-known attribute of financial returns and stock-level predictor variables. Convexity of the least squares objective () places extreme emphasis on large errors, thus outliers can undermine the stability of OLS-based predictions. The statistics literature, long aware of this problem, has developed modified least squares objective functions that tend to produce more stable forecasts than OLS in the presence of extreme observations.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">8</a></sup> In the machine learning literature, a common choice for counteracting the deleterious effect of heavy-tailed observations is the Huber robust objective function, which is defined as

(6)

where

The Huber loss, $H(⋅)$ ⁠, is a hybrid of squared loss for relatively small errors and absolute loss for relatively large errors, where the combination is controlled by a tuning parameter, $ξ$ ⁠, that can be optimized adaptively from the data.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">9</a></sup>

Although this detour introduces robust objective functions in the context of the simple linear model, they are easily applicable in almost all the methods we study. In our empirical analysis, we study the predictive benefits of robust loss functions in multiple machine learning methods.

### 1.3 Penalized linear

The simple linear model is bound to fail in the presence of many predictors. When the number of predictors $P$ approaches the number of observations $T$ ⁠, the linear model becomes inefficient or even inconsistent.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">10</a></sup> It begins to overfit noise rather than extracting signal. This is particularly troublesome for the problem of return prediction where the signal-to-noise ratio is notoriously low.

Crucial for avoiding overfit is reducing the number of estimated parameters. The most common machine learning device for imposing parameter parsimony is to append a penalty to the objective function in order to favor more parsimonious specifications. This “regularization” of the estimation problem mechanically deteriorates a model’s in-sample performance in hopes that it improves its stability out of sample. This will be the case when penalization manages to reduce the model’s fit of noise, while preserving its signal fit.

The statistical model for our penalized linear model is the same as the simple linear model in Equation (). That is, it continues to consider only the baseline, untransformed predictors. Penalized methods differ by appending a penalty to the original loss function:

(7)

The elastic net involves two nonnegative hyperparameters, $λ$ and $ρ$ ⁠, and includes two well-known regularizers as special cases. The $ρ=0$ case corresponds to the lasso and uses an absolute value, or “ $l1$ ⁠,” parameter penalization. The fortunate geometry of the lasso sets coefficients on a subset of covariates to exactly zero. In this sense, the lasso imposes sparsity on the specification and can thus be thought of as a variable *selection* method. The $ρ=1$ case corresponds to ridge regression, which uses an $l2$ parameter penalization, that draws all coefficient estimates closer to zero but does not impose exact zeros anywhere. In this sense, ridge is a *shrinkage* method that helps prevent coefficients from becoming unduly large in magnitude. For intermediate values of $ρ$ ⁠, the elastic net encourages simple models through both shrinkage and selection.

We adaptively optimize the tuning parameters, $λ$ and $ρ$ ⁠, using the validation sample. Our implementation of penalized regression uses the accelerated proximal gradient algorithm and accommodates both least squares and Huber objective functions (see [Internet Appendix B.1](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) for more details).

### 1.4 Dimension reduction: PCR and PLS

Penalized linear models use shrinkage and variable selection to manage high dimensionality by forcing the coefficients on most regressors near or exactly to zero. This can produce suboptimal forecasts when predictors are highly correlated. A simple example of this problem is a case in which all of the predictors are equal to the forecast target plus an iid noise term. In this situation, choosing a subset of predictors via lasso penalty is inferior to taking a simple average of the predictors and using this as the sole predictor in a univariate regression.

The idea of predictor averaging, as opposed to predictor selection, is the essence of dimension reduction. Forming linear combinations of predictors helps reduce noise to better isolate the signal in predictors and helps decorrelate otherwise highly dependent predictors. Two classic dimension reduction techniques are principal components regression (PCR) and partial least squares (PLS).

PCR consists of a two-step procedure. In the first step, principal components analysis (PCA) combines regressors into a small set of linear combinations that best preserve the covariance structure among the predictors. In the second step, a few leading components are used in standard predictive regression. That is, PCR regularizes the prediction problem by zeroing out coefficients on low variance components.

A drawback of PCR is that it fails to incorporate the ultimate statistical objective—forecasting returns—in the dimension reduction step. PCA condenses data into components based on the covariation *among* the predictors. This happens prior to the forecasting step and without consideration of how predictors associate with future returns.

In contrast, partial least squares performs dimension reduction by directly exploiting covariation of predictors with the forecast target.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">11</a></sup> PLS regression proceeds as follows. For each predictor $j$ ⁠, estimate its univariate return prediction coefficient via OLS. This coefficient, denoted $φj$ ⁠, reflects the “partial” sensitivity of returns to each predictor $j$ ⁠. Next, average all predictors into a single aggregate component with weights proportional to $φj$ ⁠, placing the highest weight on the strongest univariate predictors, and the least weight on the weakest. In this way, PLS performs its dimension reduction with the ultimate forecasting objective in mind. To form more than one predictive component, the target and all predictors are orthogonalized with respect to previously constructed components, and the above procedure is repeated on the orthogonalized data set. This is iterated until the desired number of PLS components is reached.

Our implementation of PCR and PLS begins from the vectorized version of the linear model in Equations ()–(). In particular, we reorganize the linear regression $ri,t+1=zi,t′θ+ϵi,t+1$ as

(9)

where $R$ is the $NT×1$ vector of $ri,t+1$ ⁠, $Z$ is the $NT×P$ matrix of stacked predictors $zi,t$ ⁠, and $E$ is a $NT×1$ vector of residuals $ϵi,t+1$ ⁠.

PCR and PLS take the same general approach to reducing the dimensionality. They both condense the set of predictors from dimension $P$ to a much smaller number of $K$ linear combinations of predictors. Thus, the forecasting model for both methods is written as

(10)

$ΩK$ is $P×K$ matrix with columns $w1,w2,…,wK$ ⁠. Each $wj$ is the set of linear combination weights used to create the $j$ th predictive components, thus $ZΩK$ is the dimension-reduced version of the original predictor set. Likewise, the predictive coefficient $θK$ is now a $K×1$ vector rather than $P×1$ ⁠.

PCR chooses the combination weights $ΩK$ recursively. The $jth$ linear combination solves <sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">12</a></sup>

(11)

Intuitively, PCR seeks the $K$ linear combinations of $Z$ that most faithfully mimic the full predictor set. The objective illustrates that the choice of components is not based on the forecasting objective at all. Instead, the emphasis of PCR is on finding components that retain the most possible common variation within the predictor set. The well known solution for () computes $ΩK$ via singular value decomposition of $Z$ ⁠, and therefore the PCR algorithm is extremely efficient from a computational standpoint.

In contrast to PCR, the PLS objective seeks $K$ linear combinations of $Z$ that have maximal predictive association with the forecast target. The weights used to construct the $j$ th PLS component solve

(12)

This objective highlights the main distinction between PCR and PLS. PLS is willing to sacrifice how accurately $ZΩK$ approximates $Z$ in order to find components with more potent return predictability. The problem in () can be efficiently solved using a number of similar routines, the most prominent being the SIMPLS algorithm of [de Jong (1993)](https://academic.oup.com/rfs/article/33/5/2223/).

Finally, given a solution for $ΩK$ ⁠, $θK$ is estimated in both PCR and PLS via OLS regression of $R$ on $ZΩK$ ⁠. For both models, $K$ is a hyperparameter that can be determined adaptively from the validation sample.

### 1.5 Generalized linear

Intrinsic error is irreducible; it is the genuinely unpredictable component of returns associated with news arrival and other sources of randomness in financial markets. Estimation error, which arises due to sampling variation, is determined by the data. It is potentially reducible by adding new observations, though this may not be under the econometrician’s control. Approximation error is directly controlled by the econometrician and is potentially reducible by incorporating more flexible specifications that improve the model’s ability to approximate the true model. But additional flexibility raises the risk of overfitting and destabilizing the model out of sample. In this and the following subsections, we introduce nonparametric models of $g(⋅)$ with increasing degrees of flexibility, each complemented by regularization methods to mitigate overfit.

The first and most straightforward nonparametric approach that we consider is the generalized linear model. It introduces nonlinear transformations of the original predictors as new additive terms in an otherwise linear model. Generalized linear models are thus the closest nonlinear counterparts to the linear approaches in Sections and .

The model we study adapts the simple linear form by adding a $K$ -term spline series expansion of the predictors

(13)

where $p(⋅)=(p1(⋅),p2(⋅),…,pK(⋅))′$ is a vector of basis functions, and the parameters are now a $K×N$ matrix $θ=(θ1,θ2,…,θN)$ ⁠. There are many potential choices for spline functions. We adopt a spline series of order two: $(1,z,(z−c1)2,(z−c2)2,…,(z−cK−2)2)$ ⁠, where $c1$ ⁠, $c2$ ⁠, … $cK−2$ are knots.

As its name suggests, the group lasso selects either all $K$ spline terms associated with a given characteristic or none of them. We embed this penalty in the general objective of Equation (). Group lasso accommodates either least squares or robust Huber objective, and it uses the same accelerated proximal gradient descent as the elastic net. It has two tuning parameters, $λ$ and $K$ ⁠.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">14</a></sup>

### 1.6 Boosted regression trees and random forests

The model in () captures individual predictors’ nonlinear impact on expected returns, but does not account for interactions among predictors. One way to add interactions is to expand the generalized model to include multivariate functions of predictors. While expanding univariate predictors with $K$ basis functions multiplies the number of parameters by a factor of $K$ ⁠, multiway interactions increase the parameterization combinatorially. Without a priori assumptions for which interactions to include, the generalized linear model becomes computationally infeasible.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">15</a></sup>

As an alternative, regression trees have become a popular machine learning approach for incorporating multiway predictor interactions. Unlike linear models, trees are fully nonparametric and possess a logic that departs markedly from traditional regressions. At a basic level, trees are designed to find groups of observations that behave similarly to each. A tree “grows” in a sequence of steps. At each step, a new “branch” sorts the data leftover from the preceding step into bins based on one of the predictor variables. This sequential branching slices the space of predictors into rectangular partitions, and approximates the unknown function $g⋆(⋅)$ with the average value of the outcome variable within each partition.

[Figure 1](https://academic.oup.com/rfs/article/33/5/2223/) shows an example with two predictors, “size” and “b/m.” The left panel describes how the tree assigns each observation to a partition based on its predictor values. First, observations are sorted on size. Those above the breakpoint of 0.5 are assigned to Category 3. Those with small size are then further sorted by b/m. Observations with small size and b/m below 0.3 are assigned to Category 1, while those with b/m above 0.3 go into Category 2. Finally, forecasts for observations in each partition are defined as the simple average of the outcome variable’s value among observations in that partition.

![Regression tree example](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/m_hhaa009f1.jpeg?Expires=1752253962&Signature=K7fpqoFVutS6hQy5yHtRspW6sB3lPBPkLl9BX0ZvjDzLmBtV-8yIV3YHhHPhEPHexb44EiwWGZXB2L8hKrNEAd7KSlF7pmvXTiqvqZmYNa~8O3fCUMitmpsrMZT7XKRzjLJgf57wCDVypxnmDzal6oy8Pby0nGSdxuGNswk5LOsO44a~2aSihNGKGFcDeozP10wBzXLcplNEkJeY3BW4XQKBEUOmu7qhoR9cTDLjW~Q3KAgUszjmfx1rzmFdFR1Z59kKuH9IYzJeoW~X97SxtqiDHFCLH40Uirp-ZOEFDZ3UOqvYAduFj~I1yJQ6jCMpBfvEmMFlJEi35y0ofA8Arw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)

Figure 1

Regression tree example

This figure presents the diagrams of a regression tree (left) and its equivalent representation (right) in the space of two characteristics (size and value). The terminal nodes of the tree are colored in blue, yellow, and red. Based on their values of these two characteristics, the sample of individual stocks is divided into three categories.

[Open in new tab](https://academic.oup.com/view-large/figure/203502795/hhaa009f1.tif) [Download slide](https://academic.oup.com/DownloadFile/DownloadImage.aspx?image=https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009f1.jpeg?Expires=1752253962&Signature=2yhuRLUN8V2R2gb0-x~VAcpL9UVDHdbA32WECzrkvxRf78CEXuiZbzeo6xx5lptJ6K3qVhprCyc~kbwa11H1rJqhhdx93G-D6F8jnTzscJ4Ke99DJFtKioCyLdSk9PUrnetYRk2t8fg7laXQdNOY8j9s-mCgIa68xarq3x7jOwYj3QOPESoFzoJiv0Pw05m-yfHqOv5BizJITV0DFwpHQTuRu4hyFwL1-QzrQb1HdtKmIjNwyRHpY5q8s0jShWkk6nMaQJYKqBB1CK4aBWqcoLvPzMt8H2Sx9yu9XmNXpSXYe9h1sgf1LcjTPSwvMMDC52bs9FGIgLQvqhVF0FiM9A__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA&sec=203502795&ar=5758276&xsltPath=~/UI/app/XSLT&imagename=&siteId=5511)

More formally, the prediction of a tree, $T$ ⁠, with $K$ “leaves” (terminal nodes), and depth $L$ ⁠, can be written as

(15)

where $Ck(L)$ is one of the $K$ partitions of the data. Each partition is a product of up to $L$ indicator functions of the predictors. The constant associated with partition $k$ (denoted $θk$ ⁠) is defined to be the sample average of outcomes within the partition.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">16</a></sup> The example in [Figure 1](https://academic.oup.com/rfs/article/33/5/2223/) has the following prediction equation:

To grow a tree is to find bins that best discriminate among the potential outcomes. The specific predictor variable upon which a branch is based, and the specific value where the branch is split, is chosen to minimize forecast error. The expanse of potential tree structures, however, precludes exact optimization. The literature has developed a set of sophisticated optimization heuristics to quickly converge on approximately optimal trees. We follow the algorithm of [Breiman et al. (1984)](https://academic.oup.com/rfs/article/33/5/2223/) and provide a detailed description of it in [Internet Appendix B.2](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA). The basic idea is to myopically optimize forecast error at the start of each branch. At each new level, we choose a sorting variable from the set of predictors and the split value to maximize the discrepancy among average outcomes in each bin.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">17</a></sup> The loss associated with the forecast error for a branch $C$ is often called “impurity,” which describes how similarly observations behave on either side of the split. We choose the most popular $l2$ impurity for each branch of the tree:

(16)

where $|C|$ denotes the number of observations in set $C$ ⁠. Given $C$ ⁠, it is clear that the optimal choice of $θ$ ⁠: $θ=1|C|∑zi,t∈Cri,t+1.$ The procedure is equivalent to finding the branch $C$ that locally minimizes the impurity. Branching halts when the number of leaves or the depth of the tree reach a prespecified threshold that can be selected adaptively using a validation sample.

Advantages of the tree model are that it is invariant to monotonic transformations of predictors, that it naturally accommodates categorical and numerical data in the same model, that it can approximate potentially severe nonlinearities, and that a tree of depth $L$ can capture $(L−1)$ -way interactions. Their flexibility is also their limitation. Trees are among the prediction methods most prone to overfit, and therefore must be heavily regularized. In our analysis, we consider two “ensemble” tree regularizers that combine forecasts from many different trees into a single forecast.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">18</a></sup>

The first regularization method is “boosting,” which recursively combines forecasts from many oversimplified trees.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">19</a></sup> Shallow trees on their own are “weak learners” with minuscule predictive power. The theory behind boosting suggests that many weak learners may, as an ensemble, comprise a single “strong learner” with greater stability than a single complex tree.

The details of our boosting procedure, typically referred to as gradient boosted regression trees (GBRT), are described in [Algorithm 4 of Internet Appendix B.2](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA). It starts by fitting a shallow tree (e.g., with depth $L=1$ ⁠). This oversimplified tree is sure to be a weak predictor with large bias in the training sample. Next, a second simple tree (with the same shallow depth $L$ ⁠) is used to fit the prediction residuals from the first tree. Forecasts from these two trees are added together to form an ensemble prediction of the outcome, but the forecast component from the second tree is shrunken by a factor $ν∈(0,1)$ to help prevent the model from overfitting the residuals. At each new step $b$ ⁠, a shallow tree is fitted to the residuals from the model with $b−1$ trees, and its residual forecast is added to the total with a shrinkage weight of $ν$ ⁠. This is iterated until there are a total of $B$ trees in the ensemble. The final output is therefore an additive model of shallow trees with three tuning parameters $(L,ν,B)$ ⁠, which we adaptively choose in the validation step.

Like boosting, a random forest is an ensemble method that combines forecasts from many different trees. It is a variation on a more general procedure known as bootstrap aggregation, or “bagging” ([Breiman 2001](https://academic.oup.com/rfs/article/33/5/2223/)). The baseline tree bagging procedure draws $B$ different bootstrap samples of the data, fits a separate regression tree to each, then averages their forecasts. Trees for individual bootstrap samples tend to be deep and overfit, making their individual predictions inefficiently variable. Averaging over multiple predictions reduces this variation, thus stabilizing the trees’ predictive performance.

Random forests use a variation on bagging designed to reduce the correlation among trees in different bootstrap samples. If, for example, firm size is the dominant return predictor in the data, then most of the bagged trees will have low-level splits on size resulting in substantial correlation among their ultimate predictions. The forest method decorrelates trees using a method known as “dropout,” which considers only a randomly drawn subset of predictors for splitting at each potential branch. Doing so ensures that, in the example, early branches for at least a few trees will split on characteristics other than firm size. This lowers the average correlation among predictions to further improve the variance reduction relative to standard bagging. Depth $L$ of the trees, number of predictors in each split and number of bootstrap samples $B$ are the tuning parameters optimized via validation. [Algorithm 3 of the Internet Appendix](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) describes the precise details of our random forest implementation.

### 1.7 Neural networks

The final nonlinear method that we analyze is the artificial neural network. Arguably the most powerful modeling device in machine learning, neural networks have theoretical underpinnings as “universal approximators” for any smooth predictive association ([Hornik, Stinchcombe, and White 1989](https://academic.oup.com/rfs/article/33/5/2223/); [Cybenko 1989](https://academic.oup.com/rfs/article/33/5/2223/)). They are the currently preferred approach for complex machine learning problems, such as computer vision, natural language processing, and automated game-playing (such as chess and go). Their flexibility draws from the ability to entwine many telescoping layers of nonlinear predictor interactions, earning the synonym “deep learning.” At the same time, their complexity ranks neural networks among the least transparent, least interpretable, and most highly parameterized machine learning tools.

Our analysis focuses on traditional “feed-forward” networks. These consist of an “input layer” of raw predictors, one or more “hidden layers” that interact and nonlinearly transform the predictors, and an “output layer” that aggregates hidden layers into an ultimate outcome prediction. Analogous to axons in a biological brain, layers of the networks represent groups of “neurons” with each layer connected by “synapses” that transmit signals among neurons of different layers. [Figure 2](https://academic.oup.com/rfs/article/33/5/2223/) shows two illustrative examples.

The number of units in the input layer is equal to the dimension of the predictors, which we set to four in this example (denoted $z1,...,z4$ ⁠). The left panel shows the simplest possible network that has no hidden layers. Each of the predictor signals is amplified or attenuated according to a 5-dimensional parameter vector, $θ$ ⁠, that includes an intercept and one weight parameter per predictor. The output layer aggregates the weighted signals into the forecast $θ0+∑k=14zkθk$ ⁠; that is, the simplest neural network is a linear regression model.

![Neural networks](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/m_hhaa009f2.jpeg?Expires=1752253962&Signature=aniTIJNtUSeUXGqkGNRlHRkfaAv4HxAdRBDCtAz8m4UEAKANBGf~AGPN~rxcUxqHD54cRnyyschPxS9auc-n11n~DpRDrPIMEXcamEnwAz3dM-CrjDW-4zIHtD8P5z6vb8S8WzSxcXh6YjnY44Jvd3a4K7vzDY3Bi1Na7kdCoVTHcrrhCEoOUG8tNjbkRFdYG2jFVXcJAHYYGQ~4pRwfL6NBTaJQdHBEwwOAx6EvX26Fs97HhBbPIR8SX2xDzbGwAq0xuTk-Vmnq8VZ774Dxtfik-~MNV7ix983NZH~el9Bwdb1aurj-pmF3rkDguZMcbN-06NkOGXa1bbBbhPe5Pg__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)

Figure 2

Neural networks

This figure provides diagrams of two simple neural networks with (right) or without (left) a hidden layer. Pink circles denote the input layer, and dark red circles denote the output layer. Each arrow is associated with a weight parameter. In the network with a hidden layer, a nonlinear activation function $f$ transforms the inputs before passing them on to the output.

[Open in new tab](https://academic.oup.com/view-large/figure/203502807/hhaa009f2.tif) [Download slide](https://academic.oup.com/DownloadFile/DownloadImage.aspx?image=https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009f2.jpeg?Expires=1752253962&Signature=Mk~g20krxtuRySmMDYL9b3Ky5-EmGIDx5Jr3OQERpRYGYXSfYieEewK5uJCAnNp5fUS2MPZ5Afz-QMn3JzABRpx5cxifsiE9G1RlxaKixgqWGUA~Sym2buINVVG3i9OJQ8Hcl4j4BvQvJRtlh4clnFgwc5cyfJU0yGgd80UAC4cyRyPaFqUccqF1Vg0u21UDGq3g6osnLJV79Szasswcyu3JlWyamRUIR0Iz5C~f1Er0zj-GyhVV9A8abi1N5w7bVp92PKNpbQZTKTNXcbpLMjcKV0lrbjFGMMR~icGNm3MIL5DT3IBxgPT1FVQYM4uanBigFwadNRBqd9MZyU95jg__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA&sec=203502807&ar=5758276&xsltPath=~/UI/app/XSLT&imagename=&siteId=5511)

The model incorporates more flexible predictive associations by adding hidden layers between the inputs and output. The right panel of [Figure 2](https://academic.oup.com/rfs/article/33/5/2223/) shows an example with one hidden layer that contains five neurons. Each neuron draws information linearly from all of the input units, just as in the simple network on the left. Then, each neuron applies a nonlinear “activation function” $f$ to its aggregated signal before sending its output to the next layer. For example, the second neuron in the hidden layer transforms inputs into an output as $x2(1)=f(θ2,0(0)+∑j=14zjθ2,j(0))$ ⁠. Lastly, the results from each neuron are linearly aggregated into an ultimate output forecast:

Thus, in this example, there are a total of 31 $=(4+1)×5+6$ parameters (five parameters to reach each neuron and six weights to aggregate the neurons into a single output).

One makes many choices when structuring a neural network, including the number of hidden layers, the number of neurons in each layer, and which units are connected. Despite the aforementioned “universal approximation” result that suggests the sufficiency of a single hidden layer, recent literature has shown that deeper networks can often achieve the same accuracy with substantially fewer parameters.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">20</a></sup>

On the other hand, in small data sets simple networks with only a few layers and nodes often perform best. Training a very deep neural network is challenging because it typically involves a large number of parameters, because the objective function is highly nonconvex, and because the recursive calculation of derivatives (known as “back-propagation”) is prone to exploding or vanishing gradients.

Selecting a successful network architecture by cross-validation is in general a difficult task. It is unrealistic and unnecessary to find the optimal network by searching over uncountably many architectures. Instead, we fix a variety of network architectures ex ante and estimate each of these. What we hope to achieve is reasonably lower bound on the performance of machine learning methods.

We consider architectures with up to five hidden layers. Our shallowest neural network has a single hidden layer of 32 neurons, which we denoted NN1. Next, NN2 has two hidden layers with 32 and 16 neurons, respectively; NN3 has three hidden layers with 32, 16, and 8 neurons, respectively; NN4 has four hidden layers with 32, 16, 8, and 4 neurons, respectively; and NN5 has five hidden layers with 32, 16, 8, 4, and 2 neurons, respectively. We choose the number of neurons in each layer according to the geometric pyramid rule (see [Masters 1993](https://academic.oup.com/rfs/article/33/5/2223/)). All architectures are fully connected so each unit receives an input from all units in the layer below. By comparing the performance of NN1 through NN5, we can infer the trade-offs of network depth in the return forecasting problem.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">21</a></sup>

Our neural network model has the following general formula. Let $K(l)$ denote the number of neurons in each layer $l=1,...,L$ ⁠. Define the output of neuron $k$ in layer $l$ as $xk(l)$ ⁠. Next, define the vector of outputs for this layer (augmented to include a constant, $x0(l)$ ⁠) as $x(l)=(1,x1(l),...,xK(l)(l))′$ ⁠. To initialize the network, similarly define the input layer using the raw predictors, $x(0)=(1,z1,...,zN)′$ ⁠. The recursive output formula for the neural network at each neuron in layer $l>0$ is then

(17)

with final output

(18)

The number of weight parameters in each hidden layer $l$ is $K(l)(1+K(l−1))$ ⁠, plus another $1+K(L−1)$ weights for the output layer.

We estimate the neural network weight parameters by minimizing the penalized $l2$ objective function of prediction errors. Unlike tree-based algorithms that require “greedy” optimization, training a neural network, in principle, allows for joint updates of all model parameters at each step of the optimization—a substantial advantage of neural networks over trees. However, the high degree of nonlinearity and nonconvexity in neural networks, together with their rich parameterization, make brute force optimization highly computationally intensive (often to the point of infeasibility). A common solution uses stochastic gradient descent (SGD) to train a neural network. Unlike standard descent that uses the entire training sample to evaluate the gradient at each iteration of the optimization, SGD evaluates the gradient from a small random subset of the data. This approximation sacrifices accuracy for enormous acceleration of the optimization routine.

For the same reasons described above (severe nonlinearity and heavy parameterization), regularization of neural networks requires more care than the methods discussed above. In addition to $l1$ penalization of the weight parameters, we simultaneously employ four other regularization techniques in our estimation: learning rate shrinkage, early stopping, batch normalization, and ensembles.

A critical tuning parameter in SGD is the learning rate, which controls the step size of the descent. It is necessary to shrink the learning rate toward zero as the gradient approaches zero, otherwise noise in the calculation of the gradient begins to dominate its directional signal. We adopt the “learning rate shrinkage” algorithm of [Kingma and Ba (2014)](https://academic.oup.com/rfs/article/33/5/2223/) to adaptively control the learning rate (described further in [Algorithm 5 of the Internet Appendix B.3](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)).<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">23</a></sup>

Next, “early stopping” is a general machine learning regularization tool. It begins from an initial parameter guess that imposes parsimonious parameterization (e.g., setting all $θ$ values close to zero). In each step of the optimization algorithm, the parameter guesses are gradually updated to reduce prediction errors in the training sample. At each new guess, predictions are also constructed for the validation sample, and the optimization is terminated when the validation sample errors begin to increase. This typically occurs before the prediction errors are minimized in the training sample, hence the name early stopping (see Algorithm 6 of the Internet Appendix B.3). By ending the parameter search early, parameters are shrunken toward the initial guess. It is a popular substitute to $l2$ penalization of $θ$ parameters because it achieves regularization at a much lower computational cost.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">24</a></sup> Early stopping can be used alone or together with $l1$ -regularization, as we do in this paper.

“Batch normalization” ([Ioffe and Szegedy 2015](https://academic.oup.com/rfs/article/33/5/2223/)) is a simple technique for controlling the variability of predictors across different regions of the network and across different data sets. It is motivated by the phenomenon of internal covariate shift in which inputs of hidden layers follow different distributions than their counterparts in the validation sample. This issue is constantly encountered when fitting deep neural networks that involve many parameters and rather complex structures. For each hidden unit in each training step (a “batch”), the algorithm cross-sectionally demeans and variance standardizes the batch inputs to restore the representation power of the unit.

Finally, we adopt an ensemble approach in training our neural networks (see also [Hansen and Salamon 1990](https://academic.oup.com/rfs/article/33/5/2223/); [Dietterich 2000](https://academic.oup.com/rfs/article/33/5/2223/)). In particular, we use multiple random seeds to initialize neural network estimation and construct predictions by averaging forecasts from all networks. This reduces prediction variance because the stochastic nature of the optimization can cause different seeds to produce different forecasts.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">25</a></sup>

### 1.8 Performance evaluation

To assess predictive performance for individual excess stock return forecasts, we calculate the out-of-sample $R2$ as

(19)

where $T3$ indicates that fits are only assessed on the testing subsample, whose data never enter into model estimation or tuning. $Roos2$ pools prediction errors across firms and over time into a grand panel-level assessment of each model.

A subtle but important aspect of our $R2$ metric is that the denominator is the sum of squared excess returns *without demeaning*. In many out-of-sample forecasting applications, predictions are compared against historical mean returns. Although this approach is sensible for the aggregate index or long-short portfolios, for example, it is flawed when it comes to analyzing individual stock returns. Predicting future excess stock returns with historical averages typically *underperforms* a naive forecast of zero by a large margin. That is, the historical mean stock return is so noisy that it artificially lowers the bar for “good” forecasting performance. We avoid this pitfall by benchmarking our $R2$ against a forecast value of zero. To give an indication of the importance of this choice, when we benchmark model predictions against historical mean stock returns, the out-of-sample monthly $R2$ of all methods rises by roughly three percentage points.

To make pairwise comparisons of methods, we use the [Diebold and Mariano (1995)](https://academic.oup.com/rfs/article/33/5/2223/) test for differences in out-of-sample predictive accuracy between two models.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">26</a></sup> While time-series dependence in returns is sufficiently weak, it is unlikely that the conditions of weak error dependence underlying the Diebold-Mariano test apply to our stock-level analysis due of potentially strong dependence in the cross-section. We adapt Diebold-Mariano to our setting by comparing the cross-sectional average of prediction errors from each model, instead of comparing errors among individual returns. More precisely, to test the forecast performance of method $(1)$ versus $(2)$ ⁠, we define the test statistic $DM12=d¯12/σ^d¯12$ ⁠, where

(20)

$e^i,t+1(1)$ and $e^i,t+1(2)$ denote the prediction error for stock return $i$ at time $t$ using each method, and $n3,t+1$ is the number of stocks in the testing sample (year $t+1$ ⁠). Then $d¯12$ and $σ^d¯12$ denote the mean and Newey-West standard error of $d12,t$ over the testing sample. This modified Diebold-Mariano test statistic, which is now based on a single time series $d12,t+1$ of error differences with little autocorrelation, is more likely to satisfy the mild regularity conditions needed for asymptotic normality and in turn provide appropriate $p$ -values for our model comparison tests.

### 1.9 Variable importance and marginal relationships

Our goal in interpreting machine learning models is modest. We aim to identify covariates that have an important influence on the cross-section of expected returns while simultaneously controlling for the many other predictors in the system.

We discover influential covariates by ranking them according to a notion of variable importance, which we denote as VI $j$ for the $j$ th input variable. We consider two different notions of importance. The first is the reduction in panel predictive $R2$ from setting all values of predictor $j$ to zero, while holding the remaining model estimates fixed (used, e.g., in the context of dimension reduction by [Kelly, Pruitt, and Su 2019](https://academic.oup.com/rfs/article/33/5/2223/)). The second, proposed in the neural networks literature by [Dimopoulos, Bourret, and Lek (1995)](https://academic.oup.com/rfs/article/33/5/2223/), is the sum of squared partial derivatives (SSD) of the model to each input variable $j$ ⁠, which summarizes the sensitivity of model fits to changes in that variable.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">27</a></sup>

As part of our analysis, we also trace out the marginal relationship between expected returns and each characteristic. Despite obvious limitations, such a plot is an effective tool for visualizing the first-order impact of covariates in a machine learning model.

## 2\. An Empirical Study of U.S. Equities

### 2.1 Data and the overarching model

We obtain monthly total individual equity returns from CRSP for all firms listed in the NYSE, AMEX, and NASDAQ. Our sample begins in March 1957 (the start date of the S&P 500) and ends in December 2016, totaling 60 years. The number of stocks in our sample is almost 30,000, with the average number of stocks per month exceeding 6,200.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">28</a></sup> We also obtain the Treasury-bill rate to proxy for the risk-free rate from which we calculate individual excess returns.

In addition, we build a large collection of stock-level predictive characteristics based on the cross-section of stock returns literature. These include 94 characteristics <sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">29</a></sup> (61 of which are updated annually, 13 are updated quarterly, and 20 are updated monthly). In addition, we include 74 industry dummies corresponding to the first two digits of Standard Industrial Classification (SIC) codes. [Table A.6 in the Internet Appendix](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) provides the details of these characteristics.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">30</a></sup>

We also construct eight macroeconomic predictors following the variable definitions detailed in [Welch and Goyal (2008)](https://academic.oup.com/rfs/article/33/5/2223/), including dividend-price ratio (dp), earnings-price ratio (ep), book-to-market ratio (bm), net equity expansion (ntis), Treasury-bill rate (tbl), term spread (tms), default spread (dfy), and stock variance (svar).<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">31</a></sup>

All of the machine learning methods we consider are designed to approximate the overarching empirical model $Et(ri,t+1)=g⋆(zi,t)$ defined in Equation (). Throughout our analysis, we define the baseline set of stock-level covariates $zi,t$ as

(21)

where $ci,t$ is a $Pc×1$ matrix of characteristics for each stock $i$ ⁠, and $xt$ is a $Px×1$ vector of macroeconomic predictors (and are thus common to all stocks, including a constant). Thus, $zi,t$ is a $P×1$ vector of features for predicting individual stock returns (with $P=PcPx$ ⁠) and includes interactions between stock-level characteristics and macroeconomic state variables. The total number of covariates is $94×(8+1)+74=920$ ⁠.

The overarching model specified by () and () nests many models proposed in the literature ([Rosenberg 1974](https://academic.oup.com/rfs/article/33/5/2223/); [Harvey and Ferson 1999](https://academic.oup.com/rfs/article/33/5/2223/), among others). The motivating example for this model structure is the standard beta pricing representation of the asset pricing conditional Euler equation,

(22)

The structure of our feature set in () allows for purely stock-level information to enter expected returns via $ci,t$ in analogy with the risk exposure function $βi,t$ ⁠, and also allows aggregate economic conditions to enter in analogy with the dynamic risk premium $λt$ ⁠. In particular, if $βi,t=θ1ci,t$ ⁠, and $λt=θ2xt$ ⁠, for some constant parameter matrices $θ1$ $(K×Pc)$ and $θ2$ $(K×Px)$ ⁠, then the beta pricing model in () becomes

(23)

where $θ=vec(θ1′θ2)$ ⁠. The overarching model is more general than this example because $g⋆(⋅)$ is not restricted to be a linear function. Considering nonlinear $g⋆(⋅)$ formulations, for example, via generalized linear models or neural networks, essentially expands the feature set to include a variety of functional transformations of the baseline $zi,t$ predictor set.

We divide the 60 years of data into 18 years of training sample (1957–1974), 12 years of validation sample (1975–1986), and the remaining 30 years (1987–2016) for out-of-sample testing. Because machine learning algorithms are computationally intensive, we avoid recursively refitting models each month. Instead, we refit once every year as most of our signals are updated once per year. Each time we refit, we increase the training sample by 1 year. We maintain the same size of the validation sample, but roll it forward to include the most recent 12 months.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">32</a></sup>

### 2.2 The cross-section of individual stocks

Table 1

[Open in new tab](https://academic.oup.com/view-large/203502842)

| ![graphic](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/m_hhaa009t1.jpeg?Expires=1752253962&Signature=R3h6GUuN~J6nC53-3uAY6m1Yt2pbfsBDBcslfP7Z-MhL~YLCqd94D54XsBZ-y35JVADaWRDpjbHai6dl3phVFKilYZyRnxKuhQ9mcFho46tVQb0rJ-fa98VE~r7iVhpMiSNbBycK-15qddiB81rfwOKyrIOp6nkCJjp1GGu-8G4xO4M2ak9cr5cnGdiLnjZ-zLzvxnG5QWeWXXJHwM8~4i8CtKmnvRdm16apeg-Mdw0gx5qz1Rg8z2Pv0s5sTns3iELlSsL8at-GZfyHR0Lunp~FZ1m7MjP3xKpif907owWn83acypzyL8bRhSU-sUKWMJ3jOWVpgc~YFlW2yFNJsQ__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) |
| --- |

In this table, we report monthly $Roos2$ for the entire panel of stocks using OLS with all variables (OLS), OLS using only size, book-to-market, and momentum (OLS-3), PLS, PCR, elastic net (ENet), generalize linear model (GLM), random forest (RF), gradient boosted regression trees (GBRT), and neural networks with 1 to 5 layers (NN1–NN5). “+H” indicates the use of Huber loss instead of the $l2$ loss. We also report these $Roos2$ within subsamples that include only the top-1,000 stocks or bottom-1,000 stocks by market value. The lower panel provides a visual comparison of the $Roos2$ statistics in the table (omitting OLS because of its large negative values).

[Table 1](https://academic.oup.com/rfs/article/33/5/2223/) presents the comparison of machine learning techniques in terms of their out-of-sample predictive $R2$ ⁠. We compare thirteen models in total, including OLS with all covariates, OLS-3 (which preselects size, book-to-market, and momentum as the only covariates), PLS, PCR, elastic net (ENet), generalized linear model with group lasso (GLM), random forest (RF), gradient boosted regression trees (GBRT), and neural network architectures with one to five layers (NN1,...,NN5). For OLS, ENet, GLM, and GBRT, we present their robust versions using Huber loss, which perform better than the version without.

The first row of [Table 1](https://academic.oup.com/rfs/article/33/5/2223/) reports $Roos2$ for the entire pooled sample. The OLS model using all 920 features produces an $Roos2$ of $−3.46%$ ⁠, indicating it is handily dominated by applying a naive forecast of zero to all stocks in all months. This may be unsurprising as the lack of regularization leaves OLS highly susceptible to in-sample overfit. However, restricting OLS to a sparse parameterization, either by forcing the model to include only three covariates (size, value, and momentum), or by penalizing the specification with the elastic net—generates a substantial improvement over the full OLS model (⁠ $Roos2$ of 0.16% and 0.11% respectively). [Figure 3](https://academic.oup.com/rfs/article/33/5/2223/) summarizes the complexity of each model at each reestimation date. The upper left panel shows the number of features to which elastic net assigns a nonzero loading. In the first 10 years of the test sample, the model typically chooses fewer than five features. After 2,000, the number of selected features rises and hovers between 20 and 40.

![Time-varying model complexity](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/m_hhaa009f3.jpeg?Expires=1752253962&Signature=sjtRlFlYKVfHkWKA4YMb~Dp6zJ06bD1WmjDAsGSroir7dTOZ06Sl88hA0ljNrAisX~qMtKfei-1JJi0jEB73ibSlX2Phf-SURyUQiNCpcIrU8XOs7PZPyWGzwEh6avhUJQFmRfi1Km-P0RlLkYDIvDcxHT8O1O0~~p5Bnvqst65BCwBj1-tqHDPGa97Sa1vXFLqsXvUS7XbINqpy3Ws3g-XawTfsFe6R9rHia1ECVjCmT8gk04KB3vJP2fZ54jhvECdqDsSERvERSkImU3sAfqiTxe037S2f6teivnAdu6mxEEeQ7Mdzfqm0sxhFs7oOLVR1MBheyUTOEK-OZX9Xrw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)

Figure 3

Time-varying model complexity

This figure demonstrates the model’s complexity for elastic net (ENet), PCR, PLS, generalized linear model with group lasso (GLM), random forest (RF), and gradient boosted regression trees (GBRT) in each training sample of our 30-year recursive out-of-sample analysis. For ENet and GLM, we report the number of features selected to have nonzero coefficients; for PCR and PLS, we report the number of selected components; for RF, we report the average tree depth; and, for GBRT, we report the number of distinct characteristics entering into the trees.

[Open in new tab](https://academic.oup.com/view-large/figure/203502845/hhaa009f3.tif) [Download slide](https://academic.oup.com/DownloadFile/DownloadImage.aspx?image=https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009f3.jpeg?Expires=1752253962&Signature=SYyrZWRMcd-ZJexteGqFFT3HCtw~k17JVjGDK3fVT-GF8VsND2hP2vUYeXZTJ9pYHQfADMG~L~MN23EcGHhaiUA~4NYeSxidYsfdfqy6yYGUjiHvpOMxIlboxJQ6auxtRuzkLXxVD48Nrbihbzdgbc7fqCRLEAl0Gy8HK-O5bxaRu6-ird8BgdkcQBGzIREkybo0lqY6sa0AyScJnYc4fFzQ6uR8RVxq-jemM6AT2QlfOp6-MhWd6rpC-WkTaaxHalenNpcVy-nupPtd4~jIcu0g6rIE0jN7M4yd7HJ1LpFV44HdqBtPjfyzjj8-d3aSXWe3xAOKesSI~jNptXjkFw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA&sec=203502845&ar=5758276&xsltPath=~/UI/app/XSLT&imagename=&siteId=5511)

Regularizing the linear model via dimension reduction improves predictions even further. By forming a few linear combinations of predictors, PLS and especially PCR, raise the out-of-sample $R2$ to 0.27% and 0.26%, respectively. [Figure 3](https://academic.oup.com/rfs/article/33/5/2223/) shows that PCR typically uses 20 to 40 components in its forecasts. PLS, on the other hand, fails to find a single reliable component for much of the early sample, but eventually settles on three to six components. The improvement of dimension reduction over variable selection via elastic net suggests that characteristics are partially redundant and fundamentally noisy signals. Combining them into low-dimension components averages out noise to better reveal their correlated signals.

The generalized linear model with group lasso penalty fails to improve on the performance of purely linear methods (⁠ $Roos2$ of 0.19%). The fact that this method uses spline functions of individual features, but includes no interaction among features, suggests that univariate expansions provide little incremental information beyond the linear model. Though it tends to select more features than elastic net, those additional features do not translate into incremental performance.

Boosted trees and random forests are competitive with PCR, producing fits of 0.34% and 0.33%, respectively. Random forests generally estimate shallow trees, with one to five layers on average. To quantify the complexity of GBRT, we report the number of features used in the boosted tree ensemble at each reestimation point. In the beginning of the sample GBRT uses around 30 features to partition outcomes, with this number increasing to 50 later in the sample.

Neural networks are the best performing nonlinear method, and the best predictor overall. The $Roos2$ is 0.33% for NN1 and peaks at 0.40% for NN3. These results point to the value of incorporating complex predictor interactions, which are embedded in tree and neural network models but that are missed by other techniques. The results also show that in the monthly return setting, the benefits of “deep” learning are limited, as four- and five-layer models fail to improve over NN3.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">33</a></sup>

The second and third rows of [Table 1](https://academic.oup.com/rfs/article/33/5/2223/) break out predictability for large stocks (the top-1,000 stocks by market equity each month) and small stocks (the bottom-1,000 stocks each month). This is based on the full estimated model (using all stocks), but focuses on fits among the two subsamples. The baseline patterns that OLS fares poorly, regularized linear models are an improvement, and nonlinear models dominate carries over into subsamples. Tree methods and neural networks are especially successful among large stocks, with $Roos2$ ranging from 0.52% to 0.70%. This dichotomy provides reassurance that machine learning is not merely picking up small scale inefficiencies driven by illiquidity.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">34</a></sup>

[Table 2](https://academic.oup.com/rfs/article/33/5/2223/) conducts our analysis at the annual horizon. The comparative performance across different methods is similar to the monthly results shown in [Table 1](https://academic.oup.com/rfs/article/33/5/2223/), but the annual $Roos2$ is nearly an order of magnitude larger. Their success in forecasting annual returns likewise illustrates that machine learning models are able to isolate risk premiums that persist over business cycle frequencies and are not merely capturing short-lived inefficiencies.

Whereas [Table 1](https://academic.oup.com/rfs/article/33/5/2223/) offers a quantitative comparison of models’ predictive performance, [Table 3](https://academic.oup.com/rfs/article/33/5/2223/) assesses the statistical significance of differences among models at the monthly frequency. It reports Diebold-Mariano test statistics for pairwise comparisons of a column model versus a row model. Diebold-Mariano statistics are distributed $N(0,1)$ under the null of no difference between models, thus the test statistic magnitudes map to $p$ -values in the same way as regression $t$ -statistics. Our sign convention is that a positive statistic indicates the column model outperforms the row model. Bold numbers denote significance at the 5% level for each individual test.

Table 2

[Open in new tab](https://academic.oup.com/view-large/203502853)

| ![graphic](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/m_hhaa009t2.jpeg?Expires=1752253962&Signature=dSEv~7HyENfepfk8aduR0dCCrzx20PKf5~YiXn3cEJjnZAeZQPgL7nivJ1ddWk~BXZEJFoJRsJM2eDS-vZzaMvfd2W3a-I2iN6V-2COQwtXE4OtULNVIdBBEzKBE3QzYPV83WOStR8RpBkx8rmtVRgtCb6tXbcQvfd~9ogkr6E3yeoz1yFOauTmBmc8E-rTiKlYTa8fzxnEHunArHXTB2zFnP43N6bjhp0NLwmAkofLEIZJ85IkKVpzEF9yDwtUmRSg5mOD0Oq3Wz-YAJRH50rmpi9ZNormjRiSZILLscS8EKOd5eLAwRk9WfXp4Kz-3u6TEI44f4lw-NtIAK8gG5A__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) |
| --- |

Annual return forecasting $Roos2$ (see the legend to [Table 1](https://academic.oup.com/rfs/article/33/5/2223/)).

Table 3

[Open in new tab](https://academic.oup.com/view-large/203502854)

Comparison of monthly out-of-sample prediction using Diebold-Mariano tests

|  | OLS-3+H | PLS | PCR | ENet+H | GLM+H | RF | GBRT+H | NN1 | NN2 | NN3 | NN4 | NN5 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| OLS+H | **3**.**26 <sup>*</sup>** | **3**.**29 <sup>*</sup>** | **3**.**35 <sup>*</sup>** | **3**.**29 <sup>*</sup>** | **3**.**28 <sup>*</sup>** | **3**.**29 <sup>*</sup>** | **3**.**26 <sup>*</sup>** | **3**.**34 <sup>*</sup>** | **3**.**40 <sup>*</sup>** | **3**.**38 <sup>*</sup>** | **3**.**37 <sup>*</sup>** | **3**.**38 <sup>*</sup>** |
| OLS-3+H |  | 1.42 | **1**.**87** | −0.27 | 0.62 | **1**.**64** | 1.28 | 1.25 | **2**.**13** | **2**.**13** | **2**.**36** | **2**.**11** |
| PLS |  |  | −0.19 | −1.18 | −1.47 | 0.87 | 0.67 | 0.63 | 1.32 | 1.37 | 1.66 | 1.08 |
| PCR |  |  |  | −1.10 | −1.37 | 0.85 | 0.75 | 0.58 | 1.17 | 1.19 | 1.34 | 1.00 |
| ENet+H |  |  |  |  | 0.64 | **1**.**90** | 1.40 | **1**.**73** | **1**.**97** | **2**.**07** | **1**.**98** | **1**.**85** |
| GLM+H |  |  |  |  |  | **1**.**76** | 1.22 | 1.29 | **2**.**28** | **2**.**17** | **2**.**68 <sup>*</sup>** | **2**.**37** |
| RF |  |  |  |  |  |  | 0.07 | −0.03 | 0.31 | 0.37 | 0.34 | 0.00 |
| GBRT+H |  |  |  |  |  |  |  | −0.06 | 0.16 | 0.21 | 0.17 | −0.04 |
| NN1 |  |  |  |  |  |  |  |  | 0.56 | 0.59 | 0.45 | 0.04 |
| NN2 |  |  |  |  |  |  |  |  |  | 0.32 | −0.03 | −0.88 |
| NN3 |  |  |  |  |  |  |  |  |  |  | −0.32 | −0.92 |
| NN4 |  |  |  |  |  |  |  |  |  |  |  | −1.04 |

This table reports pairwise Diebold-Mariano test statistics comparing the out-of-sample stock-level prediction performance among thirteen models. Positive numbers indicate the column model outperforms the row model. Bold font indicates the difference is significant at 5% level or better for individual tests, and an asterisk indicates significance at the 5% level for 12-way comparisons via our conservative Bonferroni adjustment.

The first conclusion from [Table 3](https://academic.oup.com/rfs/article/33/5/2223/) is that constrained linear models—including restricting OLS to only use three predictors, reducing dimension via PLS or PCA, and penalizing via elastic net—produce statistically significant improvements over the unconstrained OLS model. Second, we see little difference in the performance of penalized linear methods and dimension reduction methods. Third, we find that tree-based methods uniformly improve over linear models, but the improvements are at best marginally significant. Neural networks are the only models that produce large and significant statistical improvements over linear and generalized linear models. They also improve over tree models, but the difference is not statistically significant.

[Table 3](https://academic.oup.com/rfs/article/33/5/2223/) makes multiple comparisons. We highlight how inference changes under a conservative Bonferroni multiple comparisons correction that divides the significance level by the number of comparisons.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">35</a></sup> For a significance level of 5% amid 12 model comparisons, the adjusted one-sided critical value in our setting is 2.64. In the table, tests that exceed this conservative threshold are accompanied by an asterisk. The main difference with a Bonferroni adjustment is that neural networks become only marginally significant over penalized linear models.

### 2.3 Which covariates matter?

![Variable importance by model](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/m_hhaa009f4.jpeg?Expires=1752253962&Signature=hbfjns4ADm47joL0BseIILHeN6e5-o-7dgk81q1jvy-i0vIKQjYBrhuUqbsc~pLBSzllertF1RIAIfjlAVmU-KutwHU1CKyu~u~qhlOxx9fkW8Gt6crlagRRDedPnYP20OTUd5~3AoUfloOPeiunLwOWgAj76nT4f4M08AnAdWJyzN2MABNu96BL44cpHJa1WlzEaA8ZTTdof2qprY2B7LeGCZPGxRKyECAfbwXWagMVKLhMIlsvON-ORs0xTn6Kb8zzyAu~2q~3Y4~Vh1opmrCnPYZ~lGTcBCj1Bw~3esXcwHD8KlCPHaoXEpAwgJXvCrwiFDPbInfUMB8OemX5rQ__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)

Figure 4

Variable importance by model

Variable importance for the top-20 most influential variables in each model. Variable importance is an average over all training samples. Variable importance within each model is normalized to sum to one.

[Open in new tab](https://academic.oup.com/view-large/figure/203502858/hhaa009f4.tif) [Download slide](https://academic.oup.com/DownloadFile/DownloadImage.aspx?image=https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009f4.jpeg?Expires=1752253962&Signature=m0W8o~JVGuu263rwgGM3eepKfrmrhDKgbRgH3K2-LwQCq74dYRR0GyU5duX-RKgbN24tnKn7LUXsfpiOroRuRyACBx8e6ttyVeaw4yIgK8ebj76TEzew3RrN9xq85fgzGqrSo3AJhbtBckegBVsZ8JwE5hw~HccetUeaH4fkqC7KXy3n8dv~UkobWM7TFdENhSvXoQmeZOV5gkKbs1xsuh0CJ0L7eQCpNxkLMe9yEi4twyRNoN2fMh-OLAnwhlyE4bTF-SheZcK~YDDh1TsXSQCpXIkoo8fIkfGjPubVhGUqhDCnHIu6N7Hke7y~Lj7PrsnuyKxsTVBhUx0iuLptWg__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA&sec=203502858&ar=5758276&xsltPath=~/UI/app/XSLT&imagename=&siteId=5511)

![Characteristic importance](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/m_hhaa009f5.jpeg?Expires=1752253962&Signature=BiWlz4XdfoSwDJqFapr268yoHBu3ynmlmGZR405qPI7~kNDOt2J-3Wk6~hztTJT8daZsE-bKpn3MrvAPfGq8aN0eZ5xxzgGFFBPnDC1lw-L1njbTJTgrDqTKa0UywXoSMMWvMxUYglsEpOwPJb4Vfg9hYH8iXm6HeRmaT9ObEcnShgQvbhmZgJlj20PnlkGsy1RuI8Q3MxOC8DOroWem7Jtjn2F54x1ccbxdcbzwMuCTEgwAeFU-kTfYi2M2-s2p3xofBH1Lbwb2LDYglg2ebz~GdxS88ibZIOt7lzkVVLDePfWxas9bpf~kGQv2hEHWv4fzzQfIDcAiUvxYVn~PKA__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)

Figure 5

Characteristic importance

Rankings of ninety-four stock-level characteristics and the industry dummy (sic2) in terms of overall model contribution. Characteristics are ordered based on the sum of their ranks over all models, with the most influential characteristics on the top and the least influential on the bottom. Columns correspond to the individual models, and the color gradients within each column indicate the most influential (dark blue) to the least influential (white) variables.

[Open in new tab](https://academic.oup.com/view-large/figure/203502859/hhaa009f5.tif) [Download slide](https://academic.oup.com/DownloadFile/DownloadImage.aspx?image=https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009f5.jpeg?Expires=1752253962&Signature=Or5N1R5qxCkekN2O3h0t2zS1w6NbefaGIWkyugX7TrrqzCLTuAlGLn0vzpuGURkp3sKoUVtr7cBysJaXNrztezZNBvVI-C~5vdSYCNgJ0IyXzTFEiTri9hyzQMaluJ4GS3qoDXWVbkeeHrRiM6gOfDz2q3FB8NE5YivUlKhtmmaSG9DTH1IF3W1oHaU5wZFAKxl42Fk5xCq9ly9OW2rYhT0BQJ660~Wq2JKGIGqb0EkEY0B-5rjyYk7QyaEgXZ3cH2cp7s27yOIB94nclZ65Ynps~AvLavqW44x7NEDcooozZY~lj4p-pn8aYH6IA4FwztdOXSjNohk75lSG8iaPFw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA&sec=203502859&ar=5758276&xsltPath=~/UI/app/XSLT&imagename=&siteId=5511)

We now investigate the relative importance of individual covariates for the performance of each model using the importance measures described in Section . To begin, for each method, we calculate the reduction in $R2$ from setting all values of a given predictor to zero within each training sample, and average these into a single importance measure for each predictor. [Figure 4](https://academic.oup.com/rfs/article/33/5/2223/) reports the resultant importance of the top-20 stock-level characteristics for each method. Variable importance within the model is normalized to sum to one, allowing for the interpretation of relative importance for that particular model.

[Figure 5](https://academic.oup.com/rfs/article/33/5/2223/) reports overall rankings of characteristics for all models. We rank the importance of each characteristic for each method, then sum their ranks. Characteristics are ordered so that the highest total ranks are on top and the lowest ranking characteristics are at the bottom. The color gradient within each column shows the model-specific ranking of characteristics from least to most important (lightest to darkest).<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">36</a></sup>

Table 4

[Open in new tab](https://academic.oup.com/view-large/203502862)

| ![graphic](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/m_hhaa009t4.jpeg?Expires=1752253962&Signature=XuzyUslzY7-PziTgIw~Y9Yz7XQZOCtDugnY1Qw6fCqbA6tAlDw7zMXsiFSexPzn1Xu-TZNVXgGqykW4FeeX3RlUnWhs~FcYuIFu9vKzX8jPi-PtGZNLiWbCZ-tfWBQtdWrz6GfW0WTuSlQXXd0Ls83W~gfhNuc8TAQHXFAxlwzA3HON2fyuuwNsBq5ZlRH~bxvSfUaj-6S4r5aDFdp2uOTDTRGyu2ZZ9AhsnDml-rK1Gv0x85w5qdmh41YqHf8rQBkuVrybAclNV9DUZtt1ZfVkPbFUcMIEmziA59kpgjxIopdJAY6PFZPcG8DgvLPJPpnNiCQe0b-TKHdizqxRaFg__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) |
| --- |

Variable importance for eight macroeconomic variables in each model. Variable importance is an average over all training samples. Variable importance within each model is normalized to sum to one. The lower panel provides a complementary visual comparison of macroeconomic variable importance.

[Figures 4](https://academic.oup.com/rfs/article/33/5/2223/) and [5](https://academic.oup.com/rfs/article/33/5/2223/) demonstrate that models are generally in close agreement regarding the most influential stock-level predictors, which can be grouped into four categories. The first are based on recent price trends, including 5 of the top-7 variables in [Figure 5](https://academic.oup.com/rfs/article/33/5/2223/): short-term reversal (mom1m), stock momentum (mom12m), momentum change (chmom), industry momentum (indmom), recent maximum return (maxret), and long-term reversal (mom36m). Next are liquidity variables, including turnover and turnover volatility (turn, SD\_turn), log market equity (mvel1), dollar volume (dolvol), Amihud illiquidity (ill), number of zero trading days (zerotrade), and bid-ask spread (baspread). Risk measures constitute the third influential group, including total and idiosyncratic return volatility (retvol, idiovol), market beta (beta), and beta squared (betasq). The last group includes valuation ratios and fundamental signals, such as earnings-to-price (ep), sales-to-price (sp), asset growth (agr), and number of recent earnings increases (nincr). [Figure 4](https://academic.oup.com/rfs/article/33/5/2223/) shows that characteristic importance magnitudes for penalized linear models and dimension reduction models are highly skewed toward momentum and reversal. Trees and neural networks are more democratic, drawing predictive information from a broader set of characteristics.

We find that our second measure of variable importance, SSD from [Dimopoulos, Bourret, and Lek (1995)](https://academic.oup.com/rfs/article/33/5/2223/), produces very similar results to the simpler $R2$ measure. Within each model, we calculate the Pearson correlation between relative importance from SSD and the $R2$ measure. These correlations range from 84.0% on the low end (NN1) to 97.7% on the high end (random forest). That is, the two methods provide a highly consistent summary of which variables are most influential for forecast accuracy. [Figure A.2 in the Internet Appendix](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) shows the full set of SSD results.

For robustness, we rerun our analysis with an augmented set of characteristics that include five placebo “characteristics.” They are simulated according to the data-generating process [(A.1) in Internet Appendix A](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA). The parameters are calibrated to have similar behavior as our characteristics data set but are independent of future returns by construction. [Figure A.3 in Internet Appendix F](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) presents the variable importance plot (based on $R2$ ⁠) with five noise characteristics highlighted. The table confirms that the most influential characteristics that we identify in our main analysis are unaffected by the presence of irrelevant characteristics. Noise variables appear among the least informative characteristics, along with sin stocks, dividend initiation/omission, cashflow volatility, and other accounting variables.

[Table 4](https://academic.oup.com/rfs/article/33/5/2223/) shows the $R2$ -based importance measure for each macroeconomic predictor variable (again normalized to sum to one within a given model). All models agree that the aggregate book-to-market ratio is a critical predictor, whereas market volatility has little role in any model. PLS and PCR place similar weights on all other predictors, potentially because these variables are highly correlated. Linear and generalized linear models strongly favor bond market variables, including the default spread and Treasury rate. Nonlinear methods (trees and neural networks) place great emphasis on exactly those predictors ignored by linear methods, such as term spreads and issuance activity.

Many accounting characteristics are not available at the monthly frequency, which might explain their low importance in [Figure 5](https://academic.oup.com/rfs/article/33/5/2223/). To investigate this, [Figure A.6 in the Internet Appendix](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) presents the rank of variables based on the annual return forecasts. Price trend variables become less important compared to the liquidity and risk measures, although they are still quite influential. The characteristics that were ranked in the bottom half of predictors at the monthly horizon remain largely unimportant at the annual horizon. The exception is industry (sic2), which shows substantial predictive power at the annual frequency.

#### 2.3.1 Marginal association between characteristics and expected returns

[Figure 6](https://academic.oup.com/rfs/article/33/5/2223/) traces out the model-implied marginal impact of individual characteristics on expected excess returns. Our data transformation normalizes characteristics to the (-1,1) interval, and holds all other variables fixed at their median value of zero. We choose four illustrative characteristics for the figure, including size (mvel1), momentum (mom12m), stock volatility (retvol), and accruals (acc).

First, [Figure 6](https://academic.oup.com/rfs/article/33/5/2223/) illustrates that machine learning methods identify patterns similar to some well-known empirical phenomena. For example, expected stock returns are decreasing in size, increasing in past 1-year return, and decreasing in stock volatility. And, interestingly, all methods agree on a nearly exact zero relationship between accruals and future returns. Second, the (penalized) linear model finds no predictive association between returns and either size or volatility, while trees and neural networks find large sensitivity of expected returns to both of these variables. For example, a firm that drops from median size to the 20th percentile of the size distribution experiences an increase in its annualized expected return of roughly 2.4% (0.002 $×$ 12 $×$ 100), and a firm whose volatility rises from median to 80th percentile experiences a decrease of around 3.0% per year, according to NN3, and these methods detect nonlinear predictive associations. The inability of linear models to capture nonlinearities can lead them to prefer a zero association, and this can in part explain the divergence in the performance of linear and nonlinear methods.

![Marginal association between expected returns and characteristics](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/m_hhaa009f6.jpeg?Expires=1752253962&Signature=F30njEf9uKaq8xOxcexq4Wz8Gtylw8AeW7idTVVzOkcj9kShZpzuT8ZVf092oJIcojssCz0P3Fm7sYlsnXZd6x76vIEZ31YITkks~7EhBwbeSkhQKLG4gFQY2orEr8tu6rQGiOL0xVcuLi7sC6hhIcTLRAcnBPaPqpXYkw8HXR3E-PFsmqHVZGhc4SYiZWIRYFYWnHiT-~rZp~1tS6djvfWCR0u4~CFqyxy-lxrZTjbA~EiMy0nlyu0F-7HY4oosC6s5vA7iV3dvHFm5mogrtp0UW8t~ElrzHfRml7eyu7JoN1fDM2QodCdYHpPuSpJtcqUHzW3GJiXTiBDa~Od1pA__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)

Figure 6

Marginal association between expected returns and characteristics

The panels should the sensitivity of expected monthly percentage returns (vertical axis) to the individual characteristics (holding all other covariates fixed at their median values).

[Open in new tab](https://academic.oup.com/view-large/figure/203502871/hhaa009f6.tif) [Download slide](https://academic.oup.com/DownloadFile/DownloadImage.aspx?image=https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009f6.jpeg?Expires=1752253962&Signature=yKaRlGrsSUG7xdxuVqY5WyVAAs3hYHibsmQ~Igs7j5Zq7aR51KSPZNopjf0pK7Ymlom94R-sxLxyr3tv2Yc06KjX9sCeV2J3pHRl1A0DVO7U1ugEGhdZzPuGWTbp0KQ42go~6GGc~AdHEnHUZG3K-wF~5smvv3170Ripx5JUuWPR6A9GeNfcbZKn4SMcxoF8L8H13JtbqTGW7xqj5Q806pFQ3VuFaSj~2guYAVqrotLWV70GYdHgRaBYQ1nPz6188WpL7mq8nAj71KE~gqqXYoCGsb9qjX02csjEumxNqHTWzzdoTu-J8jeYiGcrAJeRn84OuJ10dT6cScxD44CgJg__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA&sec=203502871&ar=5758276&xsltPath=~/UI/app/XSLT&imagename=&siteId=5511)

#### 2.3.2 Interaction effects

The favorable performance of trees and neural networks indicates a benefit to allowing for potentially complex interactions among predictors. Machine learning models are often referred to as “black boxes,” a term that is in some sense a misnomer, as the models are readily inspectable. They are, however, complex, and this is the source of both their power and their opacity. Any exploration of interaction effect is vexed by vast possibilities for identity and functional forms for interacting predictors. In this section, we present a handful of interaction results to help illustrate the inner workings of one black box method, the NN3 model.

As a first example, we examine a set of pairwise interaction effects in NN3. [Figure 7](https://academic.oup.com/rfs/article/33/5/2223/) reports how expected returns vary as we simultaneously vary values of a pair of characteristics over their support \[-1,1\], while holding all other variables fixed at their median value of zero. We show interactions of stock size (mvel1) with four other predictors: short-term reversal (mom1m), momentum (mom12m), and total and idiosyncratic volatility (retvol and idiovol, respectively).

The upper-left figure shows that the short-term reversal effect is strongest and is essentially linear among small stocks (blue line). Among large stocks (green line), reversal is concave, occurring primarily when the prior month return is positive. The upper-right figure shows the momentum effect, which is most pronounced among large stocks for the NN3 model.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">37</a></sup> Likewise, on the lower-left side, we see that the low volatility anomaly is also strongest among large stocks. For small stocks, the volatility effect is hump shaped. Finally, the lower-right side shows that NN3 estimates no interaction effect between size and accruals—the size lines are simply vertical shifts of the univariate accruals curve.

![Expected returns and characteristic interactions (NN3)](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/m_hhaa009f7.jpeg?Expires=1752253962&Signature=X8bE3AVHreU0YU6uORb~oYb2bjWZ5-z4zHD14JedBbpOToJCYK1b20xsq2909BFrpkvG344eifmUHyx4H84mLoYspYcnSIf~s~G0blYU34XG8nEWxZK46obA5maMljHaUZr0yodkD2Git0w3G0dnMsjYbr9GUPQOR~wkbATxTIJtOXrEhFWe0TRVFd0BWOjmyvF9jL1yV3KZfwImgwD6kCmWc8Mj~NWjnSUy2j6Zh2oTchupxLcMgpdJoPjjWWeqaMZ9mV60q1nrZmV5iN-ZLNElNFYMyn6TOC3Yc9szWgmAI-9TqpiOYLMEzTqLvVEymmMhpbS6EZAZu7xX6iS4IQ__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)

Figure 7

Expected returns and characteristic interactions (NN3)

The panels should the sensitivity of the expected monthly percentage returns (vertical axis) to the interactions effects for mvel1 with mom1m, mom12m, retvol, and acc in model NN3 (holding all other covariates fixed at their median values).

[Open in new tab](https://academic.oup.com/view-large/figure/203502876/hhaa009f7.tif) [Download slide](https://academic.oup.com/DownloadFile/DownloadImage.aspx?image=https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009f7.jpeg?Expires=1752253962&Signature=QUs3pgi2tqQuDKvEHRlxWm4F~T3f1-GUsdneTdrCS8QXGCh-7zx1jCPvYUiBqTXo-lO~Q8eOwad7ZVtOlxD7ae0MnXel8A2FozrTHRvKee7swNMGAzKsy0nVfgC7E05qSS0IVWFAWiAxEnIrTAYPzareA9aEAfOa2VZmO96c8w1O8yd85CM6PoERtmxyhJaCnxFFqW0A-o9DYfPKYs8TUV91Xmqlbcw1YLhuPMfRUNpaQxmJwz0UCvjfgQIbhkI0qOwKwTv0W7KKs8WWM1XnqpYP1Bht2VvE0wfuwo4Zw4jpu8QdmN-w3NAGXFag0z7-yWrpfjTJbJpaNjvec8w9yA__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA&sec=203502876&ar=5758276&xsltPath=~/UI/app/XSLT&imagename=&siteId=5511)

![Expected returns and characteristic/macroeconomic variable interactions (NN3)](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/m_hhaa009f8.jpeg?Expires=1752253962&Signature=vLB9ExMEmIOsM7lsxtoCFT-Wh3ESygoXxUxLTkONICkvqZtK0atH0P62lo5qW4TSDYO2khwGpeaikvhxoiFtNM0mDKP0NDnMs61B9nKriIgGWBZ0McaX7wdfceQ7Gp~DaybW1hTO~6avYTCrfaebTdkl-j-EqfQvSSSCVMbny7aHoIxPHxA7Krhy7vfWdbqosKfmIO96KvPYySu3qUpGs-Gy1VCey3--PLYBZX7YKJzU37~ovh8HH4VNCgO0KKomGnx2SmXOQCk4H0jSSrb2mSR2N4vvBr~wo-AzikAeXNK6f2Ci8Un0ino0Fkwd7743piBof8FE-0NWPJ3VKUPAww__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)

Figure 8

Expected returns and characteristic/macroeconomic variable interactions (NN3)

The panels show the sensitivity of expected monthly percentage returns (vertical axis) to interactions effects for mvel1 and retvol with bm and ntis in model NN3 (holding all other covariates fixed at their median values).

[Open in new tab](https://academic.oup.com/view-large/figure/203502877/hhaa009f8.tif) [Download slide](https://academic.oup.com/DownloadFile/DownloadImage.aspx?image=https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009f8.jpeg?Expires=1752253962&Signature=ZK62wAUvP2kSbF3PpCz7WN2WRHuFEYn4XEudC9klfxRBPIpUiyOJ8xUqf9sZXtLgn2UH9CYiifGtP0fa0QIXKUBXed4c5gVVhkrmjLaHRPEK~w5H5E75ys3lck1fZDLz6TVTIykT5CqmGi74E-LVukd5JKfWFmtltL1-sNfbNfgk~N2BY4baUYC7ADLw1Ye21nEflAxwCnwk6Xq5yNnZsO4mPNfU3uuFDqLdCbUmyQRBM9aOlBzsSCi-61jtJf7T0Gqnl1rVia7A3GMnJSDDucWlYOyCyei6MKbvxohvFG-kGmjR-TkRA7eELy~fAH~ilXmJl05TrLZHRKhWOVhckw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA&sec=203502877&ar=5758276&xsltPath=~/UI/app/XSLT&imagename=&siteId=5511)

[Figure 8](https://academic.oup.com/rfs/article/33/5/2223/) illustrates interactions between stock-level characteristics and macroeconomic indicator variables. It shows, for example, that the size effect is more pronounced when aggregate valuations are low (bm is high) and when equity issuance (ntis) is low, while the low volatility anomaly is especially strong in high valuation and high issuance environments. [Figure A.4 in the Internet Appendix](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) shows the 100 most important interactions of stock characteristics with macroeconomic indicators for each machine learning model. The most influential features come from interacting a stock’s recent price trends (e.g., momentum, short-term reversal, or industry momentum) with aggregate asset price levels (e.g., valuation ratios of the aggregate stock market or Treasury-bill rates). Furthermore, the dominant macroeconomic interactions are stable over time, as illustrated in [Figure A.5 in the Internet Appendix](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA).

### 2.4 Portfolio forecasts

So far, we have analyzed predictability of individual stock returns. Next, we compare forecasting performance of machine learning methods for aggregate portfolio returns. Analyzing forecasts at the portfolio-level comes with a number of benefits.

First, because all of our models are optimized for stock-level forecasts, portfolio forecasts provide an additional indirect evaluation of the model and its robustness. Second, aggregate portfolios tend to be of broader economic interest because they represent the risky-asset savings vehicles most commonly held by investors (via mutual funds, ETFs, and hedge funds). We study value-weight portfolios to assess the extent to which a model’s predictive performance thrives in the most valuable (and most economically important) assets in the economy. Third, the distribution of portfolio returns is sensitive to dependence among stock returns, with the implication that a good stock-level prediction model is not guaranteed to produce accurate portfolio-level forecasts. Bottom-up portfolio forecasts allow us to evaluate a model’s ability to transport its asset predictions, which occur at the finest asset level, into broader investment contexts. Last, but not least, the portfolio results are one step further “out of sample” in that the optimization routine does not directly account for the predictive performance of the portfolios.

Our assessment of forecast performance up to this point has been entirely statistical, relying on comparisons of predictive $R2$ ⁠. The final advantage of analyzing predictability at the portfolio level is that we can assess the *economic* contribution of each method via its contribution to risk-adjusted portfolio return performance.

#### 2.4.1 Prespecified portfolios

We build bottom-up forecasts by aggregating individual stock return predictions into portfolios. Given the weight of stock $i$ in portfolio $p$ (denoted $wi,tp$ ⁠) and given a model-based out-of-sample forecast for stock $i$ (denoted $r^i,t+1$ ⁠), we construct the portfolio return forecast as

This bottom-up approach works for any target portfolio whose weights are known a priori.

We form bottom-up forecasts for 30 of the most well-known portfolios in the empirical finance literature, including the S&P 500, the Fama-French size, value, profitability, investment, and momentum factor portfolios (SMB, HML, RMW, CMA, and UMD, respectively), and subcomponents of these Fama-French portfolios, including six size and value portfolios, six size and investment portfolios, six size and profitability portfolios, and six size and momentum portfolios. The subcomponent portfolios are long-only and therefore substantially overlap with the market index, whereas SMB, HML, RMW, CMA, and UMD are zero-net-investment long-short portfolios that are in large part purged of market exposure. In all cases, we create the portfolios ourselves using CRSP market equity value weights. Our portfolio construction differs slightly from the actual S&P 500 index and the characteristic-based Fama-French portfolios ([Fama and French 1993](https://academic.oup.com/rfs/article/33/5/2223/), [2015](https://academic.oup.com/rfs/article/33/5/2223/)), but has the virtue that we can exactly track the ex ante portfolio weights of each.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">38</a></sup>

Table 5

[Open in new tab](https://academic.oup.com/view-large/203502887)

Monthly portfolio-level out-of-sample predictive $R2$

<table><thead><tr><th></th><th>OLS-3+H</th><th>PLS</th><th>PCR</th><th>ENet+H</th><th>GLM+H</th><th>RF</th><th>GBRT+H</th><th>NN1</th><th>NN2</th><th>NN3</th><th>NN4</th><th>NN5</th></tr></thead><tbody><tr><td colspan="13"><em>A. Common factor portfolios</em></td></tr><tr><td>S&amp;P 500</td><td>−0.22</td><td>−0.86</td><td>−1.55</td><td>0.75</td><td>0.71</td><td>1.37</td><td>1.40</td><td>1.08</td><td>1.13</td><td>1.80</td><td>1.63</td><td>1.17</td></tr><tr><td>SMB</td><td>0.81</td><td>2.09</td><td>0.39</td><td>1.72</td><td>2.36</td><td>0.57</td><td>0.35</td><td>1.40</td><td>1.16</td><td>1.31</td><td>1.20</td><td>1.27</td></tr><tr><td>HML</td><td>0.66</td><td>0.50</td><td>1.21</td><td>0.46</td><td>0.84</td><td>0.98</td><td>0.21</td><td>1.22</td><td>1.31</td><td>1.06</td><td>1.25</td><td>1.24</td></tr><tr><td>RMW</td><td>−2.35</td><td>1.19</td><td>0.41</td><td>−1.07</td><td>−0.06</td><td>−0.54</td><td>−0.92</td><td>0.68</td><td>0.47</td><td>0.84</td><td>0.53</td><td>0.54</td></tr><tr><td>CMA</td><td>0.80</td><td>−0.44</td><td>0.03</td><td>−1.07</td><td>1.24</td><td>−0.11</td><td>−1.04</td><td>1.88</td><td>1.60</td><td>1.06</td><td>1.84</td><td>1.31</td></tr><tr><td>UMD</td><td>−0.90</td><td>−1.09</td><td>−0.47</td><td>0.47</td><td>−0.37</td><td>1.37</td><td>−0.25</td><td>−0.56</td><td>−0.26</td><td>0.19</td><td>0.27</td><td>0.35</td></tr><tr><td colspan="13"><em>B. Subcomponents of factor portfolios</em></td></tr><tr><td>Big value</td><td>0.10</td><td>0.00</td><td>−0.33</td><td>0.25</td><td>0.59</td><td>1.31</td><td>1.06</td><td>0.85</td><td>0.87</td><td>1.46</td><td>1.21</td><td>0.99</td></tr><tr><td>Big growth</td><td>−0.33</td><td>−1.26</td><td>−1.62</td><td>0.70</td><td>0.51</td><td>1.32</td><td>1.19</td><td>1.00</td><td>1.10</td><td>1.50</td><td>1.24</td><td>1.11</td></tr><tr><td>Big neutral</td><td>−0.17</td><td>−1.09</td><td>−1.51</td><td>0.80</td><td>0.36</td><td>1.31</td><td>1.28</td><td>1.43</td><td>1.24</td><td>1.70</td><td>1.81</td><td>1.40</td></tr><tr><td>Small value</td><td>0.30</td><td>1.66</td><td>1.05</td><td>0.64</td><td>0.85</td><td>1.24</td><td>0.52</td><td>1.59</td><td>1.37</td><td>1.54</td><td>1.40</td><td>1.30</td></tr><tr><td>Small growth</td><td>−0.16</td><td>0.14</td><td>−0.18</td><td>−0.33</td><td>−0.12</td><td>0.71</td><td>1.24</td><td>0.05</td><td>0.42</td><td>0.48</td><td>0.41</td><td>0.50</td></tr><tr><td>Small neutral</td><td>−0.27</td><td>0.60</td><td>0.19</td><td>0.21</td><td>0.28</td><td>0.88</td><td>0.36</td><td>0.58</td><td>0.62</td><td>0.70</td><td>0.58</td><td>0.68</td></tr><tr><td>Big conservative</td><td>−0.57</td><td>−0.10</td><td>−1.06</td><td>1.02</td><td>0.46</td><td>1.11</td><td>0.55</td><td>1.15</td><td>1.13</td><td>1.59</td><td>1.37</td><td>1.07</td></tr><tr><td>Big aggressive</td><td>0.20</td><td>−0.80</td><td>−1.15</td><td>0.30</td><td>0.67</td><td>1.75</td><td>2.00</td><td>1.33</td><td>1.51</td><td>1.78</td><td>1.55</td><td>1.42</td></tr><tr><td>Big neutral</td><td>−0.29</td><td>−1.75</td><td>−1.96</td><td>0.83</td><td>0.48</td><td>1.13</td><td>0.77</td><td>0.85</td><td>0.85</td><td>1.51</td><td>1.45</td><td>1.16</td></tr><tr><td>Small conservative</td><td>−0.05</td><td>1.17</td><td>0.71</td><td>−0.02</td><td>0.34</td><td>0.96</td><td>0.56</td><td>0.82</td><td>0.87</td><td>0.96</td><td>0.90</td><td>0.83</td></tr><tr><td>Small aggressive</td><td>−0.10</td><td>0.51</td><td>0.01</td><td>−0.09</td><td>0.14</td><td>1.00</td><td>1.46</td><td>0.34</td><td>0.64</td><td>0.75</td><td>0.62</td><td>0.71</td></tr><tr><td>Small neutral</td><td>−0.30</td><td>0.45</td><td>0.12</td><td>0.42</td><td>0.35</td><td>0.76</td><td>−0.01</td><td>0.70</td><td>0.69</td><td>0.83</td><td>0.66</td><td>0.72</td></tr><tr><td>Big robust</td><td>−1.02</td><td>−1.08</td><td>−2.06</td><td>0.55</td><td>0.35</td><td>1.10</td><td>0.33</td><td>0.74</td><td>0.79</td><td>1.28</td><td>1.03</td><td>0.74</td></tr><tr><td>Big weak</td><td>−0.12</td><td>1.42</td><td>1.07</td><td>0.89</td><td>1.10</td><td>1.33</td><td>1.77</td><td>1.79</td><td>1.79</td><td>2.05</td><td>1.66</td><td>1.60</td></tr><tr><td>Big neutral</td><td>0.86</td><td>−1.22</td><td>−1.26</td><td>0.41</td><td>0.13</td><td>1.10</td><td>0.91</td><td>0.84</td><td>0.94</td><td>1.19</td><td>1.15</td><td>0.99</td></tr><tr><td>Small robust</td><td>−0.71</td><td>0.35</td><td>−0.38</td><td>−0.04</td><td>−0.42</td><td>0.70</td><td>0.19</td><td>0.24</td><td>0.50</td><td>0.63</td><td>0.53</td><td>0.55</td></tr><tr><td>Small weak</td><td>0.05</td><td>1.06</td><td>0.59</td><td>−0.13</td><td>0.44</td><td>1.05</td><td>1.42</td><td>0.71</td><td>0.92</td><td>0.99</td><td>0.90</td><td>0.89</td></tr><tr><td>Small neutral</td><td>−0.51</td><td>0.07</td><td>−0.47</td><td>−0.33</td><td>−0.32</td><td>0.60</td><td>−0.08</td><td>0.10</td><td>0.25</td><td>0.38</td><td>0.32</td><td>0.41</td></tr><tr><td>Big up</td><td>0.20</td><td>−0.25</td><td>−1.24</td><td>0.66</td><td>1.17</td><td>1.18</td><td>0.90</td><td>0.80</td><td>0.76</td><td>1.13</td><td>1.12</td><td>0.93</td></tr><tr><td>Big down</td><td>−1.54</td><td>−1.63</td><td>−1.55</td><td>0.44</td><td>−0.33</td><td>1.14</td><td>0.71</td><td>0.36</td><td>0.70</td><td>1.07</td><td>0.90</td><td>0.84</td></tr><tr><td>Big medium</td><td>−0.04</td><td>−1.51</td><td>−1.94</td><td>0.81</td><td>−0.08</td><td>1.57</td><td>1.80</td><td>1.29</td><td>1.32</td><td>1.71</td><td>1.55</td><td>1.23</td></tr><tr><td>Small up</td><td>0.07</td><td>0.78</td><td>0.56</td><td>−0.07</td><td>0.25</td><td>0.62</td><td>−0.03</td><td>0.06</td><td>0.07</td><td>0.21</td><td>0.19</td><td>0.25</td></tr><tr><td>Small down</td><td>−0.21</td><td>0.15</td><td>−0.20</td><td>0.15</td><td>−0.01</td><td>1.51</td><td>1.38</td><td>0.74</td><td>0.82</td><td>1.02</td><td>0.91</td><td>0.96</td></tr><tr><td>Small medium</td><td>0.07</td><td>0.82</td><td>0.20</td><td>0.59</td><td>0.37</td><td>1.22</td><td>1.06</td><td>1.09</td><td>1.09</td><td>1.18</td><td>1.00</td><td>1.03</td></tr></tbody></table>

In this table, we report the out-of-sample predictive $R2$ s for thirty portfolios using OLS with size, book-to-market, momentum, OLS-3, PLS, PCR, elastic net (ENet), generalized linear model with group lasso (GLM), random forest (RF), gradient boosted regression trees (GBRT), and five architectures of neural networks (NN1,...,NN5). “+H” indicates the use of Huber loss instead of the $l2$ loss. The six portfolios in panel A are the S&P 500 index and the Fama-French SMB, HML, CMA, RMW, and UMD factors. The twenty-four portfolios in panel B are $3×2$ size double-sorted portfolios used in the construction of the Fama-French value, investment, profitability, and momentum factors.

[Table 5](https://academic.oup.com/rfs/article/33/5/2223/) reports the monthly out-of-sample $R2$ over our 30-year testing sample. Regularized linear methods fail to outperform naive constant forecasts of the S&P 500. In contrast, all nonlinear models have substantial positive predictive performance. The 1-month out-of-sample $R2$ is 0.71% for the generalized linear model and reaches as high as 1.80% for the three-layer neural network. As a benchmark for comparison, nearly all of the macroeconomic return predictor variables in the survey of [Welch and Goyal (2008)](https://academic.oup.com/rfs/article/33/5/2223/) fail to produce a positive out-of-sample forecast $R2$ ⁠. [Kelly and Pruitt (2013)](https://academic.oup.com/rfs/article/33/5/2223/) find that PLS delivers an out-of-sample forecasting $R2$ around 1% per month for the aggregate market index, though their forecasts directly target the market return as opposed to being bottom-up forecasts. And the most well-studied portfolio predictors, such as the aggregate price-dividend ratio, typically produce an *in-sample* predictive $R2$ of around 1% per month (e.g., [Cochrane 2007](https://academic.oup.com/rfs/article/33/5/2223/)), smaller than what we find *out of sample*.

The patterns in S&P 500 forecasting performance across models carry over to long-only characteristic-sorted portfolios (rows 2–25) and long-short factor portfolios (SMB, HML, RMW, CMA, and UMD). Nonlinear methods excel. NN3–NN5 produce a positive $Roos2$ for *every* portfolio analyzed, with NN3 dominating. NN1 and NN2 also produce a positive $Roos2$ for all but UMD (which is by and large the most difficult strategy to forecast). The generalized linear model $Roos2$ is positive for 22 of 30 portfolios. Linear methods, on the other hand, are on balance unreliable for bottom-up portfolio return forecasting, though their performance tends to be better for “big” portfolios compared to “small.” For select long-short factor portfolios (e.g., SMB), constrained linear methods, such as PLS, perform comparatively well (consistent with the findings of [Kelly and Pruitt 2013](https://academic.oup.com/rfs/article/33/5/2223/)). In short, machine learning methods and nonlinear methods, in particular, produce unusually powerful out-of-sample portfolio predictions.

Next, we assess the economic magnitudes of portfolio predictability. [Campbell and Thompson (2008)](https://academic.oup.com/rfs/article/33/5/2223/) show that small improvements in $R2$ can map into large utility gains for a mean-variance investor. They show that the Sharpe ratio (⁠ $SR∗$ ⁠) earned by an active investor exploiting predictive information (summarized as a predictive $R2$ ⁠) improves over the Sharpe ratio (⁠ $SR$ ⁠) earned by a buy-and-hold investor according to

We use this formula to translate the predictive $Roos2$ of [Table 5](https://academic.oup.com/rfs/article/33/5/2223/) (along with the full-sample Sharpe ratio of each portfolio) into an improvement in annualized Sharpe ratio, $SR∗−SR$ ⁠, for an investor exploiting machine learning predictions for portfolio timing. [Table A.7 in the Internet Appendix](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) presents the results. For example, the buy-and-hold Sharpe ratio of the S&P 500, which is 0.51 in our 30-year out-of-sample period, can be improved to 0.71 by a market-timer exploiting forecasts from the NN3 model. For characteristic-based portfolios, nonlinear machine learning methods help improve Sharpe ratios by anywhere from a few percentage points to over 24 percentage points.

[Campbell and Thompson (2008)](https://academic.oup.com/rfs/article/33/5/2223/) also propose evaluating the economic magnitude of portfolio predictability with a market timing trading strategy. We follow their out-of-sample trading strategy exactly, scaling up/down positions each month as expected returns rise/fall, while imposing a maximum leverage constraint of 50% and excluding short sales for long-only portfolios (we do not impose these constraints for long-short factor portfolios). [Table 6](https://academic.oup.com/rfs/article/33/5/2223/) reports the annualized Sharpe ratio gains (relative to a buy-and-hold strategy) for timing strategies based on machine learning forecasts. Consistent with our other results, the strongest and most consistent trading strategies are those based on nonlinear models, with neural networks the best overall. In the case of NN3, the Sharpe ratio from timing the S&P 500 index 0.77, or 26 percentage points higher than a buy-and-hold position. Long-short factor portfolios are more difficult to time than the S&P 500 and the other 24 long-only portfolios, and all methods fail to outperform the static UMD strategy.

Table 6

[Open in new tab](https://academic.oup.com/view-large/203502893)

Market timing Sharpe ratio gains

<table><thead><tr><th></th><th>OLS-3+H</th><th>PLS</th><th>PCR</th><th>ENet+H</th><th>GLM+H</th><th>RF</th><th>GBRT+H</th><th>NN1</th><th>NN2</th><th>NN3</th><th>NN4</th><th>NN5</th></tr></thead><tbody><tr><td colspan="13"><em>A. Common factor portfolios</em></td></tr><tr><td>S&amp;P 500</td><td>0.07</td><td>0.05</td><td>−0.06</td><td>0.12</td><td>0.19</td><td>0.18</td><td>0.19</td><td>0.22</td><td>0.20</td><td>0.26</td><td>0.22</td><td>0.19</td></tr><tr><td>SMB</td><td>0.06</td><td>0.17</td><td>0.09</td><td>0.24</td><td>0.26</td><td>0.00</td><td>−0.07</td><td>0.21</td><td>0.18</td><td>0.15</td><td>0.09</td><td>0.11</td></tr><tr><td>HML</td><td>0.00</td><td>0.01</td><td>0.04</td><td>−0.03</td><td>−0.02</td><td>0.04</td><td>0.02</td><td>0.04</td><td>0.06</td><td>0.04</td><td>0.02</td><td>0.01</td></tr><tr><td>RMW</td><td>0.00</td><td>−0.01</td><td>−0.06</td><td>−0.19</td><td>−0.13</td><td>−0.11</td><td>−0.01</td><td>−0.03</td><td>−0.09</td><td>0.01</td><td>0.01</td><td>−0.07</td></tr><tr><td>CMA</td><td>0.02</td><td>0.02</td><td>0</td><td>−0.09</td><td>−0.05</td><td>0.08</td><td>−0.01</td><td>0.00</td><td>0.01</td><td>0.05</td><td>0.04</td><td>0.06</td></tr><tr><td>UMD</td><td>0.01</td><td>−0.06</td><td>−0.02</td><td>−0.02</td><td>−0.07</td><td>−0.04</td><td>−0.07</td><td>−0.04</td><td>−0.08</td><td>−0.04</td><td>−0.10</td><td>−0.01</td></tr><tr><td colspan="13"><em>B. Subcomponents of factor portfolios</em></td></tr><tr><td>Big value</td><td>−0.01</td><td>0.06</td><td>−0.03</td><td>0.09</td><td>0.06</td><td>0.09</td><td>0.08</td><td>0.11</td><td>0.11</td><td>0.13</td><td>0.10</td><td>0.11</td></tr><tr><td>Big growth</td><td>0.08</td><td>−0.01</td><td>−0.08</td><td>0.10</td><td>0.17</td><td>0.20</td><td>0.21</td><td>0.22</td><td>0.20</td><td>0.26</td><td>0.22</td><td>0.21</td></tr><tr><td>Big neutral</td><td>0.06</td><td>0.03</td><td>−0.06</td><td>0.11</td><td>0.16</td><td>0.13</td><td>0.17</td><td>0.23</td><td>0.21</td><td>0.23</td><td>0.23</td><td>0.21</td></tr><tr><td>Small value</td><td>−0.04</td><td>0.15</td><td>0.09</td><td>0.01</td><td>0.08</td><td>0.07</td><td>0.08</td><td>0.11</td><td>0.11</td><td>0.10</td><td>0.11</td><td>0.13</td></tr><tr><td>Small growth</td><td>0.00</td><td>0.03</td><td>−0.06</td><td>−0.03</td><td>−0.05</td><td>0.04</td><td>0.05</td><td>0.02</td><td>0.03</td><td>0.03</td><td>0.02</td><td>0.02</td></tr><tr><td>Small neutral</td><td>0.02</td><td>0.09</td><td>0.05</td><td>0.03</td><td>0.04</td><td>0.11</td><td>0.11</td><td>0.09</td><td>0.08</td><td>0.10</td><td>0.09</td><td>0.11</td></tr><tr><td>Big conservative</td><td>0.08</td><td>0.02</td><td>−0.04</td><td>0.08</td><td>0.15</td><td>0.09</td><td>0.13</td><td>0.17</td><td>0.14</td><td>0.19</td><td>0.16</td><td>0.14</td></tr><tr><td>Big aggressive</td><td>0.08</td><td>−0.01</td><td>−0.11</td><td>0.01</td><td>0.13</td><td>0.22</td><td>0.18</td><td>0.21</td><td>0.19</td><td>0.23</td><td>0.20</td><td>0.20</td></tr><tr><td>Big neutral</td><td>0.04</td><td>−0.01</td><td>−0.08</td><td>0.09</td><td>0.11</td><td>0.09</td><td>0.11</td><td>0.13</td><td>0.12</td><td>0.18</td><td>0.18</td><td>0.16</td></tr><tr><td>Small conservative</td><td>0.04</td><td>0.17</td><td>0.12</td><td>0.02</td><td>0.05</td><td>0.17</td><td>0.15</td><td>0.11</td><td>0.11</td><td>0.14</td><td>0.13</td><td>0.15</td></tr><tr><td>Small aggressive</td><td>0.01</td><td>0.05</td><td>−0.06</td><td>−0.05</td><td>−0.03</td><td>0.08</td><td>0.06</td><td>0.02</td><td>0.05</td><td>0.06</td><td>0.04</td><td>0.05</td></tr><tr><td>Small neutral</td><td>0.01</td><td>0.06</td><td>0.03</td><td>0.01</td><td>0.04</td><td>0.08</td><td>0.09</td><td>0.07</td><td>0.06</td><td>0.08</td><td>0.07</td><td>0.09</td></tr><tr><td>Big robust</td><td>0.10</td><td>0.07</td><td>−0.07</td><td>0.11</td><td>0.18</td><td>0.17</td><td>0.18</td><td>0.18</td><td>0.16</td><td>0.22</td><td>0.19</td><td>0.16</td></tr><tr><td>Big weak</td><td>0.05</td><td>0.12</td><td>0.05</td><td>0.09</td><td>0.12</td><td>0.21</td><td>0.17</td><td>0.22</td><td>0.20</td><td>0.21</td><td>0.18</td><td>0.19</td></tr><tr><td>Big neutral</td><td>0.09</td><td>0.00</td><td>−0.04</td><td>0.09</td><td>0.20</td><td>0.19</td><td>0.17</td><td>0.22</td><td>0.21</td><td>0.24</td><td>0.21</td><td>0.20</td></tr><tr><td>Small robust</td><td>0.09</td><td>0.04</td><td>−0.03</td><td>0.00</td><td>0.00</td><td>0.10</td><td>0.07</td><td>0.04</td><td>0.05</td><td>0.08</td><td>0.08</td><td>0.08</td></tr><tr><td>Small weak</td><td>−0.03</td><td>0.09</td><td>0.00</td><td>−0.03</td><td>−0.02</td><td>0.07</td><td>0.07</td><td>0.06</td><td>0.06</td><td>0.06</td><td>0.05</td><td>0.06</td></tr><tr><td>Small neutral</td><td>0.04</td><td>0.04</td><td>−0.03</td><td>0.00</td><td>0.01</td><td>0.11</td><td>0.09</td><td>0.04</td><td>0.04</td><td>0.07</td><td>0.07</td><td>0.08</td></tr><tr><td>Big up</td><td>0.10</td><td>0.05</td><td>−0.06</td><td>0.10</td><td>0.21</td><td>0.16</td><td>0.14</td><td>0.17</td><td>0.14</td><td>0.17</td><td>0.18</td><td>0.17</td></tr><tr><td>Big down</td><td>−0.02</td><td>0.09</td><td>−0.08</td><td>−0.02</td><td>0.02</td><td>0.08</td><td>0.10</td><td>0.10</td><td>0.07</td><td>0.12</td><td>0.11</td><td>0.09</td></tr><tr><td>Big medium</td><td>−0.01</td><td>0.04</td><td>−0.06</td><td>0.14</td><td>0.09</td><td>0.17</td><td>0.20</td><td>0.22</td><td>0.21</td><td>0.25</td><td>0.22</td><td>0.19</td></tr><tr><td>Small up</td><td>0.08</td><td>0.13</td><td>0.10</td><td>0.05</td><td>0.07</td><td>0.16</td><td>0.12</td><td>0.07</td><td>0.06</td><td>0.08</td><td>0.07</td><td>0.10</td></tr><tr><td>Small down</td><td>−0.14</td><td>0.04</td><td>−0.05</td><td>−0.09</td><td>−0.05</td><td>0.06</td><td>0.04</td><td>0.01</td><td>0.01</td><td>0.02</td><td>0.01</td><td>0.01</td></tr><tr><td>Small medium</td><td>0.05</td><td>0.11</td><td>0.07</td><td>0.08</td><td>0.09</td><td>0.13</td><td>0.15</td><td>0.13</td><td>0.12</td><td>0.14</td><td>0.13</td><td>0.15</td></tr></tbody></table>

This table documents improvement in annualized Sharpe ratio (⁠ $SR∗−SR$ ⁠). We compute the $SR∗$ by weighting the portfolios based on a market timing strategy (see [Campbell and Thompson 2008](https://academic.oup.com/rfs/article/33/5/2223/)).

As a robustness test, we also analyze bottom-up predictions for annual rather than monthly returns. The comparative patterns in predictive performance across methods is the same in annual and monthly data. [Table A.8](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) in the [Internet Appendix](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) demonstrates the superiority of nonlinear methods and in particular neural networks. NN3 continues to dominate for the market portfolio, achieving an annual $Roos2$ of $15.7%$ ⁠.

#### 2.4.2 Machine learning portfolios

Table 7

[Open in new tab](https://academic.oup.com/view-large/203502896)

Performance of the machine learning portfolios

<table><thead><tr><th></th><th colspan="4">OLS-3+H</th><th colspan="4">PLS</th><th colspan="4">PCR</th></tr><tr><th></th><th>Pred</th><th>Avg</th><th>SD</th><th>SR</th><th>Pred</th><th>Avg</th><th>SD</th><th>SR</th><th>Pred</th><th>Avg</th><th>SD</th><th>SR</th></tr></thead><tbody><tr><td>Low(L)</td><td>−0.17</td><td>0.40</td><td>5.90</td><td>0.24</td><td>−0.83</td><td>0.29</td><td>5.31</td><td>0.19</td><td>−0.68</td><td>0.03</td><td>5.98</td><td>0.02</td></tr><tr><td>2</td><td>0.17</td><td>0.58</td><td>4.65</td><td>0.43</td><td>−0.21</td><td>0.55</td><td>4.96</td><td>0.38</td><td>−0.11</td><td>0.42</td><td>5.25</td><td>0.28</td></tr><tr><td>3</td><td>0.35</td><td>0.60</td><td>4.43</td><td>0.47</td><td>0.12</td><td>0.64</td><td>4.63</td><td>0.48</td><td>0.19</td><td>0.53</td><td>4.94</td><td>0.37</td></tr><tr><td>4</td><td>0.49</td><td>0.71</td><td>4.32</td><td>0.57</td><td>0.38</td><td>0.78</td><td>4.30</td><td>0.63</td><td>0.42</td><td>0.68</td><td>4.64</td><td>0.51</td></tr><tr><td>5</td><td>0.62</td><td>0.79</td><td>4.57</td><td>0.60</td><td>0.61</td><td>0.77</td><td>4.53</td><td>0.59</td><td>0.62</td><td>0.81</td><td>4.66</td><td>0.60</td></tr><tr><td>6</td><td>0.75</td><td>0.92</td><td>5.03</td><td>0.63</td><td>0.84</td><td>0.88</td><td>4.78</td><td>0.64</td><td>0.81</td><td>0.81</td><td>4.58</td><td>0.61</td></tr><tr><td>7</td><td>0.88</td><td>0.85</td><td>5.18</td><td>0.57</td><td>1.06</td><td>0.92</td><td>4.89</td><td>0.65</td><td>1.01</td><td>0.87</td><td>4.72</td><td>0.64</td></tr><tr><td>8</td><td>1.02</td><td>0.86</td><td>5.29</td><td>0.56</td><td>1.32</td><td>0.92</td><td>5.14</td><td>0.62</td><td>1.23</td><td>1.01</td><td>4.77</td><td>0.73</td></tr><tr><td>9</td><td>1.21</td><td>1.18</td><td>5.47</td><td>0.75</td><td>1.66</td><td>1.15</td><td>5.24</td><td>0.76</td><td>1.52</td><td>1.20</td><td>4.88</td><td>0.86</td></tr><tr><td>High(H)</td><td>1.51</td><td>1.34</td><td>5.88</td><td>0.79</td><td>2.25</td><td>1.30</td><td>5.85</td><td>0.77</td><td>2.02</td><td>1.25</td><td>5.60</td><td>0.77</td></tr><tr><td>H-L</td><td>1.67</td><td>0.94</td><td>5.33</td><td>0.61</td><td>3.09</td><td>1.02</td><td>4.88</td><td>0.72</td><td>2.70</td><td>1.22</td><td>4.82</td><td>0.88</td></tr></tbody></table>

<table><thead><tr><th></th><th colspan="4">ENet+H</th><th colspan="4">GLM+H</th><th colspan="4">RF</th></tr><tr><th></th><th>Pred</th><th>Avg</th><th>SD</th><th>SR</th><th>Pred</th><th>Avg</th><th>SD</th><th>SR</th><th>Pred</th><th>Avg</th><th>SD</th><th>SR</th></tr></thead><tbody><tr><td>Low(L)</td><td>−0.04</td><td>0.24</td><td>5.44</td><td>0.15</td><td>−0.47</td><td>0.08</td><td>5.65</td><td>0.05</td><td>0.29</td><td>−0.09</td><td>6.00</td><td>−0.05</td></tr><tr><td>2</td><td>0.27</td><td>0.56</td><td>4.84</td><td>0.40</td><td>0.01</td><td>0.49</td><td>4.80</td><td>0.35</td><td>0.44</td><td>0.38</td><td>5.02</td><td>0.27</td></tr><tr><td>3</td><td>0.44</td><td>0.53</td><td>4.50</td><td>0.40</td><td>0.29</td><td>0.65</td><td>4.52</td><td>0.50</td><td>0.53</td><td>0.64</td><td>4.70</td><td>0.48</td></tr><tr><td>4</td><td>0.59</td><td>0.72</td><td>4.11</td><td>0.61</td><td>0.50</td><td>0.72</td><td>4.59</td><td>0.55</td><td>0.60</td><td>0.60</td><td>4.56</td><td>0.46</td></tr><tr><td>5</td><td>0.73</td><td>0.72</td><td>4.42</td><td>0.57</td><td>0.68</td><td>0.70</td><td>4.55</td><td>0.53</td><td>0.67</td><td>0.57</td><td>4.51</td><td>0.44</td></tr><tr><td>6</td><td>0.87</td><td>0.85</td><td>4.60</td><td>0.64</td><td>0.84</td><td>0.84</td><td>4.53</td><td>0.65</td><td>0.73</td><td>0.64</td><td>4.54</td><td>0.49</td></tr><tr><td>7</td><td>1.01</td><td>0.87</td><td>4.75</td><td>0.64</td><td>1.00</td><td>0.86</td><td>4.82</td><td>0.62</td><td>0.80</td><td>0.67</td><td>4.65</td><td>0.50</td></tr><tr><td>8</td><td>1.16</td><td>0.88</td><td>5.20</td><td>0.59</td><td>1.18</td><td>0.87</td><td>5.18</td><td>0.58</td><td>0.87</td><td>1.00</td><td>4.91</td><td>0.71</td></tr><tr><td>9</td><td>1.36</td><td>0.80</td><td>5.61</td><td>0.50</td><td>1.40</td><td>1.04</td><td>5.44</td><td>0.66</td><td>0.96</td><td>1.23</td><td>5.59</td><td>0.76</td></tr><tr><td>High(H)</td><td>1.66</td><td>0.84</td><td>6.76</td><td>0.43</td><td>1.81</td><td>1.14</td><td>6.33</td><td>0.62</td><td>1.12</td><td>1.53</td><td>7.27</td><td>0.73</td></tr><tr><td>H-L</td><td>1.70</td><td>0.60</td><td>5.37</td><td>0.39</td><td>2.27</td><td>1.06</td><td>4.79</td><td>0.76</td><td>0.83</td><td>1.62</td><td>5.75</td><td>0.98</td></tr></tbody></table>

<table><thead><tr><th></th><th colspan="4">GBRT+H</th><th colspan="4">NN1</th><th colspan="4">NN2</th></tr><tr><th></th><th>Pred</th><th>Avg</th><th>SD</th><th>SR</th><th>Pred</th><th>Avg</th><th>SD</th><th>SR</th><th>Pred</th><th>Avg</th><th>SD</th><th>SR</th></tr></thead><tbody><tr><td>Low(L)</td><td>−0.45</td><td>0.18</td><td>5.60</td><td>0.11</td><td>−0.38</td><td>−0.29</td><td>7.02</td><td>−0.14</td><td>−0.23</td><td>−0.54</td><td>7.83</td><td>−0.24</td></tr><tr><td>2</td><td>−0.16</td><td>0.49</td><td>4.93</td><td>0.35</td><td>0.16</td><td>0.41</td><td>5.89</td><td>0.24</td><td>0.21</td><td>0.36</td><td>6.08</td><td>0.20</td></tr><tr><td>3</td><td>0.02</td><td>0.59</td><td>4.75</td><td>0.43</td><td>0.44</td><td>0.51</td><td>5.07</td><td>0.35</td><td>0.44</td><td>0.65</td><td>5.07</td><td>0.44</td></tr><tr><td>4</td><td>0.17</td><td>0.63</td><td>4.68</td><td>0.46</td><td>0.64</td><td>0.70</td><td>4.56</td><td>0.53</td><td>0.59</td><td>0.73</td><td>4.53</td><td>0.56</td></tr><tr><td>5</td><td>0.34</td><td>0.57</td><td>4.70</td><td>0.42</td><td>0.80</td><td>0.77</td><td>4.37</td><td>0.61</td><td>0.72</td><td>0.81</td><td>4.38</td><td>0.64</td></tr><tr><td>6</td><td>0.46</td><td>0.77</td><td>4.48</td><td>0.59</td><td>0.95</td><td>0.78</td><td>4.39</td><td>0.62</td><td>0.84</td><td>0.84</td><td>4.51</td><td>0.65</td></tr><tr><td>7</td><td>0.59</td><td>0.52</td><td>4.73</td><td>0.38</td><td>1.11</td><td>0.81</td><td>4.40</td><td>0.64</td><td>0.97</td><td>0.95</td><td>4.61</td><td>0.71</td></tr><tr><td>8</td><td>0.72</td><td>0.72</td><td>4.92</td><td>0.51</td><td>1.31</td><td>0.75</td><td>4.86</td><td>0.54</td><td>1.13</td><td>0.93</td><td>5.09</td><td>0.63</td></tr><tr><td>9</td><td>0.88</td><td>0.99</td><td>5.19</td><td>0.66</td><td>1.58</td><td>0.96</td><td>5.22</td><td>0.64</td><td>1.37</td><td>1.04</td><td>5.69</td><td>0.63</td></tr><tr><td>High(H)</td><td>1.11</td><td>1.17</td><td>5.88</td><td>0.69</td><td>2.19</td><td>1.52</td><td>6.79</td><td>0.77</td><td>1.99</td><td>1.38</td><td>6.98</td><td>0.69</td></tr><tr><td>H-L</td><td>1.56</td><td>0.99</td><td>4.22</td><td>0.81</td><td>2.57</td><td>1.81</td><td>5.34</td><td>1.17</td><td>2.22</td><td>1.92</td><td>5.75</td><td>1.16</td></tr></tbody></table>

<table><thead><tr><th></th><th colspan="4">NN3</th><th colspan="4">NN4</th><th colspan="4">NN5</th></tr><tr><th></th><th>Pred</th><th>Avg</th><th>SD</th><th>SR</th><th>Pred</th><th>Avg</th><th>SD</th><th>SR</th><th>Pred</th><th>Avg</th><th>SD</th><th>SR</th></tr></thead><tbody><tr><td>Low(L)</td><td>−0.03</td><td>−0.43</td><td>7.73</td><td>−0.19</td><td>−0.12</td><td>−0.52</td><td>7.69</td><td>−0.23</td><td>−0.23</td><td>−0.51</td><td>7.69</td><td>−0.23</td></tr><tr><td>2</td><td>0.34</td><td>0.30</td><td>6.38</td><td>0.16</td><td>0.30</td><td>0.33</td><td>6.16</td><td>0.19</td><td>0.23</td><td>0.31</td><td>6.10</td><td>0.17</td></tr><tr><td>3</td><td>0.51</td><td>0.57</td><td>5.27</td><td>0.37</td><td>0.50</td><td>0.42</td><td>5.18</td><td>0.28</td><td>0.45</td><td>0.54</td><td>5.02</td><td>0.37</td></tr><tr><td>4</td><td>0.63</td><td>0.66</td><td>4.69</td><td>0.49</td><td>0.62</td><td>0.60</td><td>4.51</td><td>0.46</td><td>0.60</td><td>0.67</td><td>4.47</td><td>0.52</td></tr><tr><td>5</td><td>0.71</td><td>0.69</td><td>4.41</td><td>0.55</td><td>0.72</td><td>0.69</td><td>4.26</td><td>0.56</td><td>0.73</td><td>0.77</td><td>4.32</td><td>0.62</td></tr><tr><td>6</td><td>0.79</td><td>0.76</td><td>4.46</td><td>0.59</td><td>0.81</td><td>0.84</td><td>4.46</td><td>0.65</td><td>0.85</td><td>0.86</td><td>4.35</td><td>0.68</td></tr><tr><td>7</td><td>0.88</td><td>0.99</td><td>4.77</td><td>0.72</td><td>0.90</td><td>0.93</td><td>4.56</td><td>0.70</td><td>0.96</td><td>0.88</td><td>4.76</td><td>0.64</td></tr><tr><td>8</td><td>1.00</td><td>1.09</td><td>5.47</td><td>0.69</td><td>1.03</td><td>1.08</td><td>5.13</td><td>0.73</td><td>1.11</td><td>0.94</td><td>5.17</td><td>0.63</td></tr><tr><td>9</td><td>1.21</td><td>1.25</td><td>5.94</td><td>0.73</td><td>1.23</td><td>1.26</td><td>5.93</td><td>0.74</td><td>1.34</td><td>1.02</td><td>6.02</td><td>0.58</td></tr><tr><td>High(H)</td><td>1.83</td><td>1.69</td><td>7.29</td><td>0.80</td><td>1.89</td><td>1.75</td><td>7.51</td><td>0.81</td><td>1.99</td><td>1.46</td><td>7.40</td><td>0.68</td></tr><tr><td>H-L</td><td>1.86</td><td>2.12</td><td>6.13</td><td>1.20</td><td>2.01</td><td>2.26</td><td>5.80</td><td>1.35</td><td>2.22</td><td>1.97</td><td>5.93</td><td>1.15</td></tr></tbody></table>

In this table, we report the performance of prediction-sorted portfolios over the 30-year out-of-sample testing period. All stocks are sorted into deciles based on their predicted returns for the next month. Columns “Pred,” “Avg,” “SD,” and “SR” provide the predicted monthly returns for each decile, the average realized monthly returns, their standard deviations, and Sharpe ratios, respectively. All portfolios are value weighted.

Next, rather than assessing forecast performance among prespecified portfolios, we design a new set of portfolios to directly exploit machine learning forecasts. At the end of each month, we calculate 1-month-ahead out-of-sample stock return predictions for each method. We then sort stocks into deciles based on each model’s forecasts. We reconstitute portfolios each month using value weights. Finally, we construct a zero-net-investment portfolio that buys the highest expected return stocks (decile 10) and sells the lowest (decile 1).

[Table 7](https://academic.oup.com/rfs/article/33/5/2223/) reports results. Out-of-sample portfolio performance aligns very closely with results on machine learning forecast accuracy reported earlier. Realized returns generally increase monotonically with machine learning forecasts from every method (with occasional exceptions, such as decile 8 of NN1). Neural network models again dominate linear models and tree-based approaches. In particular, for all but the most extreme deciles, the quantitative match between predicted returns and average realized returns using neural networks is extraordinarily close. The best 10–1 strategy comes from NN4, which returns on average 2.3% per month (27.1% on an annualized basis). Its monthly volatility is 5.8% (20.1% annualized), amounting to an annualized out-of-sample Sharpe ratio of 1.35.

While value-weight portfolios are less sensitive to trading cost considerations, it is perhaps more natural to study equal weights in our analysis because our statistical objective functions minimize equally weighted forecast errors. [Table A.9 in the Internet Appendix](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) reports the performance of machine learning portfolios using an equal-weight formation. The qualitative conclusions of this table are identical to those of [Table 7](https://academic.oup.com/rfs/article/33/5/2223/), but the Sharpe ratios are substantially higher. For example, the long-short decile spread portfolio based on the NN4 model earns an annualized Sharpe ratio of 2.45 with equal weighting. To identify the extent to which equal-weight results are driven by micro-cap stocks, Table A.10 in the Internet Appendix reports equal-weight portfolio results excluding stocks that fall below the 20th percentile of the NYSE size distribution. In this case, the NN4 long-short decile spread earns a Sharpe ratio of 1.69.

As recommended by [Lewellen (2015)](https://academic.oup.com/rfs/article/33/5/2223/), the OLS-3 model is an especially parsimonious and robust benchmark model. He also recommends somewhat larger OLS benchmark models with either 7 or 15 predictors, which we report in [Table A.11 in the Internet Appendix](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA). The larger OLS models improve over OLS-3, but are nonetheless handily outperformed by tree-based models and neural networks.

Table 8

[Open in new tab](https://academic.oup.com/view-large/203502901)

Drawdowns, turnover, and risk-adjusted performance of machine learning portfolios

<table><thead><tr><th></th><th>OLS-3+H</th><th>PLS</th><th>PCR</th><th>ENet+H</th><th>GLM+H</th><th>RF</th><th>GBRT+H</th><th>NN1</th><th>NN2</th><th>NN3</th><th>NN4</th><th>NN5</th></tr></thead><tbody><tr><td colspan="13">Drawdowns and turnover (value weighted)</td></tr><tr><td>Max DD(%)</td><td>69.60</td><td>41.13</td><td>42.17</td><td>60.71</td><td>37.09</td><td>52.27</td><td>48.75</td><td>61.60</td><td>55.29</td><td>30.84</td><td>51.78</td><td>57.52</td></tr><tr><td>Max 1M loss(%)</td><td>24.72</td><td>27.40</td><td>18.38</td><td>27.40</td><td>15.61</td><td>26.21</td><td>21.83</td><td>18.59</td><td>37.02</td><td>30.84</td><td>33.03</td><td>38.95</td></tr><tr><td>Turnover(%)</td><td>58.20</td><td>110.87</td><td>125.86</td><td>151.59</td><td>145.26</td><td>133.87</td><td>143.53</td><td>121.02</td><td>122.46</td><td>123.50</td><td>126.81</td><td>125.37</td></tr><tr><td colspan="13">Drawdowns and turnover (equally weighted)</td></tr><tr><td>Max DD(%)</td><td>84.74</td><td>32.35</td><td>31.39</td><td>33.70</td><td>21.01</td><td>46.42</td><td>37.19</td><td>18.25</td><td>25.81</td><td>17.34</td><td>14.72</td><td>21.78</td></tr><tr><td>Max 1M loss(%)</td><td>37.94</td><td>32.35</td><td>22.33</td><td>32.35</td><td>15.74</td><td>34.63</td><td>22.34</td><td>12.79</td><td>25.81</td><td>12.50</td><td>9.01</td><td>21.78</td></tr><tr><td>Turnover(%)</td><td>57.24</td><td>104.47</td><td>118.07</td><td>142.78</td><td>137.97</td><td>120.29</td><td>134.24</td><td>112.35</td><td>112.43</td><td>113.76</td><td>114.17</td><td>114.34</td></tr><tr><td colspan="13">Risk-adjusted performance (value weighted)</td></tr><tr><td>Mean ret.</td><td>0.94</td><td>1.02</td><td>1.22</td><td>0.60</td><td>1.06</td><td>1.62</td><td>0.99</td><td>1.81</td><td>1.92</td><td>2.12</td><td>2.26</td><td>1.97</td></tr><tr><td>FF5+Mom <span><math><mi>α</mi></math></span></td><td>0.39</td><td>0.24</td><td>0.62</td><td>−0.23</td><td>0.38</td><td>1.20</td><td>0.66</td><td>1.20</td><td>1.33</td><td>1.52</td><td>1.76</td><td>1.43</td></tr><tr><td><span><math><mi>t</mi> <mo>(</mo><mi>α</mi><mo>)</mo></math></span></td><td>2.76</td><td>1.09</td><td>2.89</td><td>−0.89</td><td>1.68</td><td>3.95</td><td>3.11</td><td>4.68</td><td>4.74</td><td>4.92</td><td>6.00</td><td>4.71</td></tr><tr><td><span><math><msup><mi>R</mi> <mrow><mn>2</mn></mrow></msup></math></span></td><td>78.60</td><td>34.95</td><td>39.11</td><td>28.04</td><td>30.78</td><td>13.43</td><td>20.68</td><td>27.67</td><td>25.81</td><td>20.84</td><td>20.47</td><td>18.23</td></tr><tr><td>IR</td><td>0.54</td><td>0.21</td><td>0.57</td><td>−0.17</td><td>0.33</td><td>0.77</td><td>0.61</td><td>0.92</td><td>0.93</td><td>0.96</td><td>1.18</td><td>0.92</td></tr><tr><td colspan="13">Risk-adjusted performance (equally weighted)</td></tr><tr><td>Mean ret.</td><td>1.34</td><td>2.08</td><td>2.45</td><td>2.11</td><td>2.31</td><td>2.38</td><td>2.14</td><td>2.91</td><td>3.31</td><td>3.27</td><td>3.33</td><td>3.09</td></tr><tr><td>FF5+Mom <span><math><mi>α</mi></math></span></td><td>0.83</td><td>1.40</td><td>1.95</td><td>1.32</td><td>1.79</td><td>1.88</td><td>1.87</td><td>2.60</td><td>3.07</td><td>3.02</td><td>3.08</td><td>2.78</td></tr><tr><td><span><math><mi>t</mi> <mo>(</mo><mi>α</mi><mo>)</mo></math></span></td><td>6.64</td><td>5.90</td><td>9.92</td><td>4.77</td><td>8.09</td><td>6.66</td><td>8.19</td><td>10.51</td><td>11.66</td><td>11.70</td><td>12.28</td><td>10.68</td></tr><tr><td><span><math><msup><mi>R</mi> <mrow><mn>2</mn></mrow></msup></math></span></td><td>84.26</td><td>26.27</td><td>40.50</td><td>20.89</td><td>21.25</td><td>19.91</td><td>11.19</td><td>13.98</td><td>10.60</td><td>9.63</td><td>11.57</td><td>14.54</td></tr><tr><td>IR</td><td>1.30</td><td>1.15</td><td>1.94</td><td>0.93</td><td>1.58</td><td>1.30</td><td>1.60</td><td>2.06</td><td>2.28</td><td>2.29</td><td>2.40</td><td>2.09</td></tr></tbody></table>

The top two panels report value-weighted and equally weighted portfolio maximum drawdowns (“Max DD”), the most extreme negative monthly return (“Max 1M Loss”), and the average monthly percentage change in holdings (“Turnover”). The bottom panel reports average monthly returns expressed as a percentage as well as alphas, information ratios (IR), and $R2$ with respect to the Fama-French five-factor model augmented to include the momentum factor.

The top panel of [Table 8](https://academic.oup.com/rfs/article/33/5/2223/) reports drawdowns, portfolio turnover, and risk-adjusted performance of 10–1 spread portfolios from each machine learning model, for both value and equally weighted strategies. We define maximum drawdown of a strategy as where $Yt$ is the cumulative log return from date 0 through $t$ ⁠.

Not only do neural network portfolios have higher Sharpe ratios than alternatives, they also have comparatively small drawdowns, particularly for equal-weight portfolios. The maximum drawdown experienced for the NN4 strategy is 51.8% and 14.7% for value and equal weights, respectively. In contrast, the maximum drawdown for OLS-3 are 69.6% and 84.7%, respectively. Equal-weight neural network strategies also experience the most mild 1-month losses. For example, for NN4, the worst 1-month performance is a $−$ 9.01% return, which is the least extreme monthly loss among all models with either weighting scheme.

We define the strategy’s average monthly turnover as where $wi,t$ is the weight of stock $i$ in the portfolio at time $t$ ⁠. For NN1 through NN5, turnover is consistently between 110% and 130% per month, and turnover for tree-based methods and penalized regression is slightly higher. As a frame of reference, the monthly turnover of a short-term reversal decile spread is 172.6% per month while for a size decile spread it is 22.9%. Given the large role of price trend predictors selected by all machine learning approaches, it is perhaps unsurprising that their outperformance is accomplished with comparatively high portfolio turnover.

The bottom panel of [Table 8](https://academic.oup.com/rfs/article/33/5/2223/) reports risk-adjusted performance of machine learning portfolios based on factor pricing models. In a linear factor model, the tangency portfolio of the factors themselves represents the maximum Sharpe ratio portfolio in the economy. Any portfolio with a higher Sharpe ratio than the factor tangency portfolio possesses alpha with respect to the model. From prior work, the out-of-sample factor tangency portfolios of the Fama-French three and five-factor models have Sharpe ratios of roughly 0.8 and 1.3, respectively ([Kelly, Pruitt, and Su 2019](https://academic.oup.com/rfs/article/33/5/2223/)). It is unsurprising then that portfolios formed on the basis of machine learning forecasts earn large and significant alphas versus these models. A six-factor model (that appends a momentum factor to the Fama-French five-factor model) explains as much as 40% of the average return for strategies based on linear models, but explains only about 10% to 30% of variation in neural network-based portfolios. As a result, neural networks have information ratios ranging from 0.9 to 2.4 depending on the number of layers and the portfolio weighting scheme. Test statistics for the associated alphas are highly significant for both tree models and all neural network models.

![Cumulative return of machine learning portfolios](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/m_hhaa009f9.jpeg?Expires=1752253962&Signature=L1OtJ5p8SnaNvPI8PKMqpX9fqKzetn-1KAFDa7WIpXr2N2obodxaFSMWezBemnt9tuCNLxqwkOkBZ-DnaF9qrZEpHiJTB5b72JgP6blaq5UdLlV9V9o17dt9-qXfHWAOAydQqThdUBWc8yWmVk-7U0cx3CUZ4ybNz4nPK3NS9m3BzU7cCTzMKzEFwxJ9k-1d1Rq0t255~-Nu2gmgilYHKGSUMSmYByqHCLh5VQXqg4fx6YJ4XLB-Cr02n~o7Kgon3HrKzl~0vDDlB5ELo3MZ8ozwkAGCXgF-5Sy2hG3S5Ye~u1M2xvdpvkmMFNsCFYxYPuXWBMcvf8Txe61vwIr8Ag__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA)

Figure 9

Cumulative return of machine learning portfolios

The figure shows the cumulative log returns of portfolios sorted on out-of-sample machine learning return forecasts. The solid and dashed lines represent long (top decile) and short (bottom decile) positions, respectively. The shaded periods show NBER recession dates. All portfolios are value weighted.

[Open in new tab](https://academic.oup.com/view-large/figure/203502906/hhaa009f9.tif) [Download slide](https://academic.oup.com/DownloadFile/DownloadImage.aspx?image=https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009f9.jpeg?Expires=1752253962&Signature=MML3E0gsuv6QJTkRie5YMPPm8z-kwZnZw2rFke47~1bMFDn33G3h9VBLSMH0hkgBRdamQ5L6NsZis06rh9Ojr3byB45F-e3Obhv~VTMCqZFfeFwNRZwLoX034Mq1Jgf43OynE-K~Ij~soS2DE5XyP~Cn2pxhv33iMoqltS~At2SAygIl8w1kBzZxYl10iDm4Gva9VhaVTKPKL2vKOsUTEaQwW5MDaWCVqf4wzfrejuW-lKTOMaHCuDx6ZNMj8ADjRyb11z68Sup2dJs4-Wxs6xu7WtXsaRt1bjZP3~tqvznmLIgaT4rOgFriHJ0k5R80-GOa~x50iLGELTxUkoLqaQ__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA&sec=203502906&ar=5758276&xsltPath=~/UI/app/XSLT&imagename=&siteId=5511)

The results of [Table 8](https://academic.oup.com/rfs/article/33/5/2223/) are visually summarized in [Figure 9](https://academic.oup.com/rfs/article/33/5/2223/), which reports cumulative performance for the long and short sides for select strategies, along with the cumulative market excess return as a benchmark. NN4 dominates the other models by a large margin in both directions. Interestingly, the short side of all portfolios is essentially flat in the post-2000 sample.<sup><a href="https://academic.oup.com/rfs/article/33/5/2223/">39</a></sup>

Finally, we consider two metastrategies that combine forecasts of all machine learning portfolios. The first is a simple equally weighted average of decile long-short portfolios from our eleven machine learning methods. This achieves a stock-level predictive $R2$ of 0.43% per month and an equally weighted decile spread Sharpe ratio of 2.49, both of which are higher than any single method on its own. The value weighted decile spread Sharpe ratio is 1.33, which is slightly lower than that for the NN4 model.

The second metastrategy rotates between machine learning methods by selecting the best machine learning model for each 1-year test sample based on the predictive $R2$ during the corresponding validation sample. Over our 30-year out-of-sample period, this method selects NN3 11 times, NN1 7 times, GBRT 6 times, NN2 5 times, and NN4 1 time. This method delivers the highest overall panel $R2$ (0.45%), but underperforms the standalone NN4 model in terms of decile spread Sharpe ratio (2.42 and 1.23 with equal and value weights, respectively). Interestingly, the meta-strategy’s predictive $R2$ gain is statistically insignificant relative to the best standalone neural network models.

## 3\. Conclusion

Using the empirical context of return prediction as a proving ground, we perform a comparative analysis of methods in the machine learning repertoire. At the highest level, our findings demonstrate that machine learning methods can help improve our empirical understanding of asset prices. Neural networks and, to a lesser extent, regression trees, are the best performing methods. We track down the source of their predictive advantage to accommodation of nonlinear interactions that are missed by other methods. We also find that “shallow” learning outperforms “deep” learning, which differs from the typical conclusion in other fields, such as computer vision or bioinformatics, and is likely due to the comparative dearth of data and low signal-to-noise ratio in asset pricing problems. Machine learning methods are most valuable for forecasting larger and more liquid stock returns and portfolios. Lastly, we find that *all* methods agree on a fairly small set of dominant predictive signals, the most powerful predictors being associated with price trends including return reversal and momentum. The next most powerful predictors are measures of stock liquidity, stock volatility, and valuation ratios.

The overall success of machine learning algorithms for return prediction brings promise for both economic modeling and for practical aspects of portfolio choice. With better measurement through machine learning, risk premiums are less shrouded in approximation and estimation error, thus the challenge of identifying reliable economic mechanisms behind asset pricing phenomena becomes less steep. Finally, our findings help justify the growing role of machine learning throughout the architecture of the burgeoning fintech industry.

## Acknowledgement

We benefitted from discussions with Joseph Babcock, Si Chen (discussant), Rob Engle, Andrea Frazzini, Amit Goyal (discussant), Lasse Pedersen, Lin Peng (discussant), Alberto Rossi (discussant), and Guofu Zhou (discussant) and seminar and conference participants at Erasmus School of Economics, NYU, Northwestern, Imperial College, National University of Singapore, UIBE, Nanjing University, Tsinghua PBC School of Finance, Fannie Mae, U.S. Securities and Exchange Commission, City University of Hong Kong, Shenzhen Finance Institute at CUHK, NBER Summer Institute, New Methods for the Cross Section of Returns Conference, Chicago Quantitative Alliance Conference, Norwegian Financial Research Conference, EFA, China International Conference in Finance, 10th World Congress of the Bachelier Finance Society, Financial Engineering and Risk Management International Symposium, Toulouse Financial Econometrics Conference, Chicago Conference on New Aspects of Statistics, Financial Econometrics, and Data Science, Tsinghua Workshop on Big Data and Internet Economics, Q group, IQ-KAP Research Prize Symposium, Wolfe Research, INQUIRE UK, Australasian Finance and Banking Conference, Goldman Sachs Global Alternative Risk Premia Conference, AFA, and Swiss Finance Institute. We gratefully acknowledge the computing support from the Research Computing Center at the University of Chicago. The views and opinions expressed are those of the authors and do not necessarily reflect the views of AQR Capital Management, its affiliates, or its employees; do not constitute an offer, solicitation of an offer, or any advice or recommendation, to purchase any securities or other financial instruments, and may not be construed as such. [Supplementary data](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) can be found on *The Review of Financial Studies* web site.

## Footnotes

<sup>1</sup> Our focus is on measuring conditional expected stock returns in excess of the risk-free rate. Academic finance traditionally refers to this quantity as the “risk premium” because of its close connection with equilibrium compensation for bearing equity investment risk. We use the terms “expected return” and “risk premium” interchangeably. One may be interested in potentially distinguishing between different components of expected returns, such as those due to systematic risk compensation, idiosyncratic risk compensation, or even due to mispricing. For machine learning approaches to this problem, see [Gu, Kelly, and Xiu (2019)](https://academic.oup.com/rfs/article/33/5/2223/) and [Kelly, Pruitt, and Su (2019)](https://academic.oup.com/rfs/article/33/5/2223/).

<sup>2</sup> [Green et al. (2013)](https://academic.oup.com/rfs/article/33/5/2223/) count 330 stock-level predictive signals in published or circulated drafts. [Harvey, Liu, and Zhu (2016)](https://academic.oup.com/rfs/article/33/5/2223/) study 316 “factors,” which include firm characteristics and common factors, for describing stock return behavior. They note that this is only a subset of those studied in the literature. [Welch and Goyal (2008)](https://academic.oup.com/rfs/article/33/5/2223/) analyze nearly twenty predictors for the aggregate market return. In both stock and aggregate return predictions, there presumably exists a much larger set of predictors that were tested but failed to predict returns and were thus never reported.

<sup>3</sup> See, for example, [Hastie, Tibshirani, and Friedman (2009)](https://academic.oup.com/rfs/article/33/5/2223/).

<sup>4</sup> See, for example, [Jaggi (2013)](https://academic.oup.com/rfs/article/33/5/2223/) and [Hastie, Tibshirani, and Friedman (2009)](https://academic.oup.com/rfs/article/33/5/2223/), who discuss the equivalence of support vector machines with the lasso. For an application of the kernel trick to the cross-section of returns, see [Kozak (2019)](https://academic.oup.com/rfs/article/33/5/2223/).

<sup>5</sup> In addition to using a least squares regression, the literature often sorts assets into portfolios on the basis of characteristics and studies portfolio averages, a form of nonparametric regression.

<sup>6</sup> In machine learning, a “hyperparameter” governs the extent of estimator regularization. This usage is related to, but different from, its meaning in Bayesian statistics as a parameter of a prior distribution.

<sup>7</sup> As of [Fama and French (2008)](https://academic.oup.com/rfs/article/33/5/2223/), the smallest 20% of stocks compose only 3% of aggregate market capitalization. An example of a statistically motivated weighting scheme uses $wi,t$ inversely proportional to an observation’s estimated error variance, a choice that potentially improves prediction efficiency in the spirit of generalized least squares.

<sup>8</sup> Classical analyses include [Box (1953)](https://academic.oup.com/rfs/article/33/5/2223/), [Tukey (1960)](https://academic.oup.com/rfs/article/33/5/2223/), and [Huber (1964)](https://academic.oup.com/rfs/article/33/5/2223/).

<sup>9</sup> OLS is a special case of the () with $ξ=∞$ ⁠. Although most theoretical analysis from high-dimensional statistics assume that data have sub-Gaussian or subexponential tails, [Fan et al. (2017)](https://academic.oup.com/rfs/article/33/5/2223/) provide a theoretical justification of using this loss function in the high-dimensional setting as well as a procedure to determine the hyperparameter.

<sup>11</sup> See [Kelly and Pruitt](https://academic.oup.com/rfs/article/33/5/2223/) ([2013](https://academic.oup.com/rfs/article/33/5/2223/), [2015](https://academic.oup.com/rfs/article/33/5/2223/)) for asymptotic theory of PLS regression and its application to forecasting risk premiums in financial markets.

<sup>12</sup> For two vectors $a$ and $b$ ⁠, we denote $Cov(a,b):=(a−a¯)⊺(b−b¯)$ ⁠, where $a¯$ is the average of all entries of $a$ ⁠. Naturally, we define $Var(a):=Cov(a,a)$ ⁠.

<sup>13</sup> See [White (1980)](https://academic.oup.com/rfs/article/33/5/2223/) for a discussion of the limitations of linear models as first-order approximations.

<sup>14</sup> For additional details, see [Internet Appendix B.1](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA). [Freyberger, Neuhierl, and Weber (2020)](https://academic.oup.com/rfs/article/33/5/2223/) offers a similar model in the return prediction context.

<sup>15</sup> Parameter penalization does not solve the difficulty of estimating linear models when the number of predictors is exponentially larger than the number of observations. Instead, one must turn to heuristic optimization algorithms, such as stepwise regression (sequentially adding/dropping variables until some stopping rule is satisfied), variable screening (retaining predictors whose univariate correlations with the prediction target exceed a certain value), or others.

<sup>16</sup> We focus on recursive binary trees for their relative simplicity. [Breiman et al. (1984)](https://academic.oup.com/rfs/article/33/5/2223/) discuss more complex tree structures.

<sup>17</sup> Because splits are chosen without consideration of future potential branches, it is possible to myopically bypass an inferior branch that would have led to a future branch with an ultimately superior reduction in forecast error.

<sup>18</sup> The literature also considers a number of other approaches to tree regularization, such as early stopping and post-pruning, both of which are designed to reduce overfit in a single large tree. Ensemble methods demonstrate more reliable performance and are scalable for very large data sets, leading to their increased popularity in recent literature.

<sup>19</sup> Boosting is originally described in [Schapire (1990)](https://academic.oup.com/rfs/article/33/5/2223/) and [Freund (1995)](https://academic.oup.com/rfs/article/33/5/2223/) for classification problems to improve the performance of a set of weak learners. [Friedman et al. (2000)](https://academic.oup.com/rfs/article/33/5/2223/) and [Friedman (2001)](https://academic.oup.com/rfs/article/33/5/2223/) extend boosting to contexts beyond classification, eventually leading to the gradient boosted regression tree.

<sup>20</sup> [Eldan and Shamir (2016)](https://academic.oup.com/rfs/article/33/5/2223/) formally demonstrate that depth—even if increased by one layer—can be exponentially more valuable than increasing width in standard feed-forward neural networks. Ever since the seminal work of [Hinton, Osindero, and Teh (2006)](https://academic.oup.com/rfs/article/33/5/2223/), the machine learning community has experimented and adopted deeper (and wider) networks, with as many as 152 layers for image recognition (see, e.g., [He et al. 2016](https://academic.oup.com/rfs/article/33/5/2223/)).

<sup>21</sup> We confine the choices of architectures to a small set of five based on our limited sample size (compared to typical neural network applications).

<sup>22</sup> See, for example, [Jarrett et al. (2009)](https://academic.oup.com/rfs/article/33/5/2223/), [Nair and Hinton (2010)](https://academic.oup.com/rfs/article/33/5/2223/), and [Glorot, Bordes, and Bengio (2011)](https://academic.oup.com/rfs/article/33/5/2223/).

<sup>24</sup> Early stopping bears a comparatively low computation cost because of only partial optimization, whereas the $l2$ regularization, or more generally elastic net, search across tuning parameters fully optimizes the model subject to each tuning parameter guess. As usual, elastic net’s $l1$ -penalty component encourages neurons to connect to limited number of other neurons, whereas its $l2$ -penalty component shrinks the weight parameters toward zero (a feature known in the neural net literature as “weight decay”). In certain circumstances, early stopping and weight decay are shown to be equivalent. See, for example, [Bishop (1995)](https://academic.oup.com/rfs/article/33/5/2223/) and [Goodfellow, Bengio, and Courville (2016)](https://academic.oup.com/rfs/article/33/5/2223/).

<sup>25</sup> That estimation with different seeds can run independently in parallel limits incremental computing time.

<sup>26</sup> As emphasized by [Diebold (2015)](https://academic.oup.com/rfs/article/33/5/2223/), the model-free nature of the Diebold-Mariano test means that it should be interpreted as a comparison of forecasts, not as a comparison of “fully articulated econometric models.”

<sup>27</sup> In particular, SSD defines the $j$ th variable importance as

where, with a slight abuse of notation, $zj$ in the denominator of the derivative denotes the $j$ element of the vector of input variables. We measure SSD within the training set, $T1$ ⁠. Note that, because of nondifferentiabilities in tree-based models, the [Dimopoulos, Bourret, and Lek (1995)](https://academic.oup.com/rfs/article/33/5/2223/) method is not applicable. Therefore, when we conduct this second variable importance analysis, we measure variable importance for random forests and boosted trees using mean decrease in impurity (see, e.g., [Friedman 2001](https://academic.oup.com/rfs/article/33/5/2223/)).

<sup>28</sup> We include stocks with prices below

$ $ $

5, share codes beyond 10 and 11, and financial firms. We select the largest possible pool of assets for at least three important reasons. First, these commonly used filters remove certain stocks that are components of the S&P 500 index, and we find it clearly problematic to exclude such important stocks from an asset pricing analysis. Moreover, because we aggregate individual stock return predictions to predict the index, we cannot omit such stocks. Second, our results are less prone to sample selection or data-snooping biases that the literature (see, e.g., [Lo and MacKinlay 1990](https://academic.oup.com/rfs/article/33/5/2223/)) cautions against. Third, using a larger sample helps avoid overfitting by increasing the ratio of observation count to parameter count. That said, our results are qualitatively identical and quantitively unchanged if we filter out these firms.

<sup>29</sup> We cross-sectionally rank all stock characteristics period-by-period and map these ranks into the \[-1,1\] interval following [Kelly, Pruitt, and Su (2019)](https://academic.oup.com/rfs/article/33/5/2223/) and [Freyberger, Neuhierl, and Weber (2020)](https://academic.oup.com/rfs/article/33/5/2223/).

<sup>30</sup> The ninety-four predictive characteristics are based on those of [Green et al. (2017)](https://academic.oup.com/rfs/article/33/5/2223/), and we adapt the SAS code available from Jeremiah Green’s Web site and extend the sample period back to 1957. Our data construction differs by more closely adhering to variable definitions in original papers. For example, we construct book-equity and operating profitability following [Fama and French (2015)](https://academic.oup.com/rfs/article/33/5/2223/). Most of these characteristics are released to the public with a delay. To avoid the forward-looking bias, we assume that monthly characteristics are delayed by at most 1 month, quarterly with at least 4 months lag, and annual with at least 6 months lag. Therefore, to predict returns at month $t+1$ ⁠, we use most recent monthly characteristics at the end of month $t$ ⁠, most recent quarterly data by end $t−4$ ⁠, and most recent annual data by end $t−6$ ⁠. Another issue is missing characteristics, which we replace with the cross-sectional median at each month for each stock, respectively.

<sup>31</sup> The monthly data are available from Amit Goyal’s Web site.

<sup>32</sup> We do not use cross-validation to maintain the temporal ordering of the data.

<sup>33</sup> Because we hold the five neural networks architectures fixed and simply compare across them, we do not describe their estimated complexity in [Figure 3](https://academic.oup.com/rfs/article/33/5/2223/).

<sup>34</sup> As an aside, it is useful to know that there is a roughly 3% inflation in out-of-sample $R2$ s if performance is benchmarked against historical averages. For OLS-3, the $R2$ relative to the historical mean forecast is 3.74% per month! Evidently, the historical mean is such a noisy forecaster that it is easily beaten by a fixed excess return forecasts of zero.

<sup>35</sup> Multiple comparisons are a concern when the researcher conducts many hypotheses tests and draws conclusions based on only those that are significant. Doing so distorts the size of tests through a selection bias. Instead, we report $t$ -statistics for every comparison we consider, yet we report adjusted inference to err on the side of caution. We also note that false discoveries in multiple comparisons should be randomly distributed. The statistically significant $t$ -statistics in our analyses do not appear random, but instead follow a pattern in which nonlinear models outperform linear ones.

<sup>36</sup> [Figure 5](https://academic.oup.com/rfs/article/33/5/2223/) is based on the average rank of over thirty recursing training samples. Figure A.1 in the Internet Appendix presents the ranks for each of the recursing samples, respectively. The rank of important characteristics (top-third of the covariates) is remarkably stable over time. This is true for all models, though we show results for one representative model (NN3) in the interest of space.

<sup>37</sup> Conclusions from our model can diverge from the results in the literature, because we jointly model hundreds of predictor variables, which can lead to new conclusions regarding marginal effects, interaction effects, and so on.

<sup>38</sup> Our replication of S&P 500 returns has a correlation with the actual index of more than 0.99. For the other portfolios (SMB, HML, RMW, CMA, UMD), the return correlations between our replication and the version from Kenneth French’s Web site are 0.99, 0.97, 0.95, 0.99, and 0.96, respectively.

<sup>39</sup> [Figure A.7 in the Internet Appendix](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752253962&Signature=m2hrTjK4iZVVX1LBOfVT0fbmuBH6KODmFVyKRGClbs5sV8IUSer-KVL51Tc1DJjSahP9XAlZA0y-IDQY~XBouIl02xc5G22cr4Opkx2Oz9Xb2JEtaLSBsMeE2cbDoJQFu6keHVCyQ~XsmlOazglM33cXlZAXW8JlNPbfMk4BdixqomDTu7ybZAwEdGdff-h7Rh3Xe8pBnCJ5EF518lka~BDL4v3HFs4c5XT1Aaq8of7HyBn5zzb8z8h6tzXpATFVRCc5Hr3MAHUYoZfE6i4ZO8GcXkZvGFohLzbIi6GqG0ENe6wJMwTQdGmdNe7Pv33yLuR1QCbL57GqEjXCKVSRIw__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) plots the corresponding cumulative returns for equally weighted strategies.

## References

Bishop,

C. M.

1995

.

*Neural networks for pattern recognition*

.

Oxford, UK

:

Oxford University Press

.

Box,

G. E. P.

1953

. .

*Biometrika*

40

:

318

–

35

.

Breiman,

L.

2001

. .

*Machine Learning*

45

:

5

–

32

.

Breiman,

L.

,

Friedman

J.

,

Stone

C. J.

, and

Olshen

R. A.

.

1984

.

*Classification and regression trees*

.

Boca, Raton, FL

:

CRC press

.

Butaru,

F.

,

Chen

Q.

,

Clark

B.

,

Das

S.

,

Lo

A. W.

, and

Siddique

A.

.

2016

. .

*Journal of Banking & Finance*

72

:

218

–

39

.

Campbell,

J. Y.

, and

Thompson

S. B.

.

2008

.

*Review of Financial Studies*

21

:

1509

–

31

.

Cochrane,

J. H.

2007

. .

*Review of Financial Studies*

21

:

1533

–

75

.

Cybenko,

G.

1989

. .

*Mathematics of Control, Signals and Systems*

2

:

303

–

14

.

de Jong,

Sijmen

.

1993

. .

*Chemometrics and Intelligent Laboratory Systems*

18

:

251

–

63

. [http://www.sciencedirect.com/science/article/pii/016974399385002X](http://www.sciencedirect.com/science/article/pii/016974399385002X).

Diebold,

F. X.

2015

. .

*Journal of Business & Economic Statistics*

33

:

1

–

9

.

Diebold,

F. X.

, and

Mariano

R. S.

.

1995

. .

*Journal of Business & Economic Statistics*

13

:

134

–

44

.

Dietterich,

T. G.

2000

. . In

*International workshop on multiple classier systems*

, eds.

Schwenker

F.

,

Roli

F.

, and

Kittler

J.

,

1

–

15

.

New York

:

Springer

.

Dimopoulos,

Y.

,

Bourret

P.

, and

Lek

S.

.

1995

. .

*Neural Processing Letters*

2

:

1

–

4

.

Eldan,

R.

, and

Shamir

O.

.

2016

. . In

*29th Annual Conference on Learning Theory*

, eds.

Feldman

V.

,

Rakhlin

A.

, and

Shamir

O.

,

907

–

40

.

Brookline, MA

:

Microtome Publishing

.

Fama,

E. F.

, and

French

K. R.

.

1993

. .

*Journal of Financial Economics*

33

:

3

–

56

.

Fama,

E. F.

, and

French

K. R.

.

2008

. .

*Journal of Finance*

63

:

1653

–

78

.

Fama,

E. F.

, and

French

K. R.

.

2015

. .

*Journal of Financial Economics*

116

:

1

–

22

. [http://dx.doi.org/10.1016/j.jfineco.2014.10.010](http://doi.org/10.1016/j.jfineco.2014.10.010).

Fan,

J.

,

Li

Q.

, and

Wang

Y.

.

2017

. .

*Journal of the Royal Statistical Society, Series B*

79

:

247

–

65

.

Feng,

G.

,

Giglio

S.

, and

Xiu

D.

.

Forthcoming

. .

*Journal of Finance*

.

Freund,

Y.

1995

. .

*Information and Computation*

121

:

256

–

85

.

Freyberger,

J.

,

Neuhierl

A.

, and

Weber

M.

.

2020

. .

*Review of Financial Studies*

.

33

:

2326

–

77

.

Friedman,

J.

2001

. .

*Annals of Statistics*

5

:

1189

–

232

.

Friedman,

J.

,

Hastie

T.

, and

Tibshirani

R.

.

2000

. .

*Annals of Statistics*

28

:

337

–

74

.

Giglio,

S. W.

, and

Xiu

D.

.

2016

.

Asset Pricing with Omitted Factors

.

Tech. Report

,

University of Chicago

.

Glorot,

X.

,

Bordes

A.

, and

Bengio

Y.

.

2011

. . In

*Proceedings of the Fourteenth International Conference on Artificial Intelligence and Statistics*

, vol.

15

,

315

–

323

.

Brookline, MA

:

Microtome Publishing

.

Goodfellow,

I.

,

Bengio

Y.

, and

Courville

A.

.

2016

.

*Deep learning*

.

Cambridge

:

MIT Press

.

Green,

J.

,

Hand

J. R. M.

, and

Zhang

X. F.

.

2013

. .

*Review of Accounting Studies*

18

:

692

–

730

.

Green,

J.

,

Hand

J. R. M.

, and

Zhang

X. F.

.

2017

. .

*Review of Financial Studies*

30

:

4389

–

436

.

Gu,

S.

,

Kelly

B. T.

, and

Xiu

D.

.

2019

.

Autoencoder asset pricing models

.

Working Paper

,

Yale University

.

Hansen,

L. K.

, and

Salamon

P.

.

1990

. .

*IEEE Transactions on Pattern Analysis and Machine Intelligence*

12

:

993

–

1001

.

Harvey,

C. R.

, and

Ferson

W. E.

.

1999

. .

*Journal of Finance*

54

:

1325

–

60

.

Harvey,

C. R.

, and

Liu

Y.

.

2016

.

Lucky factors

.

Technical Report

,

Duke University

.

Harvey,

C. R.

,

Liu

Y.

, and

Zhu

H.

.

2016

. .

*Review of Financial Studies*

29

:

5

–

68

.

Hastie,

T.

,

Tibshirani

R.

, and

Friedman

J.

.

2009

.

*The elements of statistical learning*

.

New York

:

Springer

.

He,

K.

,

Zhang

X.

,

Ren

S.

, and

Sun

J.

.

2016

. . In

*2016 IEEE Conference on Computer Vision and Pattern Recognition, CVPR 2016*

,

770

–

78

.

Piscataway, NJ

:

IEEE Publications

.

Heaton,

J. B.

,

Polson

N. G.

, and

Witte

J. H.

.

2016

.

Deep learning in finance

. Preprint, [https://arxiv.org/abs/1602.06561](https://arxiv.org/abs/1602.06561).

Hinton,

G. E.

,

Osindero

S.

, and

Teh

Y.-W.

.

2006

. .

*Neural Computation*

18

:

1527

–

54

.

Hornik,

K.

,

Stinchcombe

M.

, and

White

H.

.

1989

. .

*Neural Networks*

2

:

359

–

66

.

Huber,

P. J.

1964

. .

*Annals of Mathematical Statistics*

35

:

73

–

101

.

Hutchinson,

J. M.

,

Lo

A. W.

, and

Poggio

T.

.

1994

. .

*Journal of Finance*

49

:

851

–

89

.

Ioffe,

S.

, and

Szegedy

C.

.

2015

. . In

*Proceedings of the 32nd International Conference on International Conference on Machine Learning*

, eds.

Bach

F.

and

Blei

D.

,

448

–

56

.

New York

: .

Jaggi,

M.

2013

. . In

*Regularization, optimization, kernels, and support vector machines*

, eds.

Suykens

J. A. K.

,

Signoretto

M.

, and

Argyriou

A.

,

1

–

26

.

Boca Raton, FL

:

CRC Press

.

Jarrett,

K.

,

Kavukcuoglu

K.

,

Ranzato

M.’A.

, and

Lecun

Y.

.

2009

. In

*2009 IEEE 12th International Conference on Computer Vision*

,

2146

–

53

.

Piscataway, NJ

:

IEEE

.

Kelly,

B.

, and

Pruitt

S.

.

2013

. .

*Journal of Finance*

68

:

1721

–

56

.

Kelly,

B.

, and

Pruitt

S.

.

2015

. .

*Journal of Econometrics*

186

:

294

–

316

.

Kelly,

B.

,

Pruitt

S.

, and

Su

Y.

.

2019

. .

*Journal of Financial Economics*

.

Khandani,

A. E.

,

Kim

A. J.

, and

Lo

A. W.

.

2010

. .

*Journal of Banking & Finance*

34

:

2767

–

87

.

Kingma,

D.

, and

Ba

J.

.

2014

.

Adam: A method for stochastic optimization

. Preprint, [https://arxiv.org/abs/1412.6980](https://arxiv.org/abs/1412.6980).

Koijen,

R.

, and

Nieuwerburgh

S. V.

.

2011

. .

*Annual Review of Financial Economics*

3

:

467

–

91

.

Kozak,

S.

2019

.

Kernel trick for the cross section

.

Working Paper

,

University of Maryland

.

Kozak,

S.

,

Nagel

S.

, and

Santosh

S.

.

2020

. .

*Journal of Financial Economics*

135

:

271

–

92

.

Lewellen,

J.

2015

. .

*Critical Finance Review*

4

:

1

–

44

.

Lo,

A. W.

, and

MacKinlay

A. C.

.

1990

. .

*Review of Financial Studies*

3

:

431

–

67

.

Masters,

T.

1993

.

*Practical neural network recipes in C++*

.

New York

:

Academic Press

.

Moritz,

B.

, and

Zimmermann

T.

.

2016

.

Tree-based conditional portfolio sorts: The relation between past and future stock returns

.

Working Paper

,

Ludwig Maximilian University of Munich

.

Nair,

V.

, and

Hinton

G. E.

.

2010

. . In

*Proceedings of the 27th International Conference on Machine Learning (ICML-10)*

, eds.

Fürnkranz

J.

and

Joachims

T.

,

807

–

14

.

New York

:

ACM

.

Rapach,

D.

, and

Zhou

G.

.

2013

. . In

*Handbook of economic forecasting*

, eds.

Elliott

G.

and

Timmermann

A.

,

328

–

83

.

Amsterdam, the Netherlands

:

Elsevier

.

Rapach,

D. E.

,

Strauss

J. K.

, and

Zhou

G.

.

2013

.

*Journal of Finance*

68

:

1633

–

62

.

Rosenberg,

B.

1974

. .

*Journal of Financial and Quantitative Analysis*

9

:

263

–

74

.

Schapire,

R. E.

1990

. .

*Machine Learning*

5

:

197

–

227

.

Sirignano,

J.

,

Sadhwani

A.

, and

Giesecke

K.

.

2016

.

Deep Learning for Mortgage Risk

.

Working Paper

,

University of Illinois, Urbana-Champaign

.

Tukey,

J. W.

1960

. . In

*Contributions to probability and statistics*

, eds.

Olkin

I.

,

Ghurye

S. G.

,

Hoeding

W.

,

Madow

W. G.

, and

Mann

H. B.

.

Stanford, CA

:

Stanford University Press

.

Welch,

I.

, and

Goyal

A.

.

2008

. .

*Review of Financial Studies*

21

:

1455

–

508

.

White,

H.

1980

. .

*International Economic Review*

21

:

149

–

70

.

Wilson,

D. R.

, and

Martinez

T. R.

.

2003

. .

*Neural Networks*

16

:

1429

–

51

.

Yao,

J.

,

Li

Y.

, and

Tan

C. L.

.

2000

. .

*Omega*

28

:

455

–

66

.

## Supplementary data

[hhaa009\_Supplementary\_Data](https://oup.silverchair-cdn.com/oup/backfile/Content_public/Journal/rfs/33/5/10.1093_rfs_hhaa009/4/hhaa009_supplementary_data.pdf?Expires=1752402702&Signature=PS~m2-XoqftGtVOynd36-kg4pEifMCUI6tI7Bq2xpMbEigJy3MdacHaeUoW~vNiwJGFog68NigdFFGolotFZRId8zQkUFo9uV0PNY0N9pCZJMqgLgNjOtHJu-l6AjSPqnw~2Av35IO1O8ZbYbRtE0RzZ9Rs~Cw7a1d7SEowpbSMDvMdJlB8zPMbAcOu30Iu9U4B7NUJlZ99IRxtLfAvKV4ZGb6rLS51qzR3G-0w2eHtQ8ZccSsgVQMiSadGpLlwxPfN6ePrhWQKeDiw-sV5l9mR1OA9UpLAVAPYGHWf5mbSVG-mz8lFwNuHLBvGEmsZw8pRnVNYFid5s26YyVWbJJg__&Key-Pair-Id=APKAIE5G5CRDK6RD3PGA) - pdf file

[PDF](https://scholar.google.com/scholar_url?url=https://academic.oup.com/rfs/article-pdf/33/5/2223/33209812/hhaa009.pdf&hl=zh-CN&sa=T&oi=ucasa&ct=ufr&ei=FpVFaMHZKuWs6rQPpf7X-Aw&scisig=AAZF9b_AGfYutlNWUTxIttNTrgDI) [Help](https://scholar.google.com/scholar/help.html#access)

![](https://academic.oup.com/rfs/article/33/5/2223/assets/starter/opener-left.svg)