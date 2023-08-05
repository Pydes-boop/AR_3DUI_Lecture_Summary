# Padding and Filters

## Padding
- padding is applied to images so certain algorithms do not fail at corner/edge cases
- **Zero-Padding** is simply adding rows and columns of 0 around our image

$$
\begin{align*}
Image &= 
\begin{pmatrix}
10 & 10 & 10 \\ 
10 & 10 & 10 \\ 
10 & 10 & 10
\end{pmatrix}
\\
\\
Image + Padding &= 
\begin{pmatrix}
0 & 0 & 0 & 0 & 0 \\ 
0 & 10 & 10 & 10 & 0 \\ 
0 & 10 & 10 & 10 & 0 \\ 
0 & 10 & 10 & 10 & 0 \\
0 & 0 & 0 & 0 & 0
\end{pmatrix}
\end{align*}
$$

## Sobel-Filter

- filter is applied to images for edge detection
- it finds the "most abrupt change" of contrast within an image
- this happens via a Kernel that is applied to regions of the image

Test Image:
![[teapot_no_filter.png|300]] 
With applied *Sobel-Filter*:
![[teapot_filtered.png|300]]

### Sobel Calculation

- Sobel Filter is applied to an image by applying a vertical or horizontal kernel to regions of the image

$$
\begin{align*}
Image &= 
\begin{pmatrix}
0 & 0 & 0 \\ 
10 & 10 & 0 \\ 
10 & 10 & 0
\end{pmatrix}
\\
\\
Kernel &= 
\begin{pmatrix}
1 & 0 & -1 \\ 
2 & 0 & -2 \\ 
1 & 0 & -1
\end{pmatrix}
\end{align*}
$$

- Kernel is applied and we calcualte a new value for our center pixel $x_5$: 

$$
\begin{align*}
Application &= 
\left \| \begin{pmatrix}
1 \cdot 0 & 0  \cdot 0 & -1 \cdot 0 \\
2 \cdot 10 & 0 \cdot 10 & -2 \cdot 0 \\
1 \cdot 10 & 0 \cdot 10 & -1 \cdot 0
\end{pmatrix} \right \|
\\
\\
&= 1 \cdot 0 + 0 \cdot 0 + \ldots -1 \cdot 0
\\
x_5 &= 30
\end{align*}
$$

$$
\begin{align*}
Image_{new} &= 
\begin{pmatrix}
x_1 & x_2 & x_3 \\
x_4 & 30 & x_6 \\
x_7 & x_8 & x_8
\end{pmatrix}
\end{align*}
$$

