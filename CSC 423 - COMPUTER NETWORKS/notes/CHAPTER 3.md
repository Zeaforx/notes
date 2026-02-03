# Chapter 3: Introduction to Physical Layer

### Student Resource & Study Guide

This guide provides a comprehensive technical overview of the Physical Layer, focusing on data transmission, signal analysis, impairment, and performance metrics. It combines theoretical frameworks with mathematical derivations to explain how data moves across network connections.

## 3.1 Data and Signals

The physical layer's primary function is moving data in the form of electromagnetic signals across a transmission medium. It is critical to distinguish between the _data_ (the entity conveying meaning) and the _signals_ (the electric or electromagnetic representation of data).

### 3.1.1 Analog and Digital Data

Data can be represented in two fundamental forms:

- **Analog Data:** Information that is continuous. Analog data takes on continuous values.
    
    - **[Real World Example]:** An analog clock with hour, minute, and second hands provides information in a continuous flow. Human voice is another example; when someone speaks, a continuous analog wave is created in the air.
        
- **Digital Data:** Information that has discrete states. Digital data takes on discrete values.
    
    - **[Real World Example]:** A digital clock that changes suddenly from 8:05 to 8:06. Data stored in computer memory (0s and 1s) is digital.
        

### 3.1.2 Analog and Digital Signals

Signals, like the data they represent, can be analog or digital:

- **Analog Signal:** Has infinitely many levels of intensity over a period of time. As the wave moves from value A to value B, it passes through and includes an infinite number of values along its path.
    
- **Digital Signal:** Can have only a limited number of defined values. While often as simple as 1 and 0, a digital signal can have more than two levels (e.g., 4 or 8 levels).
    
    ![[Pasted image 20260202100351.png]]

### 3.1.3 Periodic and Nonperiodic

Both analog and digital signals can exist in two forms:

1. **Periodic Signal:** Completes a pattern within a measurable time frame, called a **period**, and repeats that pattern over subsequent identical periods. The completion of one full pattern is called a **cycle**.
    
2. **Nonperiodic (Aperiodic) Signal:** Changes without exhibiting a pattern or cycle that repeats over time.
    

> **Note:** In data communications, we commonly use **periodic analog signals** and **nonperiodic digital signals**.

## 3.2 Periodic Analog Signals

Periodic analog signals can be classified as simple or composite. The most fundamental form is the **sine wave**.

### 3.2.1 Sine Wave

A sine wave is a simple periodic analog signal that cannot be decomposed into simpler signals. It is fully described by three parameters:

1. **Peak Amplitude:** The absolute value of its highest intensity, proportional to the energy it carries. For electric signals, it is normally measured in volts.
    
2. **Frequency (**$f$**):** The number of periods (cycles) in 1 second. Measured in **Hertz (Hz)**.
    
3. **Period (**$T$**):** The amount of time, in seconds, a signal needs to complete 1 cycle.
    
![[Pasted image 20260202100639.png]]

**Mathematical Relationship:**

Period and frequency are inverses of each other.

  

$$f = \frac{1}{T} \quad \text{and} \quad T = \frac{1}{f}$$

**Frequency Spectrum:**

- If a signal does not change at all, its frequency is **zero**.
    
- If a signal changes instantaneously, its frequency is **infinite**.
    
![[Pasted image 20260202100722.png]]

### 3.2.2 Phase

**Phase** (or phase shift) describes the position of the waveform relative to time 0. It indicates the status of the first cycle.

**Measurement:**

Phase is measured in degrees or radians:

  

$$360^{\circ} = 2\pi \text{ rad}$$$$1^{\circ} = \frac{2\pi}{360} \text{ rad}$$

**Common Shifts:**

- **0 degrees:** Starts at 0 amplitude, increasing.
    
- **90 degrees:** Starts at peak amplitude, decreasing. ($1/4$ cycle shift).
    
- **180 degrees:** Starts at 0 amplitude, decreasing. ($1/2$ cycle shift).
    
![[Pasted image 20260202101003.png]]

### 3.2.3 Wavelength

**Wavelength (**$\lambda$**)** binds the period or frequency of a simple sine wave to the propagation speed of the medium. It represents the distance a simple signal can travel in one period.

**Formula:**

  

$$\lambda = c \times T \quad \text{or} \quad \lambda = \frac{c}{f}$$

- $\lambda$: Wavelength (usually in micrometers, $\mu m$)
    
- $c$: Propagation speed (speed of light). In a vacuum, $c = 3 \times 10^8 \text{ m/s}$.
    
- $f$: Frequency
    
![[Pasted image 20260202101358.png]]

> **Context:** Wavelength is frequency-dependent _and_ medium-dependent. Light travels slower in a cable than in a vacuum, resulting in a shorter wavelength inside the cable.

### 3.2.4 Time and Frequency Domains

To analyze signals, we use two different plots:

1. **Time-Domain Plot:** Shows changes in signal amplitude with respect to **time**. Phase is not explicitly shown.
    
2. **Frequency-Domain Plot:** Shows the relationship between peak amplitude and **frequency**.
    
    - A complete sine wave is represented by a single spike in the frequency domain.
        
    - The height of the spike represents peak amplitude; the position represents frequency.
	![[Pasted image 20260202101513.png]]
	![[Pasted image 20260202102006.png]]

### 3.2.5 Composite Signals

A single-frequency sine wave is not useful for data communications because it carries no information. We use **Composite Signals**, which are made of many simple sine waves.

**Fourier Analysis:**

In the early 1900s, Jean-Baptiste Fourier showed that any composite signal is a combination of simple sine waves with different frequencies, amplitudes, and phases.

- **Periodic Composite Signal:** Decomposes into a series of signals with **discrete frequencies** (e.g., $f$, $3f$, $9f$).
    
    - _Fundamental Frequency:_ The frequency of the composite signal itself ($f$).
        
    - _Harmonics:_ Integer multiples of the fundamental frequency (e.g., $3f$ is the third harmonic).
        
- **Nonperiodic Composite Signal:** Decomposes into a combination of an infinite number of sine waves with **continuous frequencies** (real values).
    

### 3.2.6 Bandwidth

The **Bandwidth** of a composite signal is the difference between the highest and the lowest frequencies contained in that signal.

**Formula:**

  

$$B = f_{highest} - f_{lowest}$$

- If a composite signal contains frequencies between 1000 Hz and 5000 Hz, the bandwidth is $5000 - 1000 = 4000 \text{ Hz}$.
![[Pasted image 20260202103346.png]]
    

## 3.3 Digital Signals

Information can also be represented by digital signals (e.g., a 1 encoded as positive voltage, a 0 as zero voltage).
![[Pasted image 20260202104050.png]]

### 3.3.1 Bit Rate

Most digital signals are nonperiodic. Instead of frequency, we use **Bit Rate**.

- **Definition:** The number of bits sent in 1 second, expressed in **bits per second (bps)**.
    

### 3.3.2 Bit Length

Similar to wavelength for analog signals, **Bit Length** is the distance one bit occupies on the transmission medium.

**Formula:**

  

$$\text{Bit Length} = \text{Propagation Speed} \times \text{Bit Duration}$$

### 3.3.3 Digital Signal as a Composite Analog Signal

Mathematically, a digital signal is a composite analog signal with an **infinite bandwidth**.

- Vertical lines in a digital signal imply a frequency of infinity.
    
- Horizontal lines imply a frequency of zero.
    
- Fourier analysis of a digital signal reveals an infinite spectrum of frequencies.
	
    ![[Pasted image 20260202105114.png]]

### 3.3.4 Transmission of Digital Signals

There are two primary approaches to transmitting digital signals:

#### 1. Baseband Transmission

**Definition:** Sending a digital signal over a channel without changing the digital signal to an analog signal.

- **Requirement:** Requires a **Low-Pass Channel** (a channel with a bandwidth that starts from zero).
    
- **Bandwidth Approximation:** To transmit a digital signal with bit rate $N$, we need bandwidth.
    
    - _Rough Approximation:_ Using the first harmonic ($N/2$).
        
    - _Better Approximation:_ Using the first, third, and fifth harmonics ($5N/2$).
        
    - **Rule:** In baseband transmission, the required bandwidth is proportional to the bit rate.
        

#### 2. Broadband Transmission (Modulation)

**Definition:** Changing the digital signal to an analog signal for transmission.

- **Requirement:** Uses a **Bandpass Channel** (a channel where bandwidth does not start from zero).
    
- **Method:** Modulation allows the use of channels more available than low-pass channels (e.g., sending digital data over telephone subscriber lines designed for voice).
    

## 3.4 Transmission Impairment

Signals travel through imperfect media, causing the signal at the receiver to differ from the signal at the sender.

### 3.4.1 Attenuation

**Definition:** Loss of energy. When a signal travels through a medium, it loses energy to overcome resistance (converted to heat). Amplifiers are used to compensate.
![[Pasted image 20260202105555.png]]

**Decibel (dB):**

The unit used to measure relative strengths of two signals.

  

$$dB = 10 \log_{10} \frac{P_2}{P_1}$$

- $P_1$: Power at the input.
    
- $P_2$: Power at the output.
    
- **-3 dB:** A loss of 3 dB is equivalent to losing one-half of the power.
    

### 3.4.2 Distortion

**Definition:** The signal changes its form or shape.

- **Cause:** Composite signals are made of different frequencies. Each frequency component has its own propagation speed. Differences in delay create phase shifts, altering the composite shape upon arrival.
    ![[Pasted image 20260202110111.png]]
    

### 3.4.3 Noise

**Definition:** External energy that corrupts the signal.

- **Thermal Noise:** Random motion of electrons.
    
- **Induced Noise:** From motors and appliances.
    
- **Crosstalk:** Effect of one wire on another.
    
- **Impulse Noise:** Spikes from power lines or lightning.
    
    ![[Pasted image 20260202110226.png]]

**Signal-to-Noise Ratio (SNR):**

The ratio of signal power to noise power.

  

$$SNR = \frac{\text{Average Signal Power}}{\text{Average Noise Power}}$$$$SNR_{dB} = 10 \log_{10} SNR$$

## 3.5 Data Rate Limits

How fast can we send data? This depends on available bandwidth, signal levels, and channel quality.

### 3.5.1 Noiseless Channel: Nyquist Bit Rate

For a theoretically noiseless channel, the limit is defined by the Nyquist formula.

**Formula:**

  

$$\text{BitRate} = 2 \times \text{Bandwidth} \times \log_2 L$$

- **Bandwidth:** Bandwidth of the channel.
    
- **L:** Number of signal levels used to represent data.
    
- **Implication:** We can increase the bit rate by increasing signal levels, but this increases the burden on the receiver to distinguish levels, reducing reliability.
    

### 3.5.2 Noisy Channel: Shannon Capacity

For real, noisy channels, the limit is defined by the Shannon Capacity.

**Formula:**

  

$$\text{Capacity} = \text{Bandwidth} \times \log_2 (1 + SNR)$$

- **Capacity:** The theoretical highest data rate in bits per second.
    
- **Note:** The formula does _not_ involve signal levels. No matter how many levels are used, we cannot exceed the channel capacity.
    

### 3.5.3 Using Both Limits

In practice, both methods are used.

1. Use **Shannon Capacity** to find the upper limit of the channel.
    
2. Use **Nyquist Bit Rate** to determine how many signal levels ($L$) are needed to achieve a specific data rate (usually chosen to be lower than the Shannon limit for reliability).
    

## 3.6 Performance

### 3.6.1 Bandwidth

The term bandwidth is used in two contexts:

1. **Bandwidth in Hertz:** The range of frequencies a channel can pass.
    
2. **Bandwidth in Bits per Second:** The speed of bit transmission in a channel or link.
    

### 3.6.2 Throughput

**Definition:** A measure of how fast we can _actually_ send data through a network.

- Throughput is always less than the bandwidth.
    
- **[Real World Example]:** A highway may be designed for 1000 cars/minute (Bandwidth), but due to congestion, only 100 cars/minute can pass (Throughput).
    

### 3.6.3 Latency (Delay)

**Latency:** How long it takes for an entire message to arrive at the destination from the time the first bit is sent. It comprises four components:

$$\text{Latency} = \text{Propagation time} + \text{Transmission time} + \text{Queuing time} + \text{Processing delay}$$

1. **Propagation Time:** Time for a bit to travel from source to destination.
    
      
    
    $$\text{Propagation Time} = \frac{\text{Distance}}{\text{Propagation Speed}}$$
2. **Transmission Time:** Time to push the message onto the medium.
    
      
    
    $$\text{Transmission Time} = \frac{\text{Message Size}}{\text{Bandwidth}}$$
3. **Queuing Time:** Time spent waiting in intermediate devices before processing.
    
4. **Processing Delay:** Time for routers/switches to process the header and determine routing.
    

### 3.6.4 Bandwidth-Delay Product

**Definition:** The number of bits that can fill the link.

  

$$\text{Volume} = \text{Bandwidth} \times \text{Delay}$$

- This defines the maximum number of bits that can be in transition at any given time.
    
- Important for utilizing the link's maximum capability (burst sizing).
    

### 3.6.5 Jitter

**Definition:** Variation in the packet delay.

- If different packets encounter different delays, the application (especially audio/video) endures jitter.
    

## 3.7 End-Chapter Materials & Practice Support

### Summary

- **Data vs. Signals:** Data must be transformed into signals (analog or digital).
    
- **Fourier Analysis:** Any composite signal is a combination of simple sine waves.
    
- **Transmission:** Baseband requires low-pass channels; Broadband uses modulation for bandpass channels.
    
- **Limits:** Nyquist defines limits for noiseless channels; Shannon defines limits for noisy channels.
    
- **Performance:** Measured by bandwidth, throughput, latency (delay), and jitter.
    

### 3.8 Practice Set Overview

The chapter includes calculation exercises covering:

1. **Period/Frequency conversions:** ($T=1/f$).
    
2. **Bandwidth calculation:** ($f_{high} - f_{low}$).
    
3. **Bit Rate calculation:** Based on signal duration.
    
4. **Decibel/Power calculation:** ($dB = 10 \log_{10}(P_2/P_1)$).
    
5. **Nyquist and Shannon Limits:** Calculating max bit rates or required signal levels.
    
6. **Latency components:** Calculating propagation vs. transmission time.