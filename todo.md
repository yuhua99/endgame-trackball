# TODO

- [ ] Encoder height 5.0 → 5.1 mm (TTC 1035111112000). H is PCB surface to shaft center, so move the daughter PCB 0.1 mm further from the roller axis (or the axis away from the PCB), then re-check shell clearances and fits.
- [x] Rebuild the encoder footprint to the shared TTC/Alps/Kailh pattern (lugs ±4.5, 1.8×2.1, +2.0 from the pin row) and fix the pinout (A −2.5, B 0, C/GND +2.5, lugs toward the FPC).
- [ ] Shell fit for the new PCB: board is now 11.8 mm wide (was 11.4), so its floor-side edge sits at Z ≈ 1.3, but the bottom shell is solid below Z 1.5 there. Either cut a 0.2 mm relief in the floor under the PCB or raise the roller axis 0.2 mm.
- [ ] Encoder body position: with the real footprint (Alps geometry), the body center sits ~0.9 mm from the pin row toward the FPC (shell +Y), not on the pin row as `ttc_encoder_daughter_3d.step` models it. Re-check roller hex engagement and the body-to-roller gap, and update the 3D STEP.
- [x] Refill the B.Cu GND zone and run KiCad 9 DRC/ERC: DRC 0 / unconnected 0 / parity 0; ERC 1 expected warning (1V8 global label used once).
- [x] J1 pin 1 carries 1V8 like the stock encoder board (unused on this board).
