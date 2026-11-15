# KiCad 10 test-point footprints (custom)

This is a separate KiCad footprint library derived from the KiCad project's `TestPoint.pretty` library. Every electrical pad has the KiCad 10 fabrication property `(property pad_prop_testpoint)` set. This property is meaningful for Gerber X2 test-pad metadata and for test-point extraction tools that explicitly inspect pad fabrication properties.

## Source and provenance

- Canonical KiCad footprint library: https://gitlab.com/kicad/libraries/kicad-footprints/-/tree/master/TestPoint.pretty
- KiCad-format mirror used to retrieve the text files: https://github.com/edprojekt/kicad-footprints
- Mirror commit pinned for this import: `4c5561fdc8ef4e8f58b46c7bacb47272625d552e` (October 6, 2026)
- Imported: **57 KiCad 10-format footprints**, **68 electrical pads** tagged as test points.
- Omitted from that mirror: `TestPoint_Pad_2.0x4.0mm.kicad_mod` and `TestPoint_Pad_2.5x4.0mm.kicad_mod`, because both remain in the legacy 2021 footprint syntax and were not verified against the current official KiCad 10 library. The upstream mirror contained 59 footprint files in total.

## Modification scope

For each imported footprint, added `(property pad_prop_testpoint)` inside every electrical `(pad ...)` definition. The modified files were checked by removing that exact inserted property and verifying that their content matched the fetched source. No pad numbering, geometry, layer selection, graphics, UUIDs, 3D-model references or other source data were intentionally altered.

## License and attribution

KiCad official footprint library contributors created the original footprints. See the official upstream repository and its license/attribution information. The KiCad footprint libraries are distributed under **Creative Commons Attribution-ShareAlike 4.0 International (CC BY-SA 4.0)**; these modified footprint files are distributed under the same license: https://creativecommons.org/licenses/by-sa/4.0/.

This is a derivative custom library, not an official upstream KiCad release.

## Installation

In KiCad 10, open **Preferences → Manage Footprint Libraries** and add the existing library directory `TestPoint_Custom.pretty`. Use the distinct nickname `TestPoint_Custom` so it does not shadow KiCad's built-in `TestPoint` library. Choose a global or project-specific entry as appropriate.

Existing PCB footprints are **not** automatically modified by creating or updating library files. Change their library identifier to the custom nickname and carefully review **Tools → Update Footprints from Library** before applying to an existing board. Do not overwrite unique placement/footprint edits without reviewing the changes.

## Validation and limitations

Each footprint was checked for balanced S-expressions and a one-to-one correspondence between pads and test-point properties. The transformation was reversible against source text for all 57 imported files. This is a source-text/structural verification **not** a KiCad parser or GUI open/export test: `kicad-cli` was not available in the execution environment. Visual geometry and fabrication outputs were not independently rendered or tested.
