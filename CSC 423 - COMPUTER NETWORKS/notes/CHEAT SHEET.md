Here is a comprehensive formula cheat sheet extracted from the provided sources, organized by chapter.

### **Chapter 1: Introduction**

**Network Topology**

- **Mesh Topology Links:** In a mesh topology with $n$ nodes, the number of duplex-mode links required is: $$ \text{Links} = \frac{n(n - 1)}{2} $$
    - _Where $n$ is the number of devices._

---

### **Chapter 3: Introduction to Physical Layer**

**Signal Characteristics**

- **Period and Frequency:** Period ($T$) and frequency ($f$) are inverses of each other. $$ f = \frac{1}{T} \quad \text{and} \quad T = \frac{1}{f} $$
    
    - _Frequency is in Hertz (Hz); Period is in seconds (s)._
- **Wavelength ($\lambda$):** $$ \text{Wavelength} = \text{Propagation Speed} \times \text{Period} $$ $$ \lambda = \frac{c}{f} $$
    
    - _Where $c$ is propagation speed and $f$ is frequency._
- **Bandwidth (Composite Signal):** $$ B = f_h - f_l $$
    
    - _Where $f_h$ is the highest frequency and $f_l$ is the lowest frequency._
- **Bit Length:** $$ \text{Bit Length} = \text{Propagation Speed} \times \text{Bit Duration} $$
    
    - _The distance one bit occupies on the transmission medium._

**Transmission Impairment (Decibels)**

- **Decibel (dB):** Measures relative strength between two signals ($P_1$ and $P_2$). $$ \text{dB} = 10 \log_{10} \left( \frac{P_2}{P_1} \right) $$
    
    - _If negative, the signal has attenuated (lost power)._
- **Power in dBm:** $$ \text{dB}_m = 10 \log_{10} P_m $$
    
    - _Where $P_m$ is the power in milliwatts (mW)._
- **Signal-to-Noise Ratio (SNR):** $$ \text{SNR} = \frac{\text{Average Signal Power}}{\text{Average Noise Power}} $$ $$ \text{SNR}_{\text{dB}} = 10 \log_{10} \text{SNR} $$
    
    - _SNR is often described in decibels ($\text{SNR}_{\text{dB}}$)._

**Data Rate Limits**

- **Nyquist Bit Rate (Noiseless Channel):** Defines the theoretical maximum bit rate for a noise-free channel. $$ \text{BitRate} = 2 \times B \times \log_2 L $$
    
    - _Where $B$ is bandwidth and $L$ is the number of signal levels._
- **Shannon Capacity (Noisy Channel):** Defines the theoretical highest data rate for a noisy channel. $$ \text{Capacity} = B \times \log_2 (1 + \text{SNR}) $$
    
    - _Where $B$ is bandwidth and $\text{SNR}$ is the signal-to-noise ratio (not in dB)._

**Performance Metrics**

- **Latency (Delay):** $$ \text{Latency} = \text{Propagation Time} + \text{Transmission Time} + \text{Queuing Time} + \text{Processing Delay} $$
    
- **Propagation Time:** $$ \text{Propagation Time} = \frac{\text{Distance}}{\text{Propagation Speed}} $$
    
- **Transmission Time:** $$ \text{Transmission Time} = \frac{\text{Message Size}}{\text{Bandwidth}} $$
    
- **Bandwidth-Delay Product:** $$ \text{Capacity of Link (in bits)} = \text{Bandwidth} \times \text{Delay} $$
    
    - _Defines the number of bits that can fill the link while in transit._

---

### **Chapter 4: Digital Transmission**

**Line Coding (Digital-to-Digital)**

- **Signal Rate (Baud Rate):** The relationship between data rate ($N$) and signal rate ($S$). $$ S = \frac{N}{r} $$
    
    - _Where $N$ is the data rate (bps) and $r$ is the number of data elements carried by each signal element._
- **Average Signal Rate:** $$ S_{ave} = c \times N \times \frac{1}{r} $$
    
    - _Where $c$ is a case factor based on the specific line coding scheme (e.g., $1/2$ for worst case)._
- **Minimum Bandwidth:** $$ B_{min} = c \times N \times \frac{1}{r} $$
    
    - _Bandwidth is proportional to the signal rate._
- **Maximum Data Rate (Nyquist Inverse):** $$ N_{max} = \frac{1}{c} \times B \times r $$
    

**Pulse Code Modulation (PCM) (Analog-to-Digital)**

- **Nyquist Sampling Theorem:** The sampling rate ($f_s$) must be at least twice the highest frequency in the signal ($f_{max}$). $$ f_s \ge 2 f_{max} $$
    
- **Quantization Step Size ($\Delta$):** $$ \Delta = \frac{V_{max} - V_{min}}{L} $$
    
    - _Where $L$ is the number of quantization zones/levels._
- **Signal-to-Noise Ratio (SNR) for PCM:** $$ \text{SNR}_{\text{dB}} = 6.02 n_b + 1.76 \text{ dB} $$
    
    - _Where $n_b$ is the number of bits per sample._
- **PCM Bit Rate:** $$ \text{Bit Rate} = \text{Sampling Rate} \times \text{Bits per Sample} $$ $$ \text{Bit Rate} = f_s \times n_b $$
    
- **Minimum PCM Bandwidth:** $$ B_{min} = n_b \times B_{analog} $$
    
    - _Assumes $1/r = 1$ (like NRZ coding)._