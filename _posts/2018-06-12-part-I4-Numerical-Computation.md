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

Consider the function $$ f(\mathbf{x}) = \mathbf{A}^{-1} \mathbf{x} $$. When $$ \mathbf{A} \in \mathbb{R}^{n \times n} $$ has an eigenvalue decomposition, its condition number is $$ \mathop{max}_{\textbf{i, j}} \mid \frac{\lambda_i}{\lambda_j} $$.

* Eigenvalue / eigenvector

Def: A scalar $$ \lambda $$ is called an eighenvalue of the $$ n \times n $$ matrix A is there is a notrivial
 solution $$ \mathbf{x} $$ of $$ A\mathbf{x} = \lambda\mathbf{x}$$. Such an $$ \mathbf{x} $$ is called an eigenvector 
 corresponding o the eigenvalue $$ \lambda $$
 
 **Example:** If we have a matrix A
 
  
 $$ A = \begin{bmatrix} 1 & -3 & 3 \\ 3 & -5 & 3 \\ 6 & -6 & 4 \end{bmatrix} $$ 
 
 To find the eigenvalues and eighenvectors of A, we find the values of $$ \lambda $$ which satisfy
  the [characteristic equation](http://mathworld.wolfram.com/CharacteristicEquation.html) of the matrix A, namely those values of $$ \lambda $$ for which
  
  $$ det(A - \lambda I) = 0 $$
 
 Where $$ I $$ is the $$ 3 \times 3 $$ identity matrix. The solution $$\lambda$$ of the charateristic equation are called eigenvalues. 
 The polynomial left-hand side of the characteristic equation is known as the characteristic polynomial.
 
 Hence:
 
 $$ 
 A - \lambda I = \begin{bmatrix} 1 & -3 & 3 \\ 3 & -5 & 3 \\ 6 & -6 & 4 \end{bmatrix} - \begin{bmatrix} \lambda & 0 & 0 \\ 0 & \lambda & 0 \\ 0 & 0 & \lambda \end{bmatrix} = 
 \begin{bmatrix} 1 - \lambda & -3 & 3 \\ 3 & -5 - \lambda & 3 \\ 6 & -6 & 4 - \lambda \end{bmatrix} 
 $$
 
 ([How to calculate the determinant of a 3 x 3 matrix? ](https://www.wikihow.com/Find-the-Determinant-of-a-3X3-Matrix))
 
 Therefore:
 
 $$ det(A - \lambda I) = - \lambda^{3} + 12\lambda + 16 $$
 
 To solve:
 
 $$ \lambda^{3} - 12 \lambda - 16 = 0 $$
 
 We get the eigenvalues of $$ A $$ are $$ \lambda = 4, -2 $$
 
 **Example in python:**
 {% highlight python %}
 import numpy as np
 \# to calculate the eigenvalues of a square array A
 
 {% endhighlight %}
 
* Condition number: 


