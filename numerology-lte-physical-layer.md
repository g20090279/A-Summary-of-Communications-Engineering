# Numerology in Physical Layer of LTE and Above

It is well known that in LTE a *Resource Block (RB)* comprises 7*12=84 *Resource Elements (REs)*, 7 symbols in a time slot (0.5 ms) and 12 subcarriers with 15 kHz spacing in the frequency domain ([3GPP TS 36.211, Figure 6.2.2-1](#3GPP-TS36.211)). But did you thnk about why the numbers are defined as mentioned?

## Chip rate from 3G standard (UMTS)

In 3G, *Direct Sequence Spread Spectrum (DSSS)* in a wide-band system is used to spread the power of the signal to a wider range in the frequency domain. As consequency, the effective symbol rate is reduced, resulting in a lower inter-user interference. It is similar to OFDM. However, OFDM orthogonalize in the frequency domain, while DSSS in code domain.

Each bit of the spreading sequency is known as chip. So the *chip rate* represents the number of pulses per second (chip per second) of a code.

According to [ETSI](https://www.etsi.org/technologies/mobile/3G), both FDD and TDD modes are defined with **3.84 Mchips/s**. The supported bandwidth is 5 MHz. Later in the 2nd release, Relese 4, a further TDD option called *TD-SCDMA* or *LCR (low chip rate) TDD* was developed for China with **1.28 Mchips/s**. In Release 7, another TDD option called *VHCR (very high chip rate) TDD* was developed with **7.68 Mchips/s**.

We are not answering why the chip rate is defined as above in 3G, but just taking them out to see the logic of numerology in LTE.

## Symbol rate vs. bandwidth

In many literatures, we see that the symbol rate is approximated with the inverse of bandwidth, i.e. $R_{sym}=\frac{1}{T_{sym}}=W$, where $R_{sym}$ is symbol rate, $T_{sym}$ is the symbol duration and $W$ is the bandwidth. But why? If only considering transmission, it seems that you can transmit data symbols as many as we want, since the symbol rate is determined by how fast can the chip process, and we can produce a chip with higher chip rate.

In fact, the answer is yes, you can transmit data symbols as you want, if you have **infinite** bandwidth. However, to efficienty utilize the frequency, the system should work within a certain frequency band without leaking much power outside the working frequencies. This also means that the signals are always designed to be band-limited.

When considering a **band-limited** signal with bandwith $W$, the Nyquist theorem ([Proakis & Salehi, 2010, P605](#proakis-2018)) indicates that the symbol rate should be not larger than the bandwidth

$$R_{sym}\leq W\quad\mathrm{or}\quad T_{sym}>\frac{1}{W}$$

to achieve zero *Inter-symbol Interference (ISI)*. Remind here a little bit for narrow-band signal. Each complex signal is carried by a pulse shaping function. This pulse shaping function determines the signal bandwidth. The ideal pulse shaping function is `sinc` function, which is however noncasual and hence not physically implementable. The *raised cosine* pulse shaping function is realistic and practical, approaching the rectangle-like spectrum. By introducing roll-off factor in $\alpha\in[0,1]$ (also called *excess bandwidth*) in raised cosine pulse, the Nyquist bandwidth $\frac{1}{T}$ is achieved. Note that the excess bandwidth is then $W\cdot\alpha$, resulting in the total bandwidth of raised cosine filter is $W(1+\alpha)$.

Since we can design a small roll-off factor, for example, $\alpha=0.25$, the largest symbol rate can be simpliy approximated by

$$R_{sym}=W=\frac{1}{T_{sym}}.$$

## Design of RB

Okay, we now understand the relation between the time domain and frequency domain. First of all, the setting of RB, frequency spacing $\Delta f=15\mathrm{\ kHz}$ and symbol duration $T_{sym}=\frac{1}{7}\cdot0.5\mathrm{\ ms}\approx71.4286 \mathrm{\ \mu s}>\frac{1}{15\mathrm{\ kHz}}\approx66.6667\mathrm{\ \mu s}$, conforms to Nyquist Theorem stated above. Theoretically, the bandwidth needed for $T_{sym}=\frac{1}{7}\cdot0.5 \mathrm{\ ms}$ symbol duration is only $\frac{1}{T_{sym}}=14\mathrm{\ kHz}$. The excessive bandwidth here is raised by the practical pulse shaping filter, say raised cosine.

> **Note**:
>
> The basic designing factor is the subcarrier spacing $\Delta f$.



## References:

<a name="3GPP-TS36.211"></a>3GPP TS 36.211, (2020). 3rd Generation Partnership Project; Technical Specification Group Radio Access Network; Evolved Universal Terrestrial Radio Access (E-UTRA); Physical channels and modulation (Release 16), v16.2.0.

<a name="proakis-2018"></a>Proakis J. G., and Salehi M., (2008). Digital Communications, 5th Edition. McGraw-Hill.


