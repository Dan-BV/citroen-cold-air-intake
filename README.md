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
| Outlet | Separate bayonet flange (Part 3) on the Ø63 spigot, matching the OEM filter-inlet flange: OD 71 mm, bore Ø62 (15 mm) → seat Ø59.6 → cuff stop ring Ø56 at 31.5 mm below the rim; two through windows 32° × 11.5 mm (3.5–15 mm below the rim), two 32° entry grooves (to Ø67.4) from the rim down to the windows; twist-lock counter-clockwise viewed into the filter inlet |
| Bellows fit | OEM bellows lugs 15.2 (circumferential) × 10.3 (axial) × 2 mm, lug 27.5 mm from the cuff end, cuff end OD 58 mm; free length ≈ 146 mm, fully compressed ≈ 109 mm. Required length in the car ≈ 143 mm (rim-to-rim 80 mm), so the bellows sits almost free |
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
| `Part3_bayonet_flange` | 71 × 71 × 51 | Base (spigot sleeve) down | None (45° cone under the stop ring, windows bridge ≈ 17 mm) |
| `print/Part3_lock_test` (optional) | 71 × 71 × 20 | Cut face down | None; top 20 mm of Part 3 for a quick bayonet fit check (≈ 21 g, ≈ 1 h) |

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
   15 mm overlap) until the spigot end touches the internal cone. It rotates freely.
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
- `model/` shows the duct with the original integrated socket (OD 69, 38 mm). The printable
  `parts/Part3_bayonet_flange` supersedes it: the first version was too shallow (23 mm instead of
  31.5 mm to the cuff stop) and its entry grooves were too narrow for the 15 mm lugs. The new
  flange sits on the same spigot and base plane; only the rim end grew by 13 mm toward the filter
  (checked against the engine-bay scan, ≥ 13 mm clearance).
- Dimensions of the OEM flange and bellows come from the scans in `references/` and hand
  measurements; verify fit with a test print of a clip section before printing the full part.
