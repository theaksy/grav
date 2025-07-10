---
title: 'SDR Info'
---

## Useful Info for SDRs and Applications

#### Bouncing noise floor and random spikes
That's something that happens quite often on SDRs without band select pre-filters. Something out of band is overloading the front end, and because most SDRs do all their filtering in DSP or in software, it's not possible to exclude that signal from the input's analog to digital converter (ADC). The ADC can't unsee that energy, even when the DSP is trying to filter it out, so you get what are called "images" on almost every band you look at. They're not real signals, but internal noise inside the SDR that it doesn't know how to handle. You might try scouting to the left and right on different bands to see if there's some powerful signal, most likely on the FM or AM broadcast bands, that could be generating out of band images. There are filters you can buy for cheap that will notch out that portion of the band for you, which will allow your SDR to hear better on all the other frequencies.

Of course, it's also entirely possible you have real noise from a device nearby at that frequency, such as a harmonic of a switched mode power supply or a noisy clock source in some rando electronic gadget.


#### IF Gain
📡 **IF gain**, or **Intermediate Frequency gain**, is a stage of amplification applied after the initial RF (Radio Frequency) signal has been down-converted but before it's digitised or demodulated. It’s a key part of the signal chain in many SDRs (Software Defined Radios), including those used in SatDump.

##### 🔍 What IF Gain Does
- Boosts signal strength at the intermediate frequency stage
- Helps optimise signal-to-noise ratio (SNR) before the ADC (Analog-to-Digital Converter)
- Works in tandem with RF gain (front-end) and BB gain (baseband, post-ADC)

##### ⚖️ Why It Matters
- Too low: You might lose weak signals in the noise
- Too high: You risk ADC overload or introduce distortion
- Balanced IF gain helps preserve signal integrity while avoiding intermodulation artefacts

##### 🧪 In Practice (e.g. SatDump or SDR#)
- RTL-SDRs often don’t expose IF gain directly—it’s either fixed or unused
- Higher-end SDRs (like Airspy or SDRplay) let you adjust IF gain manually or via AGC (Automatic Gain Control)
- In SDRuno, for example, IF gain can be adjusted independently to fine-tune reception, especially in crowded bands

🧠 Pro Tip
If you're seeing distortion or ghost signals (IMD), try:
- Reducing RF gain slightly
- Adjusting IF gain to maintain SNR without overdriving the ADC
- Disabling AGC for manual control in sensitive applications (like meteor scatter or weak-signal decoding)