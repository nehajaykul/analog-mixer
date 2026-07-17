# analog-mixer
2-Channel-Analog-DJ-Mixer

A fully analog 2-channel DJ mixer designed from first principles, 
simulated in LTspice, and laid out in KiCad for JLCPCB fabrication.

## Signal Chain

Input (3.5mm TRS) → L+R summing → 4th-order Sallen-Key HPF (f₀=12Hz) 
→ Cascaded KHN SVF EQ (200Hz / 4kHz crossovers) → Gain/trim 
→ Channel fader → Crossfader → Virtual-earth summing amp → Master output

## Features

- 3-band parametric EQ per channel (HI/MID/LOW) with kill switches
- Cascaded Kerwin-Huelsman-Newcomb state-variable filters; Qs chosen for maximum passband flatness
  - Stage 1: f₀ = 200 Hz, Q = ~1.0
  - Stage 2: f₀ = 4 kHz, Q = ~.83
- Phase cancellation resolved at summing node — <1.1 dB passband deviation
- Pre-fader listen (PFL) cue system with headphone output; tapped before gain/trim stage
- Clipping LED indicator with 9.1V zener threshold (~11V signal threshold)
- Isolated ±15V dual-rail power supply (Traco TMR 6-1223)
- 15+ NE5532/TL072 op-amps throughout signal path

## Specifications

| Parameter | Value |
|-----------|-------|
| Input | 3.5mm TRS, line level |
| EQ crossovers | 200 Hz, 4 kHz |
| EQ range | Cut to +14 dB per band |
| Power supply | 12V DC input → ±15V isolated |
| Op-amps | NE5532 (signal path), TL072 (monitor path) |
| PCB | 2-layer, JLCPCB fabrication |

## Repository Structure
