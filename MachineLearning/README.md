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
