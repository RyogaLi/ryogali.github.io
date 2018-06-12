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

**Precision** is defined as $$ \beta = 1 / \sigma^{2} $$ where $$ \beta \in (0, \infty) $$ which means how concentrated are the values around the mean rather than how much spread they are. Hence: $$ \mathcal{N}(x; \mu, \beta^{-1}) $$


##### Exponential Distributions #####
$$ p(x; \lambda) = \lambda\mathcal{1}_{x\geq0} exp(-\lambda x)$$

The expression $$ \mathcal{1}_{x\geq0} $$ means that the value is 1 when $$ x \geq 0 $$

##### Laplace Distributions #####

$$ Laplace(x; \mu, \gamma) = \frac{1}{2 \gamma} exp(-\frac{\mid x - \mu \mid}{\gamma}) $$

$$ \mu $$ defines the sharp peak of probability mass. 

##### Dirac delta function #####

$$ p(x) = \delta(x - \mu) $$

A [generalized function](https://en.wikipedia.org/wiki/Generalized_function) which is zero valued everywhere except 0, integrates to 1. 

##### Multivariate normal distribution #####

[Read more on wikipedia](https://en.wikipedia.org/wiki/Multivariate_normal_distribution)

##### Empirical distribution #####

[This blog post](https://www.statlect.com/asymptotic-theory/empirical-distribution) explained the distribution with code.

##### Gaussian mixture model #####
 
[Explained in R](http://research.stowers.org/mcm/efg/R/Statistics/MixturesOfDistributions/index.html), also more on [Scikit](http://scikit-learn.org/stable/modules/mixture.html)

---

#### Useful Functions ####

##### Logistics sigmoid #####

$$ \sigma(x) = \frac{1}{1+ exp(-x)} $$

Commonly used to produce the phi parameter for Bernoulli distribution. The function saturates when it's argument \
is very positive or very negative, meaning that the function becomes very flat and insensitive to small changes in its input.

##### Softplus #####

$$ \zeta(x) = log(1 + exp(x)) $$

The range is $$ (0, \infty) $$. Useful for producing mean and variance for nomal distribution.

##### Bayes' Rule #####

$$ P(x \mid y) = \frac{P(x)P(y \mid x)}{P(y)} $$

---

#### Information theory ####

##### Self information #####
##### Shannon entropy #####

Used to quantify the amount of uncertainty in an entire probability distribution. The Shannon entropy of a distribution is the expected amount of \
information in an event drawn from that distribution. [Detail](http://www.ueltschi.org/teaching/chapShannon.pdf)

##### Kullback-Leibler (KL) divergence #####

Measuring the same random variable in two different distributions [read more](https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence)

*Cross entropy* Similar idea

##### Structured probabilistic mode, or graphical model #####

*Directed models:* represent factorizations into conditional probability distributions. 

*Undirected models:* represent factorizations into a set of functions. 