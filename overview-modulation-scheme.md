> Overview of Modulation Schemes
> ---
> Knowledge of *principle of communications* as well as *estimation and detection theory* is preferred for better understanding.
> Last update on 24.05.2021.

# Binary Phase Shift Keying (BPSK)

The BPSK modulation ofen maps a binary bit into a real symbol $a_i$, i.e., 0 maps to $a_0=-1$ and 1 maps to $a_1=+1$.

## BPSK Constellation (Gray Code)

```
    imaginary
       ^
 (-1)  |  (+1)
---x-------x---> real
       |
```

## Bit Error Rate (BER) (Also Symbol Error Probability)

Assume two hypotheses:

$$\begin{align*}\mathcal{H}_0:&\quad x=a_0=-1,\\\mathcal{H}_1:&\quad x=a_1=+1.\end{align*}$$

Assume additive white gaussian noise (AWGN) $w$ with zero mean and noise power $\sigma_w^2$, the transmission model is

$$y=x+w,$$

where $x=a_i$. For the observation $y$, we have then

$$\begin{align*}p(y;\mathcal{H_0})=\frac{1}{\sqrt{2\pi\sigma_w^2}}\exp\left\{-\frac{1}{2\sigma_w^2}(x+1)^2\right\}\\p(y;\mathcal{H_1})=\frac{1}{\sqrt{2\pi\sigma_w^2}}\exp\left\{-\frac{1}{2\sigma_w^2}(x-1)^2\right\}\end{align*}.$$

By maximum likelihood (ML) decision rule, we decide $\mathcal{H}_1$ for $x>0$. The probability of false alarm (FA) $P(\mathcal{H_1}|\mathcal{H_0})$ is

$$P(\mathcal{H_1}|\mathcal{H_0})=Q\left(\frac{0-(-1)}{\sigma_w}\right)=Q\left(\frac{1}{\sigma_w}\right).$$

The probability of miss detection (MD) $P(\mathcal{H_0}|\mathcal{H_1})$ is the same as FA in this case. Therefore, assuming equiprobable hypotheses, the total error probability is

$$P_e=P(\mathcal{H_0})P(\mathcal{H_1}|\mathcal{H_0})+P(\mathcal{H_1})(\mathcal{H_0}|\mathcal{H_1})=\frac{1}{2}2P(\mathcal{H_1}|\mathcal{H_0})=Q(1/\sigma_w).$$

# Quadrature PSK (QPSK)

For QPSK, each bit pair (two bits) is mapped into a complex symbol. Therefore, there are four different cases for a QPSK symbol $a_i$

$$a_i=\begin{cases}+1+j1 & i=0\\-1+j1 & i=1\\-1-j1 & i=2\\+1-j1&i=3,\end{cases}$$

## QPSK Constellation (Gray Code)

```
    imaginary
        ^
  a1    |    a0
(-1,+1) |  (+1,+1)
    x   |   x
        |  
-----------------> real
        | 
    x   |   x
(-1,-1) |  (+1,-1)
   a2   |    a3 
        |
```

Note that the above constellation is based on the power that $|a|^2=2$. Usually, we can set the power of each QPSK symbol as 1, resulting in a new symbol $\tilde{a}_i=\frac{\sqrt{2}}{2}a_i$.

## Symbol Error Probability

Consider the case of $a_i$ whose power is one. We consider also bit pair instead of complex symbol for simplicity. Consider also AWGN $\boldsymbol{w}\sim\mathcal{N}(0,\sigma_w^2\mathbf{I})$ and the transmission model

$$\boldsymbol{y}=\boldsymbol{x}+\boldsymbol{w},$$

Assume four hypotheses:

$$\begin{align*}\mathcal{H}_0:&\quad \boldsymbol{x}=\left[+1,+1\right]^T,\quad a_0=+1+j1,\\\mathcal{H}_0:&\quad \boldsymbol{x}=\left[-1,+1\right]^T,\quad a_1=-1+j1,\\\mathcal{H}_0:&\quad \boldsymbol{x}=\left[-1,-1\right]^T,\quad a_2=-1-j1,\\\mathcal{H}_3:&\quad \boldsymbol{x}=\left[+1,-1\right]^T,\quad a_3=+1-j1.\end{align*}$$

Since these four symbols are symmetric, the probability of error for each hypothesis is the same. Consider the probability of error for $\mathcal{H}_0$, we have

$$P_e^{\mathcal{H}_0}=P(\mathcal{H}_1|\mathcal{H}_0)+P(\mathcal{H}_2|\mathcal{H}_0)+P(\mathcal{H}_3|\mathcal{H}_0).$$

For probability density function (PDF) of $\boldsymbol{y}=[y_0,y_1]^T$ if $\mathcal{H}_0$ is true is

$$\begin{align*}p\left(\boldsymbol{y}|\mathcal{H}_0\right)&=\frac{1}{(2\pi)^{2/2}|\sigma_w^2\mathbf{I}|^{1/2}}\exp\left\{-\frac{1}{2\sigma_w^2}(\boldsymbol{y}-\boldsymbol{x})^T(\boldsymbol{y}-\boldsymbol{x})\right\}\\
&=\frac{1}{2\pi\sigma_w^2}\exp\left\{\frac{1}{2\sigma_w^2}\left[\left(y_0-1\right)^2+\left(y_1-1\right)^2\right]\right\}\\
&=\frac{1}{\sqrt{2\pi\sigma_w^2}}\exp\left\{\frac{1}{2\sigma_w^2}\left(y_0-1\right)^2\right\}\frac{1}{\sqrt{2\pi\sigma_w^2}}\exp\left\{\frac{1}{2\sigma_w^2}\left(y_0-1\right)^2\right\}.\end{align*}$$

It is obvious to see that

$$\begin{align*}
P(\mathcal{H_1}|\mathcal{H}_0)=&\int_{y_0=-\infty}^{0}\int_{y_1=0}^{+\infty}p\left(\boldsymbol{y}|\mathcal{H}_0\right)d\boldsymbol{y}\\
=&\int_{y_0=-\infty}^{0}\frac{1}{\sqrt{2\pi\sigma_w^2}}\exp\left\{\frac{1}{2\sigma_w^2}\left(y_0-1\right)^2\right\}dy_0\\
&\cdot\int_{y_1=0}^{+\infty}\frac{1}{\sqrt{2\pi\sigma_w^2}}\exp\left\{\frac{1}{2\sigma_w^2}\left(y_1-1\right)^2\right\}dy_1\\
=&Q\left(1/\sigma_w\right)Q\left(-1/\sigma_w\right).
\end{align*}$$

Similarly, $P(\mathcal{H_3}|\mathcal{H}_0)=P(\mathcal{H_1}|\mathcal{H}_0)$. And

$$P(\mathcal{H_2}|\mathcal{H}_0)=Q\left(1/\sigma_w\right)Q\left(1/\sigma_w\right)$$

As a result, the total error probability of a QPSK symbol is

$$\begin{align*}
P_e=&\frac{1}{4}\left(P_e^{\mathcal{H}_0}+P_e^{\mathcal{H}_1}+P_e^{\mathcal{H}_2}+P_e^{\mathcal{H}_3}\right)\\
=&P_e^{\mathcal{H}_0}=2Q\left(1/\sigma_w\right)Q\left(-1/\sigma_w\right)+Q\left(1/\sigma_w\right)Q\left(1/\sigma_w\right).
\end{align*}$$

Alternatively, the probability of error can be calculated as $P_e^{\mathcal{H}_0}=1-P(\mathcal{H_0}|\mathcal{H}_0)$.

## Bit Error Rate

Ulike the BPSK modulation scheme where the symbol error probability is bit error probability, they are different for QPSK. A symbol error can leads to 1-bit error (adjacent symbol) or 2-bit error (diagonal symbol). Considering a bit pair, if we define there classes

- no error,
- 1-bit error,
- 2-bit error,

the bit error probability for each bit is the average bit error

$$\bar{e}=\frac{1}{2}\sum_{n=0}^{2}nP(e=n),$$

where $e=n,n=0,1,2$ represent respectively the cases of 0-, 1- and 2-bit error.

For each symbol, there are four different cases. Take $\mathcal{H}_0$ as an example. There are one correct case ($\mathcal{H}_0$ decides $\mathcal{H}_0$), one 2-bit-error case ($\mathcal{H}_0$ decides $\mathcal{H}_2$) and two 1-bit-error cases ($\mathcal{H}_0$ decides $\mathcal{H}_1$ and $\mathcal{H}_0$ decides $\mathcal{H}_3$). Therefore, the 1-bit-error probability is

$$P_e^{1b}=\frac{1}{4}8Q(1/\sigma_w)Q(-1/\sigma_w)=2Q(1/\sigma_w)Q(-1/\sigma_w).$$

Similarly, the 2-bit-error probability is

$$P_e^{2b}=\frac{1}{4}4Q(1/\sigma_w)Q(1/\sigma_w)=Q(1/\sigma_w)Q(1/\sigma_w).$$

Consequently, the bit error probability is

$$\begin{align*}
\bar{e}=&\frac{1}{2}\sum_{n=0}^{2}nP(e=n)\\
=&\frac{1}{2}\left(1\cdot2Q(1/\sigma_w)Q(-1/\sigma_w)+2\cdot Q(1/\sigma_w)Q(-1/\sigma_w)\right)\\
=&Q(1/\sigma_w)Q(-1/\sigma_w)+Q(1/\sigma_w)Q(1/\sigma_w)\\
=&Q(1/\sigma_w)\left(Q(-1/\sigma_w)+Q(1/\sigma_w)\right)\\
=&Q(1/\sigma_w)
\end{align*}$$

It is the same as the bit error probability of BPSK. This is because they have the same $E_b/N_0$. If we consider the same symbol power instead of bit power, since $BE_b=E_s$ the bit error probability is higher for QPSK, where $B$ is the number of bits per symbol. For example, if we consider the QPSK symbol $\tilde{a}_i$ whose power is one, the bit error probability of QPSK increases to $Q(\sqrt{2}/(2\sigma_w))$.

# Differential QPSK

# Gaussian Minimum Shift Keying (GMSK)

Keywords: frequency shift keying, continuous phase

