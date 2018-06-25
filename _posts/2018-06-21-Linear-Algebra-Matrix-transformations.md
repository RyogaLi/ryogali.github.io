---
layout: post
title:  "Linear Algebra: Matrix Transformations"
tags: [Linear Algebra, Notes, Basic Math]
---

#### Linear transformation ####

A function is defined as $$f:\mathbb{R}^n \to \mathbb{R}^m$$

If we have a function $$f(\begin{bmatrix}x_{1} \\x_{2} \\x_{3} \end{bmatrix}) = \begin{bmatrix}x_{1}+x_{2} \\3x_{3} \end{bmatrix}$$, we call this **Transformation** which is 
a function operating on vectors and is represented by $$T$$

**Linear transformation:** for a transformation $$T: \mathbb{R}^{n} \to \mathbb{R}^{m} $$, it is a 
linear transformation if and only if: 
* $$ \overrightharpoon{a}, \overrightharpoon{b} \in \mathbb{R}^{n} $$
* $$T(\overrightharpoon{a}, \overrightharpoon{b}) = T(\overrightharpoon{a}) + T(\overrightharpoon{b})$$
* $$T(c\overrightharpoon{a}) = cT(\overrightharpoon{a})$$

In general, each vector $$\begin{bmatrix}x \\y \end{bmatrix}$$ (two dimentional) can be froken down as:

$$\begin{bmatrix}x \\y \end{bmatrix} = x \begin{bmatrix}1 \\0 \end{bmatrix} + y \begin{bmatrix}0 \\1 \end{bmatrix}$$

So if $$\begin{bmatrix}1 \\0 \end{bmatrix}$$ lands on $$\begin{bmatrix}a \\c \end{bmatrix}$$ and 
$$\begin{bmatrix}0 \\1 \end{bmatrix}$$ lands on $$\begin{bmatrix}b \\d \end{bmatrix}$$, then the 
vector $$\begin{bmatrix}x \\y \end{bmatrix}$$ must land on

$$x \cdot \begin{bmatrix}a \\c \end{bmatrix} + y \cdot \begin{bmatrix}b \\d \end{bmatrix} = \begin{bmatrix}ax +by \\cx+dy \end{bmatrix}$$

Matrix product with vecotrs is always linear transformation.

$$\mathbf{A} = \begin{bmatrix}\mathbf{v_{1}}, \mathbf{v_{2}}, ..., \mathbf{v_{n}} \end{bmatrix} $$

$$ T(\mathbf{x}) = \mathbf{A}\mathbf{x} $$  and $$T: \mathbb{R}^{n} \to \mathbb{R}^{m}$$

**Identity matrix** has 1s on the diagonal and 0s elsewhere. When we multiply a identity matrix 
with a vecotr, you get the same vector. If we have an $$n\times n$$ identity matrix, all the column
vectors in that matrix construct the **standard basis for $$\mathbf{R}^{n}$$**

If we have a transformation $$T: \mathbb{R}^{2} \to \mathbb{R}^3$$, $$ T(x_{1}, x_{2}) = (x_{1} +3x_{2}, 5x_{2}-x_{1}, 4x_{1} + x_{2}) $$

The standard basis (identity matrix) of $$\mathbb{R}^{2}$$ is $$I_{2} = \begin{bmatrix}1 & 0 \\0 & 1 \end{bmatrix}$$ then we can apply
the transformation to the column vector to the identity matrix:

$$ T(\begin{bmatrix}1 \\ 0\end{bmatrix}) = \begin{bmatrix}1 \\ -1\\ 4\end{bmatrix}$$ and $$ T(\begin{bmatrix}0 \\ 1 \end{bmatrix}) = \begin{bmatrix}3 \\ 5 \\ 1\end{bmatrix}$$

Now we can re-write the transformation as 

$$ T(\begin{bmatrix}x_{1} \\ x_{2}\end{bmatrix}) = \begin{bmatrix}1 &3 \\-1& 5 \\ 4 & 1\end{bmatrix} \begin{bmatrix}x_{1} \\ x_{2}\end{bmatrix}$$

---

#### Image of a transformation ####

If $$V$$ is a subspace in $$\mathbf{R}^{n}$$, $$\overrightharpoon{a}, \overrightharpoon{b} \in V$$, and 
a transformation $$T: \mathbf{R}^{n} \to \mathbf{R}^{m}$$. We say that $$T(V)$$: image of $$V$$ under $$T$$.
$$T(V)$$ is a subspace.

If $$T(\overrightharpoon{x}) = \mathbf{A}\overrightharpoon{x}$$, the image of $$\mathbf{R}^{n}$$ under $$T$$ is $$im(T) = \{ \mathbf{A}\overrightharpoon{x} \vert \overrightharpoon{x} \in \mathbf{R}^{n} \}$$

$$\mathbf{A} = \begin{bmatrix}\mathbf{a_{1}}, \mathbf{a_{2}}, ..., \mathbf{a_{n}} \end{bmatrix} \begin{bmatrix}x_{1} \\x_{2} \\ x_{n} \end{bmatrix}$$

The image of a linear transformation matrix is equivalent to its column space.

When an image is thesubset of a function's codomain which is the output of the cuntion from a subset of its domain, the **preimage** 
of a particular subset $$S$$ of the codomain of a function is the set of all elements of the domain that 
map to the members of $$S$$.

Example:

$$T: \mathbb{R}^{2} \to \mathbb{R}^{2}$$ where $$T(\overrightharpoon{x}) = \begin{bmatrix}1 & 3 \\ 2 & 6\end{bmatrix} \begin{bmatrix}x_{1}\\x_{2} \end{bmatrix}$$ and 
$$ S = \{ \begin{bmatrix}0\\0\end{bmatrix}, \begin{bmatrix}1 \\ 2\end{bmatrix}\} $$. What are all of the 
vectors in out domain maps to $$S$$? (the preimage of $$S$$ under the transformation $$T$$)

We can write this in another way:

$$T'(S) = \{\overrightharpoon{x} \in \mathbf{R}^2 \vert T(\overrightharpoon{x}) \in S \} = 
\{\overrightharpoon{x} \in \mathbf{R}^2 \vert \mathbf{A}\overrightharpoon{x} = \begin{bmatrix}0\\0\end{bmatrix} or  
\mathbf{A}\overrightharpoon{x} = \begin{bmatrix}1\\2\end{bmatrix}\}$$

To solve this euqation we need to find out the solution of all the $$x$$:

$$\begin{bmatrix}1 & 3 \\ 2 & 6\end{bmatrix} \begin{bmatrix}x_{1}\\x_{2} \end{bmatrix} = \begin{bmatrix}0\\0\end{bmatrix} $$ and 
$$ \begin{bmatrix}1 & 3 \\ 2 & 6\end{bmatrix} \begin{bmatrix}x_{1}\\x_{2} \end{bmatrix} = \begin{bmatrix}1\\2\end{bmatrix}$$

The solution set with $$x_{2} = t$$, $$t\in \mathbf{R}$$

$$ \begin{bmatrix}x_{1}\\x_{2} \end{bmatrix} = t \begin{bmatrix}-3\\1 \end{bmatrix}$$ and 
$$ \begin{bmatrix}x_{1}\\x_{2} \end{bmatrix} = \begin{bmatrix}1\\0 \end{bmatrix} + t \begin{bmatrix}-3\\1 \end{bmatrix} $$

**Kernel of T:** $$Ker(T) = \{\overrightharpoon{x} \in \mathbf{R}^2 \vert T(\overrightharpoon{x}) = \mathbb{0}\}$$

---

#### Sums and scalar multiples of linear transformations ####

$$S: \mathbb{R}^{n} \to \mathbb{R}^{m}$$ and $$T:\mathbb{R}^{n} \to \mathbb{R}^{m}$$

**Def:** $$(S+T)\overrightharpoon{x} = S(\overrightharpoon{x}) + T(\overrightharpoon{x})$$ where $$(S+T):\mathbb{R}^{n} \to \mathbb{R}^{m}$$

**Def:** $$(cS)(\overrightharpoon{x}) = c(S(\overrightharpoon{x}))$$ where $$cS:\mathbb{R}^{n} \to \mathbb{R}^{m}$$

If we have $$S(\overrightharpoon{x}) = A\overrightharpoon{x}$$ and $$T(\overrightharpoon{x}) = B\overrightharpoon{x}$$, then 
$$(S+T)\overrightharpoon{x} = A\overrightharpoon{x} + B\overrightharpoon{x} = x_{1}(a_{1}+b_{1}) + x_{2}(a_{2}+b_{2}) + ... + x_{n}(a_{n}+b_{n})$$

(Similar proof for scalars)

---

#### Rotations ####

$$Rot_{\theta}(\mathbf{x})$$: counter clockwise $$\theta$$ degree rotation of $$\mathbf{x}$$ - $$ Rot_{\theta}: \mathbb{R}^{2} \to \mathbb{R}^{2}$$

$$Rot_{\theta}(\mathbf{x}) = \begin{bmatrix}cos(\theta) & sin(\theta)\\sin(\theta) & cos(\theta) \end{bmatrix} \begin{bmatrix}x_{1}\\x_{2} \end{bmatrix}$$

$$Rot_{\theta}: \mathbb{R}^{3} \to \mathbb{R}^{3}$$: Rotate around the x-axis. We can apply the rotations to the 
column vectors of the identity matrices and find out the rules for rotations. 

---

#### Unit vector ####

Also called a **normalized vector**, vector that has "length" of 1.

$$\overrightharpoon{u} \in \mathbb{R}^{n}$$, $$ \Vert \overrightharpoon{u} \Vert = 1$$

The unit vectors in the direction of the x, y and z axes of a three dimensional Cartesian coordinate system:

$$\hat{i} = \begin{bmatrix}1 \\0 \\ 0\end{bmatrix}, \hat{j} = \begin{bmatrix}0 \\1 \\ 0\end{bmatrix}, \hat{k} = \begin{bmatrix}0 \\0 \\ 1\end{bmatrix}$$


