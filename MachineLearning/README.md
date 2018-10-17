Machine Learning
==========

## [Python Data Science Handbook](https://jakevdp.github.io/PythonDataScienceHandbook/)

[Here](https://jakevdp.github.io/PythonDataScienceHandbook/05.00-machine-learning.html) are the chapters about Machine Learning.

## K-Means clustering

K-means clustering is very faster, it can handle up to 1M records in a very short time. Benchmarks of different clustering methods can be find [here](http://hdbscan.readthedocs.io/en/latest/performance_and_scalability.html).

|	| Interactive|	Get Coffee|	Over Lunch|	Overnight|
|---|---|---|---|---|
|AffinityPropagation|	2000|	10000|	25000|	100000|
|Spectral|	2000|	5000|	25000|	75000|
|Agglomerative|	2000|	10000|	25000|	100000|
|DeBaCl|	5000|	25000|	75000|	250000|
|ScipySingleLinkage|	25000|	50000|	100000|	250000|
|Fastcluster|	50000|	100000|	500000|	1000000|
|HDBSCAN|	100000|	500000|	1000000|	5000000|
|DBSCAN|	75000|	250000|	1000000|	2500000|
|SKLearn KMeans|	1000000000|	1000000000|	1000000000|	1000000000|

Given simple, well-separated data, k-means finds suitable clustering results. An important observation for k-means is that these cluster models must be circular: k-means has no built-in way of accounting for oblong or elliptical clusters.

Two disadvantages of k-means:
  - Lack of flexibility in cluster shape (force-fit data into circular clusters) 
  - Lack of probabilistic cluster assignment (simple distance-from-cluster-center to assign cluster membership) 

## Customer Lifetime Value

  1. [Pareto/NBD Model](https://www.datascience.com/blog/intro-to-predictive-modeling-for-customer-lifetime-value)
     - non-contractual context: movie retenal, hotel stay, grocery shopping, etc.
	 
  2. [Lifetimes](https://github.com/CamDavidsonPilon/lifetimes)
     - a python package to calculate CLV
     - [This is a tutorial to calculate CLV using this package.](https://www.internetrix.com.au/blog/how-to-model-customer-lifetime-value/)
       - [BG/NBD Model](http://www.brucehardie.com/talks/cba_tut_art_15_HO.pdf)
         - [Grocery Purchases](http://www.brucehardie.com/talks/cba_tut_art_15_HO.pdf): Slide 148

  3. [Survival Analysis](https://www.youtube.com/watch?v=lBijo0WhwYM)
     - contractual context: credit cards, netflix, fitness club, etc. 
     - Contractual tends to be easier to deal with as there is certainty of the clients current status (Alive vs. Dead).

  4. [A collection of methods](http://srepho.github.io/CLV/CLV)
 
  
 
## Marketing

  1. [Bruce G.S. Hardie](http://www.brucehardie.com/talks.html)  
     - Professor of Marketing  
     - London Business School
	 - BG/NBD Model - non-contractual, discrete situation
	   (Fader, Hardie and Lee 2005c)
	   - Transaction Process:
	     - While alive, the number of transactions made by a customer follows a Poisson process with mean transaction rate **lambda**.
	     - Heterogeneity in transaction rates across customers is distributed gamma(**gamma**, **alpha**).
	   - Latent Attrition Process:
         - After any transaction, a customer dies with probability **p**.
         - Heterogeneity in death probabilities across customers is distributed beta(**a**, **b**).
     - [Noncontractual problem](http://www.brucehardie.com/talks/cba_tut_art_15_HO.pdf)

## ML System Design

  - What kind of problem? Classification or Regression or Forecast?
  - How about the data size? How about the speed requirement? How about time complexity?
  - What models to use? 
  - What data to collect? What features to use?
  - How to evaluate the model?
    - Offline evaluation
    - Online evaluation, metrics, monitoring
  - Where to spend time to improve your model?
    - More data
    - Better feature engineering
    - More sophisticated models
  - How to put into production?

Examples:
  - How would you build an ad click prediction system, or homefeed ranking system, or translation service, or query ranking model etc?
  - [Build A Spam Classifier](https://www.ritchieng.com/machine-learning-systems-design/)
  - [An example from AirBnB](https://medium.com/airbnb-engineering/designing-machine-learning-models-7d0048249e69)
  - [Here](https://medium.com/louis-dorard/from-data-to-ai-with-the-machine-learning-canvas-part-i-d171b867b047) is a blog talks about ML system design blocks.

### Ad Click Prediciton

  - There is a criteo [Kaggle competition](https://www.kaggle.com/c/criteo-display-ad-challenge) about it. 
  - There is a [blog](https://mlwave.com/predicting-click-through-rates-with-online-machine-learning/) talking about this competition.
  - Binary Classification problem
  - Requirements
    - Features are “extremely sparse”
    - Serving must happen quickly, at a rate of billions of predictions per day
  - Given sparsity level and scalability requirements, online regularized logistic regression seems to be the way to go. 
  - Data to use, feature to use
    - user information like city, state, os version, os family, device, browser family browser version, city, etc
    - user past behavior: "user's prior impressions", "user's prior clicks" and "user's prior click-through-rate", etc 
    - Publisher features, such as the domain of the url where the ad was displayed;
    - Advertiser features (advertiser id, type of products,…)
    - User features, for instance browser type;
    - Interaction of the user with the advertiser, such as the number of the times the user visited the advertiser website.
  - Algorithm to use [Vowpal Wabbit](https://github.com/VowpalWabbit/vowpal_wabbit/wiki)

### Demand Forecast

  - [5 Demand Forecasting Best Practices for Smarter Predictions and Better Results](https://dearsystems.com/inventory-software/blog/demand-forecasting-best-practices/)

### Dynamic Pricing / Surge Pricing

  - The supply and the demand curve are highly elastic. 
    - It has been proved since the advent of surge pricing that higher prices lead to an increase in supply.
  - 给出一个heuristic来计算Uber的surge price，不同heuristic的pros和cons
  - On a very basic level, surge pricing is [a direct function of the supply-demand curve.](https://www.quora.com/How-does-Ubers-surge-pricing-algorithm-work)
