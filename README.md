# Experiment 20: Undersampling in Software Defined Radio (SDR)

## Objectives
- Generate a narrowband DSBSC signal.  
- Understand undersampling (band-pass sampling) for direct down-conversion.  
- Recover a baseband message using Sample-and-Hold and LPF.  
- Investigate the role of synchronization and harmonics in SDR.

## Materials
- **Trainer:** Emona Telecoms-Trainer 101 + power-pack  
- **Oscilloscope:** Dual-channel 20MHz  
- **Modules:** Master Signals, Multiplier, Sample-and-Hold, Tuneable LPF, VCO  
- **Leads:** Oscilloscope and patch leads  

## Background
SDR allows flexible demodulation via software, but high-frequency signals require fast ADCs. Undersampling (band-pass sampling) lets a narrowband RF signal be sampled below its carrier frequency. By carefully choosing the sampling rate, one alias aligns at baseband, effectively down-converting the signal. Harmonics of the sampling clock can act as a virtual local oscillator. Synchronization is crucial; slight mismatches cause instability in the recovered signal.

## Procedure
### Bandwidth-Limited DSBSC Signal
1. Connect 2kHz sine (message) → Multiplier Y input; 100kHz cosine (carrier) → Multiplier X input.  
2. Observe DSBSC output on the oscilloscope in DUAL mode.  

### Undersampling for Direct Down-Conversion
3. Add Sample-and-Hold module; trigger with 8kHz clock.  
4. Connect S/H output to LPF; observe recovered baseband message.  

### Synchronization Effects
5. Replace 8kHz clock with VCO output (≈8.333kHz).  
6. Observe recovered message; adjust VCO frequency to reduce errors.  
7. Note that without phase-locking, recovered signal shows amplitude variations.

## Observations
- DSBSC contains sum and difference frequencies: 98 kHz & 102 kHz.  
- Bandwidth = 4 kHz (2 × message frequency).  
- LPF output reproduces the original 2kHz message.  
- 12th harmonic of 8.333kHz sampling clock aligns with 100kHz carrier.  
- Frequency mismatch causes instability due to lack of phase synchronization.

## Q&A
- **DSBSC frequencies:** f_c ± f_m → 100 ± 2 kHz = 98 kHz & 102 kHz.  
- **Bandwidth:** 2 × f_m = 4 kHz.  
- **LPF output:** Recovered baseband message.  
- **Sampling harmonic:** 12 × 8.333 kHz ≈ 100 kHz acts as virtual LO.  
- **VCO adjustment issue:** Without phase-locking, small frequency errors create beat effects, preventing stable recovery.

## Summary
Undersampling a narrowband DSBSC signal can down-convert it directly to baseband using aliasing. The LPF recovers the original message, demonstrating SDR principles. However, synchronization is critical; mismatched clocks produce amplitude fluctuations. This experiment illustrates how SDR leverages clever sampling and processing over traditional analog mixers.
