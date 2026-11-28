# AGENTS.md

Fork of the efog Endgame trackball: replace the stock encoder with side rollers (one per side wall), driven by a TTC 5.1 mm mouse encoder (`spec.md`) on a new daughter PCB.

## Layout
- `original/` — stock efog shells (`FDM_shell.step` top, `FDM_bottom.step` bottom). Read-only reference.
- `../endgame-trackball-hardware/` — stock KiCad (separate repo, read-only). Motherboard is rev7 (`trackball.kicad_pcb` in that repo is rev10; outline and encoder FPC are close enough to use as reference); stock encoder board `encoders-upgrade/encoders_upgrade.kicad_pcb` (EC05E encoder + 8P 0.5 mm FPC).
- Repo root — our outputs: `top_side_roller.step`, `bottom_side_roller.step`, `side_roller_d*.step`, `ttc_encoder_daughter.kicad_*`.
- `todo.md` — open work. Read before starting; tick items when done.
- `spec.md` — dimensions of the parts we buy or reuse (encoder, fasteners, FPC connector, self-tap hole). Read before modelling a fit, a hole, or a footprint.

## Scope
- Change: top/bottom shell, roller, encoder daughter PCB.
- Keep: motherboard, stock floor openings, Z=10.00 mm shell split, everything not touched by the roller.
- One roller + one daughter PCB per side (left and right). Both sides use the same PCB design (no mirrored variant).
- Scroll only; no middle click, so the FPC switch pins stay unused.
- The daughter PCB connects to the motherboard through the stock 8P 0.5 mm FPC and its pinout.

## Manufacturing
- Shells and rollers: JLCPCB MJF nylon (PA12). Size walls, clearances, and press fits for MJF, not FDM.
- Roller is one MJF part (`side_roller_d14.step`): Ø14 grooved drum, Ø4 stub journals at both ends, printed hex shaft into the encoder. Printed hex is intentional: no off-the-shelf metal 1.7 mm hex shaft exists.
- Daughter PCB: JLCPCB, 1.6 mm. Trim all encoder pins and lugs to ≤ 0.6 mm behind the PCB after soldering; the shell wall behind the PCB only has shallow channels for them.
- Assembly: push the roller's hex onto the encoder first, then press PCB and roller into the bottom shell as one unit: the PCB slides down its slot and snaps under two flexible hooks at its ends, both journals rest in open U seats. The top shell holds nothing: its buttons sit above this area and must stay free.
- Hardware (reuse stock parts only): heat-set insert M2×3.5×2.5, M2×4 ISO7380 screw, magnet Ø4×2.

## Workflow
- CAD: use the `cad` skill. PCB: use the `pcb` skill.
- KiCad is 9.0 (`CAD_KICAD_CLI=/usr/bin/kicad-cli`) for DRC, ERC, zone refill, and exports. cad's nightly (needed for `kicad_pcb.edit`) does not run here (glibc 2.35 < 2.36), so edit `.kicad_pcb` / `.kicad_sch` as text and keep them in KiCad 9 format.
- Measure fits against `original/` and `endgame_motherboard_3d.step`; report clearances in mm.
- Commit each finished step without asking. Messages use Conventional Commits (`feat:`, `fix:`, `docs:`, `chore:`).
- CAD scripts: OCCT is single-core. Time one pass before looping booleans, checks, or defeatures; run anything over 1 min in the background under `timeout 600`, logging progress with `flush=True`.
- Fix faulty geometry at the modelling step that made it (extend tools past coplanar faces, set a fuzzy value); run `BRepAlgoAPI_Check` once, at the end.
