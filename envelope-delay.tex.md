# Evelope Delay (Group Delay)

## Band-limited Channel

Consider a band-limited channel with a bandwidth $W$. This channel is often characterized as a linear filter. Assume an equivalent low-pass frequency response of this channel is $C(f)$.

If the channel is band-limited with bandwidth $W$, the channel response will be zero if $|f|>W$.

## Definition of Evelope Delay

Within the bandwidth of the band-limited channel, the frequency response of this channel can be written as
$$C(f)=|C(f)|e^{j\theta(f)},$$
where $|C(f)|$ is the amplitude response.

The *Evelope Delay* is defined as
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

This time difference results in inter-symbol-interference (ISI).