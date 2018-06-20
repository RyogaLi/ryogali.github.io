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

If we have $$\overrightharpoon{x}, \overrightharpoon{y} \in \mathbb{R}^{n} $$: $$ \begin{cases} \mid \overrightharpoon{x} \cdot \overrightharpoon{y} \mid \leq \Vert \overrightharpoon{x}\Vert \Vert \overrightharpoon{y} \Vert \\
\mid \overrightharpoon{x} \cdot \overrightharpoon{y} \mid = \Vert \overrightharpoon{x}\Vert \Vert \overrightharpoon{y} \Vert \iff \overrightharpoon{x} = c\overrightharpoon{y} \end{cases} $$

We define $$ P(t) = \Vert t\overrightharpoon{y} - \overrightharpoon{x} \Vert^{2} $$

$$ \because \Vert \overrightharpoon{V} \Vert^{2} = \overrightharpoon{V} \cdot \overrightharpoon{V} $$

$$\therefore P(t) = (t\overrightharpoon{y} - x) \cdot (t\overrightharpoon{y} - x)$$ Here I skipped the rest of proofs, it's just simple algebra. 

Using this inequality, we can proof the **vector triangle inequality** which is:

$$\Vert \overrightharpoon{x} + \overrightharpoon{y} \Vert^{2} \leq \Vert \overrightharpoon{x} \Vert + \Vert \overrightharpoon{y} \Vert $$

---

#### Define a plane in $$\mathbb{R}^3$$ ####

Assume we have a plane in $$\mathbb{R}^3$$. If we have normal vector 
$$\overrightharpoon{n}$$ that is perpendicular to everything on the plane, 
and we have an arbitrary vector $$\overrightharpoon{a}$$ on the plane, 
then we have $$\overrightharpoon{n} \cdot \overrightharpoon{a} = 0$$ 

Definition of a plane in $$\mathbb{R}^3$$:

Lets say we have $$ \overrightharpoon{x}_{0} = \begin{bmatrix}x_{0} \\y_{0} \\z_{0}  \end{bmatrix}$$ 
and another vector $$ \overrightharpoon{x} = \begin{bmatrix}x \\y \\z  \end{bmatrix}$$. 
Note that here neither of these vector is on the plane, however, if we consider this 
vector $$ (\overrightharpoon{x} - \overrightharpoon{x}_{0})$$, it is on the plane and 
it is perpendicular to the normal vector $$\overrightharpoon{n}$$.

We can define the normal vector $$\overrightharpoon{n} = \begin{bmatrix}n_{1} \\n_{2} \\n_{3} \end{bmatrix}$$.
Since $$\overrightharpoon{n}$$ is perpendicular with $$ (\overrightharpoon{x} - \overrightharpoon{x}_{0})$$:

$$\overrightharpoon{n} \cdot (\overrightharpoon{x} - \overrightharpoon{x}_{0}) = 0 $$

If we open this equation up, we will get:

$$ n_{1}(x - x_{0}) + n_{2}(y-y_{0}) + n_{3}(z-z_{0}) = 0 $$

This gives us the definition of a plane in $$\mathbb{R}^3$$ which is:

$$Ax + By + Cz = 0$$

---

#### Cross product ####

The Cross product is only defined in $$\mathbb{R}^3$$. 

The Cross product of $$ \overrightharpoon{a}$$ and $$\overrightharpoon{b}$$ is orthognal to a and b. 

---

#### Matrix row-echelon form ####

Here is a set of equations:

$$ \begin{aligned} x_{1} + 2x_{2} + x_{3} + x_{4} &= 7 \\
x_{1} + 2x_{2} + 2x_{3} - x_{4} &= 12 \\
2x_{1} + 4x_{2} + 6x_{4} &= 4 \end{aligned} $$

From this set of equations, we can construct a matrix using the coefficients. The last col of the matrix is the right hand side of the equations.

$$ \mathbf{A} = \begin{bmatrix}1 & 2 & 1 & 1 & 7\\1 & 2 & 2 & -1 & 12\\2 & 4 & 0 & 6 & 4\end{bmatrix}  $$

The reduced row echelon form of A $$ rref(A) $$ is:

$$ \mathbf{A} = \begin{bmatrix}1 & 2 & 1 & 1 & 7\\0 & 0 & -1 & 2 & -5\\0 & 0 & -2 & 4 & -10\end{bmatrix}  $$

Since we want to make the leading value for each row to 1, we times the second row by -1. Also we want to eliminate the $$-2$$ in the last row.

$$ rref(\mathbf{A}) = \begin{bmatrix}1 & 2 & 0 & 3 & 2\\0 & 0 & 1 & -2 & 5\\0 & 0 & 0 & 0 & 0\end{bmatrix} $$

Now we have the reduced row echelon form because all of the leading 1s in each row are the only non-zero entry in their cols.
These are called the **pivot entries**.

---

#### Matrix vector products ####

If we have a matrix $$\mathbf{A}$$ with the shape $$m \times n$$ (rows $$\times$$ cols) and a vector $$\mathbf{\overrightharpoon{x}}$$ with n elements.

$$\mathbf{A} \mathbf{\overrightharpoon{x}} = \begin{bmatrix} a_{11}x_{1} + a_{12}x_{2} + ... + a_{1n}x_{n} \\ a_{21}x_{1} + a_{22}x_{2} + ... + a_{2n}x_{n} \\ ... \\ a_{m1}x_{1} + a_{m2}x_{2} + ... + a_{mn}x_{n} \end{bmatrix} = \mathbf{\overrightharpoon{b}} $$ which is a $$ m \times 1$$ matrix.

---

#### The Null space of a matrix ####

If we have a matrix $$\mathbf{A}$$, the **null space** of $$\mathbf{A}$$ is 
$$ N(\mathbf{A)) = \{ \mathbf{\overrightharpoon{x}} \vert \mathbf{A} \mathbf{\overrightharpoon{x}} = \mathbf{\overrightharpoon{0}} \} $$

To find the null space of a matrix, we find the matrix vector products and solve for x. 

If the null space of a matrix only contains the zero vector, that means the columns of 
the matrix are linearly independent and (vice versa).

**Column space** of a $$m \times n$$ matrix $$\mathbf{A}$$ is defined as the span of the column vectors of $$\mathbf{A}$$

$$ \mathbf{A} = \begin{bmatrix} \mathbf{\overrightharpoon{v_{1}} & \mathbf{\overrightharpoon{v_{2}}} & ... & \mathbf{\overrightharpoon{v_{n}}} \end{bmatrix} $$ where $$ \mathbf{\overrightharpoon{v_{1}}}, \mathbf{\overrightharpoon{v_{2}}}, ..., \mathbf{\overrightharpoon{v_{n}}} \in \mathbb{R}^{m} $$

The column space of $$\mathbf{A}$$, $$C(A) = Span()$$

