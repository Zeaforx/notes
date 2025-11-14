# Chapter 3: Data and Signals

**Core Concept:** To be transmitted, data must be transformed into electromagnetic signals. This chapter explores the nature of data (analog vs. digital) and the signals that carry them.

## 3-1: Analog and Digital

This section defines the fundamental forms of data and signals.

### Data: Analog vs. Digital

- **Analog Data:** Refers to information that is continuous. It takes on continuous values within a range.
    
    - **Example:** A human voice, temperature readings, or a sound wave.
        
- **Digital Data:** Refers to information that has discrete states. It takes on discrete, non-continuous values.
    
    - **Example:** The text in this document, where each character is represented by a specific binary code.
        

### Signals: Analog vs. Digital

- **Analog Signals:** A signal that can have an infinite number of values within a specific range.
    
    - **Characteristics:** A continuous, smoothly varying wave.
        
- **Digital Signals:** A signal that can have only a limited number of defined values.
    
    - **Characteristics:** A series of discrete pulses, often represented as 1s and 0s (e.g., a 1 represented by a positive voltage and a 0 by zero voltage).
- ![[Pasted image 20251025123218.png]]
        

### Periodic vs. Nonperiodic Signals

In data communications, we commonly use periodic analog signals (like sine waves) and nonperiodic digital signals (like a stream of data bits).

- **Periodic Signal:** A signal that completes a pattern within a measurable time frame (called a period) and repeats that same pattern over and over.
    
- **Nonperiodic Signal:** A signal that changes without exhibiting a repeating pattern.
    

## 3-2: Periodic Analog Signals

Periodic analog signals can be classified as simple or composite.

- **Simple Periodic Signal:** A **sine wave**. It is the fundamental building block of analog signals and cannot be decomposed into simpler signals.
    
- **Composite Periodic Signal:** A signal composed of multiple sine waves added together.
    

### The Sine Wave

A simple sine wave is characterized by three key properties:

1. **Amplitude (Peak Amplitude):** The absolute value of the signal's highest intensity. It represents the "strength" of the signal.
    
2. **Frequency:** The rate of change with respect to time. It is the number of periods (cycles) a signal completes in one second, measured in Hertz (Hz).
    
    - High frequency means change in a short span of time.
        
    - Low frequency means change over a long span of time.
        
    - If a signal does not change, its frequency is zero.
        
3. **Phase:** Describes the position of the waveform relative to time 0. It indicates the "shift" of the wave.
	
	![[Pasted image 20251025125628.png]]
    

Frequency and Period:

Frequency ($f$) and Period ($T$) are the inverse of each other.

$$f = 1/T \quad \text{and} \quad T = 1/f$$

- **Period (T):** The time it takes for one complete cycle of the signal.
    
- **Frequency (f):** The number of cycles per second.
	
- ![[Pasted image 20251025124558.png]]
	
- ![[Pasted image 20251025124639.png]]
	
- ![[Pasted image 20251025124716.png]]
	
- Frequency is a measure of **how fast something changes**:

	- **No Change** (a flat line) = **0 Hz**
	    
	- **Infinitely Fast Change** (a vertical line) = **Infinite Frequency**

**Example 3.3:** The power we use at home has a frequency of 60 Hz.

- **Calculation:** 
$$
  T = \frac{1}{f} = \frac{1}{60 \text{ Hz}} = 0.0166 \text{ s} \text{ OR } 1.66 \text{ ms}
$$

**Example 3.6:** A sine wave is offset by 1/6 of a cycle. What is its phase in degrees?

- **Solution:** A complete cycle is $360^{\circ}$.
    
- **Calculation:** $\text{Phase} = (1/6) \times 360^{\circ} = 60^{\circ}$.
    

### Time vs. Frequency Domain

- **Time Domain:** A graph showing a signal's amplitude as it changes over time.
    
- **Frequency Domain:** A graph showing a signal's amplitude with respect to its frequency. A complete sine wave in the time domain is represented by a single spike in the frequency domain. This is a more compact and useful way to view signals.
	
- ![[Pasted image 20251025130349.png]]
- The frequency domain is more compact and useful when we are dealing with more than one sine wave. For example, Figure 3.8 shows three sine waves, each with different amplitude and frequency. All can be represented by three spikes in the frequency domain.
- ![[Pasted image 20251025130316.png]]
    

### Composite Signals and Bandwidth

- **Composite Signal:** A signal made of many simple sine waves. A single-frequency sine wave is not useful in data communications. we need to send a composite signal, a signal made of many simple sine waves.
    
- **Fourier Analysis:** A mathematical tool showing that any composite signal is a combination of simple sine waves with different frequencies, amplitudes, and phases.
    
    - **Periodic Composite Signal:** Decomposes into a series of sine waves with _discrete frequencies_ (harmonics).
    - ![[Pasted image 20251025130937.png]]
        
    - **Nonperiodic Composite Signal:** Decomposes into a combination of sine waves with _continuous frequencies_.
    - ![[Pasted image 20251025131003.png]]
        
- **Bandwidth (BW):** The bandwidth of a composite signal is the difference between the highest and the lowest frequencies contained in that signal.
- ![[Pasted image 20251025131056.png]]
    

**Example 3.10:** A signal is decomposed into 5 sine waves with frequencies of 100, 300, 500, 700, and 900 Hz. What is its bandwidth?

- **Solution:** Let $f_h$ be the highest frequency (900 Hz) and $f_l$ be the lowest (100 Hz).
    
- **Calculation:** $\text{BW} = f_h - f_l = 900 - 100 = 800 \text{ Hz}$.
    

## 3-3: Digital Signals

Information can also be represented by a digital signal.

### Levels and Bits

- A digital signal can have more than two levels.
    
- We can send more than one bit for each level.
    
- The number of bits ($N$) sent per level depends on the number of levels ($L$):
    
    $$L = 2^N \quad \text{or} \quad N = \log_2(L)$$
- ![[Pasted image 20251025131616.png]]

**Example 3.16:** A digital signal has 8 levels. How many bits are needed per level?

- **Calculation:** $\text{Bits per level} = \log_2(8) = 3$. Each signal level represents 3 bits.
    

**Example 3.17:** A digital signal has 9 levels. How many bits are needed per level?

- **Calculation:** $\text{Bits per level} = \log_2(9) \approx 3.17$.
    
- **Realistic Answer:** This is not realistic. The number of bits must be an integer. We must use **4 bits** to represent all 9 levels (which would allow for up to $2^4 = 16$ levels).
    

### Bit Rate and Bit Length

- **Bit Rate:** The number of bits sent in one second (measured in bits per second, bps).
    
- **Bit Length:** The distance one bit occupies on the transmission medium.
    

**Example 3.19 (Digitizing Voice):** A 4-kHz analog voice signal is digitized. We must sample at twice the highest frequency (Nyquist theorem), and each sample requires 8 bits.

- **Calculation:** $\text{Bit Rate} = (2 \times 4000 \text{ samples/sec}) \times (8 \text{ bits/sample}) = 64,000 \text{ bps or 64 kbps}$.
    

### Transmission of Digital Signals

A digital signal is a composite analog signal with an infinite bandwidth. How we transmit it depends on the channel:

1. **Baseband Transmission (Low-Pass Channel):**
    
    - Sends the digital signal directly without converting it to analog.
        
    - This requires a **low-pass channel** with an infinite or very wide bandwidth. A low-pass channel is one that passes frequencies from 0 up to a certain cutoff.
        
    - In baseband transmission, the required bandwidth is proportional to the bit rate. To send bits faster, you need more bandwidth.
        
    - **Example:** A wired LAN (Local Area Network) uses a dedicated channel for communication.
    - ![[Pasted image 20251025132045.png]]
    - ![[Pasted image 20251025132151.png]]
        
2. **Broadband Transmission (Bandpass Channel):**
    
    - If the channel is a **bandpass channel** (one that passes a range of frequencies, but not from 0), we cannot send the digital signal directly.
        
    - We must **convert the digital signal to an analog signal** for transmission. This process is called **modulation**.
        
    - **Example:** A **modem** (modulator-demodulator) converts computer data for sending over a telephone line, which is a bandpass channel.
        

## 3-4: Transmission Impairment

Signals travel through imperfect transmission media. This "imperfection" causes signal impairment, meaning the signal at the end is not the same as the signal at the beginning.

The three main causes of impairment are:

1. **Attenuation**
    
2. **Distortion**
    
3. **Noise**
    

### Attenuation

- **Definition:** Attenuation means a loss of energy. The signal loses strength as it travels through the medium.
	
- ![[Pasted image 20251025132315.png]]
    
- **Measurement:** We use the **decibel (dB)** to measure the change in signal strength. The decibel is logarithmic, so decibel numbers can be added or subtracted when they occur in a series (cascading).
    
- **Formula:** $\text{dB} = 10 \log_{10}(P_2 / P_1)$, where $P_1$ is the starting power and $P_2$ is the ending power.
    
    - **Negative dB:** Represents a loss (attenuation).
        
    - **Positive dB:** Represents a gain (amplification).
        

**Example 3.26 (Loss):** A signal's power is reduced to one-half ($P_2 = 0.5 P_1$).

- **Calculation:** $\text{dB} = 10 \log_{10}(0.5 \times P_1 / P_1) = 10 \log_{10}(0.5) \approx -3 \text{ dB}$.
    

**Example 3.27 (Gain):** A signal passes through an amplifier, and its power increases 10 times ($P_2 = 10 P_1$).

- **Calculation:** $\text{dB} = 10 \log_{10}(10 \times P_1 / P_1) = 10 \log_{10}(10) = 10 \text{ dB}$.
    

### Distortion

- **Definition:** Distortion means the signal changes its shape or form.
    
- **Cause:** This occurs in composite signals where different frequency components travel at different speeds through the medium. Some frequencies arrive later than others, changing the overall shape of the signal.
	
- ![[Pasted image 20251025132428.png]]
    

### Noise

- **Definition:** Noise is random, unwanted energy that corrupts the signal.
    
- **Types:**
    
    - **Thermal Noise:** Random motion of electrons, unavoidable.
        
    - **Induced Noise:** From external sources like motors or appliances.
        
    - **Crosstalk:** Interference from an adjacent signal.
        
- **Signal-to-Noise Ratio (SNR):** The ratio of the average signal power to the average noise power. A high SNR means a clean, usable signal; a low SNR means a noisy, corrupted signal.
    
    - **Formula:** $\text{SNR} = \text{Average Signal Power} / \text{Average Noise Power}$  
        
    - **Decibels:** $\text{SNR}_{\text{dB}} = 10 \log_{10}(\text{SNR})$  
        

## 3-5: Data Rate Limits

How fast can we send data (in bps)? This depends on three factors:

1. The bandwidth available
    
2. The number of signal levels we use
    
3. The quality of the channel (the level of noise)
    

### Noiseless Channel: Nyquist Bit Rate

For a noiseless channel, the Nyquist bit rate formula defines the theoretical maximum bit rate.

- **Formula:** $\text{Maximum Bit Rate} = 2 \times \text{Bandwidth} \times \log_2(L)$  
    
    - $L$ is the number of signal levels.
        

**Example 3.34:** A noiseless channel has a bandwidth of 3000 Hz and uses two signal levels (L=2).

- **Calculation:** $\text{Bit Rate} = 2 \times 3000 \times \log_2(2) = 2 \times 3000 \times 1 = 6000 \text{ bps (6 kbps)}$.
    

**Example 3.35:** The same channel now uses four signal levels (L=4).

- **Calculation:** $\text{Bit Rate} = 2 \times 3000 \times \log_2(4) = 2 \times 3000 \times 2 = 12,000 \text{ bps (12 kbps)}$.
    

### Noisy Channel: Shannon Capacity

In the real world, all channels have noise. The Shannon capacity gives the theoretical highest data rate (the "capacity") of a noisy channel.

- **Formula:** $\text{Capacity} = \text{Bandwidth} \times \log_2(1 + \text{SNR})$  
    
    - Note: This formula does not depend on the number of levels. It defines the _upper limit_ of the channel.
        

**Example 3.38:** A telephone line has a bandwidth of 3000 Hz and an $\text{SNR}$ of 3162.

- **Calculation:** $\text{Capacity} = 3000 \times \log_2(1 + 3162) = 3000 \times \log_2(3163)$  
    
    - $\text{Capacity} \approx 3000 \times 11.62 \approx 34,860 \text{ bps (34.86 kbps)}$.
        
- This is the _theoretical maximum_ bit rate for this telephone line.
    

### Using Both Limits

We use both formulas together:

1. **Shannon's formula** gives the upper limit (the channel's capacity).
    
2. **Nyquist's formula** tells us how many signal levels ($L$) we need to achieve a specific practical bit rate (which must be _below_ the Shannon capacity).
    

**Example 3.41:** A channel has a 1 MHz bandwidth and an $\text{SNR}$ of 63. What are the appropriate bit rate and signal level?

- **1. Find Shannon Capacity (Upper Limit):**
    
    - $C = 1,000,000 \times \log_2(1 + 63) = 1,000,000 \times \log_2(64)$  
        
    - $C = 1,000,000 \times 6 = 6 \text{ Mbps}$.
        
    - This is the theoretical maximum. We must choose a practical rate _lower_ than this, for example, 4 Mbps.
        
- **2. Find Signal Levels (Nyquist) for 4 Mbps:**
    
    - $4,000,000 \text{ (bps)} = 2 \times 1,000,000 \text{ (Hz)} \times \log_2(L)$  
        
    - $4,000,000 = 2,000,000 \times \log_2(L)$  
        
    - $2 = \log_2(L)$  
        
    - $L = 2^2 = 4$  
        
- **Answer:** To achieve a practical rate of 4 Mbps, we should use 4 signal levels.
    

## 3-6: Performance

This section covers the practical metrics of network performance.

### Bandwidth vs. Throughput

- **Bandwidth:** The _potential_ capacity of a link (measured in bps).
    
- **Throughput:** The _actual_ measure of how fast data can be sent (measured in bps). Throughput is often much lower than the bandwidth.
    

**Example 3.44:** A 10 Mbps network passes 12,000 frames/minute, and each frame has 10,000 bits. What is the throughput?

- **1. Bits per second:** $(12,000 \text{ frames} \times 10,000 \text{ bits/frame}) = 120,000,000 \text{ bits}$  
    
- **2. Convert to seconds:** $120,000,000 \text{ bits} / 60 \text{ seconds} = 2,000,000 \text{ bps}$  
    
- **Answer:** The throughput is 2 Mbps, even though the bandwidth is 10 Mbps.
    

### Latency (Delay)

Latency is the total time it takes for a message to completely arrive at the destination. It has two main components:

1. **Propagation Time:** The time it takes for a bit to travel from the source to the destination.
    
    - **Formula:** $\text{Propagation Time} = \text{Distance} / \text{Propagation Speed}$  
        
2. **Transmission Time:** The time it takes to "push" all the bits of the message onto the link.
    
    - **Formula:** $\text{Transmission Time} = \text{Message Size (bits)} / \text{Bandwidth (bps)}$  
        

**Total Latency = Propagation Time + Transmission Time**

**Example 3.46 (Short Message, High BW):**

- **Message:** 2.5-kbyte e-mail
    
- **Bandwidth:** 1 Gbps
    
- **Distance:** 12,000 km
    
- **Propagation Speed:** $2.4 \times 10^8 \text{ m/s}$  
    
- **Calculations:**
    
    - $\text{Propagation Time} = (12,000,000 \text{ m}) / (2.4 \times 10^8 \text{ m/s}) = 0.05 \text{ s or 50 ms}$  
        
    - $\text{Transmission Time} = (2.5 \times 1024 \times 8 \text{ bits}) / (1 \times 10^9 \text{ b/s}) \approx 0.00002 \text{ s or 0.02 ms}$  
        
- **Result:** The dominant factor is propagation time. The transmission time is negligible.
    

**Example 3.47 (Long Message, Low BW):**

- **Message:** 5-Mbyte image
    
- **Bandwidth:** 1 Mbps
    
- **Distance:** 12,000 km
    
- **Propagation Speed:** $2.4 \times 10^8 \text{ m/s}$  
    
- **Calculations:**
    
    - $\text{Propagation Time} = (12,000,000 \text{ m}) / (2.4 \times 10^8 \text{ m/s}) = 0.05 \text{ s or 50 ms}$  
        
    - $\text{Transmission Time} = (5 \times 1024 \times 1024 \times 8 \text{ bits}) / (1 \times 10^6 \text{ b/s}) \approx 41.94 \text{ s}$  
        
- **Result:** The dominant factor is transmission time. The propagation time is negligible.
    

### Bandwidth-Delay Product

- **Concept:** This defines the number of bits that can "fill the link" at any given time. It helps visualize the link as a pipe: bandwidth is the cross-section (width) of the pipe, and delay is the length. The product is the volume of the pipe.
    
- **Formula:** $\text{Bandwidth-Delay Product} = \text{Bandwidth (bps)} \times \text{Propagation Time (s)}$