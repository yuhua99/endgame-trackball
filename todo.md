# TODO

- [ ] Encoder height 5.0 → 5.1 mm (TTC 1035111112000). Current design assumes `H = 5.0`; update the daughter PCB placement, roller hex shaft length (now 5.0 mm, Y 1.1–6.1), and shell clearances, then re-check fits.
- [ ] Encoder footprint on `ttc_encoder_daughter.kicad_pcb` is `TTC_Gold_E203_07G4_2412_01` with lugs at ±5.0 mm (10.0 span). Drawing (`ref/ttc_103_drawing.png`) says 11.60 mm. Rebuild the footprint for 1035111112000 and decide whether 11.60 is the lug tip or lug center distance.
- [ ] Encoder pinout: footprint puts common (GND) on the left pin and A in the middle. Mouse encoders usually have common in the middle (A-C-B). Confirm with a multimeter before fab.
