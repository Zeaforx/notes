# Data Communication Formulas Cheat Sheet

A comprehensive collection of calculation formulas for data and signals, transmission, and bandwidth utilization.

## Chapter 3: Data and Signals

- Relationship between Peak and RMS Amplitude
  For power signals, the peak value is related to the RMS value:
  $$Peak\ value = 2^{1/2} \times rms\ value$$
- Frequency and Period
  Inversely related:
  $$f = \frac{1}{T}$$$$T = \frac{1}{f}$$
- Phase Offset
  The phase in degrees for an offset signal:
  $$\text{Phase} = \text{Cycle Fraction} \times 360$$
- Bandwidth of a Composite Signal
  Difference between the highest ($f_h$) and lowest ($f_l$) frequencies:
  $$B = f_h - f_l$$
- Nyquist Bit Rate (Noiseless Channel)
  Maximum bit rate for a noiseless channel:
  $$BitRate = 2 \times Bandwidth \times \log_2 L$$
  (Where $L$ is the number of signal levels)
- Shannon Capacity (Noisy Channel)
  Theoretical capacity limit for a noisy channel:
  $$C = B \log_2(1 + SNR)$$
- Signal-to-Noise Ratio (SNR) in Decibels
  Converts power ratio to logarithmic scale:
  $$SNR_{dB} = 10 \log_{10} SNR$$
- Capacity Approximation (High SNR)
  Estimate for very high SNR levels:
  $$C \approx B \times \left(\frac{SNR_{dB}}{3}\right)$$
- Network Throughput
  Total data passed over time:
  $$Throughput = \frac{\text{Frames} \times \text{Bits per Frame}}{\text{Time}}$$
- Propagation Time
  Time for a signal to travel distance:
  $$Propagation\ Time = \frac{Distance}{Propagation\ Speed}$$
- Transmission Time
  Time to push a message onto the medium:
  $$Transmission\ Time = \frac{\text{Message Size}}{\text{Bandwidth}}$$
- Bandwidth-Delay Product
  Defines the bit volume of a link:
  $$Volume = Bandwidth \times Delay$$

## Chapter 4: Digital Transmission

- Baud Rate (Signal Rate $S$)
  Number of signal elements per second:
  $$S = c \times N \times \frac{1}{r}$$
  (Where $c$ is the case factor, $N$ is the bit rate, and $r$ is bits per signal element)
- Maximum Data Rate
  $$N_{max} = \frac{1}{c} \times B \times r$$
- PCM Quantization SNR
  SNR for Analog-to-Digital conversion:
  $$SNR_{dB} = 6.02 n_b + 1.76$$
  (Where $n_b$ is the number of bits per sample)

## Chapter 5: Analog Transmission

- Digital-to-Analog Baud Rate
  Signal rate calculation:
  $$S = N \times \frac{1}{r}$$
- ASK and PSK Bandwidth
  Required bandwidth for Amplitude and Phase Shift Keying:
  $$B = (1 + d) \times S$$
  (Where $d$ is a factor related to the modulation process)
- FSK Bandwidth
  Includes frequency shift for Frequency Shift Keying:
  $$B = (1 + d) \times S + 2\Delta f$$
- Amplitude Modulation (AM) Bandwidth
  Twice the audio signal bandwidth:
  $$B_{AM} = 2B$$
- FM and PM Bandwidth
  For Frequency and Phase modulation:
  $$B_{FM/PM} = 2(1 + \beta)B$$

## Chapter 6: Bandwidth Utilization

- FDM Link Bandwidth
  Sum of channel bandwidths plus guard bands:
  $$B = \sum B_{channels} + \sum B_{guard\ bands}$$
- Synchronous TDM Data Rate
  Output link rate is $n$ times the input rate:
  $$Rate_{link} = n \times Rate_{input}$$
- TDM Time Slot Duration
  Duration of an output slot:
  $$Duration_{output} = \frac{1}{n} \times Duration_{input}$$
- TDM Frame Size with Overhead
  $$Size = (\text{Number of Inputs} \times \text{Bits per Unit}) + \text{Framing Bits}$$

### **Analogy for Visualization**

> If you think of these formulas as **vehicle specifications**:
>
> - **Bandwidth** is the width of the highway lanes.
> - **Baud Rate** is how many vehicles pass a point per second.
> - **Shannon Capacity** is the maximum speed limit the road can handle before the engine noise and traffic (noise) make it impossible to drive safely.
