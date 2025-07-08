---
title: NOAA
---

# Welcome to my blog :)

![Map](Map.PNG "Map")

### APT & LRPT Weather Satellite Transmission Frequencies
|Satellite|Format|Frequency|
|---|---|---|
|NOAA 15|APT|137.62 MHz|
|NOAA 18|APT|137.9125 MHz|
|NOAA 19|APT|137.10 MHz|
|Meteor M2|LRPT|Failed|
|Meteor M2-2|LRPT|Failed|
|Meteor M2-3|LRPT|137.90 MHz|
|Meteor M2-4|LRPT|137.90 MHz|

#### ⚡ What Causes the Center Spike?
- **DC Offset in IQ Data:** Most SDRs (especially RTL-SDRs) introduce a small DC bias in the I/Q signal. When you perform an FFT, this bias shows up as a strong spike at 0 Hz (the center of the spectrum).

- **Imperfect IQ Balance:** RTL-SDRs don’t have hardware IQ correction, so any imbalance between the I and Q channels leads to leakage at DC.

- **No Built-in DC Blocking in FFT Display:** SatDump doesn’t remove the DC spike from the waterfall or FFT display—it only blocks it behind the scenes before demodulation if you enable the right setting.

#### 🛠 How to Deal With It in SatDump
- **Enable DC Blocking:** In the Configure tab for your satellite or in Offline Processing, look for a setting called DC Blocking. This won’t remove the spike from the FFT view, but it will prevent it from interfering with decoding.

- **Offset the Tuning Frequency:** Shift your center frequency slightly so the signal of interest isn’t sitting right on top of the DC spike.

- **Use a Better SDR:** Devices like Airspy or SDRplay have better IQ balance and often don’t suffer from this issue as severely.

#### 🧪 Bonus Tip
If you're using a decimation factor, make sure your low-pass filter is properly configured—otherwise, aliasing can make the DC spike even more pronounced.