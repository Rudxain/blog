# My acoustic protocol
I was deeply pondering about how I'd go about specifying a digital communication protocol over an acoustic medium (AKA "Data Over Sound"). Other people have already done this (see dial-up), but I wanted this to be a "brain exercise".

## ∿ Sines ∿
Taking inspiration from modern WiFi protocols, it would be wise to support parallel multi-band transmission. That is, encoding data as a parallel sequence of wave pulses, each band being a range of frequencies (deemed as a "single frequency", for the purpose of being resilient against the Doppler Effect) in a geometric/logarithmic/exponential scale. 

> Side note:
> I've always found it cringe that WiFi bands and channels use a linear scale.
> I can totally understand the convenience of simply adding or subtracting a constant to switch channels, but it's just so unnatural.

For a faster transfer, each pulse must be as narrow as a single wave-cycle (we doing "quantum" now). The set of bands must be the highest frequencies such that both of these conditions are met:
- The sender can generate them. This is limited by sampling-rate, speaker quality, and environment reverberation properties (self-interference can cancel some frequencies).
- The receiver can hear them. This is limited by sampling-rate, microphone quality, and the medium of mechanical waves (hot air, cold water, etc...).

> Imagine minding your own business as an open-source maintainer, and some madlad opens an issue along the lines of "can't send files underwater".
> 
> **This** is why I'm concerned about the reliability of underwater communication.
> 
> I can understand the pain of not being able to flex about the fact that your phone's speaker works underwater.

Higher frequencies allow us to send shorter (quicker) pulses, because of the wave-length. This is why 5GHz WiFi was invented, because 2.4GHz is "too slow" and "claimed" by Bluetooth.

For the receiver to decode the data, it must perform a Discrete Sine (simpler than Fourier) Transform for 2 reasons:
- Apply a high-pass filter. This happens implicitly, as the algorithm only needs to focus on the previously-negotiated set of bands, so the lower frequencies are simply ignored.
- Get the sequence of amplitudes for each relevant band.

For even faster transfers, each pulse can be non-binary (even the waves are 🏳️‍🌈queer now, lol). We can encode more data per pulse if we allow the pulses to have 1 of multiple amplitude levels. The difference between levels should be geometric too (constant ratio).

I'm not quite sure about how to handle real-time changes in distance between sender and receiver, as the geometric amplitude decays approximately as `1 ÷ √distance` (same as light), so this is quadratic decay (non-linear and non-logarithmic).

## Digital limits
But what if we didn't use sines? What if we squeezed the full potential of the sampling rate? [Can we get much higher?](https://youtu.be/gWo12TtN9Kk)

Well, there are big technical limitations that make this not worth it:

The sender must somehow generate a pulse sequence that's twice the frequency of the receiver's sampling rate. This is because microphones can only perceive differences in air pressure, so sending a "111" will be "heard" as "100" (assuming binary amplitude levels). With twice the frequency, the sender can theoretically **pin/peg the microphone membrane** (from the POV of the ADC) to any distance from its rest position, allowing the DSP to detect the correct bit sequence ("1010" -> "11"). Even if the membrane cannot oscillate faster than the receiver's sampling-rate, its "dampening factor" will do the work for us. However this can become a problem if the intensity of a "padding 0" (the zeros that should be ignored) is just as high as the intensity of the "1", the padding must always be weaker than the real signal (and vice-versa: a "real 0" must be strong, and a "padding 1" must be weak), as this allows the membrane to stay. This is partly speculation, as I simulated all of this in my brain.

An elegant solution to the former problem, is to make the receiver aware of [delta encoding](https://en.wikipedia.org/wiki/Delta_encoding). That way, a _perceived_ change between 2 consecutive samples can be interpreted as a continuous ("held") pulse.

Before sending the payload, the sender must reset its own DAC multiple times, to **brute-force sync its own sampling phase with the receiver's sampling phase**. This can theoretically take **infinite** time, and in practice ~30 seconds?. The Doppler Effect can only corrupt the data while the devices are moving relative to each other; once the devices stand still, the data can continue to transfer "normally".

> Sampling-phase synchronization reminds me of [wireless "quantum" (sub-tick) redstone](https://youtu.be/sBNuqZKa_Lw).

Not even `root` access grants full control over sampling-phase, as this is typically "abstracted away" by the audio driver and the audio chip itself.

Also, resets can be quite slow: There was a Dell Inspiron that had a power-saving feature that lets the Realtek chip-set and integrated-speakers "sleep" (turn-off) while not playing audio. This proved to be a mistake, because the startup latency was **VERY bad** while connected to HDMI, as resuming a video would guarantee that you'd miss someone saying a word (or even short phrases). You had to _rewind the video in advance_ to avoid missing something.

These are just a few of many reasons why a specialized device (analogous to a Bluetooth chip-transceiver combo) is much better than an average DSP-speaker&microphone combo.

Another advantage of specialized hardware, is that there's no need for sine-transforms if the set of available bands depends on hardware sensors. This is exactly how the human ear works. The brain doesn't have a "Fourier-Transform neural circuit" it's just that the ears already have receptors that are sensitive to specific frequencies (like the human retina, but with **orders of magnitude** more bands).

As I said previously, hard-coded bands are bad, because you can't dynamically adapt them according to the environment and receiver.

> Then how does WiFi do it?

Because the channels are also hard-coded. You can _switch_ channels, but you can't _shift_ them.

## Error correction
We haven't even talked about this! Oh boy, don't get me started.

As I previously mentioned, the protocol must protect the signals against:
- noise
- reverb ("echo")
- Doppler Effect

Noise is mostly impossible to eliminate, unless the receiver has a [secondary mic in the opposite direction](https://en.m.wikipedia.org/wiki/Active_noise_control). This is standard for phones, but not laptops and desktops.

We can protect against noise in general by adding redundancy (see Hamming Codes and Reed-Solomon).



## Trivia
BTW, did you know that lower frequencies have more unique phases available? Me neither. This makes sense, as higher frequencies can "exhaust" the sampling-rate, reducing the set of possible phases. I actually lied, I've only similulated this in my brain with a low frequency wave and a half-sample-rate wave. I'm not sure if it's possible to preserve phase information by using a frequency that isn't perfectly half the sample-rate.

