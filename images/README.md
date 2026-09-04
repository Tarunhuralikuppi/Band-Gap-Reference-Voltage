# Images Folder

This folder contains real Cadence Virtuoso captures from the BGR project (schematics, testbench, layout, AV/parasitic extraction), plus the post-layout simulation plot.

## Subfolders

### schematics/
- `BGR_schematic_light.png` / `BGR_schematic_dark.png` — Main BGR schematic (PM0–PM5, NM0–NM6, R0–R2), light/dark Cadence themes
- `BGR_testbench_symbol_light.png` / `BGR_testbench_symbol_dark.png` — Testbench wrapping the BGR symbol with a 1.8 V DC source and Va/Vref/Vs probes

### layout/
- `BGR_layout_full_light.png` / `BGR_layout_full_dark.png` — Full chip layout, clean view
- `BGR_layout_labeled_nets.png` — Layout with net names (Va, Vb, Vss, net3, etc.) annotated
- `BGR_layout_view_alt1.png` / `BGR_layout_view_alt2.png` — Additional layout capture passes
- `BGR_layout_av_extraction_light.png` / `BGR_layout_av_extraction_dark.png` — AV (parasitic) extraction view, highlighting extracted RC elements

### simulation_results/
- `post_layout_dc_vref_vs_temp.png` — DC temperature sweep overlay of `/Vref_schematic` vs `/Vref_layout` (post-layout verification plot)

## Still missing (optional)

No dedicated **DRC** "0 errors" report screenshot or **LVS** "netlists match" report screenshot was provided. If you have these, add them as:
- `images/layout/BGR_drc_report.png`
- `images/layout/BGR_lvs_report.png`

They're already referenced and will show up automatically in `README.md` and `layout/layout_verification.md` once added.

## Linking images in README

Images are referenced in README.md using relative paths, for example:
```markdown
![BGR Schematic](images/schematics/BGR_schematic_light.png)
```
