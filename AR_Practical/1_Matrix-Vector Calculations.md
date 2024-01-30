# Matrix Vector Calculations

#homogenous-matrix-transformations 
## Vector Calculations

$$
\vec{a} =
\begin{pmatrix}
1 \\
2 \\
-1
\end{pmatrix}
\ \ \
\vec{b} =
\begin{pmatrix}
2 \\
1 \\
-1
\end{pmatrix}
$$

### Scalar Product
**Description:** calculates *sum* of dimensional products of vector

$$
\begin{align*}
\vec{a} \cdot \vec{b} &= a_1 \cdot b_1 + a_2 \cdot b_2 + a_3 \cdot b_3 \\ 
&=1 \cdot 2 + 2 \cdot 1 + (-1 \cdot -1) \\ 
&=5
\end{align*}
$$

**Angle** $\gamma$ between vectors $\vec{a}$ and $\vec{b}$ can be calculated via scalar product:

```tikz
\begin{document}
\begin{tikzpicture}[scale=1]

  % Define the two vectors
  \def\vecA{(1, 2, -1)}
  \def\vecB{(2, 1, -1)}

  % Draw the axes
  \draw[thick,->] (0,0,0) -- (3,0,0) node[anchor=north east]{$x$};
  \draw[thick,->] (0,0,0) -- (0,3,0) node[anchor=north west]{$y$};
  \draw[thick,->] (0,0,0) -- (0,0,3) node[anchor=south]{$z$};

  % Draw the vectors
  \draw[->,red,very thick] (0,0,0) -- \vecA node[midway, below left, text=black]{$\vec{A}$};
  \draw[->,blue,very thick] (0,0,0) -- \vecB node[midway, below right, text=black]{$\vec{B}$};


  % Draw angle gamma
  \draw[orange,very thick] (0.25,0.5,-0.25) arc (60:33.56:0.8);
  \draw[black] (0.44,0.18,-0.25) node[left]{$\gamma$};


\end{tikzpicture}
\end{document}
```

$$
\begin{align*}
\frac{\vec{a} \cdot \vec{b}}{\left \| \vec{a} \right \| \cdot \left \| \vec{b} \right \|} 
&= 
\frac{1 \cdot 2 + 2 \cdot 1 + (-1 \cdot -1)}{\sqrt{1^2 + 2^2 + -1^{2}} \cdot \sqrt{2^2 + 1^2 + -1^{2}}} \\
&=\frac{5}{\sqrt6 \cdot \sqrt6} \\
&=\frac{5}{6} \\
\gamma &= \cos^{-1}(\frac{5}{6}) \approx 33.56
\end{align*}
$$

### Cross-Product

$$
\vec{a} =
\begin{pmatrix}
2 \\
3 \\
4
\end{pmatrix}
\ \ \
\vec{b} =
\begin{pmatrix}
5 \\
6 \\
7
\end{pmatrix}
$$

Calculate the vector $\vec{n}$ that is orthogonal to the plane defined by vectors $\vec{a}$ and $\vec{b}$
**orthogonal:** to be at a right angle

```tikz
\usepackage{tikz-3dplot}

\begin{document}
\begin{tikzpicture}[scale=1]
  % Define the two vectors
  \def\vecA{(1, 2, -1)}
  \def\vecB{(2, 1, -1)}
  \def\vecN{(-2.45, 0.82, -2.45)}

  % Draw the plane
  \draw[fill=gray!40,opacity=0.5] (0,0,0) -- \vecA -- \vecB -- cycle;


  % Draw the vectors
  \draw[->,red,very thick] (0,0,0) -- \vecA node[midway, below left, text=black]{$\vec{A}$};
  \draw[->,blue,very thick] (0,0,0) -- \vecB node[midway, below right, text=black]{$\vec{B}$};
  \draw[->,orange,very thick] (0,0,0) -- \vecN node[midway, below right, text=black]{$\vec{N}$};

  % Draw the axes
  \draw[thick,->] (0,0,0) -- (3,0,0) node[anchor=north east]{$x$};
  \draw[thick,->] (0,0,0) -- (0,3,0) node[anchor=north west]{$y$};
  \draw[thick,->] (0,0,0) -- (0,0,3) node[anchor=south]{$z$};

\end{tikzpicture}
\end{document}
```

$$
\begin{align*}
\vec{a} \times \vec{b} &= 
\begin{pmatrix}
a_2 \times b_3 - a_3 \times b_2 \\ 
a_3 \times b_1 - a_1 \times b_3 \\ 
a_1 \times b_2 - a_2 \times b_1
\end{pmatrix}
\\
\\
&= \begin{pmatrix}
3 \times 7 - 4 \times 6 \\ 
4 \times 5 - 2 \times 7 \\ 
2 \times 6 - 3 \times 5
\end{pmatrix}
\\
\\
&= \begin{pmatrix}
-3 \\
6 \\
-3
\end{pmatrix}=\vec{n}
\end{align*}
$$

**normalize** vector $\vec{n}$ by dividing with its length

$$
\begin{align*}
\frac{\vec{n}}{ \left \| \vec{n} \right \| } &= \frac{\vec{n}}{ 3\sqrt6 }
\\
\\
&= 
\begin{pmatrix}
-1\sqrt6 \\
\sqrt{\frac{2}{3}} \\
-1\sqrt6
\end{pmatrix}
\end{align*}
$$

## Homogenous Matrices

**homogenous** transformations are operations that can be applied to matrices in a consistent format suitable for computation

### Extending by dimension w

- for homogenous operations we want to extend our matrices and vectors by an additional dimension $w$ that has a length of $1 = |w|$
- we do this so we can guarantee a consistent result, if $w$ changes we know how to scale our variable back to its original size

$$
A = \begin{pmatrix}
1 & 0 & 0 \\
0 & 2 & 0 \\
0 & 0 & 3
\end{pmatrix} \implies  
A = \begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & 2 & 0 & 0 \\
0 & 0 & 3 & 0 \\
0 & 0 & 0 & 1
\end{pmatrix}
$$

### Vector-Matrix Multiplication

- imagine "laying" the vector on-top of your matrix and applying the first dimension of the vector to the first column of the matrix

$$
\begin{align*}
A &= 
\begin{pmatrix}
1 & 0 & 0 & 1 \\
0 & 2 & 0 & 2 \\
0 & 0 & 3 & 3 \\
0 & 0 & 0 & 1
\end{pmatrix}
\times
\begin{pmatrix}
x \\ 
y \\ 
z \\ 
w
\end{pmatrix} 
\\
\\
&= 
\begin{pmatrix}
1 \cdot x + 0 \cdot y + 0 \cdot z + 1 \cdot w \\
0 \cdot x + 2 \cdot y + 0 \cdot z + 2 \cdot w \\
0 \cdot x + 0 \cdot y + 3 \cdot z + 3 \cdot w \\
0 \cdot x + 0 \cdot y + 0 \cdot z + 1 \cdot w
\end{pmatrix}
\\
\\
&= 
\begin{pmatrix}
x + w \\
2y + 2w \\
3z + 3w \\ 
w
\end{pmatrix}
\end{align*}
$$

### Matrix-Matrix Multiplication

- simply put, cell 1 of the resulting matrix $C = A \times B$ will be the [[1_Matrix-Vector Calculations#Scalar Product|Scalar]] of the first **row** of $A$ with the first **column** of $B$ 
- matrices need to match dimensions


$$
A = 
\begin{pmatrix}
a_{11} & a_{12} & \cdots & a_{1m} \\
a_{21} & a_{22} & \cdots & a_{2m} \\
\vdots & \vdots & \ddots & \vdots \\
a_{n1} & a_{n2} & \cdots & a_{nm}
\end{pmatrix}
\ \
B = 
\begin{pmatrix}
b_{11} & b_{12} & \cdots & b_{1m} \\
b_{21} & b_{22} & \cdots & b_{2m} \\
\vdots & \vdots & \ddots & \vdots \\
b_{n1} & b_{n2} & \cdots & b_{nm}
\end{pmatrix}
$$

$$
\begin{align*}
C &= A \times B = 
\begin{pmatrix}
a_{11} b_{11} + \cdots + a_{1n} b_{n1} 
& a_{11} b_{12} + \cdots + a_{1n} b_{n2} 
& \cdots & a_{11} b_{1m} + \cdots + a_{1n} b_{nm}  \\
a_{21} b_{11} + \cdots + a_{2n} b_{n1} 
& a_{21} b_{12} + \cdots + a_{2n} b_{n2} 
& \cdots & a_{21} b_{1m} + \cdots + a_{2n} b_{nm}  \\
\vdots & \vdots & \ddots & \vdots \\
a_{n1} b_{11} + \cdots + a_{nm} b_{n1} 
& a_{n1} b_{12} + \cdots + a_{nm} b_{n2} 
& \cdots & a_{n1} b_{1m} + \cdots + a_{nm} b_{nm}
\end{pmatrix}
\end{align*}
$$

### Translation

$$
Translation = 
\begin{pmatrix}
1 & 0 & 0 & t_x \\ 
0 & 1 & 0 & t_y \\ 
0 & 0 & 1 & t_z \\ 
0 & 0 & 0 & 1
\end{pmatrix}
$$

Applying a translation $T$ to a 3-Dimensional vector $\vec{a}$ (moving the point)

$$
\begin{align*}
\vec{a} \cdot T &= 
\begin{pmatrix}
a_x \\ 
a_y \\ 
a_z \\ 
1
\end{pmatrix}
\cdot
\begin{pmatrix}
1 & 0 & 0 & t_x \\ 
0 & 1 & 0 & t_y \\ 
0 & 0 & 1 & t_z \\ 
0 & 0 & 0 & 1
\end{pmatrix}
\\
\\
&=
\begin{pmatrix}
a_x + t_x \\ 
a_y + t_y \\ 
a_z + t_z \\ 
1
\end{pmatrix}
\end{align*}
$$

For a unit-vector $v_{old} = \begin{pmatrix}1\\1\\1\end{pmatrix}$ that we translate by $\begin{pmatrix}-1\\2\\1\end{pmatrix}$ the result would be $v_{new}\begin{pmatrix}0\\3\\2\end{pmatrix}$ :

```tikz
\usepackage{tikz-3dplot}

\begin{document}
\begin{tikzpicture}[scale=1]
  % Define the first vector (1, 1, 1)
  \def\vecA{(1, 1, 1)}

  % Define the second vector (2, 2, 2)
  \def\vecB{(0, 3, 2)}

  % Draw the first vector
  \draw[->,red,very thick] (0,0,0) -- \vecA node[midway, below right, text=black]{$\vec{v}_{old}$};

  % Draw the second vector
  \draw[->,blue,very thick] (0,0,0) -- \vecB node[midway, above left, text=black]{$\vec{v}_{new}$};

  % Draw the axes
  \draw[thick,->] (0,0,0) -- (3,0,0) node[anchor=north east]{$x$};
  \draw[thick,->] (0,0,0) -- (0,3,0) node[anchor=north west]{$y$};
  \draw[thick,->] (0,0,0) -- (0,0,3) node[anchor=south]{$z$};

\end{tikzpicture}
\end{document}
```

### Rotation

- There are different matrices for rotations around the x, y and z axis

$$
R_x(\alpha) = 
\begin{pmatrix}
1 & 0 & 0 \\ 
0 & \cos(\alpha) & \sin(\alpha) \\ 
0 & -\sin(\alpha) & \cos(\alpha) 
\end{pmatrix}
$$

$$
R_y(\beta) = 
\begin{pmatrix}
\cos(\beta) & 0 & -\sin(\beta) \\ 
0 & 1 & 0 \\ 
\sin(\alpha) & 0 & \cos(\alpha) 
\end{pmatrix}
$$

$$
R_x(\alpha) = 
\begin{pmatrix}
\cos(\alpha) & \sin(\alpha) & 0 \\ 
-\sin(\alpha) & \cos(\alpha) & 0 \\ 
0 & 0 & 1
\end{pmatrix}
$$

For a unit-vector $v_{old} = \begin{pmatrix}1\\2\\-1\end{pmatrix}$ that we rotate with $\begin{pmatrix}0&-1&0&0\\1&0&0&0\\0&0&1&0\\0&0&0&1\end{pmatrix}$ the result would be $v_{new}\begin{pmatrix}-2\\1\\-1\end{pmatrix}$:

```tikz
\usepackage{tikz-3dplot}

\begin{document}
\begin{tikzpicture}[scale=1]
  % Define the first vector (1, 1, 1)
  \def\vecA{(1, 2, -1)}

  % Define the second vector (2, 2, 2)
  \def\vecB{(-2, 1, -1)}

  % Draw the first vector
  \draw[->,red,very thick] (0,0,0) -- \vecA node[midway, below right, text=black]{$\vec{v}_{old}$};

  % Draw the second vector
  \draw[->,blue,very thick] (0,0,0) -- \vecB node[midway, above left, text=black]{$\vec{v}_{new}$};

  % Draw the axes
  \draw[thick,->] (0,0,0) -- (3,0,0) node[anchor=north east]{$x$};
  \draw[thick,->] (0,0,0) -- (0,3,0) node[anchor=north west]{$y$};
  \draw[thick,->] (0,0,0) -- (0,0,3) node[anchor=south]{$z$};

\end{tikzpicture}
\end{document}
```

### Scale

- Scaling operations can also just be used as stretch operations

$$
Scale = 
\begin{pmatrix}
S_x & 0 & 0 & 0 \\ 
0 & S_y & 0 & 0 \\ 
0 & 0 & S_z & 0 \\ 
0 & 0 & 0 & 1
\end{pmatrix}
$$

Applying a translation $T$ to a 3-Dimensional vector $\vec{a}$:

$$
\begin{align*}
\vec{a} \cdot T &= 
\begin{pmatrix}
a_x \\ 
a_y \\ 
a_z \\ 
1
\end{pmatrix}
\cdot
\begin{pmatrix}
S_x & 0 & 0 & 0 \\ 
0 & S_y & 0 & 0 \\ 
0 & 0 & S_z & 0 \\ 
0 & 0 & 0 & 1
\end{pmatrix}
\\
\\
&=
\begin{pmatrix}
a_x \cdot S_x \\ 
a_y \cdot S_y \\ 
a_z \cdot S_z \\ 
1
\end{pmatrix}
\end{align*}
$$

### Combining Matrix Operations

- homogenous matrix operations can be combined to apply all of your operations at once (scale + translation + rotation)
- **order of operations** matters (!)
- the same two operations will have a different result, when applied in a different order

$$
Operation = 
\begin{pmatrix}
0 & -1 & 0 & 0 \\ 
1 & 0 & 0 & 5 \\ 
0 & 0 & 1 & 0 \\ 
0 & 0 & 0 & 1
\end{pmatrix}
$$

$Operation$ can be represented by a translation and rotation (5 can be found by imagining the result of the Scalar of a second row (1,0,0,0) and last column (5,0,0,1)):

$$
Operation = 
\begin{pmatrix}
0 & -1 & 0 & 0 \\ 
1 & 0 & 0 & 0 \\ 
0 & 0 & 1 & 0 \\ 
0 & 0 & 0 & 1
\end{pmatrix}
\times
\begin{pmatrix}
1 & 0 & 0 & 5 \\ 
0 & 1 & 0 & 0 \\ 
0 & 0 & 1 & 0 \\ 
0 & 0 & 0 & 1
\end{pmatrix}
$$

**but** (!) it could have also been the result of completly different operations

### Point Mapping with homogenous Matrix Operations

**Task:** define a matrix $h$ that maps the vector $\vec{v_{old}} = \begin{pmatrix}5\\0\\0\\1\end{pmatrix}$ to the new coordinate $\vec{v_{new}} = \begin{pmatrix}0\\10\\0\\1\end{pmatrix}$

$$
\begin{align*}
v_{new} &= 
\begin{pmatrix}
5 \\ 
0 \\
0 \\
1 
\end{pmatrix} 
\cdot
\begin{pmatrix}
0 & -1 & 0 & 0 \\ 
1 & 0 & 0 & 0 \\ 
0 & 0 & 1 & 0 \\ 
0 & 0 & 0 & 1
\end{pmatrix}
\times
\begin{pmatrix}
1 & 0 & 0 & 5 \\ 
0 & 1 & 0 & 0 \\ 
0 & 0 & 1 & 0 \\ 
0 & 0 & 0 & 1
\end{pmatrix}
\\ 
\\ 
&= 
\begin{pmatrix} 
5 \\ 
0 \\ 
0 \\ 
1 
\end{pmatrix} 
\cdot 
\begin{pmatrix}
0 & -1 & 0 & 0 \\ 
1 & 0 & 0 & 5 \\ 
0 & 0 & 1 & 0 \\ 
0 & 0 & 0 & 1
\end{pmatrix}
\\
\\ 
&= 
\begin{pmatrix}
0 \\ 
10 \\ 
0 \\ 
1 \end{pmatrix}
\end{align*}
$$
