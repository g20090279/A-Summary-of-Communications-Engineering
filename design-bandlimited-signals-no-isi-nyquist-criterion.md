# Design of Band-Limited Signals for No Intersymbol Interference - The Nyquist Criterion

## Keywords

narrow-band, band-limited, inter-symbol interference, Nyquist Theorem

## Review of Narrow-band Transmission Model

From the narrow-band transmission model, we know the mathematical description is 

$$y(t)=\sum_{n=0}^{\infty}I_nx(t-nT)+n(t),$$

where $y(t)$ is the output signal of the receiver filter (note that the optimum receiver filter for AWGN channel is matched filter), and $x(t)$ the **effective pulse** that combines pulse shaping $g(t)$ at the transmitter, orginal channel response $c(t)$, as well as the receiver filter $f(t)$. Assume the band-limited channel has ideal freqeuncy-response characteristics $C(f)=1$ for $|f|\leq W$. With ideal channel, the only contribution to the effective pulse is the pulse shaping function at the transmitter, if matched filter is applied at the receiver, resulting in $X(f)=|G(f)|^2$. The time-domain pulse signal is $x(t)=\int_{-W}^{W}X(f)e^{j2\pi ft}df$.

$g(t)$ can be also written in a discrete form with $x(t=kT)=x_k$ as

$$y_k=I_k+\sum_{n=0,n\neq k}^{\infty}I_nx_{k-n}+n_k.$$

## Design Goal

The designing factor lies in $g(t)$ that determines the spectral properties of the pulse $x(t)$, resulting in no intersymbol interference, i.e.

$$x_k=\begin{cases}
    1&k=0\\0&k\neq0
\end{cases}.$$

The above equation is the condition for no intersymbol interference.

## Nyquist Theorem for Non-ISI

---

**THEOREM**: `Nyquist Theorem`

The neccessaary and sufficient condition for $x(t)$ to satisfy

$$x(nT)=\begin{cases}1&k=0\\0&k\neq0\end{cases}$$

is that its Fourier transform $X(f)$ satisfies

$$\sum_{m=-\infty}^{\infty}X(f+m/T)=T$$

---

> *The meaning of this theorem shows that for the whole spectrum $\forall f$, the frequency response of sampling effective pulse with period $1/T$ requires to be a constant value $T$.*

**Proof**. In general, $x(t)$ is the inverse Fourier transform of $X(f)$

$$x(t)=\int_{-\infty}^{\infty}X(f)e^{j2\pi ft}df.$$

At the sampling instants $t=nT$, we have

$$x(nT)=\int_{-\infty}^{\infty}X(f)e^{j2\pi fnT}df.$$

The integration in $[-\infty,\infty]$ can be separated into parts, each of which has length $\frac{1}{T}$ with center at zero as

$$\begin{aligned}
    x(nT)&=\sum_{m=-\infty}^{\infty}\int_{(2m-1)/2T}^{(2m+1)/2T}X(f)e^{j2\pi fnT}df\\
    &=\sum_{m=-\infty}^{\infty}\int_{-1/2T}^{1/2T}X(u+m/T)e^{j2\pi unT}du\\
    &=\int_{-1/2T}^{1/2T}\left[\sum_{m=-\infty}^{\infty}X(f+m/T)\right]e^{j2\pi fnT}df\\
    &=\int_{-1/2T}^{1/2T}B(f)e^{j2\pi fnT}df,
\end{aligned}$$

where $B(f)=\sum_{m=-\infty}^{\infty}X(f+m/T)$ is a **periodic function** with period $1/T$.

For a periodic signal, it can be expanded with Fourier series with coefficients $\{b_n\}$ as

$$B(f)=\sum_{-\infty}^{\infty}b_ne^{j2\pi nfT},$$

where $b_n$ can be obtained by analysis process of Fourier series

$$b_n=T\int_{-1/2T}^{1/2T}B(f)e^{-j2\pi nfT}df.$$

Comparing $x(nT)$ and $b_n$, we have

$$b_n=Tx(-nT).$$

Therefore, the necessary and sufficient condition for $x(t)$ to satisfy $x(nT)=1$ if and only if $k=0$ is

$$b_n=\begin{cases}
    T&n=0\\0&n\neq 0.
\end{cases}$$

Then review back the synthesis of Fourier series for $B(f)=\sum_{-\infty}^{\infty}b_ne^{j2\pi nfT}=T.$