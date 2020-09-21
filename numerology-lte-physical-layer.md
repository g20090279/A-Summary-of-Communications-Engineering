# Numerology in Physical Layer of LTE and Above

It is well known that in LTE a *Resource Block (RB)* comprises 7*12=84 *Resource Elements (REs)*, 7 symbols in a time slot (0.5 ms) and 12 subcarriers with 15 kHz spacing in the frequency domain. But did you thnk about why the numbers are defined as mentioned?

## Chip rate from 3G standard (UMTS)

In 3G, *Direct Sequence Spread Spectrum (DSSS)* in a wide-band system is used to spread the power of the signal to a wider range in the frequency domain. As consequency, the effective symbol rate is reduced, resulting in a lower inter-user interference. It is similar to OFDM. However, OFDM orthogonalize in the frequency domain, while DSSS in code domain.

Each bit of the spreading sequency is known as chip. So the *chip rate* represents the number of pulses per second (chip per second) of a code.

According to [ETSI](https://www.etsi.org/technologies/mobile/3G), both FDD and TDD modes are defined with **3.84 Mchips/s**. The supported bandwidth is 5 MHz. Later in the 2nd release, Relese 4, a further TDD option called *TD-SCDMA* or *LCR (low chip rate) TDD* was developed for China with **1.28 Mchips/s**. In Release 7, another TDD option called *VHCR (very high chip rate) TDD* was developed with **7.68 Mchips/s**.

We are not answering why the chip rate is defined as above in 3G, but just taking them out to see the logic of numerology in LTE.

## Symbol Rate vs. Bandwidth

In many literatures, we see that the symbol rate is approximated with the inverse of bandwidth, i.e. $R_{sym}=\frac{1}{T_{sym}}=W$, where $R_{sym}$ is symbol rate, $T_{sym}$ is the symbol duration and $W$ is the bandwidth. But why? If only considering transmission, it seems that you can transmit data symbols as many as we want, since the symbol rate is determined by how fast can the chip process, and we can produce a chip with higher chip rate.

In fact, the answer is yes, you can transmit data symbols as you want, if you have **infinite** bandwidth. However, to efficienty utilize the frequency, the system should work within a certain frequency band without leaking much power outside the working frequencies. This also means that the signals are always designed to be band-limited.

When considering a band-limited signal with bandwith $W$, the Nyquist theorem (Proakis & Salehi, 2010, P605) indicates that the symbol rate should be not larger than the bandwidth to achieve zero *Inter-symbol Interference (ISI)*.

## References:



