# Chapter 3: Introduction to Physical Layer - Practice Set Solutions

## 3.8.2 Questions

**Q3-1. What is the relationship between period and frequency?**

Period ($T$) and frequency ($f$) are inversely related to each other.

- $T = \frac{1}{f}$  
    
- $f = \frac{1}{T}$  
    

**Q3-2. What does the amplitude of a signal measure? What does the frequency of a signal measure? What does the phase of a signal measure?**

- **Amplitude:** Measures the value, strength, or energy of a signal (e.g., volts).
    
- **Frequency:** Measures the rate of change or the number of cycles per second (Hertz).
    
- **Phase:** Measures the position of the waveform relative to time zero (the status of the first cycle).
    

**Q3-3. How can a composite signal be decomposed into its individual frequencies?**

A composite signal can be decomposed into simple sine waves with different frequencies, amplitudes, and phases using **Fourier analysis**.

**Q3-4. Name three types of transmission impairment.**

1. Attenuation
    
2. Distortion
    
3. Noise
    

**Q3-5. Distinguish between baseband transmission and broadband transmission.**

- **Baseband:** Sending a digital signal over a channel without changing the digital signal to an analog signal (typically requires a low-pass channel).
    
- **Broadband:** Changing the digital signal to an analog signal (modulation) for transmission (typically uses a bandpass channel).
    

**Q3-6. Distinguish between a low-pass channel and a band-pass channel.**

- **Low-pass channel:** A channel with a bandwidth that starts from zero.
    
- **Band-pass channel:** A channel with a bandwidth that does not start from zero (it starts from a specific frequency $f_1 > 0$).
    

**Q3-7. What does the Nyquist theorem have to do with communications?**

The Nyquist theorem defines the theoretical maximum bit rate for a **noiseless** channel based on its bandwidth and the number of signal levels used.

**Q3-8. What does the Shannon capacity have to do with communications?**

The Shannon capacity defines the theoretical maximum data rate (capacity) for a **noisy** channel based on its bandwidth and the Signal-to-Noise Ratio (SNR).

**Q3-9. Why do optical signals used in fiber optic cables have a very short wavelength?**

Wavelength is inversely proportional to frequency ($\lambda = c/f$). Optical signals (light) have extremely high frequencies, which results in very short wavelengths.

**Q3-10. Can we say whether a signal is periodic or nonperiodic by just looking at its frequency domain plot? How?**

Yes.

- If the frequency domain plot shows **discrete spikes**, the signal is **periodic**.
    
- If the frequency domain plot shows a **continuous curve** (envelope), the signal is **nonperiodic**.
    

**Q3-11. Is the frequency domain plot of a voice signal discrete or continuous?**

It is **continuous** because a voice signal is a nonperiodic composite signal.

**Q3-12. Is the frequency domain plot of an alarm system discrete or continuous?**

It is usually **discrete**. Alarm systems typically produce periodic signals (repeating tones), which result in discrete frequency spikes.

**Q3-13. We send a voice signal from a microphone to a recorder. Is this baseband or broadband transmission?**

This is typically **baseband** transmission (sending the original analog signal without modulation to a higher frequency carrier).

**Q3-14. We send a digital signal from one station on a LAN to another station. Is this baseband or broadband transmission?**

This is typically **baseband** transmission. Most wired LANs (like standard Ethernet) use a dedicated channel to send digital signals directly.

**Q3-15. We modulate several voice signals and send them through the air. Is this baseband or broadband transmission?**

This is **broadband** transmission (using modulation to shift signals to different frequency bands).

## 3.8.3 Problems

**P3-1. Given the frequencies listed below, calculate the corresponding periods.**

Formula: $T = \frac{1}{f}$  

- **a. 24 Hz:** $T = 1 / 24 \approx \mathbf{0.0417 \text{ s}}$ (or 41.7 ms)
    
- **b. 8 MHz:** $T = 1 / 8,000,000 = \mathbf{0.125 \text{ } \mu\text{s}}$  
    
- **c. 140 KHz:** $T = 1 / 140,000 \approx \mathbf{7.14 \text{ } \mu\text{s}}$  
    

**P3-2. Given the following periods, calculate the corresponding frequencies.**

Formula: $f = \frac{1}{T}$  

- **a. 5 s:** $f = 1 / 5 = \mathbf{0.2 \text{ Hz}}$  
    
- **b. 12** $\mu$**s:** $f = 1 / 12 \times 10^{-6} \approx \mathbf{83.33 \text{ KHz}}$  
    
- **c. 220 ns:** $f = 1 / 220 \times 10^{-9} \approx \mathbf{4.55 \text{ MHz}}$  
    

**P3-3. What is the phase shift for the following?**

_Note: A standard sine wave_ $\sin(2\pi ft + \phi)$ _starts at 0 amplitude and increases._

- **a. A sine wave with the maximum amplitude at time zero:**
    
    $\sin(0 + \phi) = 1 \Rightarrow \phi = 90^\circ$ ($\pi/2$ rad).
    
- **b. A sine wave with maximum amplitude after 1/4 cycle:**
    
    This describes a standard sine wave (max at $90^\circ$). Shift = $\mathbf{0^\circ}$.
    
- **c. A sine wave with zero amplitude after 3/4 cycle and increasing:**
    
    A standard sine wave is at -1 (min) at 3/4 cycle ($270^\circ$). It is 0 and increasing at $0^\circ$ (or $360^\circ$). To have this condition occur at $270^\circ$, we must solve $\sin(270^\circ + \phi) = 0$ (slope positive).
    
    $270^\circ + \phi = 360^\circ \Rightarrow \phi = 90^\circ$.
    
    **Shift =** $90^\circ$ **(**$\pi/2$ **rad).**
    

**P3-4. What is the bandwidth of a signal that can be decomposed into five sine waves with frequencies at 0, 20, 50, 100, and 200 Hz?**

Bandwidth = $f_{high} - f_{low}$

$BW = 200 - 0 = \mathbf{200 \text{ Hz}}$  

**P3-5. A periodic composite signal with a bandwidth of 2000 Hz is composed of two sine waves. The first one has a frequency of 100 Hz with a maximum amplitude of 20 V; the second one has a maximum amplitude of 5 V. Draw the bandwidth.**

$BW = f_{high} - f_{low}$

$2000 = f_{high} - 100 \Rightarrow f_{high} = 2100 \text{ Hz}$

**The signal has components at 100 Hz and 2100 Hz.**

**P3-6. Which signal has a wider bandwidth, a sine wave with a frequency of 100 Hz or a sine wave with a frequency of 200 Hz?**

Technically, a simple pure sine wave has a bandwidth of **0** (single frequency). Therefore, neither has a "wider" bandwidth; they both have zero bandwidth.

**P3-7. What is the bit rate for each of the following signals?**

- **a. A signal in which 1 bit lasts 0.001 s:**
    
    Rate $= 1 / 0.001 = \mathbf{1000 \text{ bps}}$  
    
- **b. A signal in which 1 bit lasts 2 ms:**
    
    Rate $= 1 / 0.002 = \mathbf{500 \text{ bps}}$  
    
- **c. A signal in which 10 bits last 20** $\mu$**s:**
    
    10 bits = 20 $\mu$s $\rightarrow$ 1 bit = 2 $\mu$s.
    
    Rate $= 1 / 2 \times 10^{-6} = \mathbf{500 \text{ Kbps}}$  
    

**P3-8. A device is sending out data at the rate of 1000 bps.**

- **a. How long does it take to send out 10 bits?**
    
    $10 / 1000 = \mathbf{0.01 \text{ s}}$  
    
- **b. How long does it take to send out a single character (8 bits)?**
    
    $8 / 1000 = \mathbf{0.008 \text{ s}}$ (8 ms)
    
- **c. How long does it take to send a file of 100,000 characters?**
    
    Total bits $= 100,000 \times 8 = 800,000$ bits.
    
    Time $= 800,000 / 1000 = \mathbf{800 \text{ s}}$  
    

**P3-9. What is the bit rate for the signal in Figure 3.35?**

_Looking at the figure, the arrow labelled "16 ns" spans two full cycles of the wave._

Period ($T$) of 1 cycle $= 16 \text{ ns} / 2 = 8 \text{ ns}$.

Frequency $= 1 / 8 \text{ ns} = 125 \text{ MHz}$.

Assuming 2 bits per cycle (1 high, 1 low):

Bit Rate $= 2 \times 125 \text{ MHz} = \mathbf{250 \text{ Mbps}}$.

**P3-10. What is the frequency of the signal in Figure 3.36?**

_The arrow labelled "4 ms" spans 4 full cycles._

Period ($T$) $= 4 \text{ ms} / 4 = 1 \text{ ms}$.

Frequency $= 1 / 1 \text{ ms} = \mathbf{1 \text{ KHz}}$.

**P3-11. What is the bandwidth of the composite signal shown in Figure 3.37?**

_Assuming the figure shows a discrete spectrum range:_

Bandwidth = Highest Frequency - Lowest Frequency.

Based on the visual representation usually associated with this problem: If the range is 40 to 150 (approx), BW = 110 Hz. _Without clear numbers in the image, strictly:_ $f_{max} - f_{min}$_._

**P3-12. A periodic composite signal contains frequencies from 10 to 30 KHz, each with an amplitude of 10 V. Draw the frequency spectrum.**

Since it is **periodic**, the spectrum consists of **discrete spikes** at integer frequencies between 10 KHz and 30 KHz (e.g., 10, 11, ... 30), all with height 10 V.

**P3-13. A nonperiodic composite signal contains frequencies from 10 to 30 KHz...**

Since it is **nonperiodic**, the spectrum is a **continuous curve** (envelope) starting at 10 KHz and ending at 30 KHz.

**P3-14. A TV channel has a bandwidth of 6 MHz. If we send a digital signal using one channel, what are the data rates if we use one harmonic, three harmonics, and five harmonics?**

Using the baseband bandwidth formula roughly: $B = (N/2) \times \text{harmonics}$.

- **1 Harmonic:** $6 \text{ MHz} = N/2 \times 1 \Rightarrow N = \mathbf{12 \text{ Mbps}}$  
    
- **3 Harmonics:** $6 \text{ MHz} = N/2 \times 3 \Rightarrow N = 12/3 = \mathbf{4 \text{ Mbps}}$  
    
- **5 Harmonics:** $6 \text{ MHz} = N/2 \times 5 \Rightarrow N = 12/5 = \mathbf{2.4 \text{ Mbps}}$  
    

**P3-15. A signal travels from point A to point B. At point A, the signal power is 100 W. At point B, the power is 90 W. What is the attenuation in decibels?**

$dB = 10 \log_{10}(P_2 / P_1) = 10 \log_{10}(90 / 100) = 10 \log_{10}(0.9)$

$dB = 10(-0.0457) = \mathbf{-0.46 \text{ dB}}$  

**P3-16. The attenuation of a signal is -10 dB. What is the final signal power if it was originally 5 W?**

$-10 = 10 \log_{10}(P_2 / 5)$

$-1 = \log_{10}(P_2 / 5)$

$10^{-1} = P_2 / 5 \Rightarrow 0.1 = P_2 / 5$

$P_2 = \mathbf{0.5 \text{ W}}$  

**P3-17. A signal has passed through three cascaded amplifiers, each with a 4 dB gain. What is the total gain? How much is the signal amplified?**

Total Gain (dB) $= 4 + 4 + 4 = \mathbf{12 \text{ dB}}$.

Amplification factor: $12 = 10 \log_{10}(Ratio) \Rightarrow 1.2 = \log_{10}(Ratio)$

Ratio $= 10^{1.2} \approx \mathbf{15.85 \text{ times}}$  

**P3-18. If the bandwidth of the channel is 5 Kbps, how long does it take to send a frame of 100,000 bits out of this device?**

Time $= 100,000 \text{ bits} / 5,000 \text{ bps} = \mathbf{20 \text{ s}}$  

**P3-19. The light of the sun takes approximately eight minutes to reach the earth. What is the distance between the sun and the earth?**

Time $= 8 \text{ min} \times 60 = 480 \text{ s}$. Speed $c = 3 \times 10^8 \text{ m/s}$.

Distance $= 480 \times 3 \times 10^8 = 1.44 \times 10^{11} \text{ m} = \mathbf{144 \text{ million km}}$  

**P3-20. A signal has a wavelength of 1** $\mu$**m in air. How far can the front of the wave travel during 1000 periods?**

Distance $= 1000 \times \text{wavelength} = 1000 \times 1 \mu\text{m} = 1000 \mu\text{m} = \mathbf{1 \text{ mm}}$  

**P3-21. A line has a signal-to-noise ratio of 1000 and a bandwidth of 4000 KHz. What is the maximum data rate supported by this line?**

Shannon Capacity: $C = B \log_2(1 + SNR)$

$C = 4,000,000 \times \log_2(1 + 1000) \approx 4 \text{ MHz} \times 9.97$

$C \approx \mathbf{39.86 \text{ Mbps}}$ (Note: B is in KHz in question but usually phone lines are 4kHz. If B=4000 KHz = 4 MHz, answer is ~40 Mbps. If B=4000 Hz, answer is ~40 Kbps). _Assuming 4000 KHz as written._

**P3-22. We measure the performance of a telephone line (4 KHz of bandwidth). When the signal is 10 V, the noise is 5 mV. What is the maximum data rate supported by this telephone line?**

1. Calculate SNR (Power ratio $\propto$ Voltage squared):
    
    Ratio of Volts $= 10 \text{ V} / 0.005 \text{ V} = 2000$.
    
    SNR $= 2000^2 = 4,000,000$.
    
2. Calculate Capacity:
    
    $C = 4000 \log_2(1 + 4,000,000) \approx 4000 \times 21.93$
    
    $C \approx \mathbf{87.7 \text{ Kbps}}$  
    

**P3-23. A file contains 2 million bytes. How long does it take to download this file using a 56-Kbps channel? 1-Mbps channel?**

File size $= 2 \times 10^6 \times 8 = 16,000,000$ bits.

- **56-Kbps:** $16,000,000 / 56,000 \approx \mathbf{285.7 \text{ s}}$  
    
- **1-Mbps:** $16,000,000 / 1,000,000 = \mathbf{16 \text{ s}}$  
    

**P3-24. A computer monitor has a resolution of 1200 by 1000 pixels. If each pixel uses 1024 colors, how many bits are needed to send the complete contents of a screen?**

Bits per pixel $= \log_2(1024) = 10$ bits.

Total bits $= (1200 \times 1000) \times 10 = 1,200,000 \times 10 = \mathbf{12,000,000 \text{ bits}}$ (12 Megabits).

**P3-25. A signal with 200 milliwatts power passes through 10 devices, each with an average noise of 2 microwatts. What is the SNR? What is the** $SNR_{dB}$**?**

Total Noise $= 10 \times 2 \mu\text{W} = 20 \mu\text{W}$.

Signal $= 200 \text{ mW} = 200,000 \mu\text{W}$.

SNR $= 200,000 / 20 = \mathbf{10,000}$.

$SNR_{dB} = 10 \log_{10}(10,000) = \mathbf{40 \text{ dB}}$.

**P3-26. If the peak voltage value of a signal is 20 times the peak voltage value of the noise, what is the SNR? What is the** $SNR_{dB}$**?**

SNR $= (V_{signal} / V_{noise})^2 = 20^2 = \mathbf{400}$.

$SNR_{dB} = 10 \log_{10}(400) \approx \mathbf{26 \text{ dB}}$.

**P3-27. What is the theoretical capacity of a channel in each of the following cases?**

Formula: $C = B \log_2(1 + SNR)$  

- **a. BW: 20 KHz,** $SNR_{dB}=40$**:**
    
    $SNR = 10^{40/10} = 10,000$.
    
    $C = 20 \text{ KHz} \times \log_2(10001) \approx 20 \times 13.29 = \mathbf{265.8 \text{ Kbps}}$.
    
- **b. BW: 200 KHz,** $SNR_{dB}=4$**:**
    
    $SNR = 10^{0.4} \approx 2.51$.
    
    $C = 200 \text{ KHz} \times \log_2(3.51) \approx 200 \times 1.81 = \mathbf{362 \text{ Kbps}}$.
    
- **c. BW: 1 MHz,** $SNR_{dB}=20$**:**
    
    $SNR = 10^2 = 100$.
    
    $C = 1 \text{ MHz} \times \log_2(101) \approx 1 \times 6.66 = \mathbf{6.66 \text{ Mbps}}$.
    

**P3-28. We need to upgrade a channel to a higher bandwidth. Answer the following questions:**

- **a. How is the rate improved if we double the bandwidth?**
    
    The capacity is **doubled** ($C$ is directly proportional to $B$).
    
- **b. How is the rate improved if we double the SNR?**
    
    The capacity increases slightly (logarithmically), but is **not doubled**.
    

**P3-29. We have a channel with 4 KHz bandwidth. If we want to send data at 100 Kbps, what is the minimum** $SNR_{dB}$**? What is the SNR?**

$100,000 = 4000 \log_2(1 + SNR)$

$25 = \log_2(1 + SNR)$

$1 + SNR = 2^{25}$

SNR $\approx \mathbf{33,554,431}$

$SNR_{dB} = 10 \log_{10}(33,554,431) \approx \mathbf{75.2 \text{ dB}}$  

**P3-30. What is the transmission time of a packet sent by a station if the length of the packet is 1 million bytes and the bandwidth of the channel is 200 Kbps?**

Packet $= 1,000,000 \times 8 = 8,000,000$ bits.

Time $= 8,000,000 / 200,000 = \mathbf{40 \text{ s}}$.

**P3-31. What is the length of a bit in a channel with a propagation speed of** $2 \times 10^8$ **m/s if the channel bandwidth is...**

Length = Prop Speed $\times$ Bit Duration (where Duration = 1/Bandwidth).

- **a. 1 Mbps:** $2 \times 10^8 \times 10^{-6} = \mathbf{200 \text{ m}}$  
    
- **b. 10 Mbps:** $2 \times 10^8 \times 10^{-7} = \mathbf{20 \text{ m}}$  
    
- **c. 100 Mbps:** $2 \times 10^8 \times 10^{-8} = \mathbf{2 \text{ m}}$  
    

**P3-32. How many bits can fit on a link with a 2 ms delay if the bandwidth of the link is...**

Formula: Bandwidth $\times$ Delay

- **a. 1 Mbps:** $10^6 \times 0.002 = \mathbf{2000 \text{ bits}}$  
    
- **b. 10 Mbps:** $10^7 \times 0.002 = \mathbf{20,000 \text{ bits}}$  
    
- **c. 100 Mbps:** $10^8 \times 0.002 = \mathbf{200,000 \text{ bits}}$  
    

**P3-33. What is the total delay (latency) for a frame of size 5 million bits...**

Parameters: Frame = 5 Mb, Link = 2000 km, Speed = $2 \times 10^8$ m/s, BW = 5 Mbps, 10 Routers (2 $\mu$s queue, 1 $\mu$s process each).

1. **Transmission Time:** $5 \text{ Mb} / 5 \text{ Mbps} = \mathbf{1 \text{ s}}$  
    
2. **Propagation Time:** $2,000,000 \text{ m} / (2 \times 10^8 \text{ m/s}) = \mathbf{0.01 \text{ s}}$ (10 ms)
    
3. **Queuing Time:** $10 \times 2 \mu\text{s} = 20 \mu\text{s} = \mathbf{0.00002 \text{ s}}$  
    
4. **Processing Time:** $10 \times 1 \mu\text{s} = 10 \mu\text{s} = \mathbf{0.00001 \text{ s}}$  
    

**Total Latency** $= 1 + 0.01 + 0.00002 + 0.00001 = \mathbf{1.01003 \text{ s}}$

_Dominant component: Transmission time._