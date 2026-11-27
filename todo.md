# TODO

- [ ] Encoder height 5.0 → 5.1 mm (TTC 1035111112000). Current design assumes `H = 5.0`; update the daughter PCB placement, roller hex shaft length (now 5.0 mm, Y 1.1–6.1), and shell clearances, then re-check fits.
- [ ] Rebuild the encoder footprint on `ttc_encoder_daughter.kicad_pcb` (now `TTC_Gold_E203_07G4_2412_01`: lugs ±5.0 oval 0.6×1.8, no lug-row offset) to the shared pattern in AGENTS.md: lugs ±4.5, 1.8×2.1, offset 2.0 from the pin row.
- [ ] Fix encoder pinout: footprint has GND on the left pin. Common C must be the end pin matching the christrotter orientation (AGENTS.md).
