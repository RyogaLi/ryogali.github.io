---
layout: post
title:  "Deep Learning: Part I - 4"
tags: [Deep Learning, Machine Learning, Notes]
---

##### Notes on the [Deep Learning Textbook](http://www.deeplearningbook.org/) Part I - 4 -- Numerical Computation

---

#### Softmax function ####
*Overflow:* Number with large magnitude are approximated as $$ \infty $$ or $$ -\infty $$.

*Underflow:* Numbers near zero are rounded to zero.

$$ softmax(\mathbf{x})_{i} = \frac{exp(x_{i})}{\sum_{j=1}^{n} exp(x_{j})} $$

This function is often used to predict the probabilities associated with a multinoulli distribution. Quote from [wiki](https://en.wikipedia.org/wiki/Softmax_function): 
> Generalization of the logistic function that "squashes" a K-dimensional vector 
$$ \mathbf {z} $$ of arbitrary real values to a K-dimensional 
vector $$ \sigma (\mathbf {z} ) $$ of real values, 
where each entry is in the range (0, 1), and all the entries add up to 1

Example in python:

{% highlight python %}
import math
z = [1,2,3,4] # vector
z_exp = [math.exp(i) for i in z] # calculate exp(i) for each element in z

sum_z_exp = sum(z_exp) # sum over
softmax = [round(i / sum_z_exp, 3) for i in z_exp] 
{% endhighlight %}

#### Poor conditioning ####

Consider the function $$ f(\mathbf{x}) = \mathbf{A}^{-1} \mathbf{x} $$. When $$ \mathbf{A} \in \mathbb{R} $$ has an eigenvalue decomposition, its condition number is $$ \mathop{max}_{\textbf{i, j}} \mid \frac{\lambda_i}{\lambda_j} $$.

* Eigenvalue / eigenvector

Def: A scalar $$ \lambda $$ is called an eighenvalue of the $$ n \times n $$ matrix A is there is a notrivial
 solution $$ \mathbf{x} $$ of $$ A\mathbf{x} = \lambda\mathbf{x}$$. Such an $$ \mathbf{x} $$ is called an eigenvector 
 corresponding o the eigenvalue $$ \lambda $$
 
 Example: If we have a matrix A
 
  
 $$ A = \begin{bmatrix} 1 & -3 & 3 \\ 3 & -5 & 3 \\ 6 & -6 & 4 \end{bmatrix} $$ 
 
 To find the eigenvalues and eighenvectors of A, we find the values of $$ \lambda $$ which satisfy
  the characteristic equation of the matrix A, namely those values of $$ \lambda $$ for which
  
  $$ det(A - \lambda I) = 0 $$
 
 Hence:
 
 $$ A - \lambda I = $$
 
* Condition number: 


