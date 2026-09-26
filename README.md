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

All STL files are in millimetres.

## Design summary

| Feature | Value |
|---|---|
| Inlet (mouth) | True rectangle 166 × 49 mm, 90° corners, inscribed in the flat rear wall of the cross-member bump |
| Mounting face | Offset 1 mm from the bump wall for 1 mm double-sided silicone tape; flat land ≈ 8 mm all round |
| Inlet edge | 3 mm fillet on the inner edge |
| Wall thickness | 2.5 mm (10 mm at the mouth, tapering) |
| Cross-section | Decreases monotonically from ≈ 34 cm² behind the mouth to 26.4 cm² (Ø58 mm) at the socket; no pinch points |
| Outlet | Bayonet socket, mirror of the OEM filter-inlet flange: OD 69 mm, bore 62 mm → seat Ø59.6 mm, two 30° × 10 mm lug windows, twist-lock counter-clockwise viewed into the filter inlet |
| Socket axis | Tilted 25° down from the filter-inlet axis so the bellows takes part of the bend (gentler S-bend, min. centre-line radius ≈ 83 mm) |
| Clips | 2 snap saddles (26 mm wide) on the hood-seal lip + 3 snap clips (30 mm wide) on the small floor rib; 2 mm root gussets, spring legs 3.3–3.5 mm |

![Side view](images/final_side.png)

![Clips](images/clips_side.png)

## Printing

Tested setup: Creality Ender 3 Pro (220 × 220 × 250 mm), **PETG** 1.75 mm.
PLA/PLA+ is not suitable under the hood (softens at 55–60 °C). PETG is fine at the
cross-member, especially with an external heat-reflective wrap. ASA/ABS or PA-CF are better
if you have an enclosed printer.

| Part | Size (mm) | Orientation (as exported) | Supports |
|---|---|---|---|
| `Part1_mouth_clips` | 148 × 149 × 191 | Standing; clip legs lie along the layers (~5°) for strength | Slicer tree/organic, touching build plate only |
| `Part2_bend_tube` | 122 × 123 × 170 | Spigot end down (round and flat on the bed) | Usually none |
| `Part3_bayonet_flange` | 69 × 69 × 38 | Base down | None (windows bridge) |

Suggested PETG settings: nozzle 240–245 °C, bed 80 °C (glue stick as release layer),
fan 30–40 %, 40–50 mm/s, 4 perimeters, 30 % gyroid. Add a modifier over the clip area with
100 % infill and 5–6 perimeters. Brim 5–8 mm for parts 1 and 2. Dry the filament if it is not
fresh. Total material ≈ 400 g.

Do not use modelled supports — let the slicer generate tree/organic supports, restricted to
"touching build plate" so nothing grows inside the duct. Z gap 0.2 mm.

![Print layout](images/print_layout.png)

## Assembly and installation

1. Slide the collar of **Part 2** over **Part 1** (0.15 mm clearance, 10 mm overlap) and bond
   with epoxy or CA glue (acetone does not work on PETG).
2. Slide **Part 3** (bayonet flange) over the Ø63 spigot of Part 2 (0.15 mm radial clearance,
   15 mm overlap). It rotates freely.
3. Cut a rectangular opening in the rear wall of the cross-member bump, apply 1 mm
   double-sided silicone (or VHB) tape to the mouth land, and snap the saddles over the
   hood-seal lip and the clips onto the floor rib.
4. Insert the bellows into the flange and the filter inlet, twist to lock, then rotate the
   flange to its final position and fix it to the spigot (glue or a small screw).

Check hood clearance above the seal lip on the car before final assembly.

## Notes

- The master Fusion file with the engine-bay scan is kept locally and is not published.
- Dimensions of the OEM flange and bellows come from the scans in `references/` and hand
  measurements; verify fit with a test print of a clip section before printing the full part.
