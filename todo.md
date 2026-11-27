# TODO

- [ ] Encoder height 5.0 → 5.1 mm (TTC 1035111112000). Current design assumes `H = 5.0`; H is PCB surface to shaft center, so move the daughter PCB 0.1 mm further from the roller axis (or the axis away from the PCB), then re-check shell clearances and fits.
- [ ] Rebuild the encoder footprint on `ttc_encoder_daughter.kicad_pcb` (now `TTC_Gold_E203_07G4_2412_01`: lugs ±5.0 oval 0.6×1.8, no lug-row offset) to the shared pattern in AGENTS.md: lugs ±4.5, 1.8×2.1, offset 2.0 from the pin row.
- [ ] Fix encoder pinout: footprint has GND on the left pin. Common C must be the end pin matching the christrotter orientation (AGENTS.md).
