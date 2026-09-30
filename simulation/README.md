# Simulation (PSpice)

The complete link — audio input to loudspeaker — was simulated as a single circuit in PSpice. The optical channel is modelled by a current-controlled current source **F1**, which senses the laser current and injects a proportional photocurrent into the receiver node. The laser is modelled as a 2.5 V source in series with 20 Ω.

## Analyses

| Analysis | Result | Plot |
|---|---|---|
| Bias point | Mid-rail 4.500 V; U2 pin 3 at 1.154 V; Q1 emitter 1.155 V → I_laser ≈ 30 mA | [bias_point.jpg](../images/simulation/bias_point.jpg) |
| AC sweep | Flat mid-band; upper corner ≈ 10.7 kHz; roll-off below a few hundred Hz | [log](../images/simulation/ac_sweep_log.png) · [linear](../images/simulation/ac_sweep_linear.jpg) |
| Transient (500 Hz) | Clean recovered sinusoid, no clipping | [transient_500Hz.jpg](../images/simulation/transient_500Hz.jpg) |

## Project files

Place the PSpice / OrCAD Capture project files in this folder, for example:

```
simulation/
├── LiFi_Link.opj        # OrCAD project
├── LiFi_Link.DSN        # Schematic design
└── LiFi_Link-PSpiceFiles/   # Simulation profiles (*.sim) — keep; outputs (*.dat, *.out) are git-ignored
```

Generated output (`*.dat`, `*.out`, `*.log`, lock/backup files) is excluded by `.gitignore`.
