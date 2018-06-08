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
i.e.

$$ P(a, b, c) = P(a | b, c)P(b | c)P(c) $$

##### Independence and Conditionally independence
##### Expectation, Variance and Covariance

---

#### Distributions ####
##### Bernoulli Distribution (Multinoulli Distribution, or categorical distribution)
Bernoulli controlled by a single parameter $$\phi \in [0, 1]$$
##### Gaussian distribution and central limit theorem.

$$ \mathcal{N}(x; \mu, \sigma^{2}) = \sqrt{\frac{1}{2\pi\sigma^{2}}} exp(-\frac{1}{2\sigma^{2}}(x - \mu)^{2}) $$

**Precision** is defined as $$ \beta = \frac{1}{\sigma^{2}} $$ where $$ \beta \in (0, \infty) $$ which means how concentrated are the values around the mean rather than how much spread they are. Hence:

$$ \mathcal{N}(x; \mu, \beta^{-1}) = \sqrt{\frac{\beta}{2\pi} exp(-\frac{1}{2}\beta(x - \mu)^{2}) $$

$$ \mathcal{N}(x; \mu, \sigma^{2}) = \sqrt{\frac{1}{2\pi\sigma^{2}}} exp(-\frac{1}{2\sigma^{2}}(x - \mu)^{2}) $$

##### Exponential and Laplace Distributions
##### Dirac delta function
##### Multivariate normal distribution
[link](https://en.wikipedia.org/wiki/Multivariate_normal_distribution)
##### Empirical distribution
[link](https://www.statlect.com/asymptotic-theory/empirical-distribution)
##### Gaussian mixture model
[link](http://research.stowers.org/mcm/efg/R/Statistics/MixturesOfDistributions/index.html), also more on [Scikit](http://scikit-learn.org/stable/modules/mixture.html)

---

#### Useful Functions ####

##### Logistics sigmoid:
commonly used to produce the phi parameter for beunoulli distribution
##### Softplus
mean and variance for nomal distribution
* Information theory
* Self information:
* Shannon entropy
* Kullback-Leibler (KL) divergence: measuring the same random variable in two different distributions [read more](https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence)
* Cross entropy
* Structured probabilistic mode, or graphical model
