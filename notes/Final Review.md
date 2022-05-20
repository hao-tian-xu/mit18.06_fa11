# **Final Review**

线性代数可以理解为对大量离散数据的结构处理，因此核心问题为线性方程和线性映射，核心方法是因式分解 factorization，从而得到有效的计算方法。由于是对于大量离散数据的处理，因此和工程关系紧密：

- 图、网络
	- 使用矩阵进行建模，从而利用矩阵的性质进行大量节点和边的数据处理
- 最小方差
	- 数据量和变量的数量不同时，进行投影再求解最优可能解；可利用 $A=QR$ 进行分解简化计算
- 微分方程
	- 使用特征值和特征向量的出 $A=X\Lambda X^{-1}$ ，结合幂级数（power series）得到矩阵指数的计算方式，进而得到 $\frac{d u}{d t}=A \mathbf{u}$ （将微分方程拓展到高维？）的一般解
	- 对角线化也是幂和递归的一般方法
- 图像压缩
	- 通过基变换（如傅立叶矩阵的列向量）增加线性组合中的小系数，将小系数近似为零，从而减少数据量

进一步地说，线性代数可以理解为对向量空间和矩阵的研究，这部分可以作为<u>纯数学</u>的领域；但符合其属性（如向量空间的线性闭合）的对象（如函数）都可以应用其成果作为工具进行分析计算。

## Summary

线性代数的基本概念和方法：

- 求解n阶线性方程组作为核心问题

- 线性意味着什么

- <u>理解方式</u>
	
	- 行作为线性方程
	- 列作为向量（线性组合）
	- 矩阵（线性变换）
	
- <u>方法</u>

  - 矩阵乘法
  	- 行乘以列作为一个元素 / 列的线性组合作为列 / 行的线性组合作为行 / 列乘以行的结果秩一矩阵作为结果矩阵的一个因子 / 块作为元素相乘
  	- $A=BC=\left[\begin{array}{cccc}\mid & \mid & & \mid \\ b_{1} & b_{2} & ... & b_{n} \\ \mid & \mid & & \mid\end{array}\right]\left[\begin{array}{ccc}- & c_{1}^{*} & - \\ - & c_{2}^{*} & - \\ & \vdots & \\ - & c_{n}^{*} & -\end{array}\right]=b_{1} c_{1}^{*}+b_{2} c_{2}^{*}+\cdots+b_{n} c_{n}^{*}= $ 秩一方阵之和
  - 高斯消元法 elimination
  	- 得出主元变量和自由变量
  	- 将自由变量之一取$1$，其余取$0$，得到一个特殊解，所有特殊解（special solution）的线性组合为 $A$ 的零空间 $N(A)$
  - 高斯若尔当消元法：求逆矩阵 $E[A \mid I]=[I \mid E]$
  - 简化列阶梯形矩阵 reduced row echelon form：解 $A\mathbf{x}=0$，$A\mathbf{x}=b$
  	- $rref(U) = R = \left[\begin{array}{c} I& F \\ 0& 0 \end{array}\right] $ ，$\left[\begin{array}{c} F \\ 0 \end{array}\right]$ 为自由列，$N(A) = \left[\begin{array}{c} -F \\ I \end{array}\right]$
  	- $A\mathbf{x}=b$
  		- 零空间加上特解（特解：所有自由变量为0的解）

- <u>概念</u>
	
	- 主元 pivots
	- 秩 rank：主元数量
	- 维度 dimension
	- 向量空间 vector space
		- 定义：一个在线性组合下闭合的向量集合
		- 向量空间的基 basis
		  - 线性无关（数量上限）且张成空间（数量下限）的向量集合
		  - 向量空间的维度 dimension
	- 行列式 determinant
		- 性质
		  - 单位矩阵的行列式为 $1$
		  - 交换行则矩阵行列式的正负号改变
		  - 矩阵的行列式的每一行分别是线性的：乘以标量或相加
		- 由性质得出公式：$\operatorname{det} A=\sum_{n ! \text { terms }} \pm a_{1 \alpha} a_{2 \beta} a_{3 \gamma} \ldots a_{n \omega}$
		- 代数余子式 C cofactor （符号为 $(-1)^{i+j}$ 的子行列式）
			- $\operatorname{det} A=a_{11} C_{11}+a_{12} C_{12}+\cdots+a_{1 n} C_{1 n}$
		- 克莱姆法则
	- 迹 trace：对角元素之和
		- $=$ 特征值的和
	- 特征值和特征向量 eigenvalues and eigenvactors
		- $A \mathbf{x}=\lambda \mathbf{x} \quad\to\quad \operatorname{det}(A-\lambda I)=0$
			- 特征值的和 $=$ 迹
			- 特征值的积 $=$ 行列式
		- 解决幂和递归（如对角线化和基变更）
	
- <u>关系</u>
  
  - 线性无关 linear independence
  - 张成空间 spanning a space
  	- 空间包含且仅包含这些向量的所有线性组合
  - 正交 orthogonal
  	- 向量：点积为零
  	- 空间：向量两两正交
  	- 标准正交 orthonormal
  		- $\mathbf{q}_{i}^{T} \mathbf{q}_{j}= \begin{cases}0 & \text { if } i \neq j \\ 1 & \text { if } i=j\end{cases}$
  - 相似 similar：$B=M^{-1} A M$
  
- <u>矩阵变换</u>

  - 消除矩阵 $E$ elimination
  	- $E_{32}\left(E_{31}\left(E_{21} A\right)\right)=U$
  - 逆矩阵 inverse
  	- 非奇异方形矩阵 nonsingular square
  	- $(AB)^{-1}=B^{-1}A^{-1}$
  - 矩阵转置 transpose
  	- $(AB)^{T}=B^{T}A^{T}$
  	- $(A^T)^{-1} =(A^{-1})^T $
  - 置换矩阵 $P$ permutation
  	- $P^{-1}=P^{T}$
  - 投影矩阵 $P$ projection
    - 求最优可能解：误差向量 $\mathbf{e}=\mathbf{b}-\mathbf{p}=\mathbf{b}-A \hat{\mathbf{x}}$ 和 $A$ 垂直 
      - $\to\quad A^{T}(\mathbf{b}-A \hat{\mathbf{x}})=\mathbf{0}$
      - $\to\quad A^{T} A \hat{\mathbf{x}}=A^{T} \mathbf{b}$ 
      	（若 $A=QR$ 则 $R^{\mathrm{T}} Q^{\mathrm{T}} Q R \hat{\mathbf{x}}=R^{\mathrm{T}} Q^{\mathrm{T}} \boldsymbol{b}$ 使得 $R \hat{\mathbf{x}}=Q^{\mathrm{T}} \boldsymbol{b}$ ）
      - $\to\quad P =A\left(A^{T} A\right)^{-1} A^{T}$
    - $P^2 = P$

- <u>向量空间</u>
  
  - $m × n$ 矩阵 $A$ 的四个基本子空间：
    
    -   ​	<img src="image.assets/Screen Shot 2021-10-12 at 18.33.15.png" alt="Screen Shot 2021-10-12 at 18.33.15" style="zoom: 33%;" />
      
    - 行空间 row：$A^T$ 的列空间
    
    - 零空间 null： $A\mathbf{x} = 0$ 的所有解向量
    
    - 列空间 column：维度 $r$ （主变量数）
    
    - 左零空间 left null： $A^T\mathbf{x} = 0$ 的所有解向量，维度 $n-r$ （自由变量数）
    
    - 前二者垂直且维度之和为$m$，后二者垂直且维度之和为$n$
    
      - |      | $\mathbf{N}(A) \perp \mathbf{C}\left(A^{\mathrm{T}}\right)$ | $\mathbf{N}\left(A^{\mathrm{T}}\right) \perp \mathbf{C}(A)$ |
      	| ---- | ----------------------------------------------------------- | ----------------------------------------------------------- |
      	| 维度 | $n-r\qquad r$                                               | $m-r\qquad r$                                               |
    
      - 若 $A x=0$ 则 $\left[\begin{array}{c}\text { row } 1 \\ : \\ \text { row } m\end{array}\right]\left[\begin{array}{l}x\end{array}\right]=\left[\begin{array}{c}0 \\ : \\ 0\end{array}\right]$
    
      	- $\to\quad\boldsymbol{x}$ 和 $A$ 的所有行向量垂直
  
- <u>特殊矩阵</u>
  
  - 标准正交矩阵 $Q$ orthonormal
  	- $Q^TQ = I$
  	- 正交矩阵 $Q$ （**<u>方形</u>**标准正交矩阵）orthogonal
  		- $Q^T = Q^{-1}$
  - 对称矩阵 symmetric
    - 所有对称矩阵都有：实数特征值，完整的标准正交特征向量集合
    - $A^TA$ 为对称矩阵：$\left(R^{T} R\right)^{T}=R^{T}\left(R^{T}\right)^{T}=R^{T} R$
    	也是半正定矩阵
    - 正定矩阵 positive definite
    	- 四个互为因果的测试
    		- 特征值大于 0
    		- 行列式大于 0
    		- 主元大于 0
    		- 任意非0向量有 $\mathbf{x}^{T} A \mathbf{x}$ 大于 0 （通常是正定的定义）
    	- 半正定矩阵 positive semidefinite（或nonnegative definite）：以上四个测试可以等于 0
    	- 如果 $A$ 是列满秩的，则 $A^TA$ 是正定矩阵
  - 马尔可夫矩阵 Markov
  	- 元素为正数，且列之和为 $1$
  		- 因此有特征值 $1$
  - 复数矩阵 complex
  	- $\bar{A}^{T}=A=A^H$
  
- <u>因式分解 factorization</u>

	- **目标：更方便大计算 big computation**

	- $A=CR$

		- $A=C R=\left[\begin{array}{ll}
			1 & 4 \\
			3 & 2 \\
			2 & 1
			\end{array}\right]\left[\begin{array}{lll}
			1 & 0 & 1 \\
			0 & 1 & 1
			\end{array}\right]
			=\left[\begin{array}{lll}
			1 & 4 & 5 \\
			3 & 2 & 5 \\
			2 & 1 & 3
			\end{array}\right]$
		- $C$ 包含 $A$ 的线性无关的列向量
		- $R$ 的列向量是列空间的基（包含一个 $r \times r$ 的单位矩阵）
			- 也是 $A$ 的 rref

	- $A=LU$

		- $E_{32} E_{31} E_{21} A=U\quad\to\quad A=E_{21}^{-1} E_{31}^{-1} E_{32}^{-1} U= LU$
		- 如果存在转置，则 $PA=LU$
		- $U$：上三角矩阵，对角线显示了矩阵的主元
		- $L$：下三角矩阵，对角线为1，左下角显示了 $A\to U$ 的变换过程

	- 格拉姆-施密特标准正交化：$A=QR$

		- Let $\mathbf{A}=\mathbf{a}$
		- $\mathbf{B}=\mathbf{b}-\mathbf{p}=\mathbf{b}-\frac{\mathbf{a}^{T} \mathbf{b}}{\mathbf{a}^{T} \mathbf{a}} \mathbf{a}$
		- $\mathbf{q}_{1}=\frac{\mathbf{A}}{\|\mathbf{A}\|} \text { and } \mathbf{q}_{2}=\frac{\mathbf{B}}{\|\mathbf{B}\|}$

	- 对角化 diagonalization：$AX=X\Lambda \quad\to\quad X^{-1} A X=\Lambda \quad\to\quad A=X \Lambda X^{-1}$ 

		- $A$ 有 $n$ 个线性无关的特征向量
		- $X$：特征向量矩阵
		- $\Lambda$：特征值对角矩阵

	- 对称矩阵 symmetric：$A=Q \Lambda Q^{-1}=Q \Lambda Q^{T}$

		- 所有对称矩阵都有：实数特征值，完整的标准正交特征向量集合
		- $Q$：正交矩阵

	- 相似矩阵 similar：$B=M^{-1} A M$

		- 若 $A$ 的特征值为 $\lambda$ ，特征向量为 $\mathbf{x}$ ，则 $B$ 的为 $\lambda$ 和 $M^{-1} \mathbf{x}$

	- 基变更 change of basis $B=M^{-1}AM$

		- $\overbrace{B}^{\text{新基}M\text{中的变换}B}=\overbrace{M^{-1}}^{\text{用新基}M\text{表示变换后的向量}}\quad\overbrace{A}^{\text{应用旧基中的变换}A}\quad\overbrace{M}^{\text{将新基}M\text{中的向量通过旧基进行表示}}$

	- 奇异值分解 SVD：$A=U \Sigma V^{T}$

		-     ​	<img src="image.assets/Screen Shot 2021-10-20 at 16.31.33.png" alt="Screen Shot 2021-10-20 at 16.31.33" style="zoom: 25%;" />

			- $U$，$V$ 是旋转，加上可能的镜像，$\Sigma$ 是缩放，将圆形变为椭圆形

		- $U$，$V$：正交矩阵，列向量为奇异向量 singular vector

		- $\Sigma$：对角矩阵，元素为奇异值 singular value $\sigma=\sqrt{\lambda(A^TA)}$

		- 起源：找到一组行空间的正交基，经 $A$ 的变换后成为一组列空间的正交基 $A \mathbf{v}_{i}=\sigma_{i} \mathbf{u}_{i}$

			$A
			\left[\begin{array}{llll}
			\mathbf{v}_{1} & \mathbf{v}_{2} & \cdots & \mathbf{v}_{r}
			\end{array}\right]
			=
			\left[\begin{array}{lllll}
			\sigma_{1} \mathbf{u}_{1} & \sigma_{2} \mathbf{u}_{2} & \cdots & \sigma_{r} \mathbf{u}_{r}
			\end{array}\right]
			=
			\left[\begin{array}{llll}
			\mathbf{u}_{1} & \mathbf{u}_{2} & \cdots & \mathbf{u}_{r}
			\end{array}\right]
			\left[\begin{array}{cccc}
			\sigma_{1} & & & \\
			& \sigma_{2} & & \\
			& & \ddots & \\
			& & & \sigma_{r}
			\end{array}\right]$

			- 加入零空间后即为 $A V=U \Sigma$

		- 计算：$A^TA=V\Sigma U^{-1}U\Sigma V^T=V\Sigma^2V^T$ 求 $V$ 和 $\Sigma$，再通过 $A \mathbf{v}_{i} = \sigma_{i} \mathbf{u}_{i}$ 求 $U$

		- $A=U \Sigma V^{T}$ 是 $\lambda_{1} \boldsymbol{q}_{1} \boldsymbol{q}_{1}^{\mathrm{T}}+\cdots+\lambda_{r} \boldsymbol{q}_{n} \boldsymbol{q}_{n}^{\mathrm{T}}$ 这些秩一方阵之和

		- $U$ 和 $V$ 包含了四个空间的正交基

- <u>应用</u>
  
  - 图、网络、连接矩阵 incidence matrix
  - 最小方差 least squares
  	- 即求误差向量的最小长度（平方和）
  - 微分方程 differential equations $\frac{d u}{d t}=A \mathbf{u}$
  	- 一般解：$\mathbf{u}(t)=c_{1} e^{\lambda_{1} t} \mathbf{x}_{1}+c_{2} e^{\lambda_{2} t} \mathbf{x}_{2}$ 或 $\mathbf{u}(t) =e^{A t} \mathbf{u}(0)$
  		其中 $e^{At} = S e^{\Lambda t} S^{-1}$
  - 傅立叶级数 Fourier series
  - 快速傅立叶变换 FFT
  - 图像压缩

 





























