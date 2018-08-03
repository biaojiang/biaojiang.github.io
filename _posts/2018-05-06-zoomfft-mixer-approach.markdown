---
layout: post
title:  "Implement the Zoom FFT of the mixer approach in Python!"
date:   2018-05-06 12:15:00 +0100
categories: projects
math: true
---

## Zoom FFT

[Zoom FFT](https://se.mathworks.com/help/dsp/examples/zoom-fft.html) was used to analyze a frequency subband. The idea behind zoom FFT is to retain the same resolution, which could be achieved with a full-size FFT on the original signal, by computing a small-size FFT on a down-sampled shorter signal. Thus, the FFT efficient could be improved while maintaining the same resolution.

This is intuitive: for a decimation factor of $$D$$, the new sampling rate is $$f_{sd} = f_s/D$$, and the new frame size (and FFT length) is $$L_d = L/D$$, so the resolution of the decimated signal is $$f_{sd}/L_d = f_s/L$$.

## Implementation

### The Mixer Approach

See [Zoom FFT](https://se.mathworks.com/help/dsp/examples/zoom-fft.html): The popular mixer Zoom FFT method consists of first shifting the band of interest down to DC using a mixer, and then performing lowpass filtering and decimation by a factor of BWFactor (using an efficient polyphase FIR decimation structure).

**Note:** For short signal, the polyphase FIR designing is tricky, sometimes it will distort the spectrum, as in the Matlab example, the transient filtering effects were eliminated by repeating 10 times of filtering. So the conventional Fourier resampling method is recommended here.

### Python Codes

* Import modules
{% highlight Python %}
import numpy as np
from matplotlib import pyplot as plt
from numpy import pi
from numpy.fft import fft, fftfreq, fftshift
from scipy import signal
{% endhighlight %}

* Generate signal

{% highlight Python %}

def SineWave(f, fs, length, amplitude=1):
    x = amplitude * np.sin(2 * pi * f / fs * np.arange(length))
    return x

L = 32
fs = 128
res = fs/L
f1 = 40
f2 = f1 + res
x = SineWave(f1, fs, L) + SineWave(f2, fs, L, 2)

{% endhighlight %}


* Plot the original FFT
{% highlight Python %}
X = fft(x)
freq = fftfreq(L, d=1/fs)

fig1, ax1 = plt.subplots(2)
#fig1.clf()
ax1[0].stem(fftshift(freq), abs(fftshift(X)) / L)
#ax1[0].set_xlabel('Frequency (Hz)', fontsize=12)
ax1[0].set_ylabel('Magnitude', fontsize=12)
ax1[0].set_title('Two-sided spectrum', fontsize=12)
ax1[0].grid()
{% endhighlight %}

* Zoom FFT using mixer approach
{% highlight Python %}
BWOfInterest = 48 - 16
Fc = (16 + 48) / 2
BWFactor = np.floor(fs / BWOfInterest).astype(np.uint8)

# mix the signal down to DC, and filter it through the FIR decimator
indVect = np.arange(L)
y = x * np.exp(-1j * 2 * pi * indVect * Fc / fs)
xd = signal.resample(y, 8)
# polyphase method as in Matlab
#indVect = np.arange(L * 10)
#y = np.tile(x, 10) * np.exp(-1j * 2 * pi * indVect * Fc / fs)
#beta = signal.kaiser_beta(80)
#xd = signal.resample_poly(y, up=1, down=BWFactor, window=signal.get_window(('kaiser', beta), 6))
#xd = xd[-len(xd) // 10:]
#xd = xd[-2 * len(xd) // 10:-len(xd) // 10]
fftlen = len(xd)
Xd = fft(xd)

Ld  = L / BWFactor;
fsd = fs / BWFactor;
F   = Fc + fsd / fftlen * np.arange(fftlen) - fsd / 2
ax1[1]. stem(F, np.abs(fftshift(Xd)) / Ld, linefmt='C1-.', markerfmt='C1s')
ax1[1].grid()
ax1[1].set_xlabel('Frequency (Hz)', fontsize=12)
ax1[1].set_ylabel('Magnitude', fontsize=12)
ax1[1].set_title('Zoom FFT Spectrum. Mixer Approach.', fontsize=12)
fig1.subplots_adjust(hspace=0.35)
{% endhighlight %}

### Result

The following result is the same as in [Zoom FFT](https://se.mathworks.com/help/dsp/examples/zoom-fft.html), but much faster.

{:center-img: style="text-align: center;"}
![zoom fft with the mixer approach](/images/zoom_fft_mixer_approach.png){:height="400px" width="509px"}
{:center-img}

