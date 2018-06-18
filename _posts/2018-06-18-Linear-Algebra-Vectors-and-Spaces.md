---
layout: post
title:  "Linear Algebra: Vectors and Spaces"
tags: [Linear Algebra, Notes]
---

#### Linear Dependence ####
If we have a se tof vectors $$S = \{v_{1}, v_{2}, ..., v_{n}\}$$, they are **linearly dependent** iff I can 
find $$c_{1}v_{1} + c_{2}v_{2} + .. + c_{n}v_{n} = $$ **0**, where at least one $$c_{i}$$ is non-zero.

Example:

Lets say we have a set of vectors $$ S = \left\{ \begin{bmatrix}1 \\-1 \\2  \end{bmatrix}, \begin{bmatrix}2 \\1 \\3  \end{bmatrix}, \begin{bmatrix}-1 \\0 \\2  \end{bmatrix} \right\} $$

We want to find out if $$Span(x) = \mathbb{R}^{3} $$ and if they are linearly independent.

Solution: 

To Span $$\mathbb{R}^{3}$$, that means some linear combination of these vectors should be able to construct 
any vector in $$\mathbb{R}^{3}$$. Hence:

$$ \tag{1} c_{1} \begin{bmatrix}1 \\-1 \\2  \end{bmatrix} + c_{2} \begin{bmatrix}2 \\1 \\3  \end{bmatrix} + c_{3} \begin{bmatrix}-1 \\0 \\2  \end{bmatrix} = \begin{bmatrix}a \\b \\c  \end{bmatrix}$$

Now if we use algebra we can solve these equations and get a representation of $$c_{1}, c_{2} and c_{3}$$ by the constants $$a, b and c$$. Hence we can proof that 
$$Span(S) = \mathbb{R}^{3}$$.

**Linear Independent** means that $$a, b and c$$ in equation 2 are all 0. Now we can substitute the 0s to the representations of 
$$c_{1}, c_{2} and c_{3}$$, the rule is that if at least one $$c_{i}$$ is non-zero, the vectors are linearly dependent.

In this case (not go in to the details), $$c_{1}, c_{2} and c_{3}$$ are all zeros in order to get the zero vector. Hence the vectors are linearly independent.

**If there are three vectors and they span $$\mathbb{R}^{3}$$, they are linearly independent of each other (and vice versa)**

---


