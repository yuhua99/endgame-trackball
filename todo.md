# TODO

- [x] Encoder height 5.0 → 5.1 mm: daughter PCB moved away from the roller axis.
- [x] Encoder footprint on the shared TTC/Alps/Kailh pattern, pinout fixed.
- [x] Bottom shell PCB slot floor lowered for the 11.8 mm board.
- [x] Encoder footprint shifted toward the roller so the body sits where the 3D model has it and the lugs clear the screw; blind pockets for pins and lugs in the shell wall.
- [x] Daughter PCB fixing: M2 self-tap hole instead of the heat-set insert, swapped with the locating pin.
- [x] Sensor PCB mount: restored the boss the roller pocket had cut off (from `original/FDM_bottom.step`), and turned its 4 heat-set insert holes into M2 self-tap holes.
- [x] B.Cu GND zone refilled; KiCad 9 DRC/ERC clean (ERC keeps the intended 1V8 single-label warning).
- [x] J1 pin 1 carries 1V8 like the stock encoder board (unused on this board).
- [x] Bottom shell: filled the 4 exterior hex recesses, the countersunk hole above the lens, the two blind holes at (±30.17, −40.38) and the 0.01 mm floor bumps around them.
- [ ] Before fab: export Gerbers, drill files and PCB STEP for JLCPCB with kicad-cli, and run a final interference check of top shell, bottom shell, rollers and daughter PCB.
