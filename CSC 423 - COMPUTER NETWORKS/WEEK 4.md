# Comprehensive Technical Deep-Dive: Digital Transmission

This note provides a rigorous analysis of Chapter 4: Digital Transmission, covering Digital-to-Digital conversion, Analog-to-Digital conversion, and physical transmission modes.

## I. Digital-to-Digital Conversion: Line Coding

Line coding is the process of converting digital data into digital signals.

### 1. Signal Elements vs. Data Elements ($r$)

- **Technical Identification:** The ratio $r$.
    
- **'Under the Hood' Explanation:** $r$ represents the number of data elements (bits) carried by a single signal element.
    
    - If $r=1$, one signal pulse represents one bit.
        
    - If $r=1/2$, it takes two signal pulses to represent one bit (increasing bandwidth).
        
    - If $r=2$, one signal pulse represents two bits (increasing data density).
    ![[Pasted image 20251227154910.png]]
        
- **Bridge to Understanding:** Think of a signal element as a **shipping crate** and data elements as the **items** inside. $r$ tells you how many items are packed into each crate.
    
- **Professional Implementation:** A network architect calculates $r$ to determine if a specific hardware medium (like Cat6 cable) can support a desired bit rate given its physical frequency limits.
    
- **Dependencies:** Bit Rate ($N$), Baud Rate ($S$).
    

### 2. The Signal Rate Formula (Baud Rate)

- **Technical Identification:** $S = c \times N \times \frac{1}{r}$  
    
- **'Under the Hood' Explanation:**
    
    - $S$: Baud rate (signal elements per second).
        
    - $c$: Case factor (ranges from 0 to 1, average usually $1/2$).
        
    - $N$: Bit rate (data elements per second).
        
    - $r$: The ratio defined above.
        
- **Bridge to Understanding:** This is the "Traffic Flow" equation. It calculates how many physical "pulses" must be sent per second to achieve a specific digital speed.
    
- **Professional Implementation:** Used by DSP (Digital Signal Processing) engineers to ensure that the "baud" (physical transitions) does not exceed the bandwidth of the transmission line.
    

## II. Line Coding Schemes

### 1. Polar NRZ (NRZ-L and NRZ-I)

- **Technical Identification:** Non-Return-to-Zero Level (NRZ-L) and Inversion (NRZ-I).
    
- **'Under the Hood' Explanation:**
    
    - **NRZ-L:** The voltage level is constant for the duration of the bit. Positive voltage = 0, Negative voltage = 1 (or vice versa).
        
    - **NRZ-I:** The signal stays at its current level unless it encounters a '1' bit, which triggers a **transition (inversion)**. A '0' bit causes no change.
        
- **Bridge to Understanding:** NRZ-L is like a light that stays on for '1' and off for '0'. NRZ-I is like a toggle switch: you only flip it if the next instruction is a '1'.
    
- **Professional Implementation:** NRZ-I is superior for synchronization because every '1' bit guarantees a signal change, which helps the receiver's clock stay aligned.
    
- **Dependencies:** Clock Synchronization.
    ![[Pasted image 20251227155218.png]]

### 2. Biphase: Manchester and Differential Manchester

- **Technical Identification:** Manchester and Differential Manchester.
    
- **'Under the Hood' Explanation:**
    
    - **Manchester:** A transition always occurs at the **middle of the bit interval**. Low-to-High = 1; High-to-Low = 0.
        
    - **Differential Manchester:** The mid-bit transition is only for clocking. The bit value is determined by whether there is a transition at the **beginning** of the interval. (Transition = 0, No Transition = 1).
        
- **Bridge to Understanding:** This is a "Digital Heartbeat." Because there is a pulse in the middle of _every_ bit, the receiver can never lose the rhythm of the sender.
    
- **Professional Implementation:** The standard for **Classic Ethernet (10 Mbps)**. It is preferred for its self-synchronization properties despite requiring double the bandwidth of NRZ.
    
- **Dependencies:** $r = 1/2$, Average Signal Rate $S = N$.
    ![[Pasted image 20251227155459.png]]

### 3. Multilevel Schemes (2B1Q, 8B6T, 4D-PAM5)

- **Technical Identification:** mBnL (m data bits, n signal elements, L levels).
    
- **'Under the Hood' Explanation:**
    
    - **2B1Q:** 2 bits are mapped to 1 signal element using 4 voltage levels (+3, +1, -1, -3).
		
    - **8B6T (8-bit 6-ternary):** Maps an 8-bit data pattern ($2^8 = 256$ combinations) into a pattern of 6 signal elements using 3 voltage levels ($3^6 = 729$ combinations).
    
	    - To maintain DC balance, the weight (sum of voltages) of each 6-element group is calculated.
        
	    - If a group has a non-zero weight, the next group with a similar weight is **inverted** to bring the total average voltage back to zero.
        
    - **4D-PAM5:** 4-dimensional pulse amplitude modulation with 5 levels. It sends data over four wires simultaneously.
        
- **Bridge to Understanding:** Instead of just "On/Off," you use "Dim, Medium, Bright, and Blinding" to represent different combinations of bits in a single flash.
    
- **Professional Implementation:** **1000Base-T (Gigabit Ethernet)** uses 4D-PAM5 to achieve high speeds over standard copper wiring.
	![[Pasted image 20251227155853.png]]
    

## III. Scrambling (B8ZS and HDB3)

- **Technical Identification:** Bipolar 8-Zero Substitution (B8ZS) and High-Density Bipolar 3-Zero (HDB3).
    
- **'Under the Hood' Explanation:**
    
    - **B8ZS:** When eight consecutive zeros occur, the system forces a "violation" (two pulses of the same polarity) in a specific pattern (`000VB0VB`) to force the receiver's clock to tick.
		![[Pasted image 20251227171210.png]]
        
    - **HDB3:** Replaces four consecutive zeros with `000V` or `B00V` based on the number of non-zero pulses since the last substitution to keep the DC balance at zero.
		![[Pasted image 20251227171248.png]]
		
- **Bridge to Understanding:** Like a supervisor checking on a guard; if the guard hasn't moved (zeros) for too long, the supervisor pokes them (violation) to make sure they are still awake (synchronized).
    
- **Professional Implementation:** Used in T-1 and E-1 carrier lines to prevent "loss of lock" during long silent periods in data transmission.
    
- **Dependencies:** AMI (Alternate Mark Inversion).
    

## IV. Analog-to-Digital Conversion (PCM)

### 1. Pulse Code Modulation (PCM) Components

- **Technical Identification:** Sampling, Quantizing, Encoding.
    
- **'Under the Hood' Explanation:**
    
    - **Sampling:** Measuring the analog amplitude at intervals defined by the **Nyquist Rate**.
        
    - **Quantizing:** Mapping the infinite analog values into a finite set of levels ($L$).
        
    - **Encoding:** Converting levels into binary words.
        
- **Bridge to Understanding:** Like taking a high-resolution photo of a moving object. Each sample is a "pixel" in time.
    
- **Professional Implementation:** The backbone of the **PSTN (Public Switched Telephone Network)**.
	![[Pasted image 20251227171447.png]]
    

### 2. Nyquist Theorem (Sampling)

- **Formula:** $f_s = 2 \times f_{max}$  
    
- **'Under the Hood' Explanation:**
    
    - $f_s$: Sampling frequency.
        
    - $f_{max}$: The highest frequency component in the analog signal.
        
- **Bridge to Understanding:** To catch a bird flapping its wings, you must take pictures at least twice as fast as the wings move, or the wings will look like a blur.
    
- **Professional Implementation:** Audio CDs sample at 44.1 kHz because human hearing goes up to 20 kHz ($2 \times 20k = 40k$, plus a buffer).
    
- **Dependencies:** Bandwidth of the analog signal.
	![[Pasted image 20251227171831.png]]
    

### 3. Signal-to-Quantization Noise Ratio ($SNR_{dB}$)

- **Formula:** $SNR_{dB} = 6.02n + 1.76$  
    
- **'Under the Hood' Explanation:**
    
    - $n$: Number of bits per sample.
        
    - As $n$ increases, the "granularity" of quantization decreases, making the digital representation more accurate.
        
- **Professional Implementation:** A telecommunications engineer increases $n$ to 8 bits for voice (64 kbps) to ensure $SNR_{dB}$ is high enough for clear human speech.
    

## V. Transmission Modes

### 1. Parallel vs. Serial

- **Technical Identification:** Parallel/Serial Conversion.
    
- **'Under the Hood' Explanation:**
    
    - **Parallel:** $n$ bits are sent on $n$ wires simultaneously. High speed but high cost and distance-limited.
        
    - **Serial:** Bits are sent one after another on one wire. Low cost and long distance.
        
- **Bridge to Understanding:** Parallel is an 8-lane highway; Serial is a 1-lane tunnel where cars must drive in a single-file line.
    
- **Professional Implementation:** Computer motherboards use parallel for internal buses (PCIe), while USB (Universal **Serial** Bus) is used for external devices.
    

### 2. Serial Subclasses

- **Asynchronous:** Uses **Start bits (0)** and **Stop bits (1)**. Good for irregular data (keyboard typing).
    
- **Synchronous:** Data is sent in blocks called **Frames** without start/stop bits. High efficiency.
    
- **Isochronous:** Fixed timing between frames. Used for real-time video/audio.