# Transimission Model for Narrow-band Signal and Channel

## Baseband (Lowpass) Transmitted Signal

For different types of digital modulation techniques, a common form is given as (Proakis 2008, C9.2)

$$v(t)=\sum_{n=0}^{\infty}I_ng(t-nT),$$

where $1/T$ is the sampling frequency, ${I_n}$ is the discrete complex modulated symbols, no matter BPSK, QPSK, QAM, 16QAM and on. $g(t)$ is a pulse function which 

- maps the complex symbols into continuous signal (a signal can not be time-limited and frequency-limited at the same time due to Fourier Transform),
- shapes the signal into narrow-signal, $G(f)=0$ for $|f|>W$.

## Band-limited Channel

To increase the efficiency, the use of a portion of the channel is expected to not interfere other portions, which makes the target designed goal is to have a band-limited channel.

An ideal (or nondistorting) band-limited channel is defined as if the amplitude response $|C(f)|$ is constant for $|f|\leq W$, and $C(f)=0$ for $|f|>W$, and the envelope delay $\tau(f)$ is a linear function of frequency. $|C(f)|$ is the frequency response of the time-domain channel $c(t)$

## Baseband Received Signal

After $v(t)$ goes through the channel $c(t)$, the received signal is the convolution of $v(t)$ and $c(t)$

$$\begin{aligned}
r(t)&=\int_{-\infty}^{\infty}\sum_{n=0}^{\infty}I_ng(\tau-nT)c(t-\tau)d\tau+z(t)\\&=\sum_{n=0}^{\infty}I_n\int_{-\infty}^{\infty}g(\tau-nT)c(t-\tau)d\tau+z(t)\\&=\sum_{n=0}^{\infty}I_nh(t-nT)+z(t)
\end{aligned},$$

where $h(t)=\int_{-\infty}^{\infty}g(\tau)c(t-\tau)d\tau$ is the effective channel response combining pulse shaping function and pure channel response, and $z(t)$ represents the additive white Gaussian noise (AWGN).

## Filtering the Received Signal

The optimum filter (derived from the correlation receiver based on MAP decision rule) at the recevier $f(t)$ for AWGN channel from the point of view of signal detection is **mathched filed**, which matches to the received pulse $f(t)=h(T-t)$. The frequency response is $F(f)=H^*(f)e^{-j2\pi fT}$, the complex conjugate $H^*(f)$ and the phase shift $e^{-j2\pi fT}$ due to sampling delay (Proakis 2008, C4.2).

With the optimum filter at the receiver, the transmission mode can be rewritten to

$$\begin{aligned}
y(t)&=\int_{-\infty}^{\infty}r(\tau)f(t-\tau)d\tau\\
&=\int_{-\infty}^{\infty}r(\tau)h(T-t+\tau)d\tau\\
&=\sum_{n=0}^{\infty}I_n\int_{-\infty}^{\infty}[h(\tau-nT)+z(\tau)]h(\tau-t+T)d\tau\\
&=\sum_{n=0}^{\infty}I_nx(t-nT)+n(t),\\
\end{aligned}$$
where $x(t)$ is the filtered output of received response at the receiver. $n(t)$ is the filtered noise.

This is the most-used channel model in narrow-band channel. The complex signal symbols are carried by the effective pulse $x(t)$ and its shifted version. This effective pulse includes effect of pulse shaping function at the transmitter, channel response, as well as optimum receiver filter.

# Reference
Proakis J. G., and Salehi M., (2008). Digital Communications, 5th Edition. McGraw-Hill.

# Keywords

transmission, complex baseband, band-limited, pulse shaping, matched filter, optimum receiver filter
