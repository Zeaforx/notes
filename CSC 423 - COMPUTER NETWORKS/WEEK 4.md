# Chapter 4: Digital Transmission – Student Study Guide

Welcome to your comprehensive study guide for **Digital Transmission**. This document is designed to help you master the conversion of data into signals and the various modes of transmission.

## Section 4-1: Digital-to-Digital Conversion

Digital-to-digital conversion involves representing digital data using digital signals. This process relies on three primary techniques: **Line Coding**, **Block Coding**, and **Scrambling**.

### 1. The Basics

- **Line Coding:** The process of converting digital data to digital signals.
- **Block Coding:** A technique to provide redundancy and error detection by replacing $m$-bit groups with $n$-bit groups.
- **Scrambling:** A technique used to replace sequences of zeros with other levels to maintain synchronization without increasing bandwidth.

> **💡 Key Rule:** Line coding is always needed; block coding and scrambling may or may not be needed.

### 2. Key Concepts

- **Data Element:** The smallest entity that can represent a piece of information (a bit).
- **Signal Element:** The shortest unit (time-wise) of a digital signal.
- **Ratio (**$r$**):** The number of data elements carried by each signal element ($r = \text{data bits} / \text{signal elements}$).
- **Bit Rate (**$N$**):** Number of bits sent per second (bps).
- **Signal Rate (**$S$ **or Baud):** Number of signal elements sent per second.
  - **Formula:** $S = c \times N \times (1/r)$ baud, where $c$ is the case factor (usually $1/2$ for average).

#### Walkthrough: Example 4.1

Problem: A signal carries data where 1 data element is encoded as 1 signal element ($r=1$). Bit rate is $100$ kbps. Find average baud rate if $c$ is between $0$ and $1$.

Solution:

1. Assume average case $c = 1/2$.
2. Formula: $S = c \times N \times (1/r)$
3. $S = 1/2 \times 100,000 \times (1/1) = 50,000$ baud = **50 kbaud**.

### 3. Deep Dive: Line Coding Schemes

Line coding can be compared to a **Morse Code operator** deciding whether to use short taps, long taps, or silences to represent a message as efficiently as possible.

#### A. Unipolar Schemes (NRZ)

- **Non-Return-to-Zero (NRZ):** Uses a single voltage level (positive) for bit 1 and zero voltage for bit 0.
  - **The Issue:** It is very costly in terms of power and has a significant **DC component** (average voltage is not zero).
  - **Synchronization:** If a long string of 1s or 0s is sent, the signal stays flat, and the receiver's clock can drift (no self-sync).

#### B. Polar Schemes (NRZ-L, NRZ-I, RZ, Biphase)

- **NRZ-L (Level):** The voltage level determines the value (e.g., Positive = 0, Negative = 1).
- **NRZ-I (Invert):** The signal _inverts_ at the beginning of the bit interval if the bit is a 1. If the bit is a 0, there is no change.
  - **Advantage of NRZ-I:** It provides better synchronization than NRZ-L for strings of 1s, but still fails for strings of 0s.
- **RZ (Return-to-Zero):** The signal changes during the bit interval—it goes to zero halfway through every bit. This uses three values (+, 0, -) but only represents two.
  - **Benefit:** Self-synchronization. **Drawback:** Requires double the bandwidth.
- **Manchester:** A transition happens in the middle of every bit interval. A '0' is a High-to-Low transition; a '1' is a Low-to-High transition.
- **Differential Manchester:** A transition always happens in the middle of the bit for sync, but the presence or absence of a transition at the _beginning_ of the interval determines the bit (Transition = 0, No Transition = 1).

#### C. Bipolar Schemes (AMI, Pseudoternary)

- **AMI (Alternate Mark Inversion):** Bit 0 is zero voltage. Bit 1s are represented by alternating positive and negative pulses.
- **Pseudoternary:** The reverse of AMI. Bit 1 is zero voltage, and bit 0s alternate pulses.
  - **The Benefit:** No DC component because the alternating pulses average out to zero voltage.

#### D. Multilevel Schemes (mBnL)

These increase the data rate by encoding a pattern of $m$ data elements into $n$ signal elements using $L$ levels.

- **2B1Q (Two Binary, One Quaternary):** Groups of 2 bits are sent as 1 signal element with 4 possible levels.
- **8B6T (Eight Binary, Six Ternary):** Groups of 8 bits are mapped to 6 signal elements using 3 levels.
- **4D-PAM5 (Four-Dimensional 5-Level Pulse Amplitude Modulation):** Data is sent over four wires simultaneously.

#### E. Multitransition (MLT-3)

- Uses three levels (+V, 0, -V) and three transition rules. The signal only changes when a bit 1 is encountered. It moves through the levels in the order $[+ \to 0 \to - \to 0]$.
  - **Goal:** To keep the frequency (and thus bandwidth) very low while maintaining high bit rates.

> **💡 Key Rule:** NRZ-L and NRZ-I both suffer from the DC component problem and lack of synchronization for long strings of 0s or 1s. Manchester and Differential Manchester solve this by ensuring a transition in every single bit.

### 4. Calculations

- **Minimum Bandwidth (**$B_{min}$**):** $B_{min} = S = c \times N \times (1/r)$.
- **Maximum Data Rate (**$N_{max}$**):** $N_{max} = 2 \times B \times \log_2 L$.

#### Walkthrough: Example 4.4

Problem: A system uses NRZ-I for $10$-Mbps data. Find average signal rate and $B_{min}$.

Solution:

1. For NRZ-I, $r=1$ and average $c=1/2$.
2. $S = N/2 = 10 \text{ Mbps} / 2 = \mathbf{5 \text{ Mbaud}}$.
3. $B_{min} = S = \mathbf{5 \text{ MHz}}$.

## Section 4-2: Analog-to-Digital Conversion

The trend in modern communication is to change analog signals (like voice) into digital data.

### 1. Pulse Code Modulation (PCM)

The PCM process follows three distinct steps:

1. **Sampling:** Taking snapshots of the analog signal at specific intervals (Pulse Amplitude Modulation - PAM).
2. **Quantizing:** Assigning discrete values to the PAM samples.
3. **Encoding:** Converting the quantized values into binary streams.

### 2. The Nyquist Theorem

The sampling rate must be at least **twice** the highest frequency in the signal ($f_s = 2 \times f_{max}$).

> **💡 Key Rule:** Sampling at the Nyquist rate creates a good approximation; undersampling creates an incorrect signal (aliasing).

#### The Clock Analogy (Example 4.7 & 4.8):

- **Nyquist Rate:** Sampling a clock hand every 30s ($T_s = 1/2 T$). You see 12-6-12-6. You can't tell if it moves forward or back.
- **Oversampling:** Sampling every 15s. 12-3-6-9-12. Clear forward motion.
- **Undersampling:** Sampling every 45s. 12-9-6-3-12. The clock appears to move **backward**. This is why car wheels sometimes look like they rotate backward in movies!

### 3. Performance & Voice Digitization

- **SNRdB Formula:** $SNR_{dB} = 6.02 \times n + 1.76$ (where $n$ is bits per sample).

#### Walkthrough: Example 4.13

Problem: A line needs $SNR_{dB} > 40$. Find min bits per sample.

Solution:

1. $40 = 6.02n + 1.76$
2. $38.24 = 6.02n \Rightarrow n \approx 6.35$.
3. Must round up: **7 bits per sample**.

#### Walkthrough: Example 4.14

Problem: Bit rate to digitize voice (up to $4000$ Hz) at $8$ bits/sample?

Solution:

1. $f_s = 2 \times 4000 = 8000$ samples/s.
2. Bit Rate = $8000 \times 8 = \mathbf{64,000 \text{ bps (64 kbps)}}$.

### 4. Delta Modulation (DM)

DM records only the _change_ (positive or negative) from the previous sample.

- **Components:** Comparator, Staircase Maker, and Delay Unit.

## Section 4-3: Transmission Modes

### 1. Parallel Transmission

Sends $n$ bits simultaneously over $n$ wires. It is very fast but expensive and limited to short distances.

### 2. Serial Transmission

Sends 1 bit at a time over a single wire.

- **Asynchronous:** Uses **Start bits (0)** and **Stop bits (1)**. There may be gaps between bytes, but bits within a byte are synchronized.
- **Synchronous:** Bits are sent in a continuous stream without gaps. The receiver must group the bits into bytes.
- **Isochronous:** Ensures that data arrives at a steady, fixed rate (used for real-time audio/video).

> **💡 Key Rule:** In asynchronous transmission, we send 1 start bit at the beginning and 1 or more stop bits at the end of each byte.

## Modern Real-World Applications

- **4D-PAM5:** Used in **1000Base-T (Gigabit Ethernet)**. It sends data over four copper pairs simultaneously using 5-level pulse amplitude modulation.
- **MLT-3:** Primarily used in **100Base-TX (Fast Ethernet)** to reduce the bandwidth required for $100$ Mbps transmission over copper wires.
- **2B1Q:** Traditionally used in **ISDN (Integrated Services Digital Network)** for the basic rate interface.
- **8B/10B Coding:** Widely used in **Fiber Channel**, **SATA**, and **PCI Express** to ensure enough transitions for clock recovery and to maintain DC balance.

**Study Tip:** Practice drawing the Manchester and Differential Manchester waveforms for the bitstream `101100`. Remember that in Manchester, `0` is a High-to-Low transition and `1` is a Low-to-High transition!
