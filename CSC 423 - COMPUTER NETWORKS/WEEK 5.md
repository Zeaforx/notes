# Chapter 5: Analog Transmission - Comprehensive Study Notes

## **Section 1: Digital-to-Analog Conversion (Section 5-1)**

### **1. Core Definitions**

**Digital-to-Analog Conversion** is the process of changing one of the characteristics of an analog signal (amplitude, frequency, or phase) based on the information in digital data.

#### **Bit Rate vs. Baud Rate**

This is the most critical distinction in digital transmission.

- **Bit Rate (**$N$**):** The number of bits transmitted per second (bps). This is the rate of information.
- **Baud Rate (**$S$**):** The number of signal elements (symbols) transmitted per second. This is the rate of signal change.

The Relationship:

$$S = N \times \frac{1}{r} \quad \text{or} \quad N = S \times r$$

- Where $r$ is the number of data bits carried by each signal element ($r = \log_2 L$, where $L$ is the number of signal levels).

> **Pro-Tip:** Think of **Baud Rate** as a train leaving a station (the signal changes) and **Bit Rate** as the number of passengers on that train. If the train (signal) carries 1 passenger (bit), the rates are equal. If the train carries 4 passengers, the passenger rate (Bit Rate) is 4 times the train rate (Baud Rate).

### **2. Modulation Techniques**

#### **A. Amplitude Shift Keying (ASK)**

- **Explanation:** The amplitude of the carrier signal is varied to create signal elements, while frequency and phase remain constant. In Binary ASK (BASK), the amplitude is usually set to $A$ for a `1` and $0$ for a `0`.
- **Technical Implementation:**
  - Digital data is multiplied by a carrier signal using a **Multiplier**.
  - An **Oscillator** generates the carrier frequency ($f_c$).
- Bandwidth ($B$):
  $$B = (1 + d) \times S$$
  - Where $S$ is the signal rate (baud rate) and $d$ is a factor related to modulation/filtering (typically $0 \le d \le 1$).

#### **B. Frequency Shift Keying (FSK) & Multilevel FSK (MFSK)**

- **Explanation:** The frequency of the carrier signal is varied to represent data.
  - **Binary FSK:** Uses two frequencies, $f_1$ and $f_2$, for `0` and `1`.
  - **Multilevel FSK (MFSK):** Uses more than two frequencies to transmit multiple bits per signal element.
- **Technical Implementation:**
  - Uses a **Voltage-Controlled Oscillator (VCO)**. The digital input voltage changes the frequency of the oscillator output.
- Bandwidth ($B$):
  $$B = (1 + d) \times S + 2\Delta f$$
  - Where $2\Delta f$ is the frequency difference between the two carrier frequencies ($f_1$ and $f_2$).

#### **C. Phase Shift Keying (PSK)**

- **Explanation:** The phase of the carrier is varied to represent data. It is more robust against noise than ASK.
  - **BPSK (Binary PSK):** Uses 2 phases ($0^\circ, 180^\circ$). $r=1$.
  - **QPSK (Quadrature PSK):** Uses 4 phases ($0^\circ, 90^\circ, 180^\circ, 270^\circ$). $r=2$.
- **Technical Implementation:**
  - **QPSK:** The digital data is split into two streams (even and odd bits). One stream modulates an "In-phase" carrier ($I$), and the other modulates a "Quadrature" carrier ($Q$, shifted by $90^\circ$). These are summed together.
- Bandwidth ($B$):
  $$B = (1 + d) \times S$$
  - _Note: PSK uses the same bandwidth as ASK but offers better signal quality._

#### **D. Quadrature Amplitude Modulation (QAM)**

- **Explanation:** A combination of ASK and PSK. It varies both the **amplitude** and **phase** of the carrier to create a large number of signal elements (levels), allowing for high data rates.
- **Technical Implementation (Research Enhanced):**
  - Data is split into two streams: **I (In-phase)** and **Q (Quadrature)**.
  - Two carriers ($sin$ and $cos$) are generated from the same oscillator (separated by $90^\circ$).
  - Each stream is modulated (amplitude changed) separately and then added together.
  - Result: A single signal where specific combinations of amplitude and phase represent multiple bits (e.g., 16-QAM carries 4 bits per symbol).
- **Bandwidth:** Same as ASK and PSK: $B = (1+d) \times S$.

### **3. Visual Aids: Constellation Diagrams**

A **Constellation Diagram** maps the signal elements on a 2D coordinate system to help visualize the modulation.

- **X-Axis (In-Phase):** Represents the amplitude of the component with $0^\circ$ phase.
- **Y-Axis (Quadrature):** Represents the amplitude of the component with $90^\circ$ phase.
- **The Point:**
  - **Distance from origin** = Amplitude of the signal element.
  - **Angle from X-axis** = Phase of the signal element.

**Common Patterns:**

- **ASK:** Points lie only on the X-axis (e.g., at amplitude 0 and 1).
- **BPSK:** Two points on the X-axis equidistant from the origin (e.g., at +1 and -1).
- **QPSK:** Four points forming a square (one in each quadrant).
- **16-QAM:** 16 points arranged in a $4 \times 4$ grid.

### **4. Step-by-Step Examples (5.1 - 5.8)**

**Example 5.1: Finding Bit Rate from Signal Elements**

- **Given:** Analog signal carries $r=4$ bits per element. $S=1000$ signal elements/sec.
- **Formula:** $N = S \times r$  

- **Calculation:** $N = 1000 \times 4 = 4000$ bps.
- **Result:** Bit rate is **4 kbps**.

**Example 5.2: Finding Signal Levels**

- **Given:** Bit rate $N=8000$ bps. Baud rate $S=1000$ baud.
- **Step 1 (Find bits per element):** $r = N / S = 8000 / 1000 = 8$ bits/baud.
- **Step 2 (Find levels):** $L = 2^r = 2^8 = 256$.
- **Result:** We need **256 signal elements (levels)**.

**Example 5.3: Carrier Frequency and Bit Rate (ASK)**

- **Given:** Bandwidth 200 kHz to 300 kHz ($BW = 100$ kHz). ASK with $d=1$.
- **Logic:** The carrier frequency $f_c$ is the midpoint of the bandwidth.
- **Calculation (**$f_c$**):** $(200 + 300) / 2 = 250$ kHz.
- **Calculation (Bit Rate):** Formula $B = (1+d)S$. Since $r=1$ for binary ASK (implied), $S=N$.
  - $100 \text{ kHz} = (1+1)N \Rightarrow 100 = 2N \Rightarrow N = 50$ kbps.
- **Result:** $f_c = 250$ kHz, Bit Rate = **50 kbps**.

**Example 5.4: Full-Duplex ASK Bandwidth**

- **Given:** Total BW same as Ex 5.3 (100 kHz). Split into two directions (Full-Duplex).
- **Logic:** Divide total BW by 2. Each direction gets 50 kHz.
- **Calculation:**
  - Forward Channel: 200 to 250 kHz ($f_{c1} = 225$ kHz).
  - Backward Channel: 250 to 300 kHz ($f_{c2} = 275$ kHz).
  - New Data Rate: $50 = (1+1)N \Rightarrow N = 25$ kbps per direction.

**Example 5.5: FSK Bandwidth Calculation**

- **Given:** BW = 100 kHz (200-300 kHz). FSK with $d=1$. midpoint $250$ kHz. $2\Delta f = 50$ kHz.
- **Formula:** $B = (1+d)S + 2\Delta f$  

- **Calculation:**
  - $100 = (1+1)S + 50$  

  - $50 = 2S \Rightarrow S = 25$ kbaud.
  - Since Binary FSK, $N = S = 25$ kbps.
- **Result:** Bit Rate = **25 kbps**.

**Example 5.6: Multilevel FSK (MFSK)**

- **Given:** $N = 3$ Mbps. 3 bits at a time ($r=3$). Carrier $f_c = 10$ MHz.
- **Calculation:**
  - Signal Levels: $L = 2^3 = 8$.
  - Baud Rate: $S = N/r = 3 \text{ Mbps} / 3 = 1$ Mbaud.
  - Carrier Separation ($2\Delta f$): Text implies carriers are $1$ MHz apart.
  - Total Bandwidth: $B = L \times S = 8 \times 1 \text{ MHz} = 8$ MHz. (Simplified logic from text).
- **Result:** Bandwidth = **8 MHz**.

**Example 5.7: QPSK Bandwidth**

- **Given:** $N = 12$ Mbps. QPSK ($r=2$). $d=0$.
- **Calculation:**
  - Baud Rate: $S = N/r = 12 / 2 = 6$ Mbaud.
  - Bandwidth: $B = (1+d)S = (1+0)6 = 6$ MHz.
- **Result:** Bandwidth = **6 MHz**.

**Example 5.8: Drawing Constellations**

- **Task:** Show diagrams for ASK (OOK), BPSK, QPSK.
- **Solution:** Refer to "Visual Aids" section above for descriptions (ASK: 2 points on X-axis; BPSK: 2 points on X-axis symmetric; QPSK: 4 points in square).

## **Section 2: Analog-to-Analog Conversion (Section 5-2)**

### **1. Conceptual Overview**

**Why modulate an analog signal (like voice) if it's already analog?**

1. **Bandpass Channels:** Transmission media (like air for radio) are "bandpass," meaning they pass frequencies only in a specific high range. Low-frequency voice signals (0-4 kHz) cannot travel far directly.
2. **Frequency Division Multiplexing (FDM):** To send multiple stations at once, each must be shifted to a different carrier frequency (e.g., Station 1 at 100 MHz, Station 2 at 101 MHz).

### **2. Modulation Types**

#### **A. Amplitude Modulation (AM)**

- **Definition:** The amplitude of the carrier signal is changed according to the amplitude of the modulating (audio) signal.
- **Implementation:** Simple **Multiplier**. The audio signal multiplies the carrier oscillator.
- Bandwidth Formula:
  $$B_{AM} = 2B$$
  - The required bandwidth is twice the bandwidth of the audio signal ($B$).

#### **B. Frequency Modulation (FM)**

- **Definition:** The frequency of the carrier is changed according to the amplitude of the audio signal.
- **Implementation:** Uses a **Voltage-Controlled Oscillator (VCO)**.
- Bandwidth Formula (Carson's Rule):
  $$B_{FM} = 2(1 + \beta)B$$
  - Where $\beta$ is usually 4 (for standard FM radio), resulting in a bandwidth roughly 10 times the audio bandwidth.

#### **C. Phase Modulation (PM)**

- **Definition:** The phase of the carrier is changed according to the amplitude of the audio signal.
- **Implementation:**
  - The modulating signal is first passed through a **derivative** (differentiator) block.
  - The result is then fed into a **VCO** (similar to FM).
  - _Note:_ Mathematically, PM is the integral of FM.
- Bandwidth Formula:
  $$B_{PM} = 2(1 + \beta)B$$
- **Research Note (The** $\beta$ **difference):** While the bandwidth formulas look identical in the text, $\beta$ (Modulation Index) is calculated differently:
  - **FM:** $\beta = \Delta f / f_m$ (Depends on frequency deviation).
  - **PM:** $\beta = k_p A_m$ (Depends on peak amplitude directly).

### **3. Real-World Application: Band Allocation**

|              |                        |                       |                                                                                                   |
| ------------ | ---------------------- | --------------------- | ------------------------------------------------------------------------------------------------- |
| **Type**     | **Frequency Range**    | **Channel Bandwidth** | **Allocation Logic**                                                                              |
| **AM Radio** | **530 kHz - 1700 kHz** | **10 kHz**            | AM stations are spaced 10 kHz apart to prevent interference.                                      |
| **FM Radio** | **88 MHz - 108 MHz**   | **200 kHz**           | FM stations are spaced 200 kHz apart. This wider bandwidth allows for high-fidelity stereo sound. |

> **Pro-Tip (Analogy):**
>
> - **AM** is like a light dimmer switch flickering rapidly to send a code (Amplitude changes). It's simple but easy to disrupt (flickering lights can be confused by a passing shadow/noise).
> - **FM** is like changing the _color_ of the light (Red-Green-Blue) to send a code (Frequency changes). It is much harder for "shadows" (noise) to change the color of the light, which is why FM sounds clearer than AM.
