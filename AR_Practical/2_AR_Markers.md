# Augmented Reality Markers

#detection #marker

## Marker Identity

Given the following AR-Marker, how can we calculate its ID?

```tikz
\begin{document}
\begin{tikzpicture}[scale=0.5]
  % Define the grid dimensions
  \def\gridsize{6}
  
  % Define a command to draw a black cell
  \newcommand{\blackcell}[2]{
    \fill[black] (#1, #2) rectangle ++(1, 1);
  }

  % Define a command to draw a white cell
  \newcommand{\whitecell}[2]{
    \fill[white] (#1, #2) rectangle ++(1, 1);
  }

  % Manually set cells to black and white
  \blackcell{0}{0}
  \blackcell{0}{1}
  \blackcell{0}{2}
  \blackcell{0}{3}
  \blackcell{0}{4}
  \blackcell{0}{5}

  \blackcell{5}{0}
  \blackcell{5}{1}
  \blackcell{5}{2}
  \blackcell{5}{3}
  \blackcell{5}{4}
  \blackcell{5}{5}

  \blackcell{0}{0}
  \blackcell{1}{0}
  \blackcell{2}{0}
  \blackcell{3}{0}
  \blackcell{4}{0}
  \blackcell{5}{0}

  \blackcell{0}{5}
  \blackcell{1}{5}
  \blackcell{2}{5}
  \blackcell{3}{5}
  \blackcell{4}{5}
  \blackcell{5}{5}

  \blackcell{3}{2}
  \blackcell{1}{3}
  \blackcell{1}{2}
  \blackcell{2}{4}
  
  
  % Draw the grid lines
  \draw[step=1] (0,0) grid (\gridsize,\gridsize);
  
\end{tikzpicture}
\end{document}
```


$$
\begin{bmatrix}
0 \cdot 8 + 1 \cdot 4 + 0 \cdot 2 + 0 \cdot 1 \\
1 \cdot 8 + 0 \cdot 4 + 0 \cdot 2 + 0 \cdot 1 \\
1 \cdot 8 + 0 \cdot 4 + 1 \cdot 2 + 0 \cdot 1 \\
0 \cdot 8 + 0 \cdot 4 + 0 \cdot 2 + 0 \cdot 1
\end{bmatrix} = 
\begin{bmatrix}
4 \\
8 \\ 
a \\
0
\end{bmatrix}
$$

so the ID to our Marker is $0x48a0$

Consider the following rotation, that is still the same marker but would result in a different ID:

```tikz
\begin{document}
\begin{tikzpicture}[scale=0.5]
  % Define the grid dimensions
  \def\gridsize{6}
  
  % Define a command to draw a black cell
  \newcommand{\blackcell}[2]{
    \fill[black] (#1, #2) rectangle ++(1, 1);
  }

  % Define a command to draw a white cell
  \newcommand{\whitecell}[2]{
    \fill[white] (#1, #2) rectangle ++(1, 1);
  }

  % Manually set cells to black and white
  \blackcell{0}{0}
  \blackcell{0}{1}
  \blackcell{0}{2}
  \blackcell{0}{3}
  \blackcell{0}{4}
  \blackcell{0}{5}

  \blackcell{5}{0}
  \blackcell{5}{1}
  \blackcell{5}{2}
  \blackcell{5}{3}
  \blackcell{5}{4}
  \blackcell{5}{5}

  \blackcell{0}{0}
  \blackcell{1}{0}
  \blackcell{2}{0}
  \blackcell{3}{0}
  \blackcell{4}{0}
  \blackcell{5}{0}

  \blackcell{0}{5}
  \blackcell{1}{5}
  \blackcell{2}{5}
  \blackcell{3}{5}
  \blackcell{4}{5}
  \blackcell{5}{5}

  \blackcell{2}{3}
  \blackcell{4}{3}
  \blackcell{4}{2}
  \blackcell{3}{1}
  
  
  % Draw the grid lines
  \draw[step=1] (0,0) grid (\gridsize,\gridsize);
  
\end{tikzpicture}
\end{document}
```


$$
\begin{bmatrix}
0 \cdot 8 + 0 \cdot 4 + 0 \cdot 2 + 0 \cdot 1 \\
0 \cdot 8 + 1 \cdot 4 + 0 \cdot 2 + 1 \cdot 1 \\
0 \cdot 8 + 0 \cdot 4 + 0 \cdot 2 + 1 \cdot 1 \\
0 \cdot 8 + 0 \cdot 4 + 1 \cdot 2 + 0 \cdot 1
\end{bmatrix} = 
\begin{bmatrix}
0 \\
5 \\
1 \\
2
\end{bmatrix}
$$

so the smallest ID for our Marker is actually $0x512$

### Lessons

1. Markers Rotation should be unique because of **perspective transformation**
2. Sometimes Markers need to be rotated to get the smallest (actual) ID
3. smallest ID is always the smalles number you calculate when considering all rotations

### Examples

1. ╳ All Marker Rotations are the same → Issues with perspective transformation

```tikz
\begin{document}
\begin{tikzpicture}[scale=0.5]
  % Define the grid dimensions
  \def\gridsize{6}
  
  % Define a command to draw a black cell
  \newcommand{\blackcell}[2]{
    \fill[black] (#1, #2) rectangle ++(1, 1);
  }

  % Define a command to draw a white cell
  \newcommand{\whitecell}[2]{
    \fill[white] (#1, #2) rectangle ++(1, 1);
  }

  % Manually set cells to black and white
  \blackcell{0}{0}
  \blackcell{0}{1}
  \blackcell{0}{2}
  \blackcell{0}{3}
  \blackcell{0}{4}
  \blackcell{0}{5}

  \blackcell{5}{0}
  \blackcell{5}{1}
  \blackcell{5}{2}
  \blackcell{5}{3}
  \blackcell{5}{4}
  \blackcell{5}{5}

  \blackcell{0}{0}
  \blackcell{1}{0}
  \blackcell{2}{0}
  \blackcell{3}{0}
  \blackcell{4}{0}
  \blackcell{5}{0}

  \blackcell{0}{5}
  \blackcell{1}{5}
  \blackcell{2}{5}
  \blackcell{3}{5}
  \blackcell{4}{5}
  \blackcell{5}{5}

  \blackcell{2}{2}
  \blackcell{3}{3}
  \blackcell{3}{2}
  \blackcell{2}{3}
  
  
  % Draw the grid lines
  \draw[step=1] (0,0) grid (\gridsize,\gridsize);
  
\end{tikzpicture}
\end{document}
```

2. ╳ Some Marker Rotations are unique, **but** not all → Issues with perspective transformation

```tikz
\begin{document}
\begin{tikzpicture}[scale=0.5]
  % Define the grid dimensions
  \def\gridsize{6}
  
  % Define a command to draw a black cell
  \newcommand{\blackcell}[2]{
    \fill[black] (#1, #2) rectangle ++(1, 1);
  }

  % Define a command to draw a white cell
  \newcommand{\whitecell}[2]{
    \fill[white] (#1, #2) rectangle ++(1, 1);
  }

  % Manually set cells to black and white
  \blackcell{0}{0}
  \blackcell{0}{1}
  \blackcell{0}{2}
  \blackcell{0}{3}
  \blackcell{0}{4}
  \blackcell{0}{5}

  \blackcell{5}{0}
  \blackcell{5}{1}
  \blackcell{5}{2}
  \blackcell{5}{3}
  \blackcell{5}{4}
  \blackcell{5}{5}

  \blackcell{0}{0}
  \blackcell{1}{0}
  \blackcell{2}{0}
  \blackcell{3}{0}
  \blackcell{4}{0}
  \blackcell{5}{0}

  \blackcell{0}{5}
  \blackcell{1}{5}
  \blackcell{2}{5}
  \blackcell{3}{5}
  \blackcell{4}{5}
  \blackcell{5}{5}

  \blackcell{1}{1}
  \blackcell{2}{2}
  \blackcell{3}{3}
  \blackcell{4}{4}
  
  
  % Draw the grid lines
  \draw[step=1] (0,0) grid (\gridsize,\gridsize);
  
\end{tikzpicture}
\end{document}
```

3. ✓ All Marker Rotations are unique → (but currently not rotated for smallest ID)

```tikz
\begin{document}
\begin{tikzpicture}[scale=0.5]
  % Define the grid dimensions
  \def\gridsize{6}
  
  % Define a command to draw a black cell
  \newcommand{\blackcell}[2]{
    \fill[black] (#1, #2) rectangle ++(1, 1);
  }

  % Define a command to draw a white cell
  \newcommand{\whitecell}[2]{
    \fill[white] (#1, #2) rectangle ++(1, 1);
  }

  % Manually set cells to black and white
  \blackcell{0}{0}
  \blackcell{0}{1}
  \blackcell{0}{2}
  \blackcell{0}{3}
  \blackcell{0}{4}
  \blackcell{0}{5}

  \blackcell{5}{0}
  \blackcell{5}{1}
  \blackcell{5}{2}
  \blackcell{5}{3}
  \blackcell{5}{4}
  \blackcell{5}{5}

  \blackcell{0}{0}
  \blackcell{1}{0}
  \blackcell{2}{0}
  \blackcell{3}{0}
  \blackcell{4}{0}
  \blackcell{5}{0}

  \blackcell{0}{5}
  \blackcell{1}{5}
  \blackcell{2}{5}
  \blackcell{3}{5}
  \blackcell{4}{5}
  \blackcell{5}{5}

  \blackcell{1}{2}
  \blackcell{1}{3}
  \blackcell{2}{2}
  \blackcell{2}{3}
  
  
  % Draw the grid lines
  \draw[step=1] (0,0) grid (\gridsize,\gridsize);
  
\end{tikzpicture}
\end{document}
```
