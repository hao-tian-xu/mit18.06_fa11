# **Unit I: Ax = b and the Four Subspaces**

- Mathematics is a tool for **describing the world around us**. Linear equations give some of the simplest descriptions, and systems of linear equations are made by <u>combining several descriptions</u>.
- In this unit we **write systems of linear equations in the matrix form** $A\mathbf{x} = \mathbf{b}$. 
	- We explore how the properties of $A$ and $\mathbf{b}$ determine the solutions $\mathbf{x}$ (if any exist) and pay particular attention to the solutions to $A\mathbf{x} = 0$. 
	- For a given matrix $A$ we ask which $\mathbf{b}$ can be written in the form $A\mathbf{x}$.

# <u>L1. The geometry of linear equations</u>

The fundamental problem of linear algebra is to solve n linear equations in n unknowns, e.g.
$$
\begin{aligned}
2 x-y &=0 \\
-x+2 y &=3
\end{aligned}
$$

## view the problem in three ways

### 1. Row Picture

- The lines $2 x-y=0$ and $-x+2 y=3$ intersect at the point $(1,2)$
	-   <img src="image.assets/Screen Shot 2021-10-09 at 17.28.18.png" alt="Screen Shot 2021-10-09 at 17.28.18" style="zoom: 25%;" />
- The solution to a three dimensional system of equations is the common point of intersection of three planes (if there is one). 

### 2. Column Picture

- rewrite the system of linear equations as a single equation by turning the coefficients in the columns of the system into vectors:
	- $x\left[\begin{array}{r}2 \\ -1\end{array}\right]+y\left[\begin{array}{r}-1 \\ 2\end{array}\right]=\left[\begin{array}{l}0 \\ 3\end{array}\right]$
- Given two vectors $c$ and $d$ and scalars $x$ and $y$, the sum $xc + yd$ is called a **linear combination** of $c$ and $d$. 
-  A linear combination of the column vectors equals the vector $b$
	-   <img src="image.assets/Screen Shot 2021-10-09 at 17.35.53.png" alt="Screen Shot 2021-10-09 at 17.35.53" style="zoom:25%;" />

### 3. Matrix Picture

- We write the system of equations as a single equation by using matrices and vectors:
	- $\left[\begin{array}{rr}2 & -1 \\ -1 & 2\end{array}\right]\left[\begin{array}{l}x \\ y\end{array}\right]=\left[\begin{array}{l}0 \\ 3\end{array}\right]$
	- The matrix $A=\left[\begin{array}{rr}2 & -1 \\ -1 & 2\end{array}\right]$ is called the coefficient matrix
	- The vector $\mathbf{x}=\left[\begin{array}{l}x \\ y\end{array}\right]$ is the vector of unknowns
	- The values on the right hand side of the equations form the vector $\mathbf{b}$
	- $A \mathbf{x}=\mathbf{b}$

### Matrix Multiplication

- Linear combination
	- the entries of $x$ as the coefficients of a linear combination of the column vectors of the matrix
	- $\left[\begin{array}{ll}2 & 5 \\ 1 & 3\end{array}\right]\left[\begin{array}{l}1 \\ 2\end{array}\right]=1\left[\begin{array}{l}2 \\ 1\end{array}\right]+2\left[\begin{array}{l}5 \\ 3\end{array}\right]=\left[\begin{array}{r}12 \\ 7\end{array}\right]$

- Dot product
	- taking the dot product of each row of $A$ with the vector $x$
	- $\left[\begin{array}{ll}2 & 5 \\ 1 & 3\end{array}\right]\left[\begin{array}{l}1 \\ 2\end{array}\right]=\left[\begin{array}{l}2 \cdot 1+5 \cdot 2 \\ 1 \cdot 1+3 \cdot 2\end{array}\right]=\left[\begin{array}{r}12 \\ 7\end{array}\right]$



## *Thinking*

- 线性代数的主要问题是求解线性方程组
	- 几何方式看待这个问题的多个角度：
		- 行：线性方程代表的线的交点
		- 列：列向量的组合
		- 矩阵

# <u>L2. Elimination with matrices</u>

## Method of Elimination

- $A=\left[\begin{array}{lll}
	1 & 2 & 1 \\
	3 & 8 & 1 \\
	0 & 4 & 1
	\end{array}\right] \longrightarrow\left[\begin{array}{rrr}
	1 & 2 & 1 \\
	0 & 2 & -2 \\
	0 & 4 & 1
	\end{array}\right] \longrightarrow U=\left[\begin{array}{rrr}
	1 & 2 & 1 \\
	0 & 2 & -2 \\
	0 & 0 & 5
	\end{array}\right]$

	> - We started with an invertible matrix $A$ and ended with an upper triangular matrix $U$; the lower left portion of $U$ is filled with zeros. Pivots $1,2,5$ are on the diagonal of $U$.
	> - The determinant of $U$ is the product of the pivots
	> - If there is a zero in the pivot position, we must exchange that row with one below to get a non-zero value in the pivot position. 
	> - If there is a zero in the pivot position and no non-zero value below it, then the matrix A is not invertible. Elimination can not be used to find a unique solution to the system of equations – it doesn’t exist. 

## Elimination Matrices

### Matrix Multiplication

- The product of a matrix (3x3) and a column vector (3x1) is a column vector (3x1) that is a linear combination of the columns of the matrix. 
- The product of a row (1x3) and a matrix (3x3) is a row (1x3) that is a linear combination of the rows of the matrix.

### Elimination matrix

- Elementary / Elimination matrix
	- $\left[\begin{array}{rrr}1 & 0 & 0 \\ -3 & 1 & 0 \\ 0 & 0 & 1\end{array}\right]\left[\begin{array}{lll}1 & 2 & 1 \\ 3 & 8 & 1 \\ 0 & 4 & 1\end{array}\right]=\left[\begin{array}{rrr}1 & 2 & 1 \\ 0 & 2 & -2 \\ 0 & 4 & 1\end{array}\right]$
	- The elimination matrix used to eliminate the entry in row $m$ column $n$ is denoted $E_{m n}$. The calculation above took us from $A$ to $E_{21} A$. The three elimination steps leading to $U$ were: $E_{32}\left(E_{31}\left(E_{21} A\right)\right)=U$, where $E_{31}=I$. Thus $E_{32}\left(E_{21} A\right)={U}$
- Associativity
	- Matrix multiplication is associative, so we can also write $\left(E_{32} E_{21}\right) A=U$. The product $E_{32} E_{21}$ tells us how to get from $A$ to $U .$ The inverse of the matrix $E_{32} E_{21}$ tells us how to get from $U$ to $A$

- A permutation matrix exchanges two rows of a matrix; for example, 
	- $P=\left[\begin{array}{lll}0 & 1 & 0 \\ 1 & 0 & 0 \\ 0 & 0 & 1\end{array}\right]$
	- To exchange the columns of a matrix, multiply on the right (as in AP) by a permutation matrix.
	- Note that matrix multiplication is not commutative: $P A \neq A P$.

## *Thinking*

- 高斯消元法是线性代数中的一个基本方法
	- 矩阵消除
		- 行消除
		- 消除矩阵 $EA=U$

# <u>L3. Multiplication and Inverse Matrices</u>

## Matrix Multiplication

### Standard (row times column)

- $c_{i j}=\sum_{k=1}^{n} a_{i k} b_{k j}$

### Columns

- The product of matrix $A$ and column $j$ of matrix $B$ equals column $j$ of matrix C. This tells us that the columns of $C$ are combinations of columns of $A$.

### Rows

- The product of row $i$ of matrix $A$ and matrix $B$ equals row $i$ of matrix $C$. So the rows of $C$ are combinations of rows of $B$.

### Column times row

- $A B=\sum_{k=1}^{n}\left[\begin{array}{r}a_{1 k} \\ \vdots \\ a_{m k}\end{array}\right]\left[\begin{array}{lll}b_{k 1} & \cdots & b_{k n}\end{array}\right]$

### Blocks

- $\left[\begin{array}{cc}A_{1} & A_{2} \\ A_{3} & A_{4}\end{array}\right]\left[\begin{array}{ll}B_{1} & B_{2} \\ B_{3} & B_{4}\end{array}\right]=\left[\begin{array}{ll}C_{1} & C_{2} \\ C_{3} & C_{4}\end{array}\right]$

	where $C_{1}=A_{1} B_{1}+A_{2} B_{3}$

## Inverses

### Square matrices

- If $A$ is a square matrix, the most important question you can ask about it is whether it has an inverse $A^{-1}$. If it does, then $A^{-1} A=I=A A^{-1}$ and we say that $A$ is **invertible** or **nonsingular**.
- If $A$ is **singular** - i.e. $A$ does not have an inverse - its determinant is zero and we can find some non-zero vector $\mathbf{x}$ for which $A \mathbf{x}=0$.
	- $A^{-1}A \mathbf{x}=A^{-1}0\quad\to\quad \mathbf{x} = 0 $ 

### Finding the inverse of a matrix 

- e.g. $\left[\begin{array}{ll}
	1 & 3 \\
	2 & 7
	\end{array}\right]\left[\begin{array}{ll}
	a & c \\
	b & d
	\end{array}\right]=\left[\begin{array}{ll}
	1 & 0 \\
	0 & 1
	\end{array}\right]$

	can be read as saying " $A$ times column $j$ of $A^{-1}$ equals column $j$ of the identity matrix". This is just a special form of the equation $A \mathbf{x}=\mathbf{b}$.

- use Gauss-Jordan elimination to solve the two linear equations at once

## Gauss-Jordan Elimination

- $\left[\begin{array}{ll|ll}
	1 & 3 & 1 & 0 \\
	2 & 7 & 0 & 1
	\end{array}\right] \rightarrow\left[\begin{array}{ll|rl}
	1 & 3 & 1 & 0 \\
	0 & 1 & -2 & 1
	\end{array}\right] \rightarrow\left[\begin{array}{rr|rr}
	1 & 0 & 7 & -3 \\
	0 & 1 & -2 & 1
	\end{array}\right]$
- $A^{-1}=\left[\begin{array}{rr}
	7 & -3 \\
	-2 & 1
	\end{array}\right]$
- $E[A \mid I]=[I \mid E] . \text { But if } E A=I \text {, then } E=A^{-1} \text {. }$

## *Thinking*

- 乘法：左矩阵的行数等于右矩阵的列数
- 五个方法
	- 行乘以列：结果矩阵的第 $i$ 行第 $j$ 列 $=$ 左矩阵的第 $i$ 行和右矩阵的第 $j$ 列的点积
	- 列：结果矩阵的第 $j$ 列 $=$ 右矩阵的第 $j$ 列作为参数的左矩阵的列组合（column combination）
	- 行：结果矩阵的第 $i$ 行 $=$ 左矩阵的第 $i$ 行作为参数的右矩阵的行组合（row combination）
	- 列乘以行：单列乘以单行为和结果矩阵相同的一个子矩阵，结果矩阵为所有子矩阵之和
	- 块
- 逆矩阵 inverse
	- 只有所有行都独立（即满秩）的方块矩阵才可逆
	- 使用高斯-若尔当消元法$E[A \mid I]=[I \mid E]$
	- $(AB)^{-1}=B^{-1}A^{-1}$
- 转置矩阵 transpose
	- $(AB)^{T}=B^{T}A^{T}$
	- $(A^T)^{-1} =(A^{-1})^T $
	- 任意矩阵 $R$ ，$R^TR$ 都是对称的
- 置换矩阵 permutation
	- 若涉及到行置换，则 $PA=LU$
	- $P$: 行置换后的特征矩阵，有 $n!$ 种可能
	- $P^{-1}=P^{T}$

# <u>L4. Factorization into $A=L U$</u>

- Inverse of a product
	- The inverse of a matrix product $A B$ is $B^{-1} A^{-1}$.
- Transpose of a product
	- The transpose of a matrix product $A B$ is $B^{T} A^{T}$. For any invertible matrix $A$, the inverse of $A^{T}$ is $\left(A^{-1}\right)^{T}$.

## $A=L U$

- $\overbrace{\left[\begin{array}{ll}
	1 & 0 \\
	-4 & 1
	\end{array}\right]}^{E_{21}}
	\overbrace{\left[\begin{array}{ll}
	2 & 1 \\
	8 & 7
	\end{array}\right]}^A
	=
	\overbrace{\left[\begin{array}{ll}
	2 & 1 \\
	0 & 3
	\end{array}\right]}^U$
- $E_{21}^{-1} E_{21} A=E_{21}^{-1} U$
- $\overbrace{\left[\begin{array}{ll}
	2 & 1 \\
	8 & 7
	\end{array}\right]}^A
	=
	\overbrace{\left[\begin{array}{ll}
	1 & 0 \\
	4 & 1
	\end{array}\right]}^L
	\quad
	\overbrace{\left[\begin{array}{ll}
	2 & 1 \\
	0 & 3
	\end{array}\right]}^U$
- The matrix $U$ is upper triangular with pivots on the diagonal.
- The matrix $L$ is lower triangular and has ones on the diagonal.
- Sometimes we will also want to factor out a diagonal matrix whose entries are the pivots:
	$\overbrace{\left[\begin{array}{ll}
	2 & 1 \\
	8 & 7
	\end{array}\right]}^A
	=
	\overbrace{\left[\begin{array}{ll}
	1 & 0 \\
	4 & 1
	\end{array}\right]}^L
	\quad
	\overbrace{\left[\begin{array}{ll}
	2 & 0 \\
	0 & 3
	\end{array}\right] }^D
	\quad
	\overbrace{\left[\begin{array}{rr}
	1 & 1 / 2 \\
	0 & 1
	\end{array}\right]}^{U'}$

### Three Dimensional

- if $E_{32} E_{31} E_{21} A=U$ then $A=E_{21}^{-1} E_{31}^{-1} E_{32}^{-1} U= LU$

	- e.g. $\overbrace{\left[\begin{array}{rrr}1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & -5 & 1\end{array}\right] }^{E_{32}}
		\quad
		\overbrace{\left[\begin{array}{rrr}1 & 0 & 0 \\ -2 & 1 & 0 \\ 0 & 0 & 1\end{array}\right]}^{E_{21}}
		=
		\overbrace{\left[\begin{array}{rrr}1 & 0 & 0 \\ -2 & 1 & 0 \\ 10 & -5 & 1\end{array}\right]}^E$

		where $\overbrace{\left[\begin{array}{lll}1 & 0 & 0 \\ 2 & 1 & 0 \\ 0 & 0 & 1\end{array}\right] }^{E_{21}^{-1}}
		\quad
		\overbrace{\left[\begin{array}{lll}1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 5 & 1\end{array}\right]}^{E_{32}^{-1}}
		=
		\overbrace{\left[\begin{array}{lll}1 & 0 & 0 \\ 2 & 1 & 0 \\ 0 & 5 & 1\end{array}\right]}^L$

- Notice the 0 in row three column one of $L=E^{-1}$, where $E$ had a 10. If there are no row exchanges, the multipliers from the elimination matrices are copied directly into $L$.

## *Thinking*

- $LU$ 包含矩阵 $A$ 的完整且清晰直接的信息
	- $U$ 的对角线显示了矩阵的主元（pivot）
	- $L$ 的对角线为 $1$，左下角显示了 $A\to U$ 的变换过程

# <u>L5. Transposes, permutations, spaces $\mathbb{R}^n$</u>

### Permutations

- when applying the method of elimination we use permutation matrices to move zeros out of pivot positions
	- Our factorization $A=L U$ then becomes $P A=L U$
	- Recall that $P^{-1}=P^{T}$, i.e. that $P^{T} P=I$
	- $P$: identity matrix with reordered rows, $n!$ possibilities

### Transposes

- When we take the transpose of a matrix, its rows become columns and its columns become rows: $\left(A^{T}\right)_{i j}=A_{j i}$
	- A matrix $A$ is symmetric if $A^{T}=A$
	- Given any matrix $R$ (not necessarily square) the product $R^{T} R$ is always symmetric,
		because $\left(R^{T} R\right)^{T}=R^{T}\left(R^{T}\right)^{T}=R^{T} R$  (Note that $\left(R^{T}\right)^{T}=R$)

## Vector spaces

- An example of a space is $\mathbb{R}^{n}$, the set of (column) vectors with $n$ real number components.

### Closure

- If a collection of vectors is closed under linear combinations (i.e. under addition and multiplication by any real numbers), and if multiplication and addition behave in a reasonable way, then we call that collection a vector space.

### Subspace

- A vector space that is contained inside of another vector space is called a subspace of that space. 
	- For example, take any non-zero vector $\mathbf{v}$ in $\mathbb{R}^{2}$. Then the set of all vectors $c \mathbf{v}$, where $c$ is a real number, forms a subspace of $\mathbb{R}^{2}$. This collection of vectors describes a line through $\left[\begin{array}{c}0 \\ 0\end{array}\right]$ in $\mathbb{R}^{2}$ and is closed under addition.
- The subspaces of $\mathbb{R}^{2}$ are:
	1. all of $\mathbb{R}^{2}$,
	2. any line through $\left[\begin{array}{l}0 \\ 0\end{array}\right]$ and
	3. the zero vector alone $(Z)$.
- The subspaces of $\mathbb{R}^{3}$ are:
  1. all of $\mathbb{R}^{3}$,
  2. any plane through the origin,
  3. any line through the origin, and
  4. the zero vector alone $(Z)$.

### Column space

- Given a matrix $A$ with columns in $\mathbb{R}^{3}$, these columns and all their linear combinations form a subspace of $\mathbb{R}^{3}$. This is the column space $C(A)$. If $A=\left[\begin{array}{ll}1 & 3 \\ 2 & 3 \\ 4 & 1\end{array}\right]$, the column space of $A$ is the plane through the origin in $\mathbb{R}^{3}$ containing $\left[\begin{array}{l}1 \\ 2 \\ 4\end{array}\right]$ and $\left[\begin{array}{l}3 \\ 3 \\ 1\end{array}\right]$.

## *Thinking*

- 向量空间作为线性代数的核心概念
	- 定义：一个在线性组合下闭合的向量集合
	- 子空间

# <u>L6. Column space and nullspace</u>

## Column space of $A$

- The column space of a matrix $A$ is the vector space made up of all linear combinations of the columns of $A$

### Solving $A \mathbf{x}=\mathbf{b}$

- Given a matrix $A$, for what vectors $\mathbf{b}$ does $A \mathbf{x}=\mathbf{b}$ have a solution $\mathbf{x}$ ?
	- Let $A=\left[\begin{array}{lll}1 & 1 & 2 \\ 2 & 1 & 3 \\ 3 & 1 & 4 \\ 4 & 1 & 5\end{array}\right]$
	- The system of linear equations $A \mathbf{x}=\mathbf{b}$ is solvable exactly when $\mathbf{b}$ is a vector in the column space of $A$.
	- Are the columns of $A$ independent?
		- The third column of $A$ is the sum of the first two columns
		- The column space of our matrix $A$ is a two dimensional subspace of $\mathbb{R}^{4}$.

## Nullspace of $A$

- The nullspace of a matrix $A$ is the collection of all solutions $\mathbf{x}=\left[\begin{array}{l}x_{1} \\ x_{2} \\ x_{3}\end{array}\right]$ to the equation $A \mathbf{x}=0$
	- In the example: $\left[\begin{array}{lll}1 & 1 & 2 \\ 2 & 1 & 3 \\ 3 & 1 & 4 \\ 4 & 1 & 5\end{array}\right]\left[\begin{array}{l}x_{1} \\ x_{2} \\ x_{3}\end{array}\right]=\left[\begin{array}{l}0 \\ 0 \\ 0 \\ 0\end{array}\right]$
	- the nullspace $N(A)$ consists of all multiples of $ \left[\begin{array}{r}1 \\ 1 \\ -1\end{array}\right]$

### Other values of $\mathbf{b}$

- The solutions to the equation: $\left[\begin{array}{lll}
	1 & 1 & 2 \\
	2 & 1 & 3 \\
	3 & 1 & 4 \\
	4 & 1 & 5
	\end{array}\right]\left[\begin{array}{l}
	x_{1} \\
	x_{2} \\
	x_{3}
	\end{array}\right]=\left[\begin{array}{l}
	1 \\
	2 \\
	3 \\
	4
	\end{array}\right]$ do not form a subspace. 
	- The set of solutions forms a line in $\mathbb{R}^{3}$ that passes through the points $\left[\begin{array}{l}1 \\ 0 \\ 0\end{array}\right]$ and $\left[\begin{array}{r}0 \\ -1 \\ 1\end{array}\right]$ but not $\left[\begin{array}{l}0 \\ 0 \\ 0\end{array}\right]$



# <u>L7. Solving $A\mathbf{x} = 0$: Pivot Variables, Special Solutions</u>

## Computing the nullspace: elimination

- e.g. $A=\left[\begin{array}{lllr}1 & 2 & 2 & 2 \\ 2 & 4 & 6 & 8 \\ 3 & 6 & 8 & 10\end{array}\right]$
- Our algorithm for computing the nullspace of this matrix uses the method of elimination, despite the fact that A is not invertible. 
- $A=\left[\begin{array}{lllr}1 & 2 & 2 & 2 \\ 2 & 4 & 6 & 8 \\ 3 & 6 & 8 & 10\end{array}\right]  \longrightarrow\left[\begin{array}{llll}1 & 2 & 2 & 2 \\ 0 & 0 & 2 & 4 \\ 0 & 0 & 2 & 4\end{array}\right]\longrightarrow\left[\begin{array}{llll}
	1 & 2 & 2 & 2 \\
	0 & 0 & 2 & 4 \\
	0 & 0 & 0 & 0
	\end{array}\right]=U$
- The **rank** of a matrix $A$ equals the number of pivots it has. In this example, the rank of $A$ (and of $U$ ) is 2.

### Pivot variables / free variables

-  In our example, columns 1 and 3 are pivot columns containing pivots, and columns 2 and 4 are free columns.
- We can assign any value to $x_2$ and $x_4$; we call these **free variables**.

### Special solutions

- The nullspace of $A$ is the collection of all linear combinations of “special solution” vectors.
	- Letting a free variable equal 1 and setting the other free variables equal to zero
	- $\mathbf{x}=\left[\begin{array}{r}-2 \\ 1 \\ 0 \\ 0\end{array}\right]$ or $\mathbf{x}=\left[\begin{array}{r}2 \\ 0 \\ -2 \\ 1\end{array}\right]$
- The rank $r$ of $A$ equals the number of pivot columns, so the number of free columns is $n − r$. This equals the number of special solution vectors and the dimension of the nullspace.

### Reduced row echelon form

- $U=\left[\begin{array}{llll}1 & 2 & 2 & 2 \\ 0 & 0 & 2 & 4 \\ 0 & 0 & 0 & 0\end{array}\right] \rightarrow\left[\begin{array}{rrrr}1 & 2 & 0 & -2 \\ 0 & 0 & 2 & 4 \\ 0 & 0 & 0 & 0\end{array}\right] \rightarrow\left[\begin{array}{rrrr}1 & 2 & 0 & -2 \\ 0 & 0 & 1 & 2 \\ 0 & 0 & 0 & 0\end{array}\right]=R$
- By exchanging some columns, $R$ can be rewritten with a copy of the identity matrix in the upper left corner, possibly followed by some free columns on the right. If some rows of $A$ are linearly dependent, the lower rows of the matrix R will be filled with zeros:
	$R=\left[\begin{array}{ll}I & F \\ 0 & 0\end{array}\right]$
- If $N$ is the nullspace matrix $N=\left[\begin{array}{c}-F \\ I\end{array}\right]$ then $R N=0$. (Here $I$ is an $n-r$ by $n-r$ square matrix and 0 is an $m$ by $n-r$ matrix.) The columns of $N$ are the special solutions.

## *Thinking*

- 求解 $A\mathbf{x} = 0$ ：主元列/变量，自由列/变量，简化列阶梯形矩阵（rref）
	- 通过高斯消元法得出 $A\to U$ ，从而得出主元，其所在的列为主元列/变量，其余为自由列/变量
	- 将自由变量之一取$1$，其余取$0$，得到一个特殊解，所有特殊解（special solution）的线性组合为 $A$ 的零空间 $N(A)$
	- $rref(U) = R = \left[\begin{array}{c} I& F \\ 0& 0 \end{array}\right] $ ，$\left[\begin{array}{c} F \\ 0 \end{array}\right]$ 为自由列，$N(A) = \left[\begin{array}{c} -F \\ I \end{array}\right]$

# <u>L8. Solving $A \mathbf{x}=\mathbf{b}:$ row reduced form $R$</u>

## Solvability conditions on $\mathbf{b}$

### Elimination

- $\left[\begin{array}{lllrl}1 & 2 & 2 & 2 & b_{1} \\ 2 & 4 & 6 & 8 & b_{2} \\ 3 & 6 & 8 & 10 & b_{3}\end{array}\right] \rightarrow \cdots \rightarrow\left[\begin{array}{lllll}1 & 2 & 2 & 2 & b_{1} \\ 0 & 0 & 2 & 4 & b_{2}-2 b_{1} \\ 0 & 0 & 0 & 0 & b_{3}-b_{2}-b_{1}\end{array}\right]$
- If $A \mathbf{x}=\mathbf{b}$ has a solution, then $b_{3}-b_{2}-b_{1}=0$

### Column Space

- $A \mathbf{x}=\mathbf{b}$ is solvable exactly when $\mathbf{b}$ is in the column space $C(A)$

## Complete solution

### A particular solution

- set all free variables to zero, then solve for the pivot variables. 
- $\mathbf{x}_{p}=\left[\begin{array}{r}-2 \\ 0 \\ 3 / 2 \\ 0\end{array}\right]$

### Combined with the nullspace

- The general solution to $A \mathbf{x}=\mathbf{b}$ is given by $\mathbf{x}_{\text {complete }}=\mathbf{x}_{p}+\mathbf{x}_{n}$, where $\mathbf{x}_{n}$ is a generic vector in the nullspace.
	- Proof: add $A \mathbf{x}_{p}=\mathbf{b}$ to $A \mathbf{x}_{n}=\mathbf{0}$ and get $A\left(\mathbf{x}_{p}+\mathbf{x}_{n}\right)=\mathbf{b}$ for every vector $\mathbf{x}_{n}$ in the nullspace.
- $\mathbf{x}_{\text {complete }}=\left[\begin{array}{r}-2 \\ 0 \\ 3 / 2 \\ 0\end{array}\right]+c_1\left[\begin{array}{r}-2 \\ 1 \\ 0 \\ 0\end{array}\right]+c_{2}\left[\begin{array}{r}2 \\ 0 \\ -2 \\ 1\end{array}\right]$
- The nullspace of $A$ is a two dimensional subspace of $\mathbb{R}^{4}$, and the solutions to the equation $A \mathbf{x}=\mathbf{b}$ form a plane parallel to that through $x_{p}=\left[\begin{array}{r}-2 \\ 0 \\ 3 / 2 \\ 0\end{array}\right]$.

## Rank

- The rank of a matrix equals the number of pivots of that matrix

### Full column rank

- the nullspace has dimension $n − r = 0$
- no free variables or special solutions
- there is either 0 or 1 solution
- The row reduced echelon form of the matrix will look like $R=\left[\begin{array}{l}I \\ 0\end{array}\right]$
- For any vector $\mathbf{b}$ in $\mathbb{R}^{m}$ that's not a linear combination of the columns of $A$, there is no solution to $A \mathbf{x}=\mathbf{b}$.

### Full row rank

- If $r=m$, then the reduced matrix $R=[I \quad F]$ has no rows of zeros
- there are no requirements for the entries of $\mathbf{b}$ to satisfy
- The equation $A \mathbf{x}=\mathbf{b}$ is solvable for every b. There are $n-r=n-m$ free variables, so there are $n-m$ special solutions to $A \mathbf{x}=\mathbf{0}$

### Full row and column rank

- If $r=m=n$ is the number of pivots of $A$, then $A$ is an invertible square matrix and $R$ is the identity matrix.
- The nullspace has dimension zero, and $A \mathbf{x}=\mathbf{b}$ has a unique solution for every b in $\mathbb{R}^{m}$.

### Summary

|                                          | $r=m=n$ | $r = n < m$                                      | $r = m < n$                                      | $r < m, r < n$                                            |
| ---------------------------------------- | ------- | ------------------------------------------------ | ------------------------------------------------ | --------------------------------------------------------- |
| $R$                                      | $I$     | $\left[\begin{array}{l}I \\ 0\end{array}\right]$ | $\left[\begin{array}{ll}I & F\end{array}\right]$ | $\left[\begin{array}{ll}I & F \\ 0 & 0\end{array}\right]$ |
| # solutions to $A \mathbf{x}=\mathbf{b}$ | $1$     | $0$ or $1$                                       | infinitely many                                  | $0$ or infinitely many                                    |

## *Thinking*

-  求解$A \mathbf{x}=\mathbf{b}$：秩 rank
	- 当 $\mathbf{b}$ 在 $C(A)$ 中时，有解
	- 求特解（particular solution）：将所有自由变量设为$0$，求主元变量
	- 将特解和零空间相加即为方程的解
	- 秩（rank）和系数矩阵 $A$ 的尺寸的关系决定了方程的解的数量

# <u>L9. Independence, basis, and dimension</u>

### Linear independence

- Vectors $\mathbf{x}_{1}, \mathbf{x}_{2}, \ldots \mathbf{x}_{n}$ are **linearly independent** (or just independent) if $c_{1} \mathbf{x}_{1}+c_{2} \mathbf{x}_{2}+\cdots+c_{n} \mathbf{x}_{n}=\mathbf{0}$ only when $c_{1}, c_{2}, \ldots, c_{n}$ are all $0 .$ 
	- When those vectors are the columns of $A$, the only solution to $A \mathbf{x}=\mathbf{0}$ is $\mathbf{x}=\mathbf{0}$.
	- nullspace of $A$ contains only the zero vector. 
	- all columns are pivot columns, the rank of $A$ is $n$, and there are no free variables

### Spanning a space

- Vectors $\mathbf{v}_{1}, \mathbf{v}_{2}, \ldots \mathbf{v}_{k}$ **span** a space when the space consists of all combinations of those vectors.
- If vectors $\mathbf{v}_{1}, \mathbf{v}_{2}, \ldots \mathbf{v}_{k}$ span a space $S$, then $S$ is the <u>smallest</u> space containing those vectors.

## Basis and dimension

- A **basis** for a vector space is a sequence of vectors $\mathbf{v}_{1}, \mathbf{v}_{2}, \ldots \mathbf{v}_{d}$ with two properties:
	- $\mathbf{v}_{1}, \mathbf{v}_{2}, \ldots \mathbf{v}_{d}$ are independent
	- $\mathbf{v}_{1}, \mathbf{v}_{2}, \ldots \mathbf{v}_{d}$ span the vector space.
- **The basis of a space tells us everything we need to know about that space.**
- e.g. One basis for $\mathbb{R}^{3}$ is $\left\{\left[\begin{array}{l}1 \\ 0 \\ 0\end{array}\right],\left[\begin{array}{l}0 \\ 1 \\ 0\end{array}\right],\left[\begin{array}{l}0 \\ 0 \\ 1\end{array}\right]\right\}$
- In general, $n$ vectors in $\mathbb{R}^{n}$ form a basis if they are the column vectors of an invertible matrix.

### Dimension

- Given a space, every basis for that space has the same number of vectors; that number is the **dimension** of the space. So there are exactly $n$ vectors in every basis for $\mathbb{R}^{n}$.

### Bases of a column space and nullspace

- e.g. $A=\left[\begin{array}{llll}1 & 2 & 3 & 1 \\ 1 & 1 & 2 & 1 \\ 1 & 2 & 3 & 1\end{array}\right]$
	- $\operatorname{rank}(A)=$ number of pivot columns of $A=$ dimension of $C(A)$
		(Note that matrices have a rank but not a dimension. Subspaces have a dimension but not a rank.) 
	- dimension of $N(A)=$ number of free variables $=n-r$
		- The two special solutions $\left[\begin{array}{r}-1 \\ -1 \\ 1 \\ 0\end{array}\right]$ and $\left[\begin{array}{r}-1 \\ 0 \\ 0 \\ -1\end{array}\right]$ form a basis for the nullspace. 

## *Thinking*

- 向量空间的基（basis）
	- 定义：一组线性无关、并生成（span）该空间的向量
	- 空间的基包含所有该空间的信息

# <u>L10. The Four Fundamental Subspaces</u>

## Four subspaces

<img src="image.assets/Screen Shot 2021-10-12 at 18.33.15.png" alt="Screen Shot 2021-10-12 at 18.33.15" style="zoom:25%;" />

- Any $m$ by $n$ matrix $A$ determines four subspaces (possibly containing only the zero vector):

	1. **Column space**, $C(A)$
		$C(A)$ consists of all combinations of the columns of $A$ and is a vector space in $\mathbb{R}^{m}$

		- <u>Basis</u>: Pivot columns

		- <u>Dimension</u>: The $r$ pivot columns form a basis for $C(A)$

			$\operatorname{dim} C(A)=r$

	2. **Nullspace**, $N(A)$
		This consists of all solutions $\mathbf{x}$ of the equation $A \mathbf{x}=\mathbf{0}$ and lies in $\mathbb{R}^{n}$.

		- <u>Basis</u>: The special solutions to $A \mathbf{x}=\mathbf{0}$ which also correspond to free variables
		- <u>Dimension</u>: $\operatorname{dim} N(A)=n-r$

	3. **Row space**, $C\left(A^{T}\right)$
		The combinations of the row vectors of $A$ form a subspace of $R^{n} .$ We equate this with $C\left(A^{T}\right)$, the column space of the transpose of $A$.

		- <u>Basis</u>: The first $r$ rows of $R$ are the "echelon" basis for the row space of $A$

		- <u>Dimension</u>: $\operatorname{dim} C\left(A^{T}\right)=r$

	4. **Left nullspace**, $N\left(A^{T}\right)$
		We call the nullspace of $A^{T}$ the left nullspace of $A$. This is a subspace of $\mathbb{R}^{m}$.

		- <u>Basis</u>: 
			- To find a basis for the left nullspace we reduce an augmented version of A:
				- $\left[\begin{array}{ll}A_{m \times n} & I_{m \times m}\end{array}\right] \longrightarrow\left[\begin{array}{ll}R_{m \times n} & E_{m \times m}\end{array}\right]$
				- From this we get the matrix $E$ for which $E A=R$
			- e.g. $E A=\left[\begin{array}{rrr}-1 & 2 & 0 \\ 1 & -1 & 0 \\ -1 & 0 & 1\end{array}\right]\left[\begin{array}{llll}1 & 2 & 3 & 1 \\ 1 & 1 & 2 & 1 \\ 1 & 2 & 3 & 1\end{array}\right]=\left[\begin{array}{llll}1 & 0 & 1 & 1 \\ 0 & 1 & 1 & 0 \\ 0 & 0 & 0 & 0\end{array}\right]=R$
			- The bottom $m − r$ rows of $E$ describe linear dependencies of rows of $A$, because the bottom $m − r$ rows of $R$ are zero. Here $m-r=1$ (one zero row in $R$ ).
				- threefore basis: $\left[\begin{array}{rrr}-1 & 0 & 1\end{array}\right]$
		- <u>Dimension</u>: $\operatorname{dim} N\left(A^{T}\right)=m-r$

### Dimensions

- $\operatorname{dim} C\left(A^{T}\right) + \operatorname{dim} N(A) =  n$
	- $A$ has $n$ variables: $r$ pivot variables and $n-r$ free variables
- $\operatorname{dim} C(A) + \operatorname{dim} N\left(A^{T}\right) =  m$
	- $A^T$ has $m$ variables: $r$ pivot variables and $m-r$ free variables

## New vector space

- The collection of all $3 × 3$ matrices forms a vector space; call it $M$.
	- **<u>Obey all rules of vector space:</u>**
		- **We can add matrices and multiply them by scalars and there’s a zero matrix (additive identity)**
	- Some subspaces of $M$ include:
		- all upper triangular matrices
		- all symmetric matrices
		- $D$, all diagonal matrices
			- $D$ is the intersection of the first two spaces
			- Its dimension is $3$
			- One basis for $D$ is:
				- $\left[\begin{array}{lll}1 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 0\end{array}\right],\left[\begin{array}{lll}1 & 0 & 0 \\ 0 & 3 & 0 \\ 0 & 0 & 0\end{array}\right],\left[\begin{array}{lll}0 & 0 & 0 \\ 0 & 0 & 0 \\ 0 & 0 & 7\end{array}\right] .$

## *Thinking*

本讲介绍了 $m × n$ 矩阵 $A$ 的四个子空间：

- 列空间是矩阵的列向量及其线性组合；零空间是所有使 $A \mathbf{x}=\mathbf{0}$ 的 $\mathbf{x}$ ；行空间是矩阵的行向量及其线性组合；左零空间是 $A^T$ 的零空间（由于 $A^Ty=0\to y^T A=0$ 而得名）
	- 列空间和左零空间的维度之和为 $m$ ，对应 $A^T$ 的 $r$ 个主变量和 $m-r$ 个自由变量

# <u>L11. Matrix spaces; rank 1; small world graphs</u>

- we can think about **vector spaces** made up of <u>any sort of “vectors” that allow addition and scalar multiplication</u>. 

## New vector spaces

- Differential equations
- Rank $4$ matrices

### Rank $1$ matrices

- e.g. $A=\left[\begin{array}{rrr}1 & 4 & 5 \\ 2 & 8 & 10\end{array}\right]$
	- $A=\left[\begin{array}{l}1 \\ 2\end{array}\right]\left[\begin{array}{lll}1 & 4 & 5\end{array}\right]$
- Every rank 1 matrix $A$ can be written $A=\mathbf{U V}^{T}$, where $\mathbf{U}$ and $\mathbf{V}$ are column vectors. 
- We'll use rank 1 matrices as **building blocks for more complex matrices**.

## *Thinking*

- 抽象的向量空间
	- 本讲介绍了一些新的“向量”空间，事实上只要符合向量空间定义的“元素”集都可以作为向量空间来应用线性代数中的一系列成果。
	- 这些“元素”如：矩阵、微分方程等



# <u>L12. Graphs, Networks, Incidence Matrices</u>

<img src="image.assets/Screen Shot 2021-10-14 at 10.14.50.png" alt="Screen Shot 2021-10-14 at 10.14.50" style="zoom:33%;" />
$$
\text{Incidence Matrix: }
A=\left[\begin{array}{rrrr}
-1 & 1 & 0 & 0 \\
0 & -1 & 1 & 0 \\
-1 & 0 & 1 & 0 \\
-1 & 0 & 0 & 1 \\
0 & 0 & -1 & 1
\end{array}\right]
$$

$$
\begin{array}{ccc}
\mathbf{x}=x_{1}, x_{2}, x_{3}, x_{4} & & A^{T} \mathbf{y}=0 \\
\text { potentials at nodes } & & \text { Kirchhoff's Current Law } \\
\\
\mathbf{e}=A \mathbf{x} \downarrow & & \uparrow A^{T} \mathbf{y} \\
\\
x_{2}-x_{1}, \text { etc. } & \mathbf{y}=C \mathbf{e} & y_{1}, y_{2}, y_{3}, y_{4}, y_{5} \\
\text { potential differences } & \longrightarrow & \text { currents on edges } \\
& \text { Ohm's Law }
\end{array}
$$

## *Thinking*

- 矩阵作为实际问题的抽象
	- 本讲使用连接矩阵（incidence matrix）来描述一个电路，从而使用针对矩阵的各操作来研究电路的各问题





















