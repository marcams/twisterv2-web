# Changelog

## v2.1.5 - 2026-11-16

Changes since v2.1.4 (published 2026-11-11).

### Added
- **3MF and OBJ export.** The export dialog (Export 3D) now lets you choose the format: binary STL, 3MF or OBJ (Wavefront). 3MF files declare millimeter units, so slicers import the model at the right scale. The 3MF package is generated locally in the browser with no external libraries. Choosing a format updates the file name extension in the dialog.

### Changed
- Export button and dialog renamed from "Export STL" to "Export 3D" (Ctrl/Cmd+E unchanged).
- **3MF files are DEFLATE-compressed** (about 7x smaller), with automatic fallback to uncompressed when the browser lacks compression support.

### Fixed
- **3MF/OBJ exports no longer report non-manifold edges in slicers.** Duplicate rim vertices from vase-mode cap closing are welded when writing the indexed formats (STL was unaffected: slicers weld it on import).

### Notes and limits
- Vase-mode cap closing applies to all three formats, as it already did for STL.
- Mesh engine, built-in presets and quality parameters are unchanged from v2.1.4. Three.js r128 and the single-file `index.html` setup are unchanged.


## v2.1.4 - 2026-11-11

Changes since v2.1.3 (published 2026-11-09).

### Fixed
- **Preset gallery thumbnails no longer give up after 8 seconds.** A thumbnail still being generated when the 8-second mark passes now keeps running until it finishes, so heavy presets (such as Presets 04 and 05) get their thumbnails.
- **A stuck thumbnail generation is terminated after 60 seconds** before the queue moves on to the next one, so one failed generation no longer delays the rest.
- **Closing the preset gallery cancels the pending thumbnail generation.**
- **A thumbnail-generation error no longer runs heavy synchronous work on the interface thread.** The thumbnail shows the error instead, and the model remains openable from its card.

### Notes and limits
- Mesh engine, built-in presets and quality parameters are unchanged from v2.1.3.

## v2.1.3 - 2026-11-09

Changes since v2.1.2 (published 2026-11-06).

### Added
- **Preset gallery.** The presets menu shows thumbnails generated locally on demand and cached in the browser. Thumbnails appear one by one as they are ready, including right after choosing a preset folder. Only Twister projects are listed when a preset folder is chosen (other JSON files are ignored).
- **Tangent handles in the profile editor.** Spline nodes show draggable in/out tangent handles. Handle lines keep their direction while panning and are clipped at the plot edge. Handle edits support undo/redo, and a node menu command resets a node's tangents to automatic.
- **Tangent handles on the CP splines ("Raio - CP").** With symmetry on, editing one CP's tangent is replicated to the CPs aligned with it in the symmetry group; with symmetry off, only that CP changes.
- **Independent / Linked tangents selector** for each spline node. The link lasts for the session only and is not saved in the project file.
- **Pan and zoom in both 2D editors.** The wheel zooms around the cursor, dragging the background pans, and a Frame button resets the view. Each project tab keeps its own view. Vertical pan follows the drag direction, a pan that starts on the background stays a pan over handles, and the insert-node dialog suggests the height and radius of the clicked point under the current zoom. The Z line moves only when dragged over the line itself.
- **Fine node heights.** Nodes can be inserted at close heights (for example 0.15 mm between 0.10 and 0.20) with "Insert node with values...". Inserting at an occupied height shows a warning and replaces nothing. Overlapping nodes can be chosen from a "Choose node" list.
- **Ten built-in presets:** eight author-supplied presets plus two distinct earlier models (duplicate contents are not repeated).

### Fixed
- The About dialog showed version 2.1.1; it now shows the same version as the title, badge and saved projects.

### Notes and limits
- Project files that contain CP tangents are saved as project format 2. Earlier releases (v2.1.2 and older) refuse to open them. Files without CP tangents keep format 1. Save test projects as new files instead of overwriting originals.
- Touch gestures were checked with emulation. Testing on a physical tablet is planned for a later release.
- Three.js r128 and the single-file `index.html` setup are unchanged.

