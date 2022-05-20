# [Essence of linear algebra](https://www.youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab)

- 1 Vectors
- 2 Linear combinations, Basis vectors
	- The "span" of $\vec{v}$ and $\vec{w}$ is the set of all their linear combinations: 
		$a \vec{v}+b \vec{w}$
- 3 **Linear tranformations** as matrices
	- Interpreted as new basis vectors with same coordinates
	- $\left[\begin{array}{ll}a & b \\ c & d\end{array}\right]\left[\begin{array}{l}x \\ y\end{array}\right]=x\left[\begin{array}{l}a \\ c\end{array}\right]+y\left[\begin{array}{l}b \\ d\end{array}\right]=\left[\begin{array}{l}a x+b y \\ c x+d y\end{array}\right]$
- 4 Matrix multiplication as composition
	- interpreted as two consecutive transformations from right to left 
	- $\overbrace{\left[\begin{array}{ll}a & b \\ c & d\end{array}\right]}^{M_{2}} \overbrace{\left[\begin{array}{ll}e & f \\ g & h\end{array}\right]}^{M_{1}}=\left[\begin{array}{cc}a e+b g & a f+b h \\ c e+d g & c f+d h\end{array}\right]$
		- $M_1$'s left column basis vector transformed by $M_2$ 
			$\left[\begin{array}{ll}a & b \\ c & d\end{array}\right]\left[\begin{array}{l}e \\ g\end{array}\right]=e\left[\begin{array}{l}a \\ c\end{array}\right]+g\left[\begin{array}{l}b \\ d\end{array}\right]=\left[\begin{array}{l}a e+b g \\ c e+d g\end{array}\right]$
		- $M_1$'s right column basis vector transformed by $M_2$ 
			$\left[\begin{array}{ll}a & b \\ c & d\end{array}\right]\left[\begin{array}{l}f \\ h\end{array}\right]=f\left[\begin{array}{l}a \\ c\end{array}\right]+h\left[\begin{array}{l}b \\ d\end{array}\right]=\left[\begin{array}{l}a f+b h \\ c f+d h\end{array}\right]$
- 6 The determinant
	- interpreted as the unit area/volume formed by the basis vectors of the transformation
	- $\operatorname{det}\left(\left[\begin{array}{ll}a & b \\ c & d\end{array}\right]\right)=a d-b c$
	- $ \operatorname{det}\left(\left[\begin{array}{lll}a & b & c \\ d & e & f \\ g & h & i\end{array}\right]\right) =a \operatorname{det}\left(\left[\begin{array}{ll}e & f \\ h & i\end{array}\right]\right)  -b \operatorname{det}\left(\left[\begin{array}{ll}d & f \\ g & i\end{array}\right]\right)  +c \operatorname{det}\left(\left[\begin{array}{ll}d & e \\ g & h\end{array}\right]\right) $

- 7 Inverse matrices, column space and null space
	- Column Space: The columns of your matrix tell you where the basis vectors land, and the span of those transformed basis vectors gives you all possible outputs.
	- Rank: the number of dimensions in the output of a transformation.
		or: the number of dimensions in the column space.
		- Full Rank: when the rank equals the number of columns, we call the matrix "full rank."
	- Null space/Kernal of matrix: the space of all vectors that become null, in the sense that they land on the zero vector.
		- e.g. $A \vec{x}=\left[\begin{array}{l}0 \\ 0\end{array}\right]$: the null space gives you all of the possible solutions to the equation. (not full rank)
- 8 Nonsquare matrices as transformations between dimensions
	- $\left[\begin{array}{lll}a & d \\ b & e \\ c & f \end{array}\right]$
		- $\left[\begin{array}{lll}a \\ b  \\ c  \end{array}\right]$ as $\hat{\imath}$ in 3d transformed space, $\left[\begin{array}{lll}d \\ e \\ f \end{array}\right]$ as $\hat{\jmath}$ in 3d transformed space
- 9 Dot products and duality
	- Matrix-vector product: $\left[\begin{array}{ll}u_{x} & u_{y}\end{array}\right]\left[\begin{array}{l}x \\ y\end{array}\right]=u_{x} \cdot x+u_{y} \cdot y$
	- Dot product: $\left[\begin{array}{l}u_{x} \\ u_{y}\end{array}\right] \cdot\left[\begin{array}{l}x \\ y\end{array}\right]=u_{x} \cdot x+u_{y} \cdot y$
	- Duality: anytime you have one of these linear transformations whose output space is the number line, no matter how it was defined there's going to be some unique vector v corresponding to that transformation, in the sense that applying the transformation is the same thing as taking a dot product with that vector.
- 10 Cross products
	- $\left[\begin{array}{l}v_{1} \\ v_{2} \\ v_{3}\end{array}\right] \times\left[\begin{array}{l}w_{1} \\ w_{2} \\ w_{3}\end{array}\right]=\operatorname{det}\left(\left[\begin{array}{lll}\hat{\imath} & v_{1} & w_{1} \\ \hat{\jmath} & v_{2} & w_{2} \\ \hat{k} & v_{3} & w_{3}\end{array}\right]\right)$
- 11 Cross products in the light of linear transformations
	- $\left[\begin{array}{l}p_{1} \\ p_{2} \\ p_{3}\end{array}\right] \cdot\left[\begin{array}{l}x \\ y \\ z\end{array}\right]=\operatorname{det}\left(\left[\begin{array}{lll}x & v_{1} & w_{1} \\ y & v_{2} & w_{2} \\ z & v_{3} & w_{3}\end{array}\right]\right)$
- 12 Cramer's rule, explained geometrically
- 13 Change of basis
	- $A^{-1} M A$
- 14 Eigenvectors and eigenvalues
	- Interpretation: the axis of rotation (transformation)
	- $\overbrace{A \overrightarrow{\mathbf{v}}}^{\text{Matrix-vector multiplication}}=\underbrace{\lambda \overrightarrow{\mathbf{v}}}_{\text {Scalar multiplication }}$
	- $\begin{aligned} A \overrightarrow{\mathbf{v}} &=\lambda \overrightarrow{\mathbf{v}} \\ A \overrightarrow{\mathbf{v}}-\lambda I \overrightarrow{\mathbf{v}} &=0 \\(A-\lambda I) \overrightarrow{\mathbf{v}} &=0 \\ \operatorname{det}(A-\lambda I) &=0 \end{aligned}$
- 15 A quick trick for computing eigenvalues
- 16 Abstract vector spaces
	- Formal definition of linearity
		- Additivity: $L(\overrightarrow{\mathbf{v}}+\vec{w})=L(\overrightarrow{\mathbf{v}})+L(\overrightarrow{\mathrm{w}})$
		- Scaling: $L(c \overrightarrow{\mathbf{v}})=c L(\overrightarrow{\mathbf{v}})$
	- Derivative is linear
	- Vector spaces: arrows, list of numbers, functions...
		- follow 8 axioms























