---
layout: post
title:  "Linear Algebra: Vectors and Spaces"
tags: [Linear Algebra, Notes, Basic Math]
---

#### Linear Dependence ####
If we have a set of vectors $$S = \{v_{1}, v_{2}, ..., v_{n}\}$$, they are **linearly dependent** iff I can 
find $$c_{1}v_{1} + c_{2}v_{2} + .. + c_{n}v_{n} = $$ **0**, where at least one $$c_{i}$$ is non-zero.

**Example:**

Lets say we have a set of vectors $$ S = \left\{ \begin{bmatrix}1 \\-1 \\2  \end{bmatrix}, \begin{bmatrix}2 \\1 \\3  \end{bmatrix}, \begin{bmatrix}-1 \\0 \\2  \end{bmatrix} \right\} $$

We want to find out if $$Span(x) = \mathbb{R}^{3} $$ and if they are linearly independent.

**Solution:**

To Span $$\mathbb{R}^{3}$$, that means some linear combination of these vectors should be able to construct 
any vector in $$\mathbb{R}^{3}$$. Hence:

$$ c_{1} \begin{bmatrix}1 \\-1 \\2  \end{bmatrix} + c_{2} \begin{bmatrix}2 \\1 \\3  \end{bmatrix} + c_{3} \begin{bmatrix}-1 \\0 \\2  \end{bmatrix} = \begin{bmatrix}a \\b \\c  \end{bmatrix} $$

Now if we use algebra and solve for $$c_{1}, c_{2}, c_{3}$$, we can proof that $$Span(S) = \mathbb{R}^{3}$$.

*Linear Independent* means that $$a, b, c$$ are all 0. Now we can substitute the 0s to the representations of 
$$c_{1}, c_{2}, c_{3}$$, the rule is that if at least one $$c_{i}$$ is non-zero, the vectors are linearly dependent.

In this case (not go in to the details), $$c_{1}, c_{2}, c_{3}$$ are all zeros in order to get the zero vector. Hence the vectors are linearly independent.

**If there are n vectors and they span $$\mathbb{R}^{n}$$, they are linearly independent of each other (and vice versa)**

---

#### Linear Subspaces ####

If $$ V $$ is a subspace of $$\mathbb{R}^{n}$$:

* $$ V $$ contains the $$\mathbf{0}$$ vector
* **Closure under scalar multiplication**: $$\overrightharpoon{x}$$ in $$V$$, $$c\overrightharpoon{x}$$ in $$V$$ 
* **Closure under addition**: $$\overrightharpoon{a}$$ in $$V$$ and $$\overrightharpoon{b}$$ in $$V$$ then $$\overrightharpoon{b} + \overrightharpoon{a}$$ in $$V$$

Span of n vectors is a valid subspace of $$\mathbb{R}^{n}$$

Let $$V = Span(\overrightharpoon{v_{1}}, \overrightharpoon{v_{2}}, ..., \overrightharpoon{v_{n}}) $$ and $$ S = \{ \overrightharpoon{v_{1}}, \overrightharpoon{v_{2}}, ..., \overrightharpoon{v_{n}} \}$$, 
we say that $$S$$ is a basis for $$V$$.

---

#### Vector Dot product and Vector Length ####

The **Length** of a vector $$\overrightharpoon{a}$$ is defined as:

$$\lVert \overrightharpoon{a} \rVert = \sqrt{a_{1}^2 + a_{2}^2 + ... + a_{n}^2}$$

**Proof of the Cauchy Schwarz inequality**

If we have $$\overrightharpoon{x}, \overrightharpoon{y} \in \mathbb{R}^{n}$$:

$$ \begin{cases} \shortmid \overrightharpoon{x} \cdot \overrightharpoon{y} \shortmid \leq \shortmid\overrightharpoon{x}\shortmid \shortmid\overrightharpoon{y}\shortmid \end{cases} $$
