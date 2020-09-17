# Evelope Delay (Group Delay)

## Overview of the Traditional Communication System

A traditional narrow-band communication system where a sequence of complex symbols $[a_0,a_1,\cdots,a_{N-1}]$ are transmitted successively through the channel, and a pulse shaping function which is continous $p(t-nT)$ is used to shape (or carry) the discrete complex symbols $a_n$ into continuous wave form as

$$u(t)=\sum_{n=0}^{N-1}a_np(t-nT),$$

where $T$ is the sampling rate of the signal. It is also called symbol rate, showing that how fast the complex symbols are pulse-shaped and transmitted.

> ### What Is A Band-limited Channel
> 
> Consider a band-limited channel with a bandwidth $W$. This channel is often characterized as a linear filter. Assume an equivalent low-pass frequency response of this channel $c(t)$ is $C(f)$.
> 
> If the channel is band-limited with bandwidth $W$, the channel response will be zero if $|f|>W$.

An complex symbol does not have the property "bandwidth". After it is pulse-shaped into a continuous signal, it is then meaningful to analyze the bandwidth. Obviously, the pulse shaping function $p(t)$ determines the bandwidth of the signal. Since we are now talking about the band-limited channel, the bandwidth of the signal should be not larger than the channel, or there will be distortion of frequency response of the signal. Hence, $p(t)$ should also follows the band-limited rule during the design of the system.

After the channel $c(t)$, the recieved signal can be written as

$$r(t)=\int_{-\infty}^{+\infty}u(\tau)c(t-\tau)d\tau+n(t),$$

where $n(t)$ denotes the additive noise.

The continous (analog) recieved signal is then sampled to a digital signal for further baseband processing. The clock frequency of sampling at the receiver can be estimated.

## Definition of Evelope Delay

Within the bandwidth of the band-limited channel, the frequency response of this channel can be written as

$$C(f)=|C(f)|e^{j\theta(f)},$$

where $|C(f)|$ is the amplitude response.

The *Evelope Delay*, which is also called *Group Delay*, is defined as

$$\tau(f)=-\frac{1}{2\pi}\frac{d\theta(f)}{df}.$$

We can see that the evelope delay is the negative of the rate of change of phase with frequency.

Note that the time delay in time-domain corresponds to phase shift in the frequency domain. For example, if the channel shifts the signal with $T$, i.e. $c(t)=\delta(t-T)$, the frequency response is $C(f)=e^{-j2\pi fT}$. In this case, $\theta(f)=-2\pi fT$.

The evelope delay of this channel is $\tau(f)=T$. This evelope delay is then related to the signal delay, but not always in an obvious manner. We can see that for different frequency components, the rate of changing phase with respect to frequency, i.e. envelope delay, has a physical meaning of time.

## Definition of "Nondistorting" or "Ideal" Channel

According to different conditions of amplitude response and evelope delay, we can clarify a channel is

- **ideal**, if $|C(f)|$ is constant for all $|f|\leq W$ and $\theta(f)$ is linear w.r.t. $f$ (i.e. $\tau(f)$ is constant);
- **distorted in amplitude**, if $|C(f)|$ is not constant for all $|f|\leq W$;
- **distorted in delay (or phase)**, if $\tau(f)$ is constant for all $|f|\leq W$.

The channel distorted in delay (or phase) is also termed as *dispersive channel*, indicating that distortion due to delay in time-domain.

## Deeper in Evelope Delay

Generally, envelope delay is a concept within digital filters, and communication channel can be often represented as a digital filter. In reality, the channel would not be ideal, and therefore, the evelope delay would not be constant.

When the evelope delays within $|f|<W$ are not constant, it indicates that the signals from different frequency components are delayed with different time.

This will introduce interference in 

For example, if a channel modeled as having a linear envelope delay characteristic ($\tau(f)$ is a linear function of $f$) instead of ideal constant, like

$$C(f)=e^{-2\pi f^2T},\qquad |f|<W.$$

A signle with shape of `sinc` function will be distorted after going through this channel.

---

### A Simulation based on `Matlab`

Create an input signal by `sinc` function.

```matlab
% symbol rate
T = 1;

% sampling rate
fs = 20;

% time span
tSpan = 10;
t = -tSpan*T : 1/fs : tSpan*T;

% transmit signal
x = sinc(t);
figure;
plot(t,x);
xlabel('time (T)')
ylabel('amplitude')
title('time domain x(t)=sinc(t)')
```

Since the channel is complex, we have to form also complex signal. Otherwise, it is meaningless. But we analyze only the real part. Note that the complex signal represents the quadrature and in-phase paths.

```matlab
% Create baseband complex signal
xBaseband = (1+1i)*x;
```

The freqeuncy-domain of input signal will be

```matlab
N = 1024;
X = fft(xBaseband,N);
X_shift = fftshift(X);
f = ((0:N-1)-N/2)*fs/N;
figure;
plot(f,1/fs*abs(X_shift));
xlim([-T,T])
xlabel('frequency (1/T)');
ylabel('amplitude')
title('frequency domain X(f)')
```

The channel is characterized as linear evelope delay, which is quadratic in phase

```matlab
% channel freqeuncy response
C = exp(-1i*2*pi*f.^2*T);
```

The frequency-domain of received signal is the multiplication of input signal and channel in frequency domain. The time-domain received signal is the `IFFT` (inverse discrete/fast Fourier Transform) of the frequency-domain received signal.

```matlab
Y = X.*C;
y = ifft(Y);
figure;
plot(t,real(ifftshift(y)))
```

---

Note that we can also get the time-domain received signal by calculating convolution of input signal and channel in time-domain. This gives the same results.

We can see that final time-domain received signal is a bit different than expected due to the `DFT` and `IDFT` operations, we can see that the true output signal is distorted, i.e. different from the input signal. For the original input signal, the samples on $nT$ are zeros, resulting in no ISI. However, with distortion, the output signal has no longer the same characteristic, introducing ISI.