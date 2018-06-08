---
layout: post
title:  "Deep Learning: Part I - 3"
tags: [Deep Learning, Machine Learning, Notes]
---

##### Notes on the [Deep Learning Textbook](http://www.deeplearningbook.org/) Part I - 3 -- Probability and Information Theory

---
#### Basics ####

##### The chain rule of conditional probabilities

$$ P(x^{(1)}, ..., x^{(n)}) = P(x^{(1)}) \prod_{i=2}^{n} P(x^{i} | x^{(1)}, ..., x^{(n)}) $$

Some example:

\indent $$ P(a, b, c) = P(a | b, c)P(b, c) $$

\indent $$ P(a, b, c) = P(a | b, c)P(b | c)P(c) $$

##### Independence and Conditionally independence
##### Expectation, Variance and Covariance

---

#### Distributions ####
##### Bernoulli Distribution
controlled by a single parameter $$\phi \in [0, 1]$$
##### Multinoulli Distribution, or categorical distribution.
* Gaussian distribution and central limit theorem.

$$ \mathcal{N}(x; \mu, \sigma^{2}) = \sqrt{\frac{1}{2\pi\sigma^{2}}} $$

* [Multivariate normal distribution](https://en.wikipedia.org/wiki/Multivariate_normal_distribution)
* [Empirical distribution](https://www.statlect.com/asymptotic-theory/empirical-distribution)
* [Gaussian mixture model](http://research.stowers.org/mcm/efg/R/Statistics/MixturesOfDistributions/index.html), also more on [Scikit](http://scikit-learn.org/stable/modules/mixture.html)

---

#### Useful Functions ####

* Logistics sigmoid: commonly used to produce the phi parameter for beunoulli distribution
* Softplus: mean and variance for nomal distribution
* Information theory
* Self information:
* Shannon entropy
* Kullback-Leibler (KL) divergence: measuring the same random variable in two different distributions [read more](https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence)
* Cross entropy
* Structured probabilistic mode, or graphical model
