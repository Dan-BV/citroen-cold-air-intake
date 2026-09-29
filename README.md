# Citroën Cold Air Intake Flange

A 3D-printable cold air intake duct for a Citroën engine bay. It takes air from the
radiator cross-member (a rectangular opening cut into the raised plastic bump in front of
the hood-seal lip) and delivers it through a bayonet socket to the OEM corrugated hose
(bellows) that plugs into the air-filter box.

The shape was designed in Autodesk Fusion against a photogrammetry scan of the engine bay,
scaled from the known Ø63 mm filter inlet, and checked for collisions with the scan.

![Final part](images/final_iso.png)

![Mouth](images/mouth_iso.png)

## Repository layout

| Path | Contents |
|---|---|
| `model/` | Final assembled part (`.f3d`, `.step`, `.stl`) in car coordinates |
| `parts/` | The three print parts, already oriented for printing (`.stl`, `.step`, `.f3d`) |
| `print/` | Fusion print layout with all three parts on the bed |
| `references/flange_scan/` | 3D scan (OBJ) of the OEM bayonet flange used as the pattern for the outlet socket |
| `references/bellows_scan/` | 3D scan (OBJ) of the OEM corrugated hose (bellows) |
| `images/` | Renders |

All STL files are in millimetres. The full-resolution Part 1 and Part 2 STLs (≈ 55–60 MB each,
0.01 mm chord tolerance) are too large for the repository, so they are stored zipped as
`parts/Part1_mouth_clips.stl.zip` and `parts/Part2_bend_tube.stl.zip`.

## Design summary

| Feature | Value |
|---|---|
| Inlet (mouth) | True rectangle 160 × 49 mm, 90° corners, on the flat rear wall of the cross-member bump (narrowed from 166 mm after a test fit on the car) |
| Mounting face | Offset 1 mm from the bump wall for 1 mm double-sided silicone tape; flat land ≈ 8 mm all round |
| Inlet edge | 3 mm fillet on the inner edge |
| Wall thickness | 2.5 mm (10 mm at the mouth, tapering) |
| Width / cross-section | Width is largest at the 160 mm mouth and decreases smoothly and monotonically (158 → 150 mm over the hood-seal lip → 133 → 100 → Ø63 tube); inner area ≥ 26.4 cm² everywhere (Ø58 tube), no pinch points |
| Outlet | Separate bayonet flange (Part 3) on the Ø63 spigot, fitted to the measured bellows cuff with every diameter 1 mm larger than the cuff: OD 73 mm, height 46 mm; spigot sleeve Ø63.3 × 10 mm → 45° cone → Ø54 ring (flush with the cuff bore) → cuff stop → Ø62 → R4 shoulder → Ø64 up to the rim; two through windows 29° × 10 mm, two entry grooves (to Ø68) from the rim down to the windows, 30° twist; twist-lock counter-clockwise viewed into the filter inlet |
| Spigot / flange joint | The Part 2 bore narrows from Ø58 to Ø54 inside the spigot along an S-curve of two tangent R38.8 arcs (no kinks); the spigot tip is a 45° cone that seats on the flange cone, so the flow path is a continuous Ø54 from Part 2 through the flange ring into the bellows cuff, with no step or gap |
| Bellows fit | OEM bellows cuff (measured): end Ø59 with R1 edge, sealing bead Ø61, Ø60, R4 shoulder, Ø63, wall 2.5 mm (bore Ø54); two wedge lugs 15 mm wide × 9 mm long, rising to 2.5 mm (Ø67) at the back, 26 mm from the cuff end. Clearance 0.5 mm per side radially and around the lugs, 0.5 mm axial lug play. Free length ≈ 146 mm, fully compressed ≈ 109 mm; the rim position in the car is unchanged, the cuff stop is 1 mm closer to the filter than in the previous flange |
| Socket axis | Tilted 25° down from the filter-inlet axis so the bellows takes part of the bend (gentler S-bend, min. centre-line radius ≈ 83 mm) |
| Collar joint | Part 2 ends in a collar that slides over the Part 1 end (0.15 mm clearance, 10 mm overlap, 2 mm wall); Part 1 butts against an internal shoulder with a flush bore. The outside step at the start of the collar is filled by a 25° chamfer (≈ 4.6 mm long) so Part 2 prints without supports |
| Clips | 2 snap saddles (26 mm wide, at x = −30 / +60 mm) on the hood-seal lip + 3 snap clips (30 mm wide, at x = −33 / +25 / +60 mm) on the small floor rib; 2 mm root gussets, spring legs 3.3–3.5 mm |

![Side view](images/final_side.png)

![Clips](images/clips_side.png)

## Printing

Tested setup: Creality Ender 3 Pro (220 × 220 × 250 mm), **PETG** 1.75 mm.
PLA/PLA+ is not suitable under the hood (softens at 55–60 °C). PETG is fine at the
cross-member, especially with an external heat-reflective wrap. ASA/ABS or PA-CF are better
if you have an enclosed printer.

| Part | Size (mm) | Orientation (as exported) | Supports |
|---|---|---|---|
| `Part1_mouth_clips` | 172 × 106 × 162 | Joint end (the face that butts into the Part 2 collar) flat on the bed; tape land on top; clip legs at ≈ 33° to the layers | Tree supports touching build plate only — all clip overhangs are reachable from the plate, nothing inside the duct |
| `Part2_bend_tube` | 110 × 119 × 173 | Spigot tip down (1 mm flat ring Ø54–56 on the bed — use a brim) | None (steepest overhang ≈ 43° at the collar chamfer) |
| `Part3_bayonet_flange` | 73 × 73 × 46 | Base (spigot sleeve) down | None (45° cone under the stop ring, windows bridge ≈ 18 mm) |

Suggested PETG settings: nozzle 240–245 °C, bed 80 °C (glue stick as release layer),
fan 30–40 %, 40–50 mm/s, 4 perimeters, 30 % gyroid. Add a modifier over the clip area with
100 % infill and 5–6 perimeters. Brim 5–8 mm for parts 1 and 2. Dry the filament if it is not
fresh. Total material ≈ 400 g.

Do not use modelled supports — let the slicer generate tree/organic supports, restricted to
"touching build plate" so nothing grows inside the duct. Z gap 0.2 mm.
For Part 1 set **Support Overhang Angle = 46°**: the Creality default (45°) flags a strip of the
inner duct wall that is exactly at 45° and a branch grows into the duct through the mouth; at 46°
the outer underside (45–50°) and the clip teeth are still supported, which also enlarges the
footprint on the bed.

![Print layout](images/print_layout.png)

## Assembly and installation

1. Slide the collar of **Part 2** over **Part 1** (0.15 mm clearance, 10 mm overlap) and bond
   with epoxy or CA glue (acetone does not work on PETG).
2. Slide **Part 3** (bayonet flange) over the Ø63 spigot of Part 2 (0.15 mm radial clearance,
   10 mm overlap) until the conical spigot tip seats on the internal cone. It rotates freely.
3. Cut a rectangular opening in the rear wall of the cross-member bump, apply 1 mm
   double-sided silicone (or VHB) tape to the mouth land, and snap the saddles over the
   hood-seal lip and the clips onto the floor rib.
4. Insert the bellows cuff into the flange with the lugs in the entry grooves, push it down to the
   stop ring and twist counter-clockwise so the lugs move into the windows. Do the same at the
   filter inlet, then rotate the flange to its final position and fix it to the spigot (glue or a
   small screw).

Check hood clearance above the seal lip on the car before final assembly.

## Notes

- The master Fusion file with the engine-bay scan is kept locally and is not published.
- `model/` is the earlier design reference (166 mm mouth, integrated OD 69 socket). The printable
  `parts/` supersede it:
  - Parts 1 and 2 were regenerated from the loft sections with a 160 mm mouth and monotonically
    decreasing widths, the clips were re-fitted to the new walls, and the Part 2 collar (0.15 mm
    clearance, 2 mm wall, 10 mm overlap) and Ø63 spigot were rebuilt. Checked against the
    engine-bay scan: only the intended clip snap / floor contact points (≤ 0.35 mm), Part 2 is clear.
  - Part 3: the first version was too shallow (23 mm instead of 31.5 mm to the cuff stop) and its
    bore (Ø62) was too small for the bellows cuff; rebuilt to the measured OEM flange (Ø64 bore,
    Ø69 lug recesses). Same spigot sleeve and base plane; the rim end is 13 mm closer to the filter
    (≥ 12 mm clearance to the engine-bay scan).
  - Part 3 was rebuilt again from a hand-measured bellows cuff (all diameters +1 mm, wedge lugs
    with a cylindrical outer face), the spigot sleeve shortened from 15 to 10 mm, and the Part 2
    spigot given an internal Ø58 → Ø54 S-taper and a conical tip. Re-checked in the car
    assembly: Part 2 outside is unchanged, the flange rim is at the same position, no interference
    between parts or with the bellows, ≥ 12 mm to the engine-bay scan.
- Dimensions of the OEM flange and bellows come from the scans in `references/` and hand
  measurements; verify fit with a test print of a clip section before printing the full part.
