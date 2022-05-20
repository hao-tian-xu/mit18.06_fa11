# **Unit II: Least Squares, Determinants and Eigenvalues**

- Each component of a vector in $\mathbb{R}^n$ indicates a distance along one of the coordinate axes. This practice of dissecting a vector into directional components is an important one. In particular, it leads to **the "least squares" method of fitting curves to collections of data**. 
- This unit also introduces matrix *<u>eigenvalues</u>* and *<u>eigenvectors</u>*. Many **calculations become simpler when working with a basis of eigenvectors**.
- The *<u>determinant</u>* of a matrix is a number characterizing that matrix. This value is useful for **determining whether a matrix is singular, computing its inverse**, and more.

# <u>L14. Orthogonal vectors and subspaces</u>

- In this lecture we learn what it means for vectors, bases and subspaces to be orthogonal. The symbol for this is $\perp$.
- The “**big picture**” of this course is that the row space of a matrix’ is orthogonal to its nullspace, and its column space is orthogonal to its left nullspace. 

## Orthogonal vectors

- If two vectors are orthogonal, they form a right triangle whose hypotenuse is the sum of the vectors.
	- Thus, we can use the Pythagorean theorem to prove that the dot product $\mathbf{x}^{T} \mathbf{y}=\mathbf{y}^{T} \mathbf{x}$ is zero
		- $\|\mathbf{x}\|^{2} + \|\mathbf{y}\|^{2} = \|(\mathbf{x}+\mathbf{y})\|^{2}$
		- $\to\quad\begin{align}
			\mathbf{x}^{T} \mathbf{x}+\mathbf{y}^{T} \mathbf{y}
			&=(\mathbf{x}+\mathbf{y})^{T} (\mathbf{x}+\mathbf{y})
			\\&=\mathbf{x}^{T} \mathbf{x}+\mathbf{y}^{T} \mathbf{y}
			+\mathbf{x}^{T} \mathbf{y}+\mathbf{y}^{T} \mathbf{x}
			\end{align}$
		- $\to\quad\mathbf{x}^{T} \mathbf{y}+\mathbf{y}^{T} \mathbf{x}=0$
	- Note that all vectors are orthogonal to the zero vector. 

## Orthogonal subspaces

- Subspace $S$ is orthogonal to subspace $T$ means: <u>every</u> vector in $S$ is orthogonal to <u>every</u> vector in $T$.

### Nullspace is perpendicular to row space

- The row space of a matrix is **orthogonal** to the nullspace
	- because $A \mathbf{x}=\mathbf{0}$ 
		- which means the dot product of $\mathbf{x}$ with each row of $A$ is $0$,
		- and then the product of $\mathbf{x}$ with any combination of rows of $A$ must be $0$
	- The column space is orthogonal to the left nullspace of $A$ because the row space of $A^{T}$ is perpendicular to the nullspace of $A^{T}$.
- In some sense, the row space and the nullspace of a matrix subdivide $\mathbb{R}^{n}$ into two perpendicular subspaces.
	- We say that the nullspace and the row space are ***orthogonal complements*** in $\mathbb{R}^{n}$
- The fundamental theorem of linear algebra
	1. the dimensions of the four subspaces
	2. <u>those subspaces come in orthogonal pairs</u>
	3. orthogonal bases for these subspaces

### $N\left(A^{T} A\right)=N(A)$

- Due to measurement error, $A \mathbf{x}=\mathbf{b}$ is often unsolvable if $m>n$. Our next challenge is to find <u>the best possible solution</u> in this case.

	- the central equation is $A^{T} A \hat{\mathbf{x}}=A^{T} \mathbf{b}$

	- e.g. Suppose $A=\left[\begin{array}{ll}1 & 1 \\ 1 & 2 \\ 1 & 5\end{array}\right] .$ Then:

		$A^{T} A=\left[\begin{array}{lll}
		1 & 1 & 1 \\
		1 & 2 & 5
		\end{array}\right]\left[\begin{array}{ll}
		1 & 1 \\
		1 & 2 \\
		1 & 5
		\end{array}\right]=\left[\begin{array}{ll}
		3 & 8 \\
		8 & 30
		\end{array}\right]$ is invertible. 

		- $A^{T} A$ is not always invertible. In fact:
			$\begin{aligned}
			N\left(A^{T} A\right) &=N(A) \\
			\operatorname{rank} \text { of } A^{T} A &=\text { rank of } A
			\end{aligned}$

	- We conclude that $A^{T} A$ is invertible exactly when $A$ has independent columns.

## *Thinking*

- 正交向量、正交子空间
	- 正交向量：$\mathbf{x}^{T} \mathbf{y}=\mathbf{y}^{T} \mathbf{x}=\mathbf{0}$
	- 正交子空间：两子空间中的任意两向量垂直
		- 列空间和左零空间垂直，行空间和零空间垂直
- 接下来几讲的主要问题，找到 $A \mathbf{x}=\mathbf{b}$ 无解时的最优可能解
	- 核心等式：$A^{T} A \hat{\mathbf{x}}=A^{T} \mathbf{b}$
		- 其中 $N\left(A^{T} A\right)=N(A)$



# <u>L15. Projections onto subspaces</u>

## Projections

- e.g.  <img src="image.assets/Screen Shot 2021-10-13 at 17.59.47.png" alt="Screen Shot 2021-10-13 at 17.59.47" style="zoom: 25%;" />

- the length of $\mathbf{e}=\mathbf{b}-\mathbf{p}$ is the error in that approximation
- $\mathbf{p}=x \mathbf{a}$ for some number $x$ 
- $\mathbf{a}$ is perpendicular to $\mathbf{e}=\mathbf{b}-x\mathbf{a}$ 
	- $\to\quad\begin{array}{rll}
		\mathbf{a}^{T}(\mathbf{b}-x \mathbf{a})&=&0 \\
		x \mathbf{a}^{T} \mathbf{a}&=&\mathbf{a}^{T} \mathbf{b} \\
		x&=&\frac{\mathbf{a}^{T} \mathbf{b}}{\mathbf{a}^{T} \mathbf{a}}
		\end{array}$
	- $\to\quad\mathbf{p}=\mathbf{a} x=\mathbf{a} \frac{\mathbf{a}^{T} \mathbf{b}}{\mathbf{a}^{T} \mathbf{a}}$

### Projection matrix

- a projection matrix $P: \mathbf{p}=P \mathbf{b}$
	- $\to\quad P=\frac{\mathbf{a a}^{T}}{\mathbf{a}^{T} \mathbf{a}}$
	- The column space of $P$ is spanned by $\mathbf{a}$, because for any $\mathbf{b}$, $P \mathbf{b}$ lies on the line determined by $\mathbf{a}$.
	- The rank of $P$ is $1$.
	- $P$ is symmetric: $P^{T}=P$
	- $P^{2} \mathbf{b}=P \mathbf{b}$ because the projection of a vector already on the line through $\mathbf{a}$ is just that vector.

### Why project?

- The equation $A \mathbf{x}=\mathbf{b}$ may have no solution. 
	- The vector $A \mathbf{x}$ is always in the column space of $A$, and $\mathbf{b}$ is unlikely to be in the column space. 
	- So, we project $\mathbf{b}$ onto a vector $\mathbf{p}$ in the column space of $A$ and solve $A \hat{\mathbf{x}}=\mathbf{p}$.

### Projection in higher dimensions

- e.g. the column space (a plane) of a matrix $A=\left[\begin{array}{ll}\mathbf{a}_{1} & \mathbf{a}_{2}\end{array}\right]$
- $\mathbf{p}=\hat{x}_{1} \mathbf{a}_{1}+\hat{x}_{2} \mathbf{a}_{2}=A \hat{\mathbf{x}}$
- $\mathbf{e}=\mathbf{b}-\mathbf{p}=\mathbf{b}-A \hat{\mathbf{x}}$ is orthogonal to the plane
	- $\to\quad A^{T}(\mathbf{b}-A \hat{\mathbf{x}})=\mathbf{0}$
	- $\to\quad A^{T} A \hat{\mathbf{x}}=A^{T} \mathbf{b}$
	- $\to\quad \begin{aligned} \hat{\mathbf{x}} &=\left(A^{T} A\right)^{-1} A^{T} \mathbf{b} \\ \mathbf{p}=A \hat{\mathbf{x}} &=A\left(A^{T} A\right)^{-1} A^{T} \mathbf{b} \\ P &=A\left(A^{T} A\right)^{-1} A^{T} \end{aligned}$

## *Thinking*

- 投影：证明 $A^{T} A \hat{\mathbf{x}}=A^{T} \mathbf{b}$ 中的 $\hat{\mathbf{x}}$ 为 $A \mathbf{x}=\mathbf{b}$ 的最优可能解
	- 由正交投影中误差向量 $\mathbf{e}$ 和投影矩阵 $A$ 正交，得出 $ A^{T}\mathbf{e} = A^{T}(\mathbf{b}-A \hat{\mathbf{x}})=\mathbf{0}$ ，从而
		- $\begin{aligned} \hat{\mathbf{x}} &=\left(A^{T} A\right)^{-1} A^{T} \mathbf{b} \\ \mathbf{p}=A \hat{\mathbf{x}} &=A\left(A^{T} A\right)^{-1} A^{T} \mathbf{b} \\ P &=A\left(A^{T} A\right)^{-1} A^{T} \end{aligned}$

# <u>L16. Projection matrices and least squares</u>

## Projections

- If $b$ is perpendicular to the column space, then it's in the left nullspace $N\left(A^{T}\right)$ of $A$ and $\overrightarrow{P b}=0$.
- If $\mathbf{b}$ is in the column space then $\mathbf{b}=A \mathbf{x}$ for some $\mathbf{x}$, and $P \mathbf{b}=\mathbf{b}$
- A typical vector will have a component $\mathrm{p}$ in the column space and a component $\mathbf{e}$ perpendicular to the column space (in the left nullspace)
	- its projection is just the component in the column space.
- The matrix projecting $\mathbf{b}$ onto $N\left(A^{T}\right)$ is $I-P$ :  
	- $\begin{aligned}
		&\mathbf{e}=\mathbf{b}-\mathbf{p} \\
		&\mathbf{e}=(I-P) \mathbf{b}
		\end{aligned}$
	- Naturally, $I-P$ has all the properties of a projection matrix.

## Least squares

- e.g. <img src="image.assets/Screen Shot 2021-10-13 at 18.24.26.png" alt="Screen Shot 2021-10-13 at 18.24.26" style="zoom:25%;" />

- we're given a collection of data points $(t, b)$ :

	$\{(1,1),(2,2),(3,2)\}$

- we want to find the closest line $b=C+D t$ to that collection

- $\overbrace{\left[\begin{array}{ll}1 & 1 \\ 1 & 2 \\ 1 & 3\end{array}\right]}^A \quad \overbrace{\left[\begin{array}{l}C \\ D\end{array}\right]}^{\mathbf{x}}=\overbrace{\left[\begin{array}{l}1 \\ 2 \\ 2\end{array}\right]}^{\mathbf{b}}$

- In our example the line does not go through all three points, so this equation is not solvable. Instead we’ll solve: 
	$A^{T} A \hat{\mathbf{x}}=A^{T} \mathbf{b}$

### Linear regression

- to minimize $\|A \mathbf{x}-\mathbf{b}\|^{2}=\|\mathbf{e}\|^{2}$ 
- $\begin{aligned} A^{T} A \hat{\mathbf{x}} &=A^{T} \mathbf{b} \\\left[\begin{array}{rr}3 & 6 \\ 6 & 14\end{array}\right]\left[\begin{array}{c}\hat{C} \\ \hat{D}\end{array}\right] &=\left[\begin{array}{r}5 \\ 11\end{array}\right] \end{aligned}$
	- $\hat{D}=1 / 2$ and $\hat{C}=2 / 3$
	- $\mathbf{p}=\left[\begin{array}{r}7 / 6 \\ 5 / 3 \\ 13 / 6\end{array}\right]$ and $\mathbf{e}=\left[\begin{array}{r}-1 / 6 \\ 2 / 6 \\ -1 / 6\end{array}\right]$

## *Thinking*

- 投影的更多特性，使用线性回归（linear regression）求解最小二乘法（least squares）

# <u>L17. Orthogonal matrices and Gram-Schmidt</u>

### Orthonormal vectors

- The vectors $\mathbf{q}_{1}, \mathbf{q}_{2}, \ldots \mathbf{q}_{n}$ are **orthonormal** if:
	- $\mathbf{q}_{i}^{T} \mathbf{q}_{j}= \begin{cases}0 & \text { if } i \neq j \\ 1 & \text { if } i=j\end{cases}$
- In other words, they all have (normal) length $1$ and are perpendicular (ortho) to each other.

## Orthonormal matrix

- If the columns of $Q=\left[\begin{array}{lll}\mathbf{q}_{1} & \ldots & \mathbf{q}_{n}\end{array}\right]$ are **orthonormal**, then $Q^{T} Q=I$
- A <u>square</u> orthonormal matrix $Q$ is called an **orthogonal matrix**. If $Q$ is square, then $Q^{T} Q=I$ tells us that $Q^{T}={Q}^{-1}$.
	- Permutation matrices are orthogonal
	- The matrix $Q=\left[\begin{array}{cr}\cos \theta & -\sin \theta \\ \sin \theta & \cos \theta\end{array}\right]$ is orthogonal
- Hadamard matrices
	- e.g. $Q=\frac{1}{2}\left[\begin{array}{rrrr}1 & 1 & 1 & 1 \\ 1 & -1 & 1 & -1 \\ 1 & 1 & -1 & -1 \\ 1 & -1 & -1 & 1\end{array}\right]$, $\frac{1}{\sqrt{2}}\left[\begin{array}{rr}1 & 1 \\ 1 & -1\end{array}\right]$

### Orthonormal columns are good

- $P=Q^{T}\left(Q^{T} Q\right)^{-1} Q^{T} = Q Q^{T}$
	- $\hat{\mathbf{x}}=Q^{T} \mathbf{b}$
	- $\to\quad\hat{x}_{i} = \mathbf{q}_{i}^{T} \mathbf{b}$
- if $Q$ is square, $P=I$

### Gram-Schmidt

- With elimination, our goal was “make the matrix triangular”. Now our goal is “<u>make the matrix ortho-normal</u>”.
- Steps
	- Let $\mathbf{A}=\mathbf{a}$
	- $\mathbf{B}=\mathbf{b}-\mathbf{p}=\mathbf{b}-\frac{\mathbf{a}^{T} \mathbf{b}}{\mathbf{a}^{T} \mathbf{a}} \mathbf{a}$
	- $\mathbf{q}_{1}=\frac{\mathbf{A}}{\|\mathbf{A}\|} \text { and } \mathbf{q}_{2}=\frac{\mathbf{B}}{\|\mathbf{B}\|}$
	- if  three independent vectors: $\mathbf{C}=\mathbf{c}-\frac{\mathbf{A}^{T} \mathbf{c}}{\mathbf{A}^{T} \mathbf{A}} \mathbf{A}-\frac{\mathbf{B}^{T} \mathbf{c}}{\mathbf{B}^{T} \mathbf{B}} \mathbf{B}$

- $A=QR$

### Important matrices

- triangular, diagonal, permutation, symmetric, reduced row echelon, projection, and orthonormal matrices

## *Thinking*

- 标准正交矩阵对于解线性方程的<u>最优可能解</u>有种种优势
	- 通过格拉姆-施密特正交化将一组向量转化为标准正交向量，且其组成的子空间不变



# <u>L18. Properties of Determinants</u>

- The determinant is a number associated with any square matrix; we’ll write it as $\operatorname{det} A$ or $|A|$
- A matrix is invertible exactly when the determinant is non-zero. 

## Properties

1. $\operatorname{det} I=1$
2. If you <u>exchange two rows of a matrix</u>, you <u>reverse the sign</u> of its determinant from positive to negative or from negative to positive.
	- The determinant of a permutation matrix $P$ is $1$ or $-1$ depending on whether $P$ exchanges an even or odd number of rows.
3. (a) If we <u>multiply one row of a matrix by $t$</u>, the determinant is multiplied by $t:\left|\begin{array}{rr}t a & t b \\ c & d\end{array}\right|=t\left|\begin{array}{cc}a & b \\ c & d\end{array}\right| .$
    (b) The determinant behaves like <u>a linear function on the rows</u> of the matrix: $\left|\begin{array}{cc}
    a+a^{\prime} & b+b^{\prime} \\
    c & d
    \end{array}\right|=\left|\begin{array}{cc}
    a & b \\
    c & d
    \end{array}\right|+\left|\begin{array}{cc}
    a^{\prime} & b^{\prime} \\
    c & d
    \end{array}\right|$

### Corollary

1. If two rows of a matrix are equal, its determinant is zero. 
2. If $i \neq j$, subtracting $t$ times row $i$ from row $j$ doesn't change the determinant.
  - $\begin{aligned}\left|\begin{array}{cc}a & b \\ c-t a & d-t b\end{array}\right| &=\left|\begin{array}{ll}a & b \\ c & d\end{array}\right|-\left|\begin{array}{rr}a & b \\ t a & t b\end{array}\right| \quad \text { property 3(b) } \\ &=\left|\begin{array}{ll}a & b \\ c & d\end{array}\right|-t\left|\begin{array}{cc}a & b \\ a & b\end{array}\right| \quad \text { property 3(a) } \\ &=\left|\begin{array}{ll}a & b \\ c & d\end{array}\right| \text { property } 4 . \end{aligned}$
3. If $A$ has a row that is all zeros, then $\operatorname{det} A=0$.
4. The determinant of a triangular matrix is <u>the product of the diagonal entries</u> (pivots) $d_{1}, d_{2}, \ldots, d_{n}$
  - Corollary 2 tells us that the determinant of the triangular matrix won’t change if we use elimination to convert it to a diagonal matrix
5. $\operatorname{det} A=0$ exactly when $A$ is singular.
6. $\operatorname{det} A B=(\operatorname{det} A)(\operatorname{det} B)$
7. $\operatorname{det} A^{T}=\operatorname{det} A$

## *Thinking*

- 行列式（determinant）的性质（而不谈其公式）
	- 单位矩阵的行列式为 $1$
	- 交换行则矩阵行列式的正负号改变
	- 矩阵的行列式的每一行分别是线性的：乘以标量或相加



# <u>L19. Determinant formulas and cofactors</u>

### Determinant Formula

- $\operatorname{det} A=\sum_{n ! \text { terms }} \pm a_{1 \alpha} a_{2 \beta} a_{3 \gamma} \ldots a_{n \omega}$
	- where $(\alpha, \beta, \gamma, \ldots \omega)$ is some permutation of $(1,2,3, \ldots, n)$.
- Alternative way: Applying the method of elimination and multiplying the diagonal entries of the result (the pivots)

### Cofactor formula

- rewrites the big formula for the determinant of an $n$ by $n$ matrix in terms of the determinants of smaller matrices. 
- $\operatorname{det} A=a_{11} C_{11}+a_{12} C_{12}+\cdots+a_{1 n} C_{1 n}$
	- $C_{i j}$ equals $(-1)^{i+j}$ times the determinant of the $n-1$ by $n-1$ square matrix obtained by removing row $i$ and column $j .\left(C_{i j}\right.$ is positive if $i+j$ is even and negative if $i+j$ is odd.)

### Tridiagonal matrix

- $\left|A_{1}\right|=1,\left|A_{2}\right|=\left|\begin{array}{ll}1 & 1 \\ 1 & 1\end{array}\right|=0,\left|A_{3}\right|=\left|\begin{array}{lll}1 & 1 & 0 \\ 1 & 1 & 1 \\ 0 & 1 & 1\end{array}\right|=-1$
	$\left|A_{4}\right|=1\left|\begin{array}{lll}1 & 1 & 0 \\ 1 & 1 & 1 \\ 0 & 1 & 1\end{array}\right|-1\left|\begin{array}{lll}1 & 1 & 0 \\ 0 & 1 & 1 \\ 0 & 1 & 1\end{array}\right|=\left|A_{3}\right|-1\left|A_{2}\right|=-1$
- $\left|A_{n}\right|=\left|A_{n-1}\right|-\left|A_{n-2}\right|$

## *Thinking*

- 通过行列式的性质推导出行列式的公式

# <u>L20. Cramer’s rule, inverse matrix, and volume</u>

### Formula for $A^{-1}$

- $A^{-1}=\frac{1}{\operatorname{det} A} C^{T}$
	- $A C^{T}=\left[\begin{array}{rrr}a_{11} & \cdots & a_{1 n} \\ \vdots & \ddots & \vdots \\ a_{n 1} & \cdots & a_{n n}\end{array}\right]\left[\begin{array}{rrr}C_{11} & \cdots & C_{n 1} \\ \vdots & \ddots & \vdots \\ C_{1 n} & \cdots & C_{n n}\end{array}\right]$
	- $\sum_{j=1}^{n} a_{1 j} C_{j 1}=\operatorname{det} A$ 
		(This is just the cofactor formula for the determinant.)
	- <u>*see Notebook*</u>: The product of the first row of $A$ and the last column of $C^T$ equals the determinant of a matrix whose first and last rows are identical

### Cramer's Rule for $\mathbf{x}=A^{-1} \mathbf{b}$

- $\mathbf{x}=A^{-1}\mathbf{b}=\frac{1}{\operatorname{det} A} C^{T} \mathbf{b}$
- $x_{j}=\frac{\operatorname{det} B_{j}}{\operatorname{det} A}$
	where $B_{j}$ is the matrix created by starting with $A$ and then replacing column $j$ with $\mathbf{b}$
	- Proof: When taking the determinant of $B_{1}$ we get a sum whose first term is $b_{1}$ times the cofactor $C_{11}$ of $A$.

### $|\operatorname{det} A|=$ volume of box

- Claim: $|\operatorname{det} A|$ is the volume of the box (parallelepiped) whose edges are the column vectors of $A$. 
	(We could equally well use the row vectors, forming a different box with the same volume.)

## *Thinking*

- 克莱姆法则很精美但并没有卵用
- 行列式的绝对值等于列向量组成的“box”的体积



# <u>L21. Eigenvalues and eigenvectors</u>

## Eigenvectors and eigenvalues

- A matrix $A$ acts on vectors $\mathbf{x}$ like a function does, with input $\mathbf{x}$ and output $A \mathbf{x}$.
	- 3B1B: Linear Transformation
- **Eigenvectors** are vectors for which $A \mathbf{x}$ is parallel to $\mathbf{x}$. In other words:
	- $A \mathbf{x}=\lambda \mathbf{x}$
	- In this equation, $\mathbf{x}$ is an eigenvector of $A$ and $\lambda$ is an **eigenvalue** of $A$.
- Eigenvalue $0$
	- If the eigenvalue $\lambda$ equals 0 then $A \mathbf{x}=0 \mathbf{x}=\mathbf{0}$. 
		- Vectors with eigenvalue 0 make up the nullspace of $A$
		- if $A$ is singular, then $\lambda=0$ is an eigenvalue of $A$.
- Complex Eigenvalues
	- 3B1B: Eigenvalues that are complex numbers generally correspond to some kind of rotation in the transformation
	- e.g. $\left[\begin{array}{c} 0&-1\\1&0\end{array}\right]$, $\lambda = i, -i$

### $\operatorname{det}(A-\lambda I)=0$

- An $n$ by $n$ matrix will have $n$ eigenvalues, and <u>their sum will be the sum of the diagonal entries</u> of the matrix: $a_{11}+a_{22}+\cdots+a_{n n}$. 
- This sum is the **trace** of the matrix.
- $\begin{aligned} A \mathbf{x} &=\lambda \mathbf{x} \\(A-\lambda I) \mathbf{x} &=\mathbf{0} \end{aligned}\quad\to\quad \operatorname{det}(A-\lambda I)=0$
- use elimination to find the nullspace of $A-\lambda I$. 
	The vectors in that <u>nullspace</u> are eigenvectors of $A$ with eigenvalue $\lambda$.

### Calculating eigenvalues and eigenvectors

- e.g. $A=\left[\begin{array}{ll}
	3 & 1 \\
	1 & 3
	\end{array}\right]$
	- $\begin{aligned} \operatorname{det}(A-\lambda I) &=\left|\begin{array}{cc}3-\lambda & 1 \\ 1 & 3-\lambda\end{array}\right| \\ &=(3-\lambda)^{2}-1 \\ &=\lambda^{2}-6 \lambda+8 \end{aligned}$
	- In general, $\lambda^{2}-\operatorname{trace}(A) \cdot \lambda+\operatorname{det} A=0$
	- e.g. $B=\left[\begin{array}{ll}0 & 1 \\ 1 & 0\end{array}\right]$
		- $A \mathbf{x}=(B+3 I) \mathbf{x}=\lambda \mathbf{x}+3 \mathbf{x}=(\lambda+3) \mathbf{x}$

## *Thinking*

- 特征值和特征向量
	- 几何解释1: $\mathbf{x}$ 经过基变换 $A$ 后方向不变（或相反）
	- 几何解释2: $A$ 的线性组合 $A\mathbf{x}$ 和 $\mathbf{x}$ 平行



# <u>L22. Diagonalization and powers of $A$</u>

## Diagonalizing a matrix $S^{-1} A S=\Lambda$

### Diagonal Matrix (3B1B)

- All column vectors are <u>eigenvectors</u>
- All diagonal elements are <u>eigenvalues</u>

### Diagonalization

- If $A$ has $n$ linearly independent eigenvectors, we can put those vectors in the columns of a (square, invertible) matrix $S$. Then
	- $\begin{aligned} A S &=A\left[\begin{array}{llll}\mathbf{x}_{1} & \mathbf{x}_{2} & \cdots & \mathbf{x}_{n}\end{array}\right] \\ &=\left[\begin{array}{llll}\lambda_{1} \mathbf{x}_{1} & \lambda_{2} \mathbf{x}_{2} & \cdots & \lambda_{n} \mathbf{x}_{n}\end{array}\right] \\ &=S\left[\begin{array}{rrrr}\lambda_{1} & 0 & \cdots & 0 \\ 0 & \lambda_{2} & & 0 \\ \vdots & & \ddots & \vdots \\ 0 & \cdots & & 0 & \lambda_{n}\end{array}\right]=S \Lambda \end{aligned}$
	- $\to\quad S^{-1} A S=\Lambda\quad\to$
- $A=S \Lambda S^{-1}$
- Column vectors of $\Lambda$ form an **eigenbasis** (3B1B)

### Powers of $A$

- If $A \mathbf{x}=\lambda \mathbf{x}$ then $A^{2} \mathbf{x}=\lambda A \mathbf{x}=\lambda^{2} \mathbf{x}$
- $A^{2}=S \Lambda S^{-1} S \Lambda S^{-1}=S \Lambda^{2} S^{-1}$

### Repeated eigenvalues

- If $A$ has repeated eigenvalues, it may or may not have $n$ independent eigenvectors.

## Difference equations $\mathbf{u}_{k+1}=A \mathbf{u}_{k}$

- $\mathbf{u}_{k+1}=A \mathbf{u}_{k}$ is a first order difference equation, and $\mathbf{u}_{k}=A^{k} \mathbf{u}_{0}$ is a solution to this system.
	- We get a more satisfying solution if we write $\mathbf{u}_{0}$ as a combination of eigenvectors of $A$ : $\mathbf{u}_{0}=c_{1} \mathbf{x}_{1}+c_{2} \mathbf{x}_{2}+\cdots+c_{n} \mathbf{x}_{n}=S \mathbf{c}$
	- Then: $A \mathbf{u}_{0}=c_{1} \lambda_{1} \mathbf{x}_{1}+c_{2} \lambda_{2} \mathbf{x}_{2}+\cdots+c_{n} \lambda_{n} \mathbf{x}_{n}$
	- and: $\mathbf{u}_{k}=A^{k} \mathbf{u}_{0}=c_{1} \lambda_{1}^{k} \mathbf{x}_{1}+c_{2} \lambda_{2}^{k} \mathbf{x}_{2}+\cdots+c_{n} \lambda_{n}^{k} \mathbf{x}_{n}=\Lambda^{k} S \mathbf{c}$

### Fibonacci sequence

- $F_{k+2}=F_{k+1}+F_{k}$
	- If $\mathbf{u}_{k}=\left[\begin{array}{r}F_{k+1} \\ F_{k}\end{array}\right]$, then: $\begin{aligned}
		&F_{k+2}=F_{k+1}+F_{k} \\
		&F_{k+1}=F_{k+1}
		\end{aligned}$ is equivalent to the first order system:
		$\mathbf{u}_{k+1}=\left[\begin{array}{ll}1 & 1 \\ 1 & 0\end{array}\right] \mathbf{u}_{k}$
		- Eigenvalues: $|A-\lambda I|=\left|\begin{array}{cc}1-\lambda & 1 \\ 1 & -\lambda\end{array}\right|=\lambda^{2}-\lambda-1 \quad\to\quad \lambda=\frac{1 \pm \sqrt{1+4}}{2}$
		- Eigenvectors: $\mathbf{x}_{1}=\left[\begin{array}{r}
			\lambda_{1} \\
			1
			\end{array}\right] \text { and } \mathbf{x}_{2}=\left[\begin{array}{r}
			\lambda_{2} \\
			1
			\end{array}\right]$
		- Finally, $\mathbf{u}_{0}=\left[\begin{array}{c}F_{1} \\ F_{0}\end{array}\right]=\left[\begin{array}{l}1 \\ 0\end{array}\right]=c_{1} \mathbf{x}_{1}+c_{2} \mathbf{x}_{2}$ tells us that $c_{1}=-c_{2}=\frac{1}{\sqrt{5}}$
		- Because $\left[\begin{array}{c}F_{k+1} \\ F_{k}\end{array}\right]=\mathbf{u}_{k}=c_{1} \lambda_{1}^{k} x_{1}+c_{2} \lambda_{2}^{k} x_{2}$, we get: $F_{k}=\frac{1}{\sqrt{5}}\left(\frac{1+\sqrt{5}}{2}\right)^{k}-\frac{1}{\sqrt{5}}\left(\frac{1-\sqrt{5}}{2}\right)^{k}$

- Summary
	- When a sequence evolves over time according to the rules of a first order system, the eigenvalues of the matrix of that system determine the long term behavior of the series. To get an exact formula for the series we find the eigenvectors of the matrix and then solve for the coefficients $c1, c2, ...$ 

## *Thinking*

- 对角线化作为处理递归问题的方式：矩阵的幂
	- 3B1B的几何解读
		- 基变更：$\overbrace{M^{-1}}^{\text{用变更基}M\text{表示变换后的向量}}\quad\overbrace{A}^{\text{应用变换}A}\quad\overbrace{M}^{\text{将变更基}M\text{中的向量通过当前基进行表示}}$
		- 因此由 $A$ 的特征向量组成的基底中进行变换 $A$ ，则该变换只根据特征值缩放向量各坐标值，因此该变换为对角线值为特征值的对角线矩阵
	- 本讲介绍了代数证明
	- 使用差分方程（即递归关系）介绍了其应用

# <u>L23. Differential equations and $e^{A t}$</u>

- e.g. $\begin{gathered}
	\frac{d u_{1}}{d t}=-u_{1}+2 u_{2} \\
	\frac{d u_{2}}{d t}=u_{1}-2 u_{2}
	\end{gathered}$

## Differential equations $\frac{d u}{d t}=A \mathbf{u}$

- The general solution to this system of differential equations will be: 
	$$
	\mathbf{u}(t)=c_{1} e^{\lambda_{1} t} \mathbf{x}_{1}+c_{2} e^{\lambda_{2} t} \mathbf{x}_{2}
	$$

	- plug in $\mathbf{u}=e^{\lambda_{1} t} \mathbf{x}_{1}$, $\frac{d \mathbf{u}}{d t}=\lambda_{1} e^{\lambda_{1} t} \mathbf{x}_{1}$

		which agrees with: $A \mathbf{u}=e^{\lambda_{1} t} A \mathbf{x}_{1}=\lambda_{1} e^{\lambda_{1} t} \mathbf{x}_{1}$

- $A=\left[\begin{array}{rr}-1 & 2 \\ 1 & -2\end{array}\right]$

	- Eigenvalue: $\lambda_1 = 0$ and $\lambda_2 = -3$
	- Eigenvector: $\mathbf{x}_{1}=\left[\begin{array}{l}2 \\ 1\end{array}\right]$ and $\mathbf{x}_{2}=\left[\begin{array}{r}1 \\ -1\end{array}\right]$
	- ...

### Stability

1. Stability: $\mathbf{u}(t) \rightarrow 0$ when $\operatorname{Re}(\lambda)<0$
2. Steady state: One eigenvalue is $0$ and all other eigenvalues have negative real part.
3. Blow up: if $\operatorname{Re}(\lambda)>0$ for any eigenvalue $\lambda$.

### Applying $S$

- Set $\mathbf{u}=S \mathbf{v}$, where $S$ is the matrix of eigenvectors of $A$, to get: $S \frac{d \mathbf{v}}{d t}=A S \mathbf{v}$

	or: $\frac{d \mathbf{v}}{d t}=S^{-1} A S \mathbf{v}=\Lambda \mathbf{v}$

- This diagonalizes the system: $\frac{d v_{i}}{d t}=\lambda_{i} v_{i} .$ The general solution is then:
	$$
	\begin{aligned}
	\mathbf{v}(t) &=e^{\Lambda t} \mathbf{v}(0), \quad \text { and } \\
	\mathbf{u}(t) &=S e^{\Lambda t} S^{-1} \mathbf{v}(0)=e^{A t} \mathbf{u}(0)
	\end{aligned}
	$$

### Matrix exponential $e^{A t}$

- Power series: $e^{x}=\sum_{n=0}^{\infty} \frac{x^{n}}{n !}=1+x+\frac{x^{2}}{2}+\frac{x^{3}}{6}+\cdots$
- $\to \quad e^{A t}=I+A t+\frac{(A t)^{2}}{2}+\frac{(A t)^{3}}{6}+\cdots$
- $\to\quad\begin{aligned} e^{A t} &=I+A t+\frac{(A t)^{2}}{2}+\frac{(A t)^{3}}{6}+\cdots \\ &=S S^{-1}+S \Lambda S^{-1} t+\frac{S \Lambda^{2} S^{-1}}{2} t^{2}+\frac{S \Lambda^{3} S^{-1}}{6} t^{3}+\cdots \\ &=S e^{\Lambda t} S^{-1} \end{aligned}$
- and $e^{\Lambda t}=\left[\begin{array}{rrrr}e^{\lambda_{1} t} & 0 & \cdots & 0 \\ 0 & e^{\lambda_{2} t} & & 0 \\ \vdots & & \ddots & \vdots \\ 0 & \cdots & 0 & e^{\lambda_{n} t}\end{array}\right]$

### Second Order

- e.g. $y^{\prime \prime}+b y^{\prime}+k y=0$
	- If $u=\left[\begin{array}{c}y^{\prime} \\ y\end{array}\right]$, then $u^{\prime}=\left[\begin{array}{c}
		y^{\prime \prime} \\
		y^{\prime}
		\end{array}\right]=\left[\begin{array}{rr}
		-b & -k \\
		1 & 0
		\end{array}\right]\left[\begin{array}{c}
		y^{\prime} \\
		y
		\end{array}\right]$

## *Thinking*

- 特征值、特征向量和对角线矩阵在微分方程中的应用
	- 并定义了矩阵指数 $e^A$

# <u>L24. Markov matrices; Fourier series</u>

### Eigenvalues of $A^{T}$

- The eigenvalues of $A$ and the eigenvalues of $A^{T}$ are the same:
	- Proof: $(A-\lambda I)^{T}=A^{T}-\lambda I$

## Markov matrices

- e.g. A matrix like: $A=\left[\begin{array}{rrr}
	.1 & .01 & .3 \\
	.2 & .99 & .3 \\
	.7 & 0 & .4
	\end{array}\right]$
	- in which all entries are non-negative and each column adds to 1 is called a Markov matrix. 
	- These requiremen ts come from Markov matrices' use in probability. 
	- Squaring or raising a Markov matrix to a power gives us another Markov matrix.
- The fact that the columns sum to $1$ guarantee that $1$ is an eigenvalue?
	- Proof: $A-1 I=\left[\begin{array}{rrr}
		-.9 & .01 & .3 \\
		.2 & -.01 & .3 \\
		.7 & 0 & -.6
		\end{array}\right]$ should be singular
		- Since we've subtracted $1$ from each diagonal entry, the sum of the entries in each column of $A-I$ is zero.
- The eigenvector $\mathbf{x}_{1}$ is in the nullspace of $A-I$ and has eigenvalue 1. It's not very hard to find $\mathbf{x}_{1}=\left[\begin{array}{c}.6 \\ 33 \\ .7\end{array}\right]$.

### Application

- e.g. Population move (see notes)

## Fourier series and projections

### Expansion with an orthonormal basis

- If we have an orthonormal basis $\mathbf{q}_{1}, \mathbf{q}_{2}, \ldots, \mathbf{q}_{n}$ then we can write any vector $\mathbf{v}$ as $\mathbf{v}=x_{1} \mathbf{q}_{1}+x_{2} \mathbf{q}_{2}+\cdots+x_{n} \mathbf{q}_{n}$, where:
	$$
	\mathbf{q}_{i}^{T} \mathbf{v}=x_{1} \mathbf{q}_{i}^{T} \mathbf{q}_{1}+x_{2} \mathbf{q}_{i}^{T} \mathbf{q}_{2}+\cdots+x_{n} \mathbf{q}_{i}^{T} \mathbf{q}_{n}=x_{i}
	$$
	Since $\mathbf{q}_{i}^{T} \mathbf{q}_{j}=0$ unless $i=j$, this equation gives $x_{i}=\mathbf{q}_{i}^{T} \mathbf{v}$.

### Fourier series

- $f(x)=a_{0}+a_{1} \cos x+b_{1} \sin x+a_{2} \cos 2 x+b_{2} \sin 2 x+\cdots$

	- The vectors in this space are functions and the (orthogonal) basis vectors are $1, \cos x, \sin x$ $\cos 2 x, \sin 2 x, \ldots$

	- What does “orthogonal” mean in this context?

		- For vectors in $\mathbb{R}^{n}$ the inner product is $\mathbf{v}^{T} \mathbf{w}=v_{1} w_{1}+v_{2} w_{2}+\cdots+v_{n} w_{n} .$  
		- The best parallel to the vector dot product is: $f^{T} g=\int_{0}^{2 \pi} f(x) g(x) d x$

	- The inner product of two basis vectors is zero, as desired. For example, 
		$\int_{0}^{2 \pi} \sin x \cos x d x=\left.\frac{1}{2}(\sin x)^{2}\right|_{0} ^{2 \pi}=0$

	- Because we're working with an orthonormal basis, we can use the inner product to find the coefficients $a_{i}$
		$$
		\begin{aligned}
		\int_{0}^{2 \pi} f(x) \cos x d x &=\int_{0}^{2 \pi}\left(a_{0}+a_{1} \cos x+b_{1} \sin x+a_{2} \cos 2 x+\cdots\right) \cos x d x \\
		&=0+\int_{0}^{2 \pi} a_{1} \cos ^{2} x d x+0+0+\cdots \\
		&=a_{1} \pi
		\end{aligned}
		$$

## *Thinking*

- 马尔可夫矩阵：特征值和特征向量的应用
- 傅里叶级数：向量投影和标准正交基的应用



# <u>L24b. Exam 2 Review</u>

- Material covered by the exam
	- Orthogonal matrices $Q=\left[\begin{array}{lll}\mathbf{q}_{1} & \ldots & \mathbf{q}_{n}\end{array}\right] \cdot Q^{T} Q=I$
	  Projections - Least Squares "best fit" solution to $A \mathbf{x}=\mathbf{b}$.
	  Gram-Schmidt process for getting an orthonormal basis from any basis.
	- $\operatorname{det} A$
	  Properties $1-3$ that define the determinant.
	  Big formula for the determinant with $n !$ terms, each with $+$ or $-$.
	  Cofactors formula, leading to a formula for $A^{-1}$.
	- Eigenvalues $A \mathbf{x}=\lambda \mathbf{x}$
		$\operatorname{det}(A-\lambda I)=0$
		Diagonalization: If $A$ has $n$ independent eigenvectors, then $S^{-1} A S=\Lambda$ (this is $A \mathbf{x}=\lambda \mathbf{x}$ for all $n$ eigenvectors at once).
		Powers of $A: A^{k}=\left(S \Lambda S^{-1}\right)^{k}=S \Lambda^{k} S^{-1}$

## *Thinking*

这节复习课总结了并综合了这个单元的内容：

- 通过**投影**找到线性方程的<u>最优可能解</u> $\hat{\mathbf{x}}$： $A^{T} A \hat{\mathbf{x}}=A^{T} \mathbf{b}$
	- **标准正交**矩阵在这个过程中有很大优势，因为 $Q^TQ=I$
	- 使用格拉姆-施密特正交化来将一般矩阵转化为标准正交矩阵：$A=QR$
- 行列式
	- 行列式的三个特性
	- 行列式的公式 $\operatorname{det} A=\sum_{n ! \text { terms }} \pm a_{1 \alpha} a_{2 \beta} a_{3 \gamma} \ldots a_{n \omega}$
	- 余子式（cofactor）公式 $\operatorname{det} A=a_{11} C_{11}+a_{12} C_{12}+\cdots+a_{1 n} C_{1 n}$
	- $A^{-1}=\frac{1}{\operatorname{det} A} C^{T}$
- 通过 $A$ 的**特征向量**找到的 $S$ 和**特征值**的**对角线矩阵** $\Lambda$ ，从而计算 $A$ 的<u>幂</u>
	- $A \mathbf{x}=\lambda \mathbf{x}\quad\to\quad \operatorname{det}(A-\lambda I)=0$
	- 对角线化：如果 $A$ 有 $n$ 个独立的特征向量，那么 $S^{-1} A S=\Lambda$
	- $A$ 的幂：$A^{k}=\left(S \Lambda S^{-1}\right)^{k}=S \Lambda^{k} S^{-1}$















