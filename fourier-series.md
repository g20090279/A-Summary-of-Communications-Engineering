# Fourier Series

## Definition

A **periodic** function $f(x)$ can be decomposed into an *infinite* set of $\cos$ and $\sin$, each of which is with a single-frequency component,

$$f(x)=\frac{1}{2}a_0+\sum_{n=1}^{\infty}a_n\cos(nx)+\sum_{n=1}^{\infty}b_n\sin(nx),\quad x\in[-\pi,\pi].$$

This is also called **synthesis** process.

We call $a_n$ Fourier cosine coefficient and $b_n$ Fourier sine coefficient. Both of them are named Fourier series coefficient. The computation of Fourier series is known as *harmonic analysis*.

## Calculate the Fourier Series Components

That determines the weights, $a_n$ and $b_n$ is named as **analysis** process,

$$\begin{aligned}a_0=&\frac{1}{\pi}\int_{-\pi}^{\pi}f(x)dx\\a_n=&\frac{1}{\pi}\int_{-\pi}^{\pi}f(x)\cos(nx)dx\\b_n=&\frac{1}{\pi}\int_{-\pi}^{\pi}f(x)\sin(nx)dx\end{aligned},$$

where $n=1,2,3,\cdots,\infty$.

## Importances

An important charateristic of this decomposition is that the base functions form an orthogonal base, i.e.

$$\begin{aligned}\int_{-\pi}^{\pi}\sin(mx)\sin(nx)dx&=\pi\delta_{m,n}\\\int_{-\pi}^{\pi}\cos(mx)\cos(nx)dx&=\pi\delta_{m,n}\\\int_{-\pi}^{\pi}\sin(mx)\cos(nx)dx&=0\\\int_{-\pi}^{\pi}\sin(mx)dx&=0\\\int_{-\pi}^{\pi}\cos(mx)dx&=0\end{aligned},$$

where $\delta_{m,n}$ is the Kronecker delta

$$\delta_{m,n}=\begin{cases}1,&m\neq n\\0,&\mathrm{otherwise}\end{cases}$$

From the analysis process, we can see that the magnitude of a coefficient reflects actually the components that the periodic function $f(x)$ falls in the corresponding cosine base or sine base. In other words, if $\cos(nx)$ contributes more to the $f(x)$, the coeffient $a_n$ is larger.

The important of the orthogonality of the base is that the original periodic function $f(x)$ can be approximated by the most significant components while the other components with small coefficients can be discarded. We can do that due to the independency of each component (orthogonality).

