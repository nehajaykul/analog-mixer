# LTspice Simulation Guide

This document summarizes the LTspice simulation procedures used to verify the analog mixer design, including frequency response, noise performance, audio playback testing, potentiometer parameter sweeps, and clipping behavior.

---

* ==========================================
* NOISE ANALYSIS
* ==========================================
.noise V(sum_out_a) track_a dec 100 1 100000

* ==========================================
* WAV OUTPUT TESTING
* ==========================================
.wave "suma_mix.wav" 16 44100 V(sum_out_a)
.wave "high_test.wav" 16 44100 V(high_pass_a)
.wave "band_test.wav" 16 44100 V(band_pass_a)
.wave "low_test2.wav" 16 44100 V(low_pass_a)
.wave "mix.wav" 16 44100 V(master_out)
Purpose: Export simulated signals as WAV files for audio evaluation.

.tran 0 10m 0 1u
Purpose: Analyze time-domain audio waveforms and verify signal behavior.

* ==========================================
* POT VALUES & STANDARD RUNS
* ==========================================
.ac dec 100 20 20000

.step param master .001 .999 .1
Purpose: Evaluate circuit response across potentiometer ranges.

* ==========================================
* TRACK A
* ==========================================
.param low_a=.999
.param band_a=.999
.param high_a=.999
.param ch_a=.45
.param fade_a=.001
.param cfx_a=.5

**Note:** .999 pot values are used for testing voltage clipping

* ==========================================
* TRACK B
* ==========================================
.param low_b=.5
.param band_b=.5
.param high_b=.5
.param ch_b=.45
.param fade_b=.001
.param cfx_b=.5

**Note:** .5  pot values are used for testing standard functionality

* ==========================================
* MASTER
* ==========================================
.param cross=.5
.param master=.5
.param pfl=.5

* ==========================================
* VOLTAGE CLIPPING
* ==========================================
.param amp=1
.tran 0 10m 0 1u
.step param amp 1 14 1

.model CLIPLED (BV=9.1 IBV=0.001)
**Note:** CLIPLED is used to simulate 9.1V Zener Diodes
