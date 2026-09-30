# Hardware

Two independent breadboard assemblies (transmitter and receiver), each with its own 9 V supply, ground and decoupling, plus a bench power supply built by the group.

## Transmitter — key values

| Part | Value | Purpose |
|---|---|---|
| R1 / R6 | 1 kΩ / 2.2 kΩ | Preamp gain = 1 + R6/R1 = 3.2 (U1A, TL072) |
| R13 | 100 kΩ | Input bias to 4.5 V mid-rail |
| C6 | 47 pF | Preamp bandwidth limit / stability |
| C5 | 47 µF | Mid-rail (4.5 V) reference decoupling |
| R7 = R8, C7, C8 | 10 kΩ, 1 nF, 470 pF | Sallen-Key LPF, f_c ≈ 23 kHz, Q ≈ 0.73 (U1B) |
| R10 / R9 | 68 kΩ / 10 kΩ | Driver bias, V+ = 1.154 V |
| R11 | 38 Ω | Sets laser current: I = V_in / R11 (≈ 30 mA design) |
| U2, Q1 | LM358, BD135 | Closed-loop constant-current laser driver |
| C3 | — | Couples audio onto the driver bias |

## Receiver — key values

| Part | Value | Purpose |
|---|---|---|
| D (PD) | BPW34 | Reverse-biased PIN photodiode, C_j ≈ 25 pF |
| R18 | 470 Ω | Photodiode load, detector pole ≈ 13.5 kHz |
| R15 / R16 | 2.2 kΩ / 47 kΩ | Gain ≈ 22 (U3A, TL072) |
| C13 | 470 nF | High-pass ≈ 154 Hz — rejects 100 Hz lamp flicker |
| C10 | 100 pF | Stage stability |
| R23 = R24, C15, C16 | 10 kΩ, 2.2 nF, 1 nF | Sallen-Key LPF, f_c ≈ 10.7 kHz, Q ≈ 0.74 (U3B) |
| Volume | 10 kΩ pot | Output level |
| LM386 | Gain 20 (pins 1, 8 open) | Speaker driver, 220 µF output coupling |
| 100 Ω + 470 µF | — | Isolates front end from speaker current pulses |

Every IC has a 100 nF ceramic at its supply pin.

## Bench power supply

12 V / 1 A step-down transformer → 1N4007 full-wave bridge → 1000 µF reservoir → LM317 → 7809 (9 V rail).

## Recommended build order

1. Build the constant-current laser driver alone; verify the DC voltage across R11 with a multimeter before applying any signal.
2. Add the preamp and filter; check for a clean, unclipped waveform at U1B output.
3. Build the receiver; align the photodiode until its DC node voltage sits mid-range.
4. Bring both halves together and assess audio quality.

See [`BOM.csv`](BOM.csv) for the full parts list and prices.
