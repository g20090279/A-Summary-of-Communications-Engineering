# Evelope Delay (Group Delay)

## Band-limited Channel

Consider a band-limited channel with a bandwidth <img src="/tex/84c95f91a742c9ceb460a83f9b5090bf.svg?invert_in_darkmode&sanitize=true" align=middle width=17.80826024999999pt height=22.465723500000017pt/>. This channel is often characterized as a linear filter. Assume an equivalent low-pass frequency response of this channel is <img src="/tex/eb4f97ba702bd39acf29c3da12874af9.svg?invert_in_darkmode&sanitize=true" align=middle width=35.52748319999999pt height=24.65753399999998pt/>.

If the channel is band-limited with bandwidth <img src="/tex/84c95f91a742c9ceb460a83f9b5090bf.svg?invert_in_darkmode&sanitize=true" align=middle width=17.80826024999999pt height=22.465723500000017pt/>, the channel response will be zero if <img src="/tex/6191bc42d6cf99894dec07389de9c87c.svg?invert_in_darkmode&sanitize=true" align=middle width=58.675752299999985pt height=24.65753399999998pt/>.

## Definition of Evelope Delay

Within the bandwidth of the band-limited channel, the frequency response of this channel can be written as
<p align="center"><img src="/tex/94627609ce1b3fd2eb75e702120b9eba.svg?invert_in_darkmode&sanitize=true" align=middle width=145.84094414999998pt height=19.526994300000002pt/></p>
where <img src="/tex/fca7cb16330a73a4f0039fa9fc87893f.svg?invert_in_darkmode&sanitize=true" align=middle width=44.65993124999999pt height=24.65753399999998pt/> is the amplitude response.

The *Evelope Delay* is defined as
<p align="center"><img src="/tex/2add446a14116c34d7e2e71ad24040d0.svg?invert_in_darkmode&sanitize=true" align=middle width=136.32095565pt height=37.9216761pt/></p>
We can see that the evelope delay is the negative of the rate of change of phase with frequency.

Note that the time delay in time-domain corresponds to phase shift in the frequency domain. For example, if the channel shifts the signal with <img src="/tex/2f118ee06d05f3c2d98361d9c30e38ce.svg?invert_in_darkmode&sanitize=true" align=middle width=11.889314249999991pt height=22.465723500000017pt/>, i.e. <img src="/tex/109fdeeaa013d31c9090ffbabe40494d.svg?invert_in_darkmode&sanitize=true" align=middle width=106.38307019999999pt height=24.65753399999998pt/>, the frequency response is <img src="/tex/52778185704a88ac50593f1673c4361e.svg?invert_in_darkmode&sanitize=true" align=middle width=113.36384894999998pt height=27.91243950000002pt/>. In this case, <img src="/tex/99b3f54f9f0d972b44f421dbaed2465f.svg?invert_in_darkmode&sanitize=true" align=middle width=105.3654624pt height=24.65753399999998pt/>.

The evelope delay of this channel is <img src="/tex/15b29b9dbe462f033087b7f9615d3b12.svg?invert_in_darkmode&sanitize=true" align=middle width=65.45662529999998pt height=24.65753399999998pt/>. This evelope delay is then related to the signal delay, but not always in an obvious manner. We can see that for different frequency components, the rate of changing phase with respect to frequency, i.e. envelope delay, has a physical meaning of time.

## Definition of "Nondistorting" or "Ideal" Channel

According to different conditions of amplitude response and evelope delay, we can clarify a channel is

- **ideal**, if <img src="/tex/fca7cb16330a73a4f0039fa9fc87893f.svg?invert_in_darkmode&sanitize=true" align=middle width=44.65993124999999pt height=24.65753399999998pt/> is constant for all <img src="/tex/ca96de155e55a64bb0ee3e69eb3b3d31.svg?invert_in_darkmode&sanitize=true" align=middle width=58.675752299999985pt height=24.65753399999998pt/> and <img src="/tex/7ada21c69306bbc3c8c7992de2c0ee48.svg?invert_in_darkmode&sanitize=true" align=middle width=30.776374199999985pt height=24.65753399999998pt/> is linear w.r.t. <img src="/tex/190083ef7a1625fbc75f243cffb9c96d.svg?invert_in_darkmode&sanitize=true" align=middle width=9.81741584999999pt height=22.831056599999986pt/> (i.e. <img src="/tex/a2a68ba43c76fcbda88a5b2cc1e89337.svg?invert_in_darkmode&sanitize=true" align=middle width=31.649679599999992pt height=24.65753399999998pt/> is constant);
- **distorted in amplitude**, if <img src="/tex/fca7cb16330a73a4f0039fa9fc87893f.svg?invert_in_darkmode&sanitize=true" align=middle width=44.65993124999999pt height=24.65753399999998pt/> is not constant for all <img src="/tex/ca96de155e55a64bb0ee3e69eb3b3d31.svg?invert_in_darkmode&sanitize=true" align=middle width=58.675752299999985pt height=24.65753399999998pt/>;
- **distorted in delay (or phase)**, if <img src="/tex/a2a68ba43c76fcbda88a5b2cc1e89337.svg?invert_in_darkmode&sanitize=true" align=middle width=31.649679599999992pt height=24.65753399999998pt/> is constant for all <img src="/tex/ca96de155e55a64bb0ee3e69eb3b3d31.svg?invert_in_darkmode&sanitize=true" align=middle width=58.675752299999985pt height=24.65753399999998pt/>.

The channel distorted in delay (or phase) is also termed as *dispersive channel*, indicating that distortion due to delay in time-domain.

## Deeper in Evelope Delay

Generally, envelope delay is a concept within digital filters, and communication channel can be often represented as a digital filter. In reality, the channel would not be ideal, and therefore, the evelope delay would not be constant.

When the evelope delays within <img src="/tex/d1102267b6da02f0ba72bad80d772e8d.svg?invert_in_darkmode&sanitize=true" align=middle width=58.675752299999985pt height=24.65753399999998pt/> are not constant, it indicates that the signals from different frequency components are delayed with different time.

This time difference results in inter-symbol-interference (ISI).