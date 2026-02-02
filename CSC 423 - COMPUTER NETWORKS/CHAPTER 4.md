# Chapter 4: Digital Transmission

## Introduction

A computer network is designed to send information from one point to another. This information must be converted into either a digital or an analog signal. This chapter focuses on **Digital Transmission**, which involves:

1. **Digital-to-Digital Conversion:** Converting digital data into digital signals.
    
2. **Analog-to-Digital Conversion:** Digitizing analog signals.
    
3. **Transmission Modes:** The serial or parallel transfer of data.
    

## 4.1 Digital-to-Digital Conversion

Digital-to-digital conversion involves representation. We treat digital data (sequences of 0s and 1s) as the input and generating digital signals (pulses of voltage) as the output. This process relies on three key techniques: **Line Coding**, **Block Coding**, and **Scrambling**.

### 4.1.1 Line Coding

**Definition:** Line coding is the process of converting digital data (binary) into digital signals. The sender encodes the data, and the receiver decodes it.
![[Pasted image 20260202120436.png]]

#### Characteristics of Line Coding

**1. Signal Element vs. Data Element**

It is crucial to distinguish between the information and the carrier.

- **Data Element:** The smallest entity that can represent a piece of information (the **bit**).
    
- **Signal Element:** The shortest unit (timewise) of a digital signal.
    
- **Ratio (**$r$**):** The number of data elements carried by each signal element.
    

$$r = \frac{\text{Number of Data Elements}}{\text{Number of Signal Elements}}$$

> **[Analogy]:** Think of data elements as _people_ and signal elements as _vehicles_.
> 
> - $r=1$: One person per car.
>     
> - $r>1$: Carpooling (multiple people per car).
>     
> - $r<1$: One person requires a car and a trailer (multiple vehicles for one person).

![[Pasted image 20260202120723.png]]

**2. Data Rate vs. Signal Rate**

- **Data Rate (**$N$**):** The number of data elements (bits) sent in 1 second. Measured in **bits per second (bps)**.
    
- **Signal Rate (**$S$**):** The number of signal elements sent in 1 second. Measured in **baud**. Also called the _pulse rate_ or _modulation rate_.
    

**Formula for Signal Rate:**

  

$$S = c \times N \times \frac{1}{r}$$

Where:

- $S$ = Signal rate (baud)
    
- $N$ = Data rate (bps)
    
- $c$ = Case factor (varies based on the data pattern; usually $0.5$ for average case, $1$ for worst case)
    
- $r$ = Ratio of data elements to signal elements
    

**3. Bandwidth**

Although digital signals theoretically have infinite bandwidth, their **effective bandwidth** is finite. The minimum bandwidth ($B_{min}$) required is proportional to the signal rate.

$$B_{min} = c \times N \times \frac{1}{r}$$

**Maximum Data Rate (Nyquist):**

If the bandwidth ($B$) is given, the maximum data rate ($N_{max}$) is:

  

$$N_{max} = \frac{1}{c} \times B \times r$$

**4. Transmission Issues**

- **Baseline Wandering:** The receiver calculates a running average (baseline) of the received signal power to decode the value. A long string of 0s or 1s can cause this baseline to drift, leading to decoding errors.
    
    - **Solution:** Use coding schemes that prevent long sequences of constant voltage levels (e.g., **Manchester**, **Block Coding**, **Scrambling**).
        
- **DC Components:** Frequencies around zero (Direct Current) create problems for systems that cannot pass low frequencies (e.g., telephone lines) or use electrical coupling (transformers).
    
    - **Solution:** Select a scheme with no DC component (e.g., **Bipolar AMI**, **Manchester**), where the average amplitude is zero.
        
- **Self-Synchronization:** The receiver's clock must match the sender's. If the receiver is faster or slower, bit intervals mismatch. A self-synchronizing signal includes timing information (usually transitions) within the data.
    
    - **Solution:** Ensure transitions occur regularly in the signal (e.g., **Manchester** encoding has a transition in the middle of every bit) to allow the receiver to reset its clock.
    

### 4.1.2 Line Coding Schemes

We categorize line coding into five broad groups.
![[Pasted image 20260202122354.png]]

#### 1. Unipolar Scheme

- **NRZ (Non-Return-to-Zero):** Uses positive voltage for 1 and zero voltage for 0.
    
- **Drawbacks:** High power usage (double that of polar). Not typically used in modern data communications.
	  
    ![[Pasted image 20260202122445.png]]
    

#### 2. Polar Schemes

Voltages are on both sides of the time axis (positive and negative).

- **NRZ-L (Non-Return-to-Zero-Level):** The level of the voltage determines the bit value.
    
- **NRZ-I (Non-Return-to-Zero-Invert):** The _change_ (or lack thereof) in voltage determines the bit value.
    
    - No change = 0
        
    - Change = 1
        
    - **Note:** Both NRZ-L and NRZ-I suffer from baseline wandering and DC component issues.
	      
	![[Pasted image 20260202122640.png]]
        
- **RZ (Return-to-Zero):** Uses three values (positive, negative, zero). The signal goes to 0 in the middle of each bit.
    
    - **Pros:** Solves synchronization (transition in every bit).
        
    - **Cons:** Requires two signal changes per bit, increasing bandwidth. Complex to generate (3 levels).
        ![[Pasted image 20260202122902.png]]
        
- **Biphase (Manchester & Differential Manchester):**
    
    - **Manchester:** Combines RZ and NRZ-L. The duration of the bit is divided into two halves. A transition occurs in the middle of _every_ bit.
        
    - **Differential Manchester:** Combines RZ and NRZ-I. Transition at the middle for sync. Bit value determined by the presence/absence of a transition at the _beginning_ of the bit.
        
    - **Pros:** Excellent synchronization; No DC component.
        
    - **Cons:** Signal rate is double that of NRZ ($B_{min} = 2 \times B_{NRZ}$).
![[Pasted image 20260202123116.png]]  
        

#### 3. Bipolar Schemes

Uses three levels: Positive, Negative, and Zero.

- **AMI (Alternate Mark Inversion):**
    
    - Binary 0 = Neutral zero voltage.
        
    - Binary 1 = Alternating positive and negative voltages.
        
- **Pseudoternary:**
    
    - Binary 1 = Zero voltage.
        
    - Binary 0 = Alternating positive and negative voltages.
        
- **Pros:** No DC component. Lower bandwidth than Biphase.
![[Pasted image 20260202123355.png]]
    

#### 4. Multilevel Schemes ($mBnL$)

Encodes a pattern of $m$ data elements into a pattern of $n$ signal elements using $L$ levels.

- - **2B1Q (Two Binary, One Quaternary):**
    
    - Data pattern size: $m=2$. Signal pattern size: $n=1$. Levels: $L=4$.
        
    - Used in **DSL (Digital Subscriber Line)**.
        
    - Average signal rate: $S = N/4$.
        
    - **Pros:** Highly efficient bandwidth usage (data sent 2 times faster than NRZ-L).
        
    - **Cons:** Receiver complexity (must distinguish 4 voltage thresholds); No redundancy for error detection or DC balance.
        
    - **How to Draw:**
        
        1. **Group bits into pairs** (e.g., `1101` $\rightarrow$ `11`, `01`).
            
        2. **Map pairs to voltage levels** (Standard convention: `00` $\rightarrow$ -3, `01` $\rightarrow$ -1, `10` $\rightarrow$ +3, `11` $\rightarrow$ +1).
            
        3. **Draw the pulse**: Draw a horizontal line at the corresponding level for one signal duration per pair.
	    ![[Pasted image 20260202123714.png]]
        
- **8B6T (Eight Binary, Six Ternary):**
    
    - Encodes 8 bits into 6 signal elements using 3 levels.
        
    - Used in **100BASE-4T** cable.
        
    - Redundancy: $3^6 - 2^8 = 473$ redundant patterns used for sync and error detection.
        
    - **Pros:** Good DC balance (uses signal inversion for weight management); Built-in error detection and synchronization.
        
    - **Cons:** Higher bandwidth requirement than 2B1Q; Complex mapping logic.
        
    - **How to Draw:**
        
        1. **Group bits into bytes** (8 bits).
            
        2. **Consult the Table**: Map the byte to a standardized sequence of 6 ternary signals (+, 0, -).
            
        3. **Check DC Balance**: Calculate the pattern weight. If the new pattern worsens the line's DC imbalance, **invert** the entire 6-signal pattern (swap + and -).
            
        4. **Draw the sequence**: Plot the 6 signal elements in order using three levels (+V, 0, -V).**
	  ![[Pasted image 20260202124538.png]]
        
- **4D-PAM5 (Four-Dimensional Five-Level Pulse Amplitude Modulation):**
    
    - Sends data over 4 wires simultaneously. Uses 5 voltage levels (-2, -1, 0, 1, 2).
        
    - Level 0 is used for forward error detection.
        
    - Used in **Gigabit LANs**.
        
    - **Pros:** Extremely efficient signal rate ($N/8$ per wire); Allows Gigabit speeds over standard copper cables; Forward error detection capability.
        
    - **Cons:** Complex implementation (requires 4 simultaneous channels/wires).
        
    - **How to Draw:**
        
        1. **Group bits** into blocks.
            
        2. **Distribute** the bits across 4 separate communication wires.
            
        3. **Assign Voltage Levels**: Each wire carries a signal at one of 5 levels (-2, -1, 0, 1, 2).
            
        4. **Draw 4 Parallel Graphs**: Stack 4 graphs vertically sharing the same time axis. At each clock tick, draw the symbol change on all 4 wires simultaneously.
        ![[Pasted image 20260202125103.png]]
        

#### 5. Multitransition Scheme

- **MLT-3 (Multiline Transmission, Three-Level):**
    
    - Uses three levels (+V, 0, -V) and three transition rules.
        
    - **Rules:**
        
        1. Next bit 0: No transition.
            
        2. Next bit 1 + Current Level not 0: Next level is 0.
            
        3. Next bit 1 + Current Level is 0: Next level is opposite of the last non-zero level.
            
    - **Pros:** Signal rate is effectively 1/4 the bit rate, suitable for copper wires with limited bandwidth (e.g., 100 Mbps transmission).
        
        ![[Pasted image 20260202125303.png]]

![[Pasted image 20260202125322.png]]

### 4.1.3 Block Coding

**Definition:** Block coding adds redundancy to ensure synchronization and error detection. It is usually referred to as **mB/nB coding**, where it replaces each $m$-bit group with an $n$-bit group ($n > m$).

**Process:**

1. **Division:** Stream divided into m-bit groups.
    
2. **Substitution:** m-bit group substituted with n-bit group.
    
3. **Combination:** n-bit groups combined into a stream.
    
    ![[Pasted image 20260202125717.png]]

**Schemes:**

- **4B/5B:** Used with NRZ-I. Ensures that the stream does not have more than three consecutive 0s (solving NRZ-I's sync problem). Signal rate increases by 25%.
	  ![[Pasted image 20260202125742.png]]
    
- **8B/10B:** Similar to 4B/5B but provides better error detection. Actually a combination of 5B/6B and 3B/4B.
    

### 4.1.4 Scrambling

**Context:** Biphase is good for LANs but uses too much bandwidth for long distance. Block coding + NRZ has DC issues. Bipolar AMI is good (narrow bandwidth, no DC) but loses sync with long sequences of 0s. **Scrambling** modifies AMI to prevent long sequences of 0s without increasing bit rate.

**1. B8ZS (Bipolar with 8-Zero Substitution)**

- Used in North America.
    
- **Rule:** If 8 consecutive 0s are detected, replace them with `000VB0VB`.
    
    - **V (Violation):** A non-zero voltage with the _same_ polarity as the previous non-zero pulse (violates AMI).
        
    - **B (Bipolar):** A non-zero voltage with _opposite_ polarity (follows AMI).
        

**2. HDB3 (High-Density Bipolar 3-Zero)**

- Used outside North America (Europe/Japan).
    
- **Rule:** Substitutes 4 consecutive 0s based on the number of non-zero pulses since the last substitution.
    
    - If number of pulses is **Odd**: Substitute `000V`.
        
    - If number of pulses is **Even**: Substitute `B00V`.
        

## 4.2 Analog-to-Digital Conversion

To transmit analog signals (voice, video) digitally, we must digitize them.

### 4.2.1 Pulse Code Modulation (PCM)

PCM consists of three steps: Sampling, Quantizing, and Encoding.
![[Pasted image 20260202130044.png]]

**1. Sampling (Pulse Amplitude Modulation - PAM)**

The analog signal is measured every $T_s$ seconds.

- **Nyquist Theorem:** The sampling rate ($f_s$) must be at least twice the highest frequency in the original signal.
    
      
    
    $$f_s \ge 2 \times f_{max}$$

> **[Real World Example]:** The human voice has a max frequency of 4000 Hz. Telephone systems sample at $2 \times 4000 = 8000$ samples/sec.

**2. Quantization**

Converting the continuous analog sample height into a discrete integer value.

- Assume signal range is $V_{min}$ to $V_{max}$.
    
- Divide range into $L$ zones of height $\Delta$.
    
      
    
    $$\Delta = \frac{V_{max} - V_{min}}{L}$$
- **Quantization Error:** The difference between the actual signal value and the quantized value.
    
- **Signal-to-Noise Ratio (**$SNR_{dB}$**):**
    
      
    
    $$SNR_{dB} = 6.02 n_b + 1.76$$
    
    Where $n_b$ is the number of bits per sample.
    

**3. Encoding**

Convert the quantized values into bits.

- **Bit Rate:**
    
      
    
    $$\text{Bit Rate} = \text{Sampling Rate} \times \text{Bits per sample} = f_s \times n_b$$

**PCM Bandwidth**

The minimum bandwidth required for a PCM channel is:

  

$$B_{min} = n_b \times B_{analog}$$

### 4.2.2 Delta Modulation (DM)

A simpler alternative to PCM.

- **Mechanism:** Instead of finding the absolute amplitude, DM records the **change** from the previous sample.
    
- **Process:** If the amplitude is higher than the previous, send a 1; if lower, send a 0.
    
- **Components:** Modulator, Comparator, Delay Unit, Staircase Maker.
    
- **Adaptive DM:** Adjusts the step size ($\delta$) dynamically based on signal amplitude changes to reduce quantization error.
    

## 4.3 Transmission Modes

This section defines how the data stream moves across the link (wiring and timing).

### 4.3.1 Parallel Transmission

- **Mechanism:** Sending $n$ bits at the same time using $n$ wires.
    
- **Pros:** High speed (factor of $n$ faster than serial).
    
- **Cons:** Expensive (requires $n$ communication lines). Limited to short distances.
    

### 4.3.2 Serial Transmission

- **Mechanism:** Sending bits one after another using one communication channel.
    
- **Pros:** Reduced cost (only one wire required). Suitable for long distances.
    

**Subclasses of Serial Transmission:**

1. **Asynchronous Transmission**
    
    - Timing is unimportant at the stream level.
        
    - Patterns are based on bytes.
        
    - **Start Bit (0):** Added to the beginning of each byte.
        
    - **Stop Bit (1):** Added to the end of each byte.
        
    - **Gap:** Variable time gap between bytes.
        
    - **Application:** Keyboard to computer connection (low speed).
        
2. **Synchronous Transmission**
    
    - Bit stream is combined into long "frames" containing multiple bytes.
        
    - **No gaps** or start/stop bits between bytes.
        
    - Requires tight timing coordination (synchronization) between sender and receiver.
        
    - **Application:** High-speed computer-to-computer data transfer.
        
3. **Isochronous Transmission**
    
    - Guarantees data arrives at a **fixed rate**.
        
    - Uneven delays between frames are not acceptable.
        
    - **Application:** Real-time audio and video (e.g., TV broadcasts at 30 images/sec).
        

## 4.4 End-Chapter Materials Summary

- **Line Coding Schemes:** Unipolar (NRZ), Polar (NRZ-L, I, RZ, Biphase), Bipolar (AMI), Multilevel (2B1Q, 8B6T, 4D-PAM5), Multitransition (MLT-3).
    
- **Block Coding:** 4B/5B, 8B/10B.
    
- **Scrambling:** B8ZS, HDB3.
    
- **PCM:** Includes Sampling (Nyquist), Quantization, Encoding.
    
- **Modes:** Parallel vs. Serial (Asynch, Synch, Isoch).
    

### 4.5 Practice Set

Refer to the textbook for:

- **Questions (Q4-1 to Q4-12):** Conceptual review.
    
- **Problems (P4-1 to P4-20):** Calculations involving Nyquist rates, SNRdB, and bandwidth requirements.