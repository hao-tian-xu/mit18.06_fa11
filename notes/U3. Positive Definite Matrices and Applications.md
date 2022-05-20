

# **Unit III: Positive Definite Matrices and Applications**

- In this unit we discuss **matrices with special properties** – <u>symmetric, possibly complex, and positive definite</u>. 
- The central topic of this unit is **converting matrices to nice form (diagonal or nearly-diagonal)** through <u>multiplication by other matrices</u>. 
- Generally, this process requires some knowledge of <u>the eigenvectors and eigenvalues</u> of the matrix.

# <u>L25. Symmetric matrices and positive definiteness</u>

- Symmetric matrices are good
	- their <u>eigenvalues are real</u> 
	- and each has a complete set of <u>orthonormal eigenvectors</u>. 
- Positive definite matrices are even better. 

## Symmetric matrices

- If $A$ has $n$ independent eigenvectors we can write $A=S \Lambda S^{-1} .$ 
- If $A$ is symmetric we can write $A=Q \Lambda Q^{-1}=Q \Lambda Q^{T}$, where $Q$ is an orthogonal matrix.

### Projection onto eigenvectors

- If $A=A^{T}$, we can write:
	$$
	\begin{aligned}
	A &=Q \Lambda Q^{T} \\
	&=\left[\begin{array}{llll}
	\mathbf{q}_{1} & \mathbf{q}_{2} & \cdots & \mathbf{q}_{n}
	\end{array}\right]\left[\begin{array}{lll}
	\lambda_{1} & & \\
	& \lambda_{2} & & \\
	& \ddots & \\
	& & \lambda_{n}
	\end{array}\right]\left[\begin{array}{c}
	\mathbf{q}_{1}^{T} \\
	\mathbf{q}_{2}^{T} \\
	\vdots \\
	\mathbf{q}_{n}^{T}
	\end{array}\right] \\
	&=\lambda_{1} \mathbf{q}_{1} \mathbf{q}_{1}^{T}+\lambda_{2} \mathbf{q}_{2} \mathbf{q}_{2}^{T}+\cdots+\lambda_{n} \mathbf{q}_{n} \mathbf{q}_{n}^{T}
	\end{aligned}
	$$
- The matrix $\mathbf{q}_{k} \mathbf{q}_{k}^{T}$ is the projection matrix onto $\mathbf{q}_{k}$, so every symmetric matrix is a combination of perpendicular projection matrices.

## Positive definite matrices

- a symmetric matrix
- all eigenvalues are positive
- all pivots are positive
- all subdeterminants are positive

## *Thinking*

- 对称矩阵 $A=Q \Lambda Q^{T}$
- 正定矩阵

# <u>L26. Complex Matrices; Fast Fourier Transform (FFT)</u>

## Complex vectors

### Length

- $|\mathbf{z}|^{2}=\overline{\mathbf{z}}^{T} \mathbf{z}=\left|z_{1}\right|^{2}+\left|z_{2}\right|^{2}+\cdots+\left|z_{n}\right|^{2} = \mathbf{z}^H\mathbf{z}$

### Inner product

- $\mathbf{y}^{H} \mathbf{x}=\overline{\mathbf{y}}^{T} \mathbf{x}=\bar{y}_{1} x_{1}+\bar{y}_{2} x_{2}+\cdots+\bar{y}_{n} x_{n}$

## Complex matrices

### Symmetric(Hermitian) matrices

- $\bar{A}^{T}=A=A^H$
	- real eigenvalues
	- perpendicular eigenvectors

### Orthonormal(Unitary) Matrices

- $\overline{\mathbf{q}}_{j} \mathbf{q}_{k}=\left\{\begin{array}{cc}0 & j \neq k \\ 1 & j=k\end{array}\right.$
	- $Q^{H} Q=I$

## Fast Fourier transform

- $F_{n}=\left[\begin{array}{ccccc}1 & 1 & 1 & \cdots & 1 \\ 1 & w & w^{2} & & w^{n-1} \\ 1 & w^{2} & w^{4} & & w^{2(n-1)} \\ \vdots & & & \ddots & \vdots \\ 1 & w^{n-1} & w^{2(n-1)} & \cdots & w^{(n-1)^{2}}\end{array}\right]$, where $w=e^{i \cdot 2 \pi / n}\left(\right.$ so $\left.w^{n}=1\right)$
	- $O(n^2)$
- $F_{2 n}=\left[\begin{array}{rr}I & D \\ I & -D\end{array}\right]\left[\begin{array}{rr}F_{n} & 0 \\ 0 & F_{n}\end{array}\right] P$, where $D$ is a diagonal matrix and $P$ is a $2 n$ by $2 n$ permutation matrix
	- $O(n\log n)$



## *Thinking*

- 矩阵特性对应的复数版本
- 通过矩阵操作增加傅立叶变换的速度



# <u>L27. Positive definite matrices and minima</u>

- Studying positive definite matrices brings the whole course together
	- we use <u>pivots</u>, <u>determinants</u>, <u>eigenvalues</u> and <u>stability</u>. 
	- The new quantity here is $\mathbf{x}^TA\mathbf{x}$
- This lecture covers how to tell if a matrix is positive definite, what it means for it to be positive definite, and some geometry. 

## Positive definite matrices

Given a symmetric two by two matrix $\left[\begin{array}{cc}a & b \\ b & c\end{array}\right]$, here are four ways to tell if it's positive definite:
1. Eigenvalue test: $\lambda_{1}>0, \lambda_{2}>0$.
2. Determinants test: $a>0, a c-b^{2}>0$.
3. Pivot test: $a>0, \frac{a c-b^{2}}{a}>0$.
4. $\mathbf{x}^{T} A \mathbf{x}$ is positive except when $\mathbf{x}=\mathbf{0}$ (this is usually the definition of positive definiteness).

### Positive Semidefinite Matrix

The matrix $\left[\begin{array}{cc}2 & 6 \\ 6 & 18\end{array}\right]$ is on the borderline of positive definiteness and is called a positive semidefinite matrix. It's a singular matrix with eigenvalues 0 and 20. Positive semidefinite matrices have eigenvalues greater than or equal to 0 . For a singular matrix, the determinant is 0 and it only has one pivot.

### Hessian matrix

- The matrix of second derivatives of $f(x, y)$ is:
	$$
	\left[\begin{array}{ll}
	f_{x x} & f_{x y} \\
	f_{y x} & f_{y y}
	\end{array}\right]
	$$
	- This matrix is symmetric because $f_{x y}=f_{y x} .$ 
	- Its determinant is positive when the matrix is positive definite, which matches the $f_{x x} f_{y y}>f_{x y}^{2}$ test for a minimum that we learned in calculus.

## *Thinking*

- 正定矩阵
	- 对称矩阵中，特征值、子行列式、主元，只要有一个全为正数，其余两个也全为正数

# <u>L28. Similar matrices and Jordan form</u>

- We’ve nearly covered the entire heart of linear algebra – once we’ve finished <u>singular value decompositions</u> we’ll have seen all the most central topics.

### $A^{T} A$ is positive definite

- $A$ is positive definite $\longrightarrow$ $A^{-1}$ is also positive definitive
	- the eigenvalues $1 / \lambda_{1}, 1 / \lambda_{2}, \cdots 1 / \lambda_{d}$ of $A^{-1}$ are also positive
- $A$ and $B$ positive definite $\longrightarrow$  $A+B$ is positive definitive
	- the property $\mathbf{x}^{T} A \mathbf{x}>0$ and $\mathbf{x}^{T} B \mathbf{x}>0$ to show that $\mathbf{x}^{T}(A+B) \mathbf{x}>0$ for $\mathbf{x} \neq 0$
- Now suppose $A$ is a rectangular $(m$ by $n)$ matrix
	- $\mathbf{x}^{T}\left(A^{T} A\right) \mathbf{x}=(A \mathbf{x})^{T}(A \mathbf{x})=|A \mathbf{x}|^{2} \geq 0$
	- If $A$ has rank $n$ (independent columns), then $\mathbf{x}^{T}\left(A^{T} A\right) \mathbf{x}=\mathbf{0}$ only if $\mathbf{x}=\mathbf{0}$ and $A^TA$ is positive definite.

## Similar matrices $A$ and $B=M^{-1} A M$

- Two square matrices $A$ and $B$ are **similar** if $B=M^{-1} A M$ for some matrix $M$.
	- All matrices in a **family** are similar to each other. 
	- Each family can be <u>represented by a diagonal (or nearly diagonal) matrix</u>.

### Distinct eigenvalues 

- $S^{-1} A S=\Lambda$. So $A$ is similar to $\Lambda$ (choosing $M$ to be this $S$ ).
- if $B=M^{-1} A M$, then
	$\begin{aligned}
	A M M^{-1} \mathbf{x} &=\lambda \mathbf{x} \\
	M^{-1} A M M^{-1} \mathbf{x} &=\lambda M^{-1} \mathbf{x} \\
	B M^{-1} \mathbf{x} &=\lambda M^{-1} \mathbf{x} .
	\end{aligned}$
	- The matrix $B$ has the same $\lambda$ as an eigenvalue. $M^{-1} \mathbf{x}$ is the eigenvector.

### Repeated eigenvalues

- There are two families of similar matrices with eigenvalues 4 and 4 . 

	- The larger family includes $\left[\begin{array}{ll}4 & 1 \\ 0 & 4\end{array}\right]$. Each of the members of this family has only one eigenvector.

	- The matrix $\left[\begin{array}{cc}4 & 0 \\ 0 & 4\end{array}\right]$ is the only member of the other family, because:

		$M^{-1}\left[\begin{array}{ll}
		4 & 0 \\
		0 & 4
		\end{array}\right] M=4 M^{-1} M=\left[\begin{array}{ll}
		4 & 0 \\
		0 & 4
		\end{array}\right]$

## Jordan form

- A Jordan block $J_{i}$ has a repeated eigenvalue $\lambda_{i}$ on the diagonal, zeros below the diagonal and in the upper right hand corner, and ones above the diagonal:
	$$
	J_{i}=\left[\begin{array}{ccccc}
	\lambda_{i} & 1 & 0 & \cdots & 0 \\
	0 & \lambda_{i} & 1 & & 0 \\
	\vdots & & \ddots & 1 & \vdots \\
	0 & 0 & & \lambda_{i} & 1 \\
	0 & 0 & \cdots & 0 & \lambda_{i}
	\end{array}\right]
	$$

- Jordan's theorem says that every square matrix $A$ is similar to a Jordan matrix $J$, with Jordan blocks on the diagonal:
	$$
	J=\left[\begin{array}{cccc}
	J_{1} & 0 & \cdots & 0 \\
	0 & J_{2} & \cdots & 0 \\
	\vdots & & \ddots & \vdots \\
	0 & 0 & \cdots & J_{d}
	\end{array}\right]
	$$

- To summarize:
	- If $A$ has $n$ distinct eigenvalues, it is diagonalizable and its Jordan matrix is the diagonal matrix $J=\Lambda$.
	- If $A$ has repeated eigenvalues and "missing" eigenvectors, then its Jordan matrix will have $n-d$ ones above the diagonal.

## *Thinking*

- 矩阵相似 $B=M^{-1} A M$
	- 可以变换为相同的对角线矩阵
	- 有相同的特征值，特征矩阵为 $M^{-1} \mathbf{x}$
	- 3B1B：基变换

# <u>L29. Singular value decomposition</u>

## SVD

$$
A=U \Sigma V^{T}
$$
where $U$ is orthogonal, $\Sigma$ is diagonal, and $V$ is orthogonal.

- if $A$ is symmetric positive definite its eigenvectors are orthogonal and we can write $A = Q\Lambda Q^T$. This is a special case of a SVD, with $U = V = Q$

### How it works

- $A$ as a linear transformation taking a vector $\mathbf{v}_{1}$ in its row space to a vector $\mathbf{u}_{1}=A \mathbf{v}_{1}$ in its column space.
	- The SVD arises from finding an orthogonal basis for the row space that gets transformed into an orthogonal basis for the column space: $A \mathbf{v}_{i}=\sigma_{i} \mathbf{u}_{i}$.
	- zeros on the diagonal of $\Sigma$ will take care of the nullspaces of $A$ and $A^{T}$.

### Matrix language

The heart of the problem is to find an orthonormal basis $\mathbf{v}_{1}, \mathbf{v}_{2}, \ldots \mathbf{v}_{r}$ for the row space of $A$ for which
$$
\begin{aligned}
A\left[\begin{array}{llll}
\mathbf{v}_{1} & \mathbf{v}_{2} & \cdots & \mathbf{v}_{r}
\end{array}\right]&=\left[\begin{array}{lllll}
\sigma_{1} \mathbf{u}_{1} & \sigma_{2} \mathbf{u}_{2} & \cdots & \sigma_{r} \mathbf{u}_{r}
\end{array}\right] & & & \\
&=\left[\begin{array}{llll}
\mathbf{u}_{1} & \mathbf{u}_{2} & \cdots & \mathbf{u}_{r}
\end{array}\right]\left[\begin{array}{cccc}
\sigma_{1} & & & \\
& \sigma_{2} & & \\
& & \ddots & \\
& & & \sigma_{r}
\end{array}\right]
\end{aligned}
$$
with $\mathbf{u}_{1}, \mathbf{u}_{2}, \ldots \mathbf{u}_{r}$ an orthonormal basis for the column space of $A .$ 

- Once we add in the nullspaces, this equation will become $A V=U \Sigma$. 

	- We can complete the orthonormal bases $\mathbf{v}_{1}, \ldots \mathbf{v}_{r}$ and $\mathbf{u}_{1}, \ldots \mathbf{u}_{r}$ to orthonormal bases for the entire space any way we want. 
	- Since $\mathbf{v}_{r+1}, \ldots \mathbf{v}_{n}$ will be in the nullspace of $A$, the diagonal entries $\sigma_{r+1}, \ldots \sigma_{n}$ will be $0$.

- Since $V$ is orthogonal, we can multiply both sides by $V^{-1}=V^{T}$ to get:
	$$
	A=U \Sigma V^{T}
	$$

### Calculation

- multiply both sides by $A^{T}=V \Sigma^{T} U^{T}$ to get:
	$$
	\begin{aligned}
	A^{T} A &=V \Sigma U^{-1} U \Sigma V^{T} \\
	&=V \Sigma^{2} V^{T} \\
	&=V\left[\begin{array}{llll}
	\sigma_{1}^{2} & & \\
	& \sigma_{2}^{2} & & \\
	& & \ddots & \\
	& & & \sigma_{n}^{2}
	\end{array}\right] V^{T}
	\end{aligned}
	$$
	This is in the form $Q \Lambda Q^{T}$

	- we can now find $V$ by diagonalizing the symmetric positive definite (or semidefinite) matrix $A^{T} A$. 
	- The columns of $V$ are eigenvectors of $A^{T} A$ and the eigenvalues of $A^{T} A$ are the values $\sigma_{i}^{2}$. (We choose $\sigma_{i}$ to be the positive square root of $\lambda_{i}$.)

- Use $A \mathbf{v}_{i} = \sigma_{i} \mathbf{u}_{i}$ to find $U$

### Example with a nullspace

$$
\overbrace{\left[\begin{array}{cc}
4 & 3 \\
8 & 6
\end{array}\right]}^A
=
\overbrace{\frac{1}{\sqrt{5}}\left[\begin{array}{rr}
1 & 2 \\
2 & -1
\end{array}\right] }^U
\quad
\overbrace{\left[\begin{array}{rr}
\sqrt{125} & 0 \\
0 & 0
\end{array}\right]}^{\Sigma}
\quad
\overbrace{\left[\begin{array}{rr}
.8 & .6 \\
.6 & -.8
\end{array}\right]}^{V^T}
$$

- Four fundamental subspaces
	- $\mathbf{v}_{1}, \mathbf{v}_{2}, \ldots \mathbf{v}_{r}$ is an orthonormal basis for the row space. 
	- $\mathbf{u}_{1}, \mathbf{u}_{2}, \ldots \mathbf{u}_{r}$ is an orthonormal basis for the column space. 
	- $\mathbf{v}_{r+1}, \ldots \mathbf{v}_{n}$ is an orthonormal basis for the nullspace. 
	- $\mathbf{u}_{r+1}, \ldots \mathbf{u}_{m}$ is an orthonormal basis for the left nullspace.
- These are the "right" bases to use, because $A \mathbf{v}_{i} = \sigma_{i} \mathbf{u}_{i}$

## *Thinking*

- 奇异值分解 SVD (Singular Value Decomposition) $A=U \Sigma V^{T}$
	- 与四个基本空间的标准正交基的紧密关系
	- 特殊情况：正定矩阵 $A = Q\Lambda Q^T$



# <u>L30. Linear transformations and their matrices</u> 

- In older linear algebra courses, linear transformations were introduced before matrices. 
- This geometric approach to linear algebra initially avoids the need for coordinates.

### Without coordinates (no matrix) 

- Definition of linear
	- $T(\mathbf{v}+\mathbf{w})=T(\mathbf{v})+T(\mathbf{w})$
	- $T(c \mathbf{v})=c T(\mathbf{v})$

## *Thinking*

- 线性变换：3B1B利用这个角度从几何层面解释了这门线性代数的很多内容

# <u>L31. Change of basis; image compression</u>

### Compression of images

$$
\text { signal } \mathbf{x} \stackrel{\text { lossless }}{\longrightarrow} 64 \text { coefficients } c \stackrel{\text { lossy compression }}{\longrightarrow} \hat{c} \text { (many zeros) } \longrightarrow \hat{\mathbf{x}}=\sum \hat{c}_{i} \mathbf{v}_{i}
$$

- e.g. using column vectors of <u>Fourier Matrix</u> as bases instead of those of <u>Identity Matrix</u>

## Change of basis

### Vector

Let the columns of matrix $W$ be the basis vectors of the new basis. Then if $\mathbf{x}$ is a vector in the old basis, we can convert it to a vector $\mathbf{c}$ in the new basis using the relation:
$$
\mathbf{x}=W \mathbf{c}
$$

### Transformation matrices

Let the columns of matrix $M$ be the basis vectors of the new basis. Then if $A$ is a transformation matrix in the old basis, we can convert it to a transformation matrix $B$ in the new basis using the relation:
$$
B=M^{-1}AM
$$

## *Thinking*

- 通过改变基向量进行图像压缩（线性组合中出现零系数）
	- 基变换（3B1B）有更清晰的基于线性变换的讲述（见L22 Thinking）



# <u>L32. Exam3 review</u>

- Eigenvalues and eigenvectors
- Differential equations $\frac{d \mathbf{u}}{d t}=A \mathbf{u}$ and exponentials $e^{A t}$
- Symmetric matrices $A=A^{T}:$ These always have real eigenvalues, and they always have "enough" eigenvectors. The eigenvector matrix $Q$ can be an orthogonal matrix, with $A=Q \Lambda Q^{T}$.
- Positive definite matrices
- Similar matrices $B=M^{-1} A M .$ Matrices $A$ and $B$ have the same eigenvalues; powers of $A$ will "look like" powers of $B$.
- Singular value decomposition























