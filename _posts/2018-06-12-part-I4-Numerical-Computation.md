---
layout: post
title:  "Deep Learning: Part I - 4"
tags: [Deep Learning, Machine Learning, Notes]
---

##### Notes on the [Deep Learning Textbook](http://www.deeplearningbook.org/) Part I - 4 -- Numerical Computation

---

##### Softmax function #####
*Overflow:* Number with large magnitude are approximated as $$ \infty $$ or $$ -\infty $$.

*Underflow:* Numbers near zero are rounded to zero.

$$ softmax(x)_{i} = \frac{exp(x_{i})}{\sum_{j=1}^{n} exp(x_{j})} $$

This function is often used to predict the probabilities associated with a multinoulli distribution. [wiki](https://en.wikipedia.org/wiki/Softmax_function)

Example in python:

{% highlight python %}
import math
z = [1,2,3,4] # vector
z_exp = [math.exp(i) for i in z] # calculate exp(i) for each element in z

sum_z_exp = sum(z_exp) # sum over
softmax = [round(i / sum_z_exp, 3) for i in z_exp] 
{% endhighlight %}

