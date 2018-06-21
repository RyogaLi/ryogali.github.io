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

$$\mathbf{A} = \begin{bmatrix}\mathbf{v_{1}}, \mathbf{v_{1}}, ..., \mathbf{v_{n}} \end{bmatrix} $$

$$ T(\mathbf{x}) = \mathbf{A}\mathbf{x} $$  and $$T: \mathbb{R}^{n} \to \mathbb{R}^{m}$$

**Identity matrix** has 1s on the diagonal and 0s elsewhere. When we multiply a identity matrix 
with a vecotr, you get the same vector. If we have an $$n\times n$$ identity matrix, all the column
vectors in that matrix construct the **standard basis for \mathbf{R}^{n}$$**

