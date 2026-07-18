# 2-Channel-Analog-DJ-Mixer

A fully analog 2-channel DJ mixer designed from first principles, 
simulated in LTspice, and laid out in KiCad for JLCPCB fabrication.

## Signal Chain

[3.5mm Input] → [L+R Sum] → [Sallen-Key HPF] → [SVF EQ Stage 1: 200Hz]
    → [SVF EQ Stage 2: 4kHz] → [Gain/Trim] → [Channel Fader]
    → [Crossfader] → [Virtual-Earth Sum] → [Master Output]

## Features

- 3-band parametric EQ per channel (HI/MID/LOW) with kill switches
- Cascaded Kerwin-Huelsman-Newcomb state-variable filters; Qs chosen for maximum passband flatness
  - Stage 1: f₀ = 200 Hz, Q = ~1.0
  - Stage 2: f₀ = 4 kHz, Q = ~.83
- Reduced summing-node phase cancellation, achieving <1.1 dB response variation across the band-pass (200 Hz–4 kHz)
- Pre-fader listen (PFL) cue system with headphone output; tapped after gain/trim stage and before channel fader
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

```
/ltspice     — LTspice simulation files (.asc) for each circuit stage
/kicad       — KiCad schematic (.kicad_sch) and PCB layout (.kicad_pcb)
/gerbers     — Fabrication files for JLCPCB 2-layer PCB production
/docs        — Schematic PDF, simulation result plots, BOM
README.md    — Project overview
```
