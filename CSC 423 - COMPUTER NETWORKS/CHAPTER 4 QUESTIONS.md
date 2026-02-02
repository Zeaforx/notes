# Chapter 4: Digital Transmission - Practice Set Solutions

## 4.5.2 Questions

**Q4-1. List three techniques of digital-to-digital conversion.**

1. Line Coding
    
2. Block Coding
    
3. Scrambling
    

**Q4-2. Distinguish between a signal element and a data element.**

- **Data Element:** The smallest entity that can represent a piece of information (the bit). It is what we need to send.
    
- **Signal Element:** The shortest unit (timewise) of a digital signal. It is the carrier.
    

**Q4-3. Distinguish between data rate and signal rate.**

- **Data Rate (Bit Rate):** The number of data elements (bits) sent in 1 second (bps).
    
- **Signal Rate (Baud Rate):** The number of signal elements sent in 1 second (baud).
    

**Q4-4. Define baseline wandering and its effect on digital transmission.**

Baseline wandering is the drift in the running average of the received signal power, caused by a long string of 0s or 1s. It makes it difficult for the receiver to decode the signal correctly because the receiver uses this average to distinguish between high and low levels.

**Q4-5. Define a DC component and its effect on digital transmission.**

A DC component refers to frequencies around zero (constant voltage) present in the signal spectrum. It creates problems for systems that cannot pass low frequencies (e.g., telephone lines) or systems using electrical coupling (transformers).

**Q4-6. Define the characteristics of a self-synchronizing signal.**

A self-synchronizing signal includes timing information within the data being transmitted. This is typically achieved by having transitions in the signal level (e.g., at the middle of the bit interval) that alert the receiver to the timing of the pulse, allowing the receiver to reset its clock.

**Q4-7. List five line coding schemes discussed in this book.**

1. Unipolar (NRZ)
    
2. Polar (NRZ-L, NRZ-I, RZ, Manchester, Differential Manchester)
    
3. Bipolar (AMI, Pseudoternary)
    
4. Multilevel (2B1Q, 8B6T, 4D-PAM5)
    
5. Multitransition (MLT-3)
    

**Q4-8. Define block coding and give its purpose.**

Block coding (mB/nB coding) involves changing a block of $m$ bits into a block of $n$ bits, where $n > m$. Its purpose is to provide redundancy to ensure synchronization and to provide inherent error detection.

**Q4-9. Define scrambling and give its purpose.**

Scrambling is a technique used in long-distance communication (often with bipolar AMI) to substitute long sequences of zero-level pulses with a combination of other levels. Its purpose is to provide synchronization without increasing the number of bits (unlike block coding) and to avoid baseline wandering issues.

**Q4-10. Compare and contrast PCM and DM.**

- **PCM (Pulse Code Modulation):** Finds the value of the signal amplitude for each sample. It is more complex and typically requires a higher bandwidth.
    
- **DM (Delta Modulation):** Finds the change (delta) from the previous sample. It is simpler to implement but can suffer from slope overload if the signal changes too rapidly.
    

**Q4-11. What are the differences between parallel and serial transmission?**

- **Parallel:** Multiple bits are sent simultaneously over multiple wires (n bits on n wires). It is faster but more expensive and limited to short distances.
    
- **Serial:** Bits are sent one after another over a single wire. It is cheaper and used for longer distances but is slower (factor of n) compared to parallel.
    

**Q4-12. List three different techniques in serial transmission and explain the differences.**

1. **Asynchronous:** Uses start and stop bits (and gaps) to group data into bytes. Timing is unimportant at the byte level, but synchronization is maintained within the byte.
    
2. **Synchronous:** Sends a continuous stream of bits without start/stop bits or gaps. The receiver is responsible for grouping bits (often using framing). Requires tighter clock synchronization.
    
3. **Isochronous:** Guarantees data arrival at a fixed rate. Used for real-time applications (audio/video) where uneven delays are unacceptable.
    

## 4.5.3 Problems

**P4-1. Calculate the value of the signal rate for each case in Figure 4.2 if the data rate is 1 Mbps and** $c=1/2$**.**

Formula: $S = c \times N \times (1/r)$  

- **a. (**$r=1$**):** $S = 0.5 \times 1 \text{ Mbps} \times 1 = \mathbf{500 \text{ kbaud}}$  
    
- **b. (**$r=1/2$**):** $S = 0.5 \times 1 \text{ Mbps} \times 2 = \mathbf{1 \text{ Mbaud}}$  
    
- **c. (**$r=2$**):** $S = 0.5 \times 1 \text{ Mbps} \times 0.5 = \mathbf{250 \text{ kbaud}}$  
    
- **d. (**$r=4/3$**):** $S = 0.5 \times 1 \text{ Mbps} \times (3/4) = \mathbf{375 \text{ kbaud}}$  
    

**P4-2. In a digital transmission, the sender clock is 0.2 percent faster than the receiver clock. How many extra bits per second does the sender send if the data rate is 1 Mbps?**

Extra bits $= 1,000,000 \text{ bps} \times 0.002 = \mathbf{2,000 \text{ bits}}$  

**P4-3. Draw the graph of the NRZ-L scheme...**

_(Description of graph)_:

- **a. 00000000:** A constant positive voltage level (assuming previous level was positive and next bit 0 is positive? Or usually 0 is positive and 1 is negative in NRZ-L, or vice-versa. Text says "level determines value". If we assume 0 = High, 1 = Low). Graph is a straight horizontal line at High. Bandwidth is very close to 0 (DC).
    
- **b. 11111111:** A constant low voltage level. Graph is a straight horizontal line at Low. Bandwidth is near 0.
    
- **c. 01010101:** Alternating High and Low. Looks like a sine wave with frequency $N/2$. Bandwidth is around $N/2$.
    
- **d. 00110011:** High for 2 bits, Low for 2 bits. Frequency is $N/4$. Bandwidth is around $N/4$.
    

**P4-7. Repeat Problem P4-3 for the 2B1Q scheme...**

_2B1Q maps 2 bits to 1 signal level (Levels: -3, -1, +1, +3)._

- **a. 00...:** (Assuming 00 maps to +1 or similar). Constant level.
    
- **b. 11...:** Constant level.
    
- **c. 0101...:** (01 maps to -1? check standard). Constant level.
    
- **d. 0011...:** 00 -> Level A, 11 -> Level B. Alternating levels.
    

**P4-9. Find the 8-bit data stream for each case depicted in Figure 4.36.**

- **a. NRZ-I:** (Transition = 1, No Transition = 0).
    
    - Bit 1: High (Transition from prev state? Assume yes). -> 1
        
    - Bit 2: Low (Transition). -> 1
        
    - Bit 3: Low (No Trans). -> 0
        
    - Bit 4: Low (No Trans). -> 0
        
    - Bit 5: High (Transition). -> 1
        
    - Bit 6: Low (Transition). -> 1
        
    - Bit 7: High (Transition). -> 1
        
    - Bit 8: High (No Trans). -> 0
        
    - **Result:** `1 1 0 0 1 1 1 0`
        
- **b. Differential Manchester:** (Transition at start = 0, No Trans at start = 1).
    
    - Bit 1: Transition at start. -> 0
        
    - Bit 2: No transition at start. -> 1
        
    - Bit 3: No transition at start. -> 1
        
    - Bit 4: Transition at start. -> 0
        
    - Bit 5: No transition at start. -> 1
        
    - Bit 6: Transition at start. -> 0
        
    - Bit 7: Transition at start. -> 0
        
    - Bit 8: No transition at start. -> 1
        
    - **Result:** `0 1 1 0 1 0 0 1`
        
- **c. AMI:** (0 = Zero level, 1 = Alternating Non-Zero).
    
    - Bit 1: 0 level -> 0
        
    - Bit 2: +V -> 1
        
    - Bit 3: 0 level -> 0
        
    - Bit 4: -V -> 1
        
    - Bit 5: +V -> 1
        
    - Bit 6: 0 level -> 0
        
    - Bit 7: 0 level -> 0
        
    - Bit 8: -V -> 1
        
    - **Result:** `0 1 0 1 1 0 0 1`
        

**P4-10. An NRZ-I signal has a data rate of 100 Kbps... calculate normalized energy (P)...**

Using Figure 4.6 (Bandwidth graph):

- $f = 0$ Hz ($f/N = 0$): $P \approx \mathbf{1.0}$  
    
- $f = 50$ KHz ($f/N = 0.5$): $P \approx \mathbf{0.4 \text{ to } 0.5}$  
    
- $f = 100$ KHz ($f/N = 1$): $P \approx \mathbf{0.0}$  
    

**P4-11. A Manchester signal has a data rate of 100 Kbps... calculate normalized energy (P)...**

Using Figure 4.8:

- $f = 0$ Hz ($f/N = 0$): $P \approx \mathbf{0.0}$  
    
- $f = 50$ KHz ($f/N = 0.5$): $P \approx \mathbf{0.3 \text{ to } 0.4}$  
    
- $f = 100$ KHz ($f/N = 1$): $P \approx \mathbf{0.6 \text{ (Peak)}}$  
    

**P4-12. The input stream to a 4B/5B block encoder is 0100 0000 0000 0000 0000 0001...**

- **a. Output stream:**
    
    Using Table 4.2 Mapping:
    
    0100 -> 01010
    
    0000 -> 11110
    
    0001 -> 01001
    
    **Output:** `01010 11110 11110 11110 11110 01001`
    
- **b. Longest sequence of 0s in input:**
    
    Input: `01`**`00 0000 0000 0000 0000 000`**`1`.
    
    Count: $2 + 16 + 3 = \mathbf{21}$ zeros.
    
- **c. Longest sequence of 0s in output:**
    
    Output stream junction: `...11110` followed by `01001`.
    
    Sequence: `01` or `00`.
    
    Max consecutive zeros = **2**.
    

**P4-13. How many invalid (unused) code sequences can we have in 5B/6B encoding? How many in 3B/4B encoding?**

- **5B/6B:** Total codes ($2^6 = 64$). Valid data ($2^5 = 32$). Unused = $64 - 32 = \mathbf{32}$.
    
- **3B/4B:** Total codes ($2^4 = 16$). Valid data ($2^3 = 8$). Unused = $16 - 8 = \mathbf{8}$.
    

**P4-14. What is the result of scrambling the sequence 11100000000000 using...**

_(Sequence: 1 1 1 followed by 11 zeros. Last level +)_

- **a. B8ZS:** (Substitutes 8 zeros with 000VB0VB).
    
    Sequence: 1(+) 1(-) 1(+) **0 0 0 0 0 0 0 0** 0 0 0.
    
    Violation (V) has same polarity as prev (+). Bipolar (B) has opposite.
    
    Substitution: 0 0 0 V(+) B(-) 0 V(+) B(-).
    
    **Result:** `+ - + 0 0 0 + - 0 + - 0 0 0`
    
- **b. HDB3:** (Substitutes 4 zeros).
    
    Sequence: 1(+) 1(-) 1(+) **0 0 0 0** **0 0 0 0** 0 0 0.
    
    1. First 4 zeros: # of 1s since last sub is 3 (odd). Sub: **000V**.
        
        Prev pulse (+). V is (+).
        
        Pattern: `0 0 0 +`.
        
    2. Next 4 zeros: # of 1s since last sub (which was the V in step 1) is 0 (even). Sub: **B00V**.
        
        Prev pulse was V(+). B is (-). V is (-).
        
        Pattern: `- 0 0 -`.
        
    3. Remaining 3 zeros: Encoded as `0 0 0`.
        
        **Result:** `+ - + 0 0 0 + - 0 0 - 0 0 0`
        

**P4-15. What is the Nyquist sampling rate for each...**

- **a. Low-pass bandwidth 200 KHz:** $2 \times 200 \text{ KHz} = \mathbf{400,000 \text{ samples/s}}$  
    
- **b. Band-pass bandwidth 200 KHz (lowest 100 KHz):**
    
    Highest freq = $100 + 200 = 300 \text{ KHz}$.
    
    Rate = $2 \times 300 \text{ KHz} = \mathbf{600,000 \text{ samples/s}}$  
    

**P4-16. We have sampled a low-pass signal with a bandwidth of 200 KHz using 1024 levels...**

- **a. Bit rate:**
    
    Sampling rate = $400,000$ samples/s.
    
    Bits per sample ($n$) = $\log_2(1024) = 10$ bits.
    
    Rate = $400,000 \times 10 = \mathbf{4 \text{ Mbps}}$  
    
- **b. SNRdB:**
    
    $SNR_{dB} = 6.02n + 1.76 = 6.02(10) + 1.76 = \mathbf{61.96 \text{ dB}}$  
    
- **c. PCM Bandwidth:**
    
    $B_{min} = n \times B_{analog} = 10 \times 200 \text{ KHz} = \mathbf{2 \text{ MHz}}$  
    

**P4-17. What is the maximum data rate of a channel with a bandwidth of 200 KHz if we use four levels of digital signaling.**

Nyquist Formula: $N_{max} = 2 \times B \times \log_2(L)$

$N_{max} = 2 \times 200,000 \times \log_2(4) = 400,000 \times 2 = \mathbf{800 \text{ kbps}}$  

**P4-18. An analog signal has a bandwidth of 20 KHz. If we sample this signal and send it through a 30 Kbps channel, what is the SNRdB?**

_Note: The channel capacity (30 Kbps) limits the bit rate. Minimum sampling rate (Nyquist) for 20 KHz signal is 40,000 samples/s._

Bits per sample $n = \text{Data Rate} / \text{Sampling Rate} = 30,000 / 40,000 = 0.75$ bits.

(This implies undersampling or insufficient quantization for standard PCM).

Using the formula strictly:

$SNR_{dB} = 6.02(0.75) + 1.76 = \mathbf{6.28 \text{ dB}}$  

**P4-19. We have a baseband channel with a 1-MHz bandwidth. What is the data rate for this channel if we use each of the following...**

_Using minimum bandwidth formulas from Table 4.1 (_$N = \text{Rate}$_)_

- **a. NRZ-L (**$B = N/2$**):** $1 \text{ MHz} = N/2 \Rightarrow N = \mathbf{2 \text{ Mbps}}$  
    
- **b. Manchester (**$B = N$**):** $1 \text{ MHz} = N \Rightarrow N = \mathbf{1 \text{ Mbps}}$  
    
- **c. MLT-3 (**$B = N/3$**):** $1 \text{ MHz} = N/3 \Rightarrow N = \mathbf{3 \text{ Mbps}}$  
    
- **d. 2B1Q (**$B = N/4$**):** $1 \text{ MHz} = N/4 \Rightarrow N = \mathbf{4 \text{ Mbps}}$  
    

**P4-20. We want to transmit 1000 characters with each character encoded as 8 bits.**

Total Data bits = $1000 \times 8 = 8000$ bits.

- **a. Synchronous transmission:** (Assuming continuous stream with negligible overhead).
    
    Transmitted bits $\approx \mathbf{8000 \text{ bits}}$.
    
- **b. Asynchronous transmission:** (Requires 1 start bit, 1 stop bit per char = 10 bits/char).
    
    Transmitted bits = $1000 \times 10 = \mathbf{10,000 \text{ bits}}$.
    
- **c. Redundancy percent:**
    
    - **Synchronous:** $\approx \mathbf{0\%}$  
        
    - **Asynchronous:** $(10000 - 8000) / 10000 = \mathbf{20\%}$ (or $25\%$ if calculated as overhead/data).