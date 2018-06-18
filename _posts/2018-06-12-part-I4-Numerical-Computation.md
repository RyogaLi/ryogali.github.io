---
layout: post
title:  "Deep Learning: Part I - 4"
tags: [Deep Learning, Machine Learning, Notes]
---

##### Notes on the [Deep Learning Textbook](http://www.deeplearningbook.org/) Part I - 4 -- Numerical Computation

---

#### Softmax function ####
**Overflow:** Number with large magnitude are approximated as $$ \infty $$ or $$ -\infty $$.

**Underflow:** Numbers near zero are rounded to zero.

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

---

#### Poor conditioning ####

Consider the function $$ f(\mathbf{x}) = \mathbf{A}^{-1} \mathbf{x} $$. When $$ \mathbf{A} \in \mathbb{R}^{n \times n} $$ has an eigenvalue decomposition, its condition number is $$ \mathop{max}_{\textbf{i, j}} \mid \frac{\lambda_i}{\lambda_j} $$.

* Eigenvalue / eigenvector

Def: A scalar $$ \lambda $$ is called an eighenvalue of the $$ n \times n $$ matrix A is there is a notrivial
 solution $$ \mathbf{x} $$ of $$ A\mathbf{x} = \lambda\mathbf{x}$$. Such an $$ \mathbf{x} $$ is called an eigenvector 
 corresponding o the eigenvalue $$ \lambda $$
 
 **Example:** If we have a matrix A
  
 $$ A = \begin{bmatrix} 1 & -3 & 3 \\ 3 & -5 & 3 \\ 6 & -6 & 4 \end{bmatrix} $$ 
 
 To find the eigenvalues of A, we find the values of $$ \lambda $$ which satisfy
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
 
 To find the eigenvectors of A, we know that for each eigenvalue $$\lambda$$ we have $$ (A - \lambda I)\mathbf{x} = 0$$, 
 where $$x$$ is the eigenvector associated with eigenvalue $$ \lambda $$.
 
 
 **Example in python:**
 {% highlight python %}
 import numpy as np
 # to calculate the eigenvalues of a square array A
 values, vectors = np.linalg.eig(A)
 {% endhighlight %}
 
* Condition number: Conditioning referes to how rapidly a function changes with respect to small changes in its inputs. 
This is the ratio of the mgnitude of the largest and smallest eigenvalue. When this number is large, matrix inversion is particularly sensitive to error in the input.

---

#### Gradient-Based Input ####

Objective function (criterion); Cost function, loss function, or error function.

We often denote the value that minizes or maximizes a function with a superscript $$ * $$. i.e: $$ \mathbf(x)^{*} = argminf(\mathbf{x})$$

Suppose we have a function $$ y = f(x) $$, $$ f(x+\epsilon) \approx f(x) + \epsilon f'(x) $$. The idea of **gradient descent** is 
that if we know $$ f(x - \epsilon sign(f\prime(x)) $$ is less than $$ f(x) $$ for small enough $$\epsilon$$, we can reduce $$f(x)$$ by
moving $$x$$ in small setps with the opposite sign of the derivative.

**Partial derivatives:** $$ \frac{\partial}{\partial x_{i}} f(x) $$ measures how $$f$$ changes as only the variable $$x_i$$ increases at point $$x$$.

Some basic math ... 

$$ f(x, y) = f_{y}(x) = x^{2} + xy + y^{2} $$

If we substitute a into this function, the function $$ f_{a} $$ which traces a curve $$ x^{2} + ax + a^{2} $$ 
on the $$\mathbf{xz}$$ plane. Now $$a$$ is a constant, so $$f_{a}$$ is a function of only one real variable and the derivative
of this function is:

$$f'_{a} = 2x + a$$

So in this case, the above equation can be performed for any choice of $$a$$:

$$\frac{\partial }{\partial x}f(x, y) = 2x + y$$

If we have a scalar-valued function $$f(x_{1}, ..., x_{n})$$ on a domain in Euclidean space $$ \mathbb{R}^{n} $$. In this 
case $$f$$ has a partial derivative $$\frac{\partial }{\partial x_{j}}$$with respect to each variable $$x_{j}$$, these partial derivatives define the vector
**gradient of a**:

$$\triangledown f(a) = (\frac{\partial }{\partial x_{1}}f(a), ..., \frac{\partial }{\partial x_{n}}f(a))$$

In multidimensions, **critical points** are points where evvery element of the gradient is equal to zero.

**Directional derivative** is the derivative of the function $$f(\mathbf{x}+\alpha\mathbf{u})$$ with respect to $$\alpha$$.

More basic math ...

Lets say we have a scalar function $$f(x)= f(x_{1}, x_{2}, ...,x_{n})$$ along a vector $$\mathbf{v} = (v_{1}, v_{2}, ...,v_{n})$$

is the function $$\triangledown_{v}f$$ defined by the limit:

$$\triangledown_{v} f(\mathbf{x}) = \lim_{h \rightarrow 0}{\frac{f(\bold{x} + h\bold{v}) - f(\bold{x})}{h}}$$

If the function $$f$$ is differentiable at $$\mathbf{x}$$, then the directional derivative exists along any vector $$\mathbf{v}$$, and one has

$$\triangledown_{v} f(\mathbf{x}) = \triangledown f(\mathbf{x}) \cdot \mathbf{v}$$

Intuitively, the directional derivative of $$f$$ at a point $$\mathbf{x}$$ represents the rate of change of f, 
in the direction of $$\mathbf{v}$$ with respect to time, when moving past $$\mathbf{x}$$.

--- 

#### Jacobian and Hessian Matrices ####

**Jacobian Matrix:** If we have a function $$f : \mathbb{R}^{m} \rightarrow \mathbb{R} $$, then the Jacobian matrix $$J \in \mathbb{R}^{n\times m}$$ of $$f$$ is defined such that 
$$J_{i, j} = \frac{\partial }{\partial x_j}f(x)$$