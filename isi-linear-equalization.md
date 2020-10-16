# Linear Equalization for Intersymbol Interference Channel

Hashname: 

Keywords: linear equalization, intersymbol interference， transversal filter

## Optimum Detection For ISI

The optimal method to detect signal in ISI channel is maximum likelihood sequence Estimation (MLSE). However, it has a large computational complexity growing exponentially with the length of the channel time dispersion.

## The Suboptimum Channel Equalization - Linear Methods

One approach is a linear transversal filter, whose computational complexity is a linear function of the channel dispersion length $L$.

<img src="isi-linear-equalization-fig-1.png" alt="linear transversal filter" width="500"/>

Figure: Linear equalizer in the form of transversal filter

Consider the **equivalent discrete-time whitened noise filter** with impulse respnse $\{a_n\}$, the output sequence $\{q_n\}$ of the linear equalizer with coefficients $\{c_n\}$ is

$$q_n=\sum_{j=-\infty}^{\infty}c_ja_{n-j}.$$

The estimated (or called compensated) $k$th sample can be expressed as

$$\begin{aligned}
    \hat{I}_k=&\sum_{n=-\infty}^{\infty}c_nq_{k-n}+\sum_{j=-\infty}^{\infty}c_j\eta_{k-j}\\
    =&q_0I_k+\sum_{n=-\infty,n\neq k}^{\infty}c_nq_{k-n}+\sum_{j=-\infty}^{\infty}c_j\eta_{k-j},
\end{aligned}$$

where $\eta_k$ is the AWGN for equivalent discrete-time whitened noise filter. Note that the equivalent discrete-time whitened noise filter is the cascade of pulse shape, channel, matched filter, and noise whitening filter.

Many researches have been done to optimize $c_k$. The **most meaningful** measure of performance for a digital communication system is the **average probability of error**. There are two criteria have been widely used in optimizing the equalizer coefficients.

## Criterion 1: Peak Distortion - Zero-forcing Filter

he second term in $\hat{I}_k$ is the **intersymbol interference**. The peak value of this interference is when the complex $I_nq_{k-n}$ has same phase. Therefore, the *peak distortion* is defined as

$$\mathcal{D}(\mathbf{c})=\sum_{n=-\infty,n\neq0}^{\infty}|q_n|=\sum_{n=-\infty,n\neq0}^{\infty}\left|\sum_{j=-\infty}^{\infty}c_ja_{n-j}\right|.$$

From the above equation, we know that if $q_n=0$ for all $n$ except $n=0$, the intersymbol interference can be completely eliminated, i.e.

$$q_n=\sum_{j=-\infty}^{\infty}c_ja_{n-j}=\begin{cases}
    1,&n=0\\0,&n\neq0
\end{cases}.$$

Since the equalizer have an infinite number of taps, it is possible to select the tap weights to fulfill the above requirement.

Considering the $z$ transform, we have

$$Q(z)=C(z)A(z)=1.$$

One simple equalizer, called **zero-forcing (ZF) filter** is

$$C(z)=\frac{1}{A(z)}.$$

In other words, we need an inverse filter to $F(z)$ to eliminate ISI completely. The cascade of noise-whitening filter $1/A^*(1/z^*)$ and zero-forcing filter $1/A(z)$ results in an equivalent zero-forcing equalizer with transfer function

$$C'(z)=\frac{1}{A(z)A^*(1/z^*)}=\frac{1}{X(z)},$$

where $\{x_k\}$ is the equivalent pulse combining pulse shaping, channel, and matched filter. Note that the noise after equalizer becomes again a **colored Gaussian noise**.

### Finite-length Equalizer

If the equalizer is finite with $2K+1$ taps, i.e. $c_j=0$ for $|j|>K$, instead of inifinite, it is generally impossible to completely eliminate the intersymbol interference at the output of the equalizer.

## Criterion 2: Mean Square Error (MSE)

Int he MSE criterion, we can minimize the mean square value of the error

$$\epsilon_k=I_k-\hat{I}_k$$

by adjusting the equalizer filter coefficients $c_k$.

Therefore, we need to minimize

$$O=\mathbb{E}\left[\|\epsilon_k\|^2\right].$$

Assume that the equalizer has an **infinite** number of taps. The estimate $\hat{I}_k$ is expressed as

$$\hat{I}_k=\sum_{j=-\infty}^{\infty}c_jy_{k-j},$$

where $y_k$ is the received symbol with discrete-time noise-whitening equivalent channel.

Note that here we consider Linear minimum MSE (LMMSE), where the estimate is an affine function of the observation. Therefore, in the vector space, the estimation is inside the space spanned by the observation. The error $\epsilon_k$ is an *error vector*, having the meaning that the distance between vector $I_k$ and the space spanned by the observation. This means that $\epsilon_k$ is minimized if it is orthogonal to the space spanned by the observation (Kay, 2009, P386),

$$\mathbb{E}[\epsilon_kv_{k-l}^*],\qquad-\infty<l<\infty.$$

Substitution for $\epsilon_k$ in the above leads to

$$\mathbb{E}\left[\left(I_k-\sum_{j=-\infty}^{\infty}c_jy_{k-j}\right)y_{k-l}^*\right].\tag{1}$$

Rewriting the Eq. (1) in this form

$$\sum_{j=-\infty}^{\infty}c_j\mathbb{E}[y_{k-j}y_{k-l}^*]=\mathbb{E}[I_ky_{k-l}^*],\quad -\infty<l<\infty.\tag{2}$$

Note that we consider [discrete-time noise-whitening channel model](6ad0611ed5bc0a29f0cafafe0bfc24ee), we have

$$y_k=\sum_{n=0}^{L}a_nI_{k-n}+\eta_k,$$

where $a_n$ is the coefficients of equivalent channel taps, and $\eta_k$ is the AWGN. After substitution, we have

$$\begin{aligned}
    \mathbb{E}[y_{k-j}y_{k-l}^*]&=\mathbb{E}\left[\left(\sum_{n=0}^{L}a_nI_{k-j-n}+\eta_{k-j}\right)\left(\sum_{m=0}^{L}a_mI_{k-l-m}+\eta_{k-l}\right)^*\right]\\
    &=\mathbb{E}\left[\left(\sum_{n=0}^{L}a_nI_{k-j-n}\right)\left(\sum_{m=0}^{L}a_mI_{k-l-m}\right)^*\right]+\sigma^2\delta_{l-j}\\
    &\overset{a.}{=}\sum_{n=0}^{L}a^*_na_{n+l-j}+\sigma^2\delta_{l-j}\\
    &=\begin{cases}
        x_{l-j}+\sigma^2\delta_{l-j},&(|l-j|\leq L)\\
        0,&\mathrm{otherwise}.
    \end{cases}
\end{aligned}\tag{3}$$

In Eq. (3), (a.) occurs because $I_{k}$ is independent to each other, i.e. $\mathbb{E}[I_kI_j]=0$ for $k\neq j$.

And for the right-hand side of Eq. (2), we have

$$\begin{aligned}
    \mathbb{E}[I_ka_{k-l}^*]&=\mathbb{E}\left[I_k\left(\sum_{n=0}^{L}a_nI_{k-l-n}+\eta_{k-l}\right)^*\right]\\
    &=\begin{cases}
        a_{-l}^*,&-L\leq l\leq0\\
        0,&\mathrm{otherwise}.
    \end{cases}
\end{aligned}\tag{4}$$

If we substitute Eq. (3) and Eq. (4) into Eq. (2) and take $z$ transform, we have

$$C(z)\left(A(z)A^*(1/z^*)+\sigma^2\right)=A^*(1/z^*).$$

Therefore, the transfer function of the equalizer based on the MSE criterion comes to

$$C(z)=\frac{A^*(1/z^*)}{A(z)A^*(1/z^*)+\sigma^2}.$$

If the noise-whitening filter is applied, the transfer function becomes

$$C'(z)=\frac{1}{A(z)A^*(1/z^*)+\sigma^2}=\frac{1}{X(z)+\sigma^2}.$$

We can compare the $C'(z)$ between peak distortion criterion (ZF) and MSE criterion, showing that the difference is that only **the noise spectral density factor $\sigma^2$ is considered in MSE criterion**. If the SNR is high, or the noise factor $\sigma^2$ is small ($\sigma^2\rightarrow0$), these two criterion have approximately equal performance. On the other hand, if $\sigma^2$ is not neglectable, there is both residual intersymbol interference and additive noise at the output of the MSE equalizer.

## Baseband Equalizer

<img src="linear-equalization-baseband.png" alt="linear transversal filter" width="600"/>

## Passband Equalizer

---

References

Kay M. Steven, (2009). Fundamentals of Statistical Signal Processing Volume 1 Estimation Theory. Prentice Hall PTR, New Jersey USA.

