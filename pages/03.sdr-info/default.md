---
title: 'SDR Info'
---

## Useful Info for SDRs and Applications

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